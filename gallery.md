---
layout: page
title: "🎥 Research Gallery"
permalink: /gallery/
---
{% assign en = site.data.i18n.en %}
{% assign zh = site.data.i18n.zh %}

<p data-en="Research demonstrations, videos, and experimental results will be displayed here." data-zh="研究演示、视频及实验结果将在此展示。">{{ en.gallery.placeholder }}</p>

<div style="display:flex;flex-wrap:wrap;gap:20px;margin-top:8px">
{% assign itemsEn = "UAV Swarm Experiment,Cascading Failure Simulation,IBR Grid Integration" | split: "," %}
{% assign itemsZh = "无人机集群实验,级联故障仿真,IBR电网集成" | split: "," %}
{% for item in itemsEn %}
  <div style="flex:1;min-width:230px;background:#fff;border:1px solid #ddd;border-radius:8px;padding:36px 24px;text-align:center;box-shadow:0 1px 3px rgba(0,0,0,0.06)">
    <div style="font-size:44px;margin-bottom:14px">📹</div>
    <h3 style="font-size:16px;color:#000;margin-bottom:8px" data-en="{{ item }}" data-zh="{{ itemsZh[forloop.index0] }}">{{ item }}</h3>
    <p style="font-size:13px;color:#888" data-en="Video / Demo coming soon" data-zh="视频/演示即将上线">Video / Demo coming soon</p>
  </div>
{% endfor %}
</div>
