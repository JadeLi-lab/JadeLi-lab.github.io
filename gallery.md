---
layout: page
title: "🎥 Research Gallery"
permalink: /gallery/
---

<div style="text-align:center;padding:60px 20px;border:2px dashed #ddd;border-radius:12px;background:#fafafa;margin-bottom:24px">
  <div style="font-size:64px;margin-bottom:16px">🎬</div>
  <h2>Research Gallery</h2>
  <p style="color:#888">Research demonstrations, videos, and experimental results will be displayed here.</p>
</div>

<div style="display:flex;flex-wrap:wrap;gap:20px">
{% assign items = "UAV Swarm Experiment,Cascading Failure Simulation,IBR Grid Integration" | split: "," %}
{% for item in items %}
  <div style="flex:1;min-width:200px;text-align:center;padding:40px 20px;background:#fff;border:1px solid #ddd;border-radius:8px">
    <div style="font-size:48px;margin-bottom:12px">📹</div>
    <h3 style="font-size:16px">{{ item }}</h3>
    <p style="font-size:13px;color:#888;margin-top:6px">Video / Demo coming soon</p>
  </div>
{% endfor %}
</div>
