---
layout: page
title: "📝 Daily Sharing"
permalink: /daily/
---
{% assign en = site.data.i18n.en %}
{% assign zh = site.data.i18n.zh %}

<p data-en="Research thoughts, tech notes, and inspirations." data-zh="科研随想、技术笔记与灵感分享。">{{ en.daily.subtitle }}</p>

<div style="display:flex;flex-wrap:wrap;gap:20px;margin-top:8px">
{% for i in (0..2) %}
{% assign cardEn = en.daily.cards[i] %}
{% assign cardZh = zh.daily.cards[i] %}
  <div style="flex:1;min-width:230px;background:#fff;border:1px solid #ddd;border-radius:8px;padding:36px 24px;text-align:center;box-shadow:0 1px 3px rgba(0,0,0,0.06)">
    <div style="font-size:40px;margin-bottom:14px">{{ cardEn.icon }}</div>
    <h3 style="font-size:16px;color:#000;margin-bottom:8px" data-en="{{ cardEn.title }}" data-zh="{{ cardZh.title }}">{{ cardEn.title }}</h3>
    <p style="font-size:13px;color:#888" data-en="Coming soon" data-zh="即将更新">Coming soon</p>
  </div>
{% endfor %}
</div>
