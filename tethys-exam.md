---
layout: null
title: "[ DIRECTORY // TETHYS ] - BÀI KIỂM TRA ĐẠI TRI GIẢ"
permalink: /tethys-exam/
---
<!DOCTYPE html>
<html lang="vi">
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=0">
    <title>{{ page.title }}</title>
    <script async src="https://tally.so/widgets/embed.js"></script>
    
    <style type="text/css">
      html, body { margin: 0; height: 100%; overflow: hidden; background: #040609; font-family: monospace; }
      
      /* Iframe Tally full màn hình */
      .tally-iframe { position: absolute; top: 0; left: 0; width: 100%; height: 100%; border: 0; z-index: 1; }
      
      /* Màn hình chờ bắt buộc để vượt rào Pop-up Blocker & Khởi tạo Audio */
      .init-overlay {
        position: absolute; top: 0; left: 0; width: 100%; height: 100%;
        background: #040609; z-index: 9999;
        display: flex; flex-direction: column; align-items: center; justify-content: center;
        transition: opacity 0.5s ease;
      }
      
      .init-box {
        border: 1px solid rgba(92, 225, 230, 0.3); border-left: 4px solid var(--accent-tho, #5ce1e6);
        background: rgba(255,255,255,0.02); padding: 40px; text-align: center;
        box-shadow: 0 0 20px rgba(92, 225, 230, 0.1);
      }

      .init-title { color: #fff; font-size: 1.2em; margin-bottom: 10px; text-transform: uppercase; letter-spacing: 2px; }
      .init-desc { color: #888; font-size: 0.9em; margin-bottom: 30px; }

      .btn-launch {
        background: var(--accent-tho, #5ce1e6); color: #040609; font-family: monospace; font-weight: bold;
        padding: 15px 30px; border: none; cursor: pointer; font-size: 1em; letter-spacing: 1px;
        transition: all 0.2s ease; box-shadow: 0 0 15px rgba(92, 225, 230, 0.3);
      }
      .btn-launch:hover { transform: scale(1.05); box-shadow: 0 0 25px rgba(92, 225, 230, 0.6); }
    </style>
  </head>
  <body>
    
    <!-- Lớp màn chờ -->
    <div id="init-screen" class="init-overlay">
      <div class="init-box">
        <div class="init-title">TETHYS SCHOLAR EXAM</div>
        <div class="init-desc">[ KẾT NỐI MẠNG LƯỚI & THIẾT LẬP KÊNH TRUYỀN ÂM THAM CHIẾU ]</div>
        <!-- Bấm nút này để mở Pop-up Radio và hiện Tally Form -->
        <button class="btn-launch" onclick="launchProtocol()">// INITIALIZE CONNECTION</button>
      </div>
    </div>

    <!-- Form Tally ẩn phía sau -->
    <iframe class="tally-iframe" data-tally-src="https://tally.so/r/1A1arO" frameborder="0" marginheight="0" marginwidth="0" title="{{ page.title }}"></iframe>

    <script>
      function launchProtocol() {
        // Mở cửa sổ Radio riêng biệt (kích thước cố định, ẩn thanh địa chỉ)
        // Lưu ý: Đảm bảo bạn ĐÃ TẠO file radio.html có permalink là /radio/ như hướng dẫn ở trên
        window.open('{{ "/radio/" | relative_url }}', 'THORadio', 'width=380,height=160,left=100,top=100,menubar=no,toolbar=no,location=no,status=no');
        
        // Làm mờ và ẩn màn hình chờ đi để lộ form làm bài
        var overlay = document.getElementById('init-screen');
        overlay.style.opacity = '0';
        setTimeout(function() {
          overlay.style.display = 'none';
        }, 500);
      }
    </script>
  </body>
</html>
