---
layout: page
title: "📝 Daily Sharing"
permalink: /daily/
---

<div style="text-align:center;padding:60px 20px;border:2px dashed #ddd;border-radius:12px;background:#fafafa;margin-bottom:24px">
  <div style="font-size:64px;margin-bottom:16px">📝</div>
  <h2>Content Coming Soon</h2>
  <p style="color:#888">Research musings, technical notes, and inspirations will be shared here.</p>
</div>

<div style="display:flex;flex-wrap:wrap;gap:20px">
{% assign cards = "Research Methodology,Life Off the Grid,Tech Trends" | split: "," %}
{% assign icons = "🔬,🌸,🔭" | split: "," %}
{% for card in cards %}
{% assign idx = forloop.index0 %}
  <div style="flex:1;min-width:200px;text-align:center;padding:40px 20px;background:#fff;border:1px solid #ddd;border-radius:8px">
    <div style="font-size:40px;margin-bottom:12px">{{ icons[idx] }}</div>
    <h3 style="font-size:16px">{{ card }}</h3>
    <p style="font-size:13px;color:#888;margin-top:6px">Coming soon</p>
  </div>
{% endfor %}
</div>
