---
layout: page
title: "🌐 Vibe Coding Works"
permalink: /vibecoding/
---
{% assign en = site.data.i18n.en %}
{% assign zh = site.data.i18n.zh %}
{% assign vEn = en.vibecoding %}
{% assign vZh = zh.vibecoding %}

<a href="{{ vEn.aiMapLink }}" target="_blank" rel="noopener" style="display:block;text-decoration:none;color:inherit;background:#fff;border:1px solid #ddd;border-radius:8px;overflow:hidden;transition:all 0.3s" onmouseenter="this.style.boxShadow='0 8px 30px rgba(0,0,0,0.12)'" onmouseleave="this.style.boxShadow='none'">

  <div style="background:linear-gradient(135deg,#0a0e17 0%,#111827 40%,#1a1040 70%,#0c0e1a 100%);padding:40px 32px;position:relative;min-height:260px;display:flex;align-items:center;justify-content:center;border-bottom:1px solid #1e293b">

    <div style="position:absolute;top:30px;left:40px;width:56px;height:56px;border-radius:50%;background:radial-gradient(circle,#10a37f,#10a37f44);opacity:0.8"></div>
    <div style="position:absolute;top:70px;left:170px;width:46px;height:46px;border-radius:50%;background:radial-gradient(circle,#d97706,#d9770644);opacity:0.8"></div>
    <div style="position:absolute;top:45px;right:110px;width:50px;height:50px;border-radius:50%;background:radial-gradient(circle,#4285f4,#4285f444);opacity:0.8"></div>
    <div style="position:absolute;bottom:55px;right:70px;width:44px;height:44px;border-radius:50%;background:radial-gradient(circle,#76b900,#76b90044);opacity:0.8"></div>
    <div style="position:absolute;bottom:35px;left:110px;width:48px;height:48px;border-radius:50%;background:radial-gradient(circle,#ff9900,#ff990044);opacity:0.8"></div>
    <div style="position:absolute;top:130px;right:190px;width:40px;height:40px;border-radius:50%;background:radial-gradient(circle,#0668e1,#0668e144);opacity:0.8"></div>
    <div style="position:absolute;bottom:90px;left:290px;width:42px;height:42px;border-radius:50%;background:radial-gradient(circle,#00a4ef,#00a4ef44);opacity:0.8"></div>

    <svg style="position:absolute;inset:0;width:100%;height:100%">
      <line x1="68" y1="58" x2="193" y2="93" stroke="#22d3ee33" stroke-width="2" />
      <line x1="193" y1="93" x2="340" y2="70" stroke="#f0c06033" stroke-width="1.5" />
      <line x1="340" y1="70" x2="450" y2="160" stroke="#22d3ee33" stroke-width="2" />
      <line x1="68" y1="58" x2="134" y2="225" stroke="#f8717133" stroke-width="1.5" stroke-dasharray="6,4" />
      <line x1="340" y1="70" x2="470" y2="240" stroke="#22d3ee33" stroke-width="2" />
      <line x1="134" y1="225" x2="311" y2="245" stroke="#a78bfa33" stroke-width="1.5" />
      <line x1="311" y1="245" x2="450" y2="240" stroke="#22d3ee33" stroke-width="2" />
    </svg>

    <div style="position:relative;z-index:2;text-align:center;background:rgba(10,14,23,0.85);border-radius:16px;padding:24px 36px;backdrop-filter:blur(8px)">
      <div style="font-size:44px;margin-bottom:6px">🕸️</div>
      <h2 style="font-size:26px;font-weight:900;color:#fff;margin:0" data-en="{{ vEn.aiMapTitle }}" data-zh="{{ vZh.aiMapTitle }}">{{ vEn.aiMapTitle }}</h2>
      <p style="font-size:14px;color:#22d3ee;font-weight:500;margin:4px 0 0" data-en="{{ vEn.aiMapSub }}" data-zh="{{ vZh.aiMapSub }}">{{ vEn.aiMapSub }}</p>
    </div>
  </div>

  <div style="padding:24px 28px">
    <p style="font-size:14px;color:#555;line-height:1.7;margin-bottom:14px" data-en="{{ vEn.aiMapDesc }}" data-zh="{{ vZh.aiMapDesc }}">{{ vEn.aiMapDesc }}</p>
    <div style="display:flex;gap:8px;flex-wrap:wrap;margin-bottom:16px">
      {% for tag in vEn.techTags %}
      <span style="font-size:12px;background:#e8f0fe;color:#1967d2;padding:4px 10px;border-radius:10px;font-weight:600">{{ tag }}</span>
      {% endfor %}
    </div>
    <div style="display:inline-flex;align-items:center;gap:8px;color:#4d90fe;font-weight:700;font-size:14px;padding:10px 20px;background:#e8f0fe;border-radius:6px">
      <span data-en="{{ vEn.aiMapCTAText }}" data-zh="{{ vZh.aiMapCTAText }}">{{ vEn.aiMapCTAText }}</span>
    </div>
  </div>
</a>
