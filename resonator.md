---
layout: default
title: "Resonator Archive"
---

<style>
  .filter-btn { background: transparent; border: 1px solid rgba(255,255,255,0.1); color: var(--text-secondary); cursor: pointer; padding: 5px 10px; transition: all 0.2s ease; font-family: inherit; }
  .filter-btn:hover { border-color: #ff3344; color: #ff3344 !important; background: rgba(255, 51, 68, 0.05); }
  .filter-btn.active { color: #ff3344 !important; border-color: #ff3344; box-shadow: 0 0 8px rgba(255, 51, 68, 0.3); }
  .res-card:hover .res-img-wrapper img { filter: grayscale(0%) contrast(1.1); transform: scale(1.05); }
  .res-card:hover .res-overlay { border-left: 2px solid #ff3344; box-shadow: inset 0 0 20px rgba(255, 51, 68, 0.1); }
  .res-card:hover .res-label { color: #ff3344; border-color: rgba(255, 51, 68, 0.5); }
</style>

<div class="archive-list" style="margin-top: 25px;">
  <h3 style="color: var(--accent-tho); font-family: var(--font-mono); letter-spacing: 1px; border-bottom: 1px solid rgba(255,255,255,0.1); padding-bottom: 10px; margin-bottom: 20px;">
    > DIRECTORY // RESONATOR ARCHIVE
  </h3>

  <!-- CHỈ QUÉT BÀI VIẾT CÓ LAYOUT: REPORT -->
  {% assign resonator_posts = site.posts | where: "layout", "report" %}
  {% assign raw_tags = "" %}
  
  {% for post in resonator_posts %}
    {% for tag in post.tags %}
      {% assign tag_lower = tag | downcase %}
      <!-- Loại bỏ tag hệ thống khỏi nút bấm -->
      {% if tag_lower != "archive_record" and tag_lower != "resonator" %}
        {% assign raw_tags = raw_tags | append: tag_lower | append: "," %}
      {% endif %}
    {% endfor %}
  {% endfor %}
  
  {% assign unique_tags = raw_tags | split: "," | uniq | sort %}

  <div class="filter-bar" style="margin-bottom: 30px; font-family: var(--font-mono); font-size: 0.85em;">
    <span style="color: var(--text-secondary); margin-right: 15px;">> CLASSIFICATION:</span>
    <div class="filter-group" style="display: flex; gap: 10px; flex-wrap: wrap; margin-top: 10px;">
      <button class="filter-btn active" data-filter="all">[ ALL ]</button>
      {% for tag in unique_tags %}
        {% if tag != "" %}
          <button class="filter-btn" data-filter="{{ tag }}">[ {{ tag | upcase | replace: "_", " " }} ]</button>
        {% endif %}
      {% endfor %}
    </div>
  </div>

  <div class="resonator-grid" style="display: grid; grid-template-columns: repeat(auto-fill, minmax(130px, 1fr)); gap: 15px;">
    {% for post in resonator_posts %}
      {% assign post_tags = post.tags | join: ' ' | downcase %}
      {% assign char_name = post.title | split: " //" | first %}

      <a href="{{ post.url | relative_url }}" class="res-card" data-tags="{{ post_tags }}" style="text-decoration: none;">
        <div class="res-img-wrapper" style="background: rgba(255,255,255,0.02); border: 1px solid var(--border-color); position: relative; overflow: hidden; aspect-ratio: 1/1;">
          <img src="{{ post.avatar | relative_url | default: '/assets/img/default-avatar.png' }}" alt="{{ char_name }}" style="width: 100%; height: 100%; object-fit: cover; object-position: top; transition: all 0.3s ease; filter: grayscale(80%) contrast(1.2);">
          <div class="res-overlay" style="position: absolute; top: 0; left: 0; right: 0; bottom: 0; border-left: 2px solid transparent; transition: all 0.3s ease;"></div>
        </div>
        <div class="res-label" style="background: #000; border: 1px solid var(--border-color); border-top: none; padding: 8px 5px; text-align: center; color: #fff; font-family: var(--font-mono); font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
          {{ char_name }}
        </div>
      </a>
    {% endfor %}
  </div>
</div>

<script>
  document.addEventListener("DOMContentLoaded", function() {
    const filterBtns = document.querySelectorAll('.filter-btn');
    const resCards = document.querySelectorAll('.res-card');

    filterBtns.forEach(btn => {
      btn.addEventListener('click', function() {
        filterBtns.forEach(b => { b.classList.remove('active'); b.style.color = 'var(--text-secondary)'; });
        this.classList.add('active'); this.style.color = '#ff3344'; 
        
        const filterValue = this.getAttribute('data-filter');
        resCards.forEach(card => {
          const tags = card.getAttribute('data-tags');
          if (filterValue === 'all' || tags.includes(filterValue)) {
            card.style.display = 'block';
          } else {
            card.style.display = 'none';
          }
        });
      });
    });
  });
</script>
