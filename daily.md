---
layout: page
title: "📝 Daily Sharing"
permalink: /daily/
---
{% assign en = site.data.i18n.en %}
{% assign zh = site.data.i18n.zh %}

<div style="text-align:center;padding:60px 20px;border:2px dashed #ddd;border-radius:12px;background:#fafafa;margin-bottom:24px">
  <div style="font-size:64px;margin-bottom:16px">📝</div>
  <h2><span data-en="Content Coming Soon" data-zh="内容即将上线">Content Coming Soon</span></h2>
  <p style="color:#888" data-en="{{ en.daily.placeholder }}" data-zh="{{ zh.daily.placeholder }}">{{ en.daily.placeholder }}</p>
</div>

<div style="display:flex;flex-wrap:wrap;gap:20px">
{% for i in (0..2) %}
{% assign cardEn = en.daily.cards[i] %}
{% assign cardZh = zh.daily.cards[i] %}
  <div style="flex:1;min-width:200px;text-align:center;padding:40px 20px;background:#fff;border:1px solid #ddd;border-radius:8px">
    <div style="font-size:40px;margin-bottom:12px">{{ cardEn.icon }}</div>
    <h3 style="font-size:16px" data-en="{{ cardEn.title }}" data-zh="{{ cardZh.title }}">{{ cardEn.title }}</h3>
    <p style="font-size:13px;color:#888;margin-top:6px" data-en="Coming soon" data-zh="即将更新">Coming soon</p>
  </div>
{% endfor %}
</div>
