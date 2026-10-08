---
layout: default
title: "Wuthering Waves Theory"
---
<style>
  /* Đã thay đổi cấu trúc bên trong để Markdown không bị vỡ khối */
  .sector-card { 
    display: block; 
    background: rgba(4, 6, 9, 0.8); 
    border: 1px solid rgba(92, 225, 230, 0.2); 
    border-left: 4px solid var(--accent-tho); 
    padding: 25px; 
    margin-bottom: 20px; 
    text-decoration: none; 
    transition: all 0.3s ease; 
    border-radius: 2px; 
  }
  .sector-card:hover { 
    background: rgba(92, 225, 230, 0.05); 
    border-color: var(--accent-tho); 
    box-shadow: 0 0 15px rgba(92, 225, 230, 0.2); 
    transform: translateX(5px); 
  }
  
  .sector-card.s2 { 
    border-left-color: #ff3344; 
    border-color: rgba(255, 51, 68, 0.2); 
  }
  .sector-card.s2:hover { 
    background: rgba(255, 51, 68, 0.05); 
    border-color: #ff3344; 
    box-shadow: 0 0 15px rgba(255, 51, 68, 0.2); 
  }

  /* Định dạng lại chữ bằng thẻ inline để an toàn tuyệt đối với Jekyll */
  .sector-title {
    display: block;
    color: var(--accent-tho);
    font-family: var(--font-mono);
    font-size: 1.2em;
    letter-spacing: 1px;
    margin-bottom: 10px;
    font-weight: bold;
  }
  .sector-card.s2 .sector-title { color: #ff3344; }
  
  .sector-desc {
    display: block;
    color: var(--text-secondary);
    font-size: 0.9em;
    line-height: 1.6;
  }
</style>

<h2 style="color: #fff; font-family: var(--font-display); text-transform: uppercase; border-bottom: 2px solid rgba(255,255,255,0.1); padding-bottom: 15px;">
  // 03. WUTHERING WAVE THEORY
</h2>
<blockquote style="border-left: 3px solid var(--accent-tho); padding-left: 15px; color: var(--text-secondary); font-style: italic; margin-bottom: 35px; background: rgba(255,255,255,0.02); padding: 15px;">
  "Phân tích thế giới quan Solaris-3, giải mã Tacet Discords, Resonator Fortes và hệ thống vũ trụ học."
</blockquote>

<!-- PANEL 1 BẤM ĐỂ CHUYỂN TRANG (Đã fix dứt điểm lỗi vỡ HTML) -->
<a href="{{ '/sector-01/' | relative_url }}" class="sector-card">
  <span class="sector-title">> SECTOR 01 // WORLD COSMOLOGY & LORE</span>
  <span class="sector-desc">Truy cập kho dữ liệu về thế giới quan, các thực thể Endless, Somnoire và các giả thuyết vũ trụ học.</span>
</a>

<!-- PANEL 2 BẤM ĐỂ CHUYỂN TRANG -->
<a href="{{ '/sector-02/' | relative_url }}" class="sector-card s2">
  <span class="sector-title">> SECTOR 02 // ARCHIVE RECORDS</span>
  <span class="sector-desc">Hồ sơ tuyệt mật về các Tacet Field, Dị thể, Thế lực và các báo cáo phân tích hiện tượng Sóng mòn.</span>
</a>
