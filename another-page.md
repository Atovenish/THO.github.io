---
layout: default
title: "Wuthering Waves Theory"
---

## // 03. WUTHERING WAVE THEORY
> *"Phân tích thế giới quan Solaris-3, giải mã Tacet Discords, Resonator Fortes và hệ thống vũ trụ học."*

<div class="archive-list" style="margin-top: 25px;">
{% assign wuwa_posts = site.posts | where_exp: "item", "item.categories contains 'wuwa-theory'" %}
{% for post in wuwa_posts %}
  <div style="padding: 14px 16px; margin-bottom: 12px; background: rgba(255,255,255,0.02); border-left: 2px solid var(--accent-tho); border-top: 1px solid var(--border-color); border-right: 1px solid var(--border-color); border-bottom: 1px solid var(--border-color);">
    <span style="font-family: var(--font-mono); font-size: 0.78em; color: var(--accent-tho);">LOG_{{ post.date | date: "%Y%m%d" }} // {{ post.date | date: "%d/%m/%Y" }}</span>
    <h3 style="margin: 6px 0; font-size: 1.1em;"><a href="{{ post.url | relative_url }}" style="color: #ffffff; text-decoration: none;">{{ post.title }}</a></h3>
    {% if post.description %}
      <p style="font-size: 0.85em; color: var(--text-secondary); margin: 0;">{{ post.description }}</p>
    {% endif %}
  </div>
{% else %}
  <p style="font-family: var(--font-mono); font-size: 0.85em; color: var(--text-secondary);">[NO LOGS REGISTERED IN SECTOR 03]</p>
{% endfor %}
</div>
