---
layout: page
title: "🎥 Research Gallery"
permalink: /gallery/
---
{% assign en = site.data.i18n.en %}
{% assign zh = site.data.i18n.zh %}

<div style="text-align:center;padding:60px 20px;border:2px dashed #ddd;border-radius:12px;background:#fafafa;margin-bottom:24px">
  <div style="font-size:64px;margin-bottom:16px">🎬</div>
  <h2 data-en="{{ en.gallery.title }}" data-zh="{{ zh.gallery.title }}">{{ en.gallery.title }}</h2>
  <p style="color:#888" data-en="{{ en.gallery.placeholder }}" data-zh="{{ zh.gallery.placeholder }}">{{ en.gallery.placeholder }}</p>
</div>

<div style="display:flex;flex-wrap:wrap;gap:20px">
{% assign itemsEn = "UAV Swarm Experiment,Cascading Failure Simulation,IBR Grid Integration" | split: "," %}
{% assign itemsZh = "无人机集群实验,级联故障仿真,IBR电网集成" | split: "," %}
{% for item in itemsEn %}
  <div style="flex:1;min-width:200px;text-align:center;padding:40px 20px;background:#fff;border:1px solid #ddd;border-radius:8px">
    <div style="font-size:48px;margin-bottom:12px">📹</div>
    <h3 style="font-size:16px" data-en="{{ item }}" data-zh="{{ itemsZh[forloop.index0] }}">{{ item }}</h3>
    <p style="font-size:13px;color:#888;margin-top:6px" data-en="Video / Demo coming soon" data-zh="视频/演示即将上线">Video / Demo coming soon</p>
  </div>
{% endfor %}
</div>
