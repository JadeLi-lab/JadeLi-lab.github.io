---
layout: page
title: "🔬 Research Directions"
permalink: /research/
---
{% assign enDir = site.data.i18n.en.directions %}
{% assign zhDir = site.data.i18n.zh.directions %}
{% assign dKeys = "d1,d2,d3" | split: "," %}
{% assign colors = "#4d90fe,#9b59b6,#2ecc71" | split: "," %}

{% for dk in dKeys %}
{% assign i = forloop.index0 %}
{% assign d = enDir[dk] %}
{% assign dz = zhDir[dk] %}
{% assign dirNum = i | plus: 1 %}
{% assign dirPubs = site.data.pubs | where_exp: "pub", "pub.direction == dirNum" | sort: "year" | reverse %}

<h2 style="color:{{ colors[i] }};border-bottom:3px solid {{ colors[i] }};padding-bottom:8px;margin-top:32px">
  <span style="background:{{ colors[i] }};color:#fff;padding:6px 14px;border-radius:6px;margin-right:12px">{{ dirNum }}</span>
  {{ d.title }}
</h2>
<p style="color:#666;font-weight:600">{{ d.subtitle }}</p>

<div style="background:#fff;border:1px solid #ddd;border-radius:6px;padding:20px;margin:16px 0">
  <h3>📋 Research Content</h3>
  <p style="line-height:1.9;color:#555">{{ d.content }}</p>
</div>

<div style="background:#fffef0;border:1px solid #e6d88a;border-left:4px solid #d69e2e;border-radius:6px;padding:20px;margin:16px 0">
  <h3 style="color:#d69e2e">💡 Core Innovation</h3>
  <p style="line-height:1.9;color:#744210">{{ d.innovation }}</p>
</div>

<div style="background:#fff;border:1px solid #ddd;border-radius:6px;padding:20px;margin:16px 0">
  <h3 style="color:#2ecc71">📄 Related Publications ({{ dirPubs | size }})</h3>
  {% for pub in dirPubs %}
  <div style="padding:12px 0;border-bottom:1px solid #eee;display:flex;gap:14px;align-items:flex-start">
    <span style="background:{{ colors[i] }};color:#fff;border-radius:6px;padding:3px 10px;font-size:12px;font-weight:700;flex-shrink:0;margin-top:3px">{{ pub.year }}</span>
    <div>
      <div style="font-weight:700;font-size:15px">{{ pub.title }}</div>
      <div style="font-size:12px;color:#888">{{ pub.journal }} · DOI: {{ pub.doi }}</div>
    </div>
  </div>
  {% endfor %}
</div>
{% endfor %}
