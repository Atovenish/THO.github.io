---
layout: default
title: "Wuthering Waves Theory"
---

## // 03. WUTHERING WAVE THEORY
> *"Phân tích thế giới quan Solaris-3, giải mã Tacet Discords, Resonator Fortes và hệ thống vũ trụ học."*

{% assign wuwa_posts = site.posts | where_exp: "item", "item.categories contains 'wuwa-theory'" %}

<div class="archive-list" style="margin-top: 25px;">

  <!-- ==========================================
       SECTOR 01 // WORLD COSMOLOGY & LORE 
       ========================================== -->
  <div class="sector-block" style="margin-bottom: 40px;">
    <h3 style="color: var(--accent-tho); font-family: var(--font-mono); letter-spacing: 1px; border-bottom: 1px solid rgba(255,255,255,0.1); padding-bottom: 10px; margin-bottom: 20px;">
      > SECTOR 01 // WORLD COSMOLOGY & LORE
    </h3>
    
    {% assign sector1_count = 0 %}
    {% for post in wuwa_posts %}
      {% if post.layout == 'post' or post.layout == 'slide_theory' %}
        {% assign sector1_count = sector1_count | plus: 1 %}
        <div style="padding: 14px 16px; margin-bottom: 12px; background: rgba(255,255,255,0.02); border-left: 2px solid var(--accent-tho); border-top: 1px solid var(--border-color); border-right: 1px solid var(--border-color); border-bottom: 1px solid var(--border-color); transition: all 0.3s ease;">
          
          <!-- Thanh Meta Data & Tags -->
          <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 8px;">
            <span style="font-family: var(--font-mono); font-size: 0.78em; color: var(--accent-tho);">LOG_{{ post.date | date: "%Y%m%d" }} // {{ post.date | date: "%d/%m/%Y" }}</span>
            <span style="font-family: var(--font-mono); font-size: 0.78em; color: #facc15; font-weight: bold; text-shadow: 0 0 5px rgba(250, 204, 21, 0.4);">// LORE_THEORY</span>
          </div>
          
          <h3 style="margin: 0 0 6px 0; font-size: 1.1em; text-transform: uppercase;">
            <a href="{{ post.url | relative_url }}" style="color: #ffffff; text-decoration: none;">{{ post.title }}</a>
          </h3>
          
          {% if post.description %}
            <p style="font-size: 0.85em; color: var(--text-secondary); margin: 0;">{{ post.description }}</p>
          {% endif %}
        </div>
      {% endif %}
    {% endfor %}
    
    {% if sector1_count == 0 %}
      <p style="font-family: var(--font-mono); font-size: 0.85em; color: var(--text-secondary);">[NO LOGS REGISTERED IN SECTOR 01]</p>
    {% endif %}
  </div>

  <!-- ==========================================
       SECTOR 02 // RESONATOR DOSSIERS 
       ========================================== -->
  <div class="sector-block">
    <h3 style="color: #ff3344; font-family: var(--font-mono); letter-spacing: 1px; border-bottom: 1px solid rgba(255,255,255,0.1); padding-bottom: 10px; margin-bottom: 20px;">
      > SECTOR 02 // RESONATOR DOSSIERS
    </h3>

    {% assign sector2_count = 0 %}
    {% for post in wuwa_posts %}
      {% if post.layout == 'resonator' %}
        {% assign sector2_count = sector2_count | plus: 1 %}
        <!-- Viền trái đổi thành Đỏ -->
        <div style="padding: 14px 16px; margin-bottom: 12px; background: rgba(255,255,255,0.02); border-left: 2px solid #ff3344; border-top: 1px solid var(--border-color); border-right: 1px solid var(--border-color); border-bottom: 1px solid var(--border-color); transition: all 0.3s ease;">
          
          <!-- Thanh Meta Data & Tags -->
          <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 8px;">
            <span style="font-family: var(--font-mono); font-size: 0.78em; color: var(--text-secondary);">LOG_{{ post.date | date: "%Y%m%d" }} // {{ post.date | date: "%d/%m/%Y" }}</span>
            <span style="font-family: var(--font-mono); font-size: 0.78em; color: #ff3344; font-weight: bold; text-shadow: 0 0 5px rgba(255, 51, 68, 0.4);">// ARCHIVE RECORD</span>
          </div>
          
          <h3 style="margin: 0 0 6px 0; font-size: 1.1em; text-transform: uppercase;">
            <a href="{{ post.url | relative_url }}" style="color: #ffffff; text-decoration: none;">{{ post.title }}</a>
          </h3>
          
          {% if post.description %}
            <p style="font-size: 0.85em; color: var(--text-secondary); margin: 0;">{{ post.description }}</p>
          {% endif %}
        </div>
      {% endif %}
    {% endfor %}

    {% if sector2_count == 0 %}
      <p style="font-family: var(--font-mono); font-size: 0.85em; color: var(--text-secondary);">[NO LOGS REGISTERED IN SECTOR 02]</p>
    {% endif %}
  </div>

</div>
