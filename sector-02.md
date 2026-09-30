---
layout: default
title: "Sector 02: Archive Records"
permalink: /sector-02/
---

<h3 style="color: #ff3344; font-family: var(--font-mono); letter-spacing: 1px; border-bottom: 1px solid rgba(255,255,255,0.1); padding-bottom: 10px; margin-bottom: 25px; margin-top: 20px;">
  > SECTOR 02 // ARCHIVE RECORDS
</h3>
<a href="{{ '/wuwa-theory/' | relative_url }}" style="color: var(--text-secondary); text-decoration: none; font-family: var(--font-mono); font-size: 0.8em;">[ <- RETURN TO MAIN DIRECTORY ]</a>

<div class="archive-list" style="margin-top: 25px;">
  {% assign wuwa_posts = site.posts | where_exp: "item", "item.categories contains 'wuwa-theory'" %}
  {% assign count = 0 %}
  
  {% for post in wuwa_posts %}
    {% assign downcased_tags = post.tags | join: " " | downcase %}
    <!-- Lọc: Bắt buộc phải có tag archive_record -->
    {% if downcased_tags contains 'archive_record' %}
      {% assign count = count | plus: 1 %}
      <div style="padding: 14px 16px; margin-bottom: 12px; background: rgba(255,255,255,0.02); border: 1px solid var(--border-color); border-left: 2px solid #ff3344; transition: all 0.3s ease;">
        <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 8px;">
          <span style="font-family: var(--font-mono); font-size: 0.78em; color: var(--text-secondary);">LOG_{{ post.date | date: "%Y%m%d" }}</span>
          <span style="font-family: var(--font-mono); font-size: 0.78em; color: #ff3344; font-weight: bold;">// ARCHIVE RECORD</span>
        </div>
        <h3 style="margin: 0 0 6px 0; font-size: 1.1em; text-transform: uppercase;">
          <a href="{{ post.url | relative_url }}" style="color: #ffffff; text-decoration: none;">{{ post.title }}</a>
        </h3>
      </div>
    {% endif %}
  {% endfor %}

  {% if count == 0 %}
    <p style="font-family: var(--font-mono); font-size: 0.85em; color: var(--text-secondary);">[NO LOGS REGISTERED IN SECTOR 02]</p>
  {% endif %}
</div>
