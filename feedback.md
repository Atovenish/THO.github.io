---
layout: default
title: "THO's PROTOCOLS"
---

## // 06. TRANSMISSION PROTOCOLS
> *"Kênh giao tiếp và hệ thống đánh giá năng lực của The Hideous One."*

<!-- KHUNG LƯỚI CHIA 2 CỘT -->
<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 30px; margin-top: 40px; margin-bottom: 40px;">

  <!-- ==========================================
       Ô SỐ 1: FEEDBACK BÌNH THƯỜNG (POP-UP)
       ========================================== -->
  <div style="text-align: center; padding: 40px 20px; background: rgba(255,255,255,0.02); border: 1px solid var(--border-color); border-left: 3px solid #ff3344; box-shadow: inset 2px 0 10px rgba(255, 51, 68, 0.05);">
    <h3 style="color: #ff3344; font-family: var(--font-mono); font-size: 1.2em; text-transform: uppercase; margin-top: 0;">
      > THO FEEDBACK
    </h3>
    <p style="font-size: 0.9em; color: var(--text-secondary); margin-bottom: 25px; line-height: 1.6; padding: 0 15px;">
      Kênh gửi về các góp ý và nhận xét đến THO. Cảm ơn Tri Giả đã quan tâm, chúc Tri Giả có Foibem.
    </p>
    
    <!-- Nút mở Pop-up Feedback -->
    <button data-tally-open="2EG0Qg" data-tally-emoji-text="💬" data-tally-emoji-animation="wave" style="font-family: var(--font-mono); font-size: 0.9em; color: #ffffff; background: #ff3344; border: none; padding: 12px 24px; cursor: pointer; letter-spacing: 1px; box-shadow: 0 0 15px rgba(255, 51, 68, 0.4); transition: all 0.2s ease;">
      // LAUNCH FEEDBACK
    </button>
  </div>


  <!-- ==========================================
       Ô SỐ 2: BÀI KIỂM TRA ĐẠI TRI GIẢ (FULL PAGE)
       ========================================== -->
  <div style="text-align: center; padding: 40px 20px; background: rgba(255,255,255,0.02); border: 1px solid var(--border-color); border-left: 3px solid var(--accent-tho); box-shadow: inset 2px 0 10px rgba(92, 225, 230, 0.05);">
    <h3 style="color: var(--accent-tho); font-family: var(--font-mono); font-size: 1.2em; text-transform: uppercase; margin-top: 0;">
      > TETHYS SCHOLAR EXAM
    </h3>
    <p style="font-size: 0.9em; color: var(--text-secondary); margin-bottom: 25px; line-height: 1.6; padding: 0 15px;">
      Bài kiểm tra đánh giá năng lực Đại Tri Giả Tethys. Hoàn thành bài thi để cấp quyền truy cập dữ liệu tuyệt mật.
    </p>

    <!-- Nút dẫn tới trang Full Page Exam -->
    <a href="{{ '/tethys-exam/' | relative_url }}" target="_blank" style="display: inline-block; font-family: var(--font-mono); font-size: 0.9em; color: #040609; font-weight: bold; background: var(--accent-tho); border: none; padding: 12px 24px; cursor: pointer; letter-spacing: 1px; text-decoration: none; box-shadow: 0 0 15px rgba(92, 225, 230, 0.4); transition: all 0.2s ease;">
      // INITIATE EXAM
    </a>
  </div>

</div>

<!-- SCRIPT KÍCH HOẠT TALLY POP-UP -->
<script async src="https://tally.so/widgets/embed.js"></script>
