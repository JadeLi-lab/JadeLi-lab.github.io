---
layout: page
title: "📄 Publications"
echarts: true
permalink: /publications/
---
{% assign pubs = site.data.pubs %}
{% assign en = site.data.i18n.en %}
{% assign zh = site.data.i18n.zh %}

<p><span data-en="{{ pubs | size }} publications · 2023–2026" data-zh="{{ pubs | size }} 篇论文 · 2023–2026">{{ pubs | size }} publications · 2023–2026</span></p>

<!-- Filter Bar -->
<div style="display:flex;gap:8px;flex-wrap:wrap;margin-bottom:20px;align-items:center">
  <input type="text" id="pubSearch"
    data-en-placeholder="Search title, keyword..."
    data-zh-placeholder="搜索标题、关键词..."
    placeholder="Search title, keyword..."
    style="flex:1;min-width:180px;padding:10px 16px;border:1px solid #ddd;border-radius:6px;font-size:14px"
    oninput="filterPubs()" />
  <button class="filter-btn active" data-filter="0" onclick="setFilter(0, this)" style="padding:10px 18px;border:1px solid #ddd;border-radius:6px;background:#4d90fe;color:#fff;cursor:pointer;font-size:14px" data-en="All" data-zh="全部">All</button>
  <button class="filter-btn" data-filter="1" onclick="setFilter(1, this)" style="padding:10px 18px;border:1px solid #ddd;border-radius:6px;background:#fff;cursor:pointer;font-size:14px">Dir 1</button>
  <button class="filter-btn" data-filter="2" onclick="setFilter(2, this)" style="padding:10px 18px;border:1px solid #ddd;border-radius:6px;background:#fff;cursor:pointer;font-size:14px">Dir 2</button>
  <button class="filter-btn" data-filter="3" onclick="setFilter(3, this)" style="padding:10px 18px;border:1px solid #ddd;border-radius:6px;background:#fff;cursor:pointer;font-size:14px">Dir 3</button>
  <button id="viewToggleBtn" onclick="toggleView()" style="padding:10px 18px;border:1px solid #4d90fe;border-radius:6px;background:#4d90fe;color:#fff;cursor:pointer;font-size:14px"
    data-en="View Graph" data-zh="查看关系图">View Graph</button>
</div>

<!-- List View -->
<div id="listView">
{% for pub in pubs %}{% if pub.id %}
<div class="pub-item" data-dir="{{ pub.direction }}"
     data-search="{{ pub.title | downcase }} {{ pub.titleCN | downcase }} {{ pub.journal | downcase }} {% for k in pub.keywords %}{{ k | downcase }} {% endfor %}"
     style="background:#fff;border:1px solid #ddd;border-radius:8px;padding:20px 24px;margin-bottom:12px;cursor:pointer;transition:all 0.2s"
     onclick="showPaperForPub({{ pub.id }})"
     onmouseenter="this.style.borderColor='#4d90fe';this.style.boxShadow='0 2px 8px rgba(0,0,0,0.1)'"
     onmouseleave="this.style.borderColor='#ddd';this.style.boxShadow='none'">
  <span style="display:inline-block;padding:3px 12px;border-radius:10px;font-size:12px;font-weight:700;color:#fff;background:#4d90fe;margin-right:8px">{{ pub.year }}</span>
  <span style="font-size:12px;color:#888">{{ pub.journal }}</span>
  <h3 style="margin:6px 0;font-size:16px;color:#333" data-en="{{ pub.title }}" data-zh="{{ pub.titleCN }}">{{ pub.title }}</h3>
  <div style="font-size:12px;color:#4d90fe;margin-bottom:8px">DOI: {{ pub.doi }}</div>
  <div style="padding:8px 12px;background:#f0fff4;border-left:3px solid #2ecc71;border-radius:4px;font-size:13px;color:#22543d;margin-bottom:8px" data-en="{{ pub.highlight }}" data-zh="{{ pub.highlightCN }}">{{ pub.highlight }}</div>
  <div style="display:flex;flex-wrap:wrap;gap:4px">
    {% for k in pub.keywords %}
    <span style="font-size:11px;background:#e8f0fe;color:#1967d2;padding:2px 8px;border-radius:10px;font-weight:600">{{ k }}</span>
    {% endfor %}
  </div>
</div>
{% endif %}{% endfor %}
</div>

<!-- Graph View -->
<div id="graphView" style="display:none">
  <div id="pubGraphChart" style="height:620px;width:100%;background:#fff;border:1px solid #ddd;border-radius:8px;padding:16px"></div>
  <p style="text-align:center;color:#888;font-size:13px;margin-top:8px"
     data-en="Drag nodes · Scroll to zoom · Click node for details"
     data-zh="拖拽节点 · 滚轮缩放 · 点击节点查看详情">Drag nodes · Scroll to zoom · Click node for details</p>
</div>

<!-- Modal -->
<div id="pubModal" style="display:none;position:fixed;inset:0;background:rgba(0,0,0,0.5);z-index:1000;align-items:center;justify-content:center" onclick="this.style.display='none'">
  <div style="background:#fff;border-radius:8px;padding:32px;max-width:680px;max-height:85vh;overflow-y:auto;width:90%;position:relative" onclick="event.stopPropagation()">
    <button onclick="document.getElementById('pubModal').style.display='none'" style="position:absolute;top:12px;right:12px;width:32px;height:32px;border-radius:50%;border:1px solid #ddd;background:#fff;font-size:16px;cursor:pointer">✕</button>
    <span id="pubModalYear" style="display:inline-block;padding:3px 12px;border-radius:10px;font-size:12px;font-weight:700;color:#fff;background:#4d90fe"></span>
    <span id="pubModalJournal" style="font-size:12px;color:#888;margin-left:8px"></span>
    <h3 id="pubModalTitle" style="margin-top:12px;font-size:1.2em;color:#333"></h3>
    <div style="font-size:13px;color:#888;margin-bottom:12px">DOI: <a id="pubModalDOI" href="#" target="_blank"></a></div>
    <div id="pubModalHighlight" style="padding:10px 14px;background:#f0fff4;border-left:3px solid #2ecc71;border-radius:4px;font-size:13px;color:#22543d;margin-bottom:12px"></div>
    <div id="pubModalAbstract" style="font-size:14px;line-height:1.8;color:#555"></div>
    <div id="pubModalKeywords" style="margin-top:12px;display:flex;flex-wrap:wrap;gap:4px"></div>
    <h4 style="margin-top:20px;color:#888" data-en="🔗 Related Papers" data-zh="🔗 相关论文">🔗 Related Papers</h4>
    <div id="pubModalRelated"></div>
  </div>
</div>

<script>
var publications = [
{% for pub in site.data.pubs %}{% if pub.id %}
  {id:{{pub.id}},title:"{{pub.title|escape}}",titleCN:"{{pub.titleCN|escape}}",journal:"{{pub.journal|escape}}",year:{{pub.year}},doi:"{{pub.doi}}",
   keywords:[{%for k in pub.keywords%}"{{k|escape}}"{%unless forloop.last%},{%endunless%}{%endfor%}],
   keywordsCN:[{%for kc in pub.keywordsCN%}"{{kc|escape}}"{%unless forloop.last%},{%endunless%}{%endfor%}],
   direction:{{pub.direction}},highlight:"{{pub.highlight|escape}}",highlightCN:"{{pub.highlightCN|escape}}",
   abstract:"{{pub.abstract|escape}}",abstractCN:"{{pub.abstractCN|escape}}"}{%unless forloop.last%},{%endunless%}
{%endif%}{%endfor%}];

var paperRelations = [
{%for rel in site.data.paper_relations%}
  {source:{{rel.source}},target:{{rel.target}},label:"{{rel.label|escape}}",labelCN:"{{rel.labelCN|escape}}"}{%unless forloop.last%},{%endunless%}
{%endfor%}];

var currentFilter = 0, isListView = true;

function filterPubs() {
  var s = document.getElementById('pubSearch').value.toLowerCase();
  document.querySelectorAll('#listView .pub-item').forEach(function(el) {
    var dir = parseInt(el.getAttribute('data-dir'));
    var txt = el.getAttribute('data-search') || '';
    el.style.display = (currentFilter === 0 || dir === currentFilter) && (!s || txt.indexOf(s) !== -1) ? '' : 'none';
  });
}

function setFilter(f, btn) {
  currentFilter = f;
  document.querySelectorAll('.filter-btn').forEach(function(b) { b.classList.remove('active'); b.style.background='#fff'; b.style.color='#333'; });
  btn.classList.add('active'); btn.style.background='#4d90fe'; btn.style.color='#fff';
  filterPubs();
}

function toggleView() {
  isListView = !isListView;
  document.getElementById('listView').style.display = isListView ? '' : 'none';
  document.getElementById('graphView').style.display = isListView ? 'none' : '';
  var btn = document.getElementById('viewToggleBtn');
  btn.textContent = isListView ? (isEn ? 'View Graph' : '查看关系图') : (isEn ? 'View List' : '查看列表');
  if (!isListView) setTimeout(renderPubGraph, 200);
}

function renderPubGraph() {
  var dom = document.getElementById('pubGraphChart');
  if (!dom) return; if (dom._echart) dom._echart.dispose();
  var chart = echarts.init(dom);
  var nodes = publications.map(function(p) {
    return {id:p.id,name:p.id+'. '+(isEn?p.title:p.titleCN).slice(0,55)+'...',symbolSize:38,category:p.direction-1,label:{show:true,fontSize:11,color:'#333'},data:p};
  });
  var links = paperRelations.map(function(r) {
    return {source:r.source,target:r.target,label:{show:true,formatter:isEn?r.label:r.labelCN,fontSize:10,color:'#888'}};
  });
  var cats = isEn ? ['Dir 1: Complex Systems','Dir 2: CPS Resilience','Dir 3: UAV Swarms'] : ['方向一：复杂系统建模','方向二：CPS韧性','方向三：无人集群'];
  chart.setOption({
    tooltip:{formatter:function(p){if(p.dataType==='node'){var d=p.data.data;return'<strong>'+(isEn?d.title:d.titleCN)+'</strong><br/>'+d.journal+' ('+d.year+')<br/>'+(isEn?d.highlight:d.highlightCN)}return''}},
    legend:{data:cats,bottom:10,textStyle:{color:'#888',fontSize:12}},
    series:[{type:'graph',layout:'force',force:{repulsion:500,gravity:0.1,edgeLength:[150,320]},roam:true,draggable:true,data:nodes,links:links,
      categories:[{name:cats[0],itemStyle:{color:'#4d90fe'}},{name:cats[1],itemStyle:{color:'#9b59b6'}},{name:cats[2],itemStyle:{color:'#2ecc71'}}],
      emphasis:{focus:'adjacency',lineStyle:{width:4}},lineStyle:{color:'#ddd',curveness:0.3,opacity:0.7}}]
  });
  chart.on('click',function(p){if(p.dataType==='node')showPaperModal(p.data.data,isEn)});
  dom._echart = chart;
}

function showPaperForPub(id) { var p = publications.find(function(x){return x.id===id}); if(p) showPaperModal(p, isEn); }

function showPaperModal(p, enVal) {
  document.getElementById('pubModalYear').textContent = p.year;
  document.getElementById('pubModalJournal').textContent = p.journal;
  document.getElementById('pubModalTitle').textContent = enVal ? p.title : p.titleCN;
  var d = document.getElementById('pubModalDOI'); d.textContent = p.doi; d.href = 'https://doi.org/' + p.doi;
  document.getElementById('pubModalHighlight').innerHTML = '<strong>💡 ' + (enVal ? 'Core Highlight' : '核心亮点') + '：</strong>' + (enVal ? p.highlight : p.highlightCN);
  document.getElementById('pubModalAbstract').innerHTML = '<strong>' + (enVal ? 'Abstract' : '摘要') + '：</strong>' + (enVal ? p.abstract : p.abstractCN);
  var kw = document.getElementById('pubModalKeywords'); kw.innerHTML = '';
  (enVal ? p.keywords : p.keywordsCN).forEach(function(k) {
    var s = document.createElement('span');
    s.style.cssText = 'display:inline-block;padding:3px 10px;border-radius:12px;font-size:11px;font-weight:600;background:#e8f0fe;color:#1967d2;margin:2px';
    s.textContent = k; kw.appendChild(s);
  });
  var relDiv = document.getElementById('pubModalRelated'); relDiv.innerHTML = '';
  paperRelations.filter(function(r){return r.source===p.id||r.target===p.id}).forEach(function(r) {
    var oid = r.source===p.id ? r.target : r.source;
    var o = publications.find(function(x){return x.id===oid});
    if (!o) return;
    var div = document.createElement('div');
    div.style.cssText = 'padding:10px 14px;background:#f7fafc;border-radius:6px;margin-bottom:6px;font-size:13px;cursor:pointer;border:1px solid #e2e8f0';
    div.innerHTML = '<span style="color:#4d90fe;font-weight:600">' + (enVal ? r.label : r.labelCN) + '</span><div style="font-size:12px;color:#888;margin-top:2px">→ [' + o.id + '] ' + (enVal ? o.title : o.titleCN).slice(0,70) + '...</div>';
    div.onclick = function(ev) { ev.stopPropagation(); showPaperModal(o, enVal); };
    relDiv.appendChild(div);
  });
  document.getElementById('pubModal').style.display = 'flex';
}

function onLangChange(enVal) {
  isEn = enVal;
  var btn = document.getElementById('viewToggleBtn');
  if (btn) btn.textContent = isListView ? (enVal ? 'View Graph' : '查看关系图') : (enVal ? 'View List' : '查看列表');
  var dom = document.getElementById('pubGraphChart');
  if (dom && dom._echart) renderPubGraph();
}
</script>
