---
layout: null
permalink: /tethys-exam/
---
<html>
  <head>
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=0">
    <title>[ DIRECTORY // TETHYS ] - BÀI KIỂM TRA ĐẠI TRI GIẢ</title>
    <script async src="https://tally.so/widgets/embed.js"></script>
    <style type="text/css">
      html, body { margin: 0; height: 100%; overflow: hidden; background: #040609; }
      
      /* Cấu trúc cho Form Tally */
      .tally-iframe { position: absolute; top: 0; right: 0; bottom: 0; left: 0; border: 0; z-index: 1; }
      
      /* Khung điều khiển nhạc (Audio Widget) */
      .terminal-audio-widget {
        position: fixed;
        bottom: 25px;
        left: 25px;
        z-index: 9999;
        background: rgba(4, 6, 9, 0.9);
        border: 1px solid rgba(92, 225, 230, 0.3);
        border-left: 3px solid var(--accent-tho, #5ce1e6);
        padding: 10px;
        border-radius: 2px;
        box-shadow: 0 0 20px rgba(92, 225, 230, 0.15);
        transition: all 0.3s ease;
        display: flex;
        flex-direction: column;
        gap: 5px;
      }
      
      .terminal-audio-widget:hover {
        border-color: var(--accent-tho, #5ce1e6);
        box-shadow: 0 0 25px rgba(92, 225, 230, 0.3);
      }

      .audio-label {
        font-family: monospace;
        font-size: 11px;
        color: #5ce1e6;
        text-transform: uppercase;
        letter-spacing: 1px;
      }

      /* Kích thước video (giấu đi, chỉ hiện phần control bar) */
      .youtube-player {
        width: 250px;
        height: 60px; 
      }
    </style>
  </head>
  <body>
    <!-- Iframe Form Tally gốc của bạn -->
    <iframe class="tally-iframe" data-tally-src="https://tally.so/r/1A1arO" width="100%" height="100%" frameborder="0" marginheight="0" marginwidth="0" title="[ DIRECTORY // TETHYS ] - BÀI KIỂM TRA ĐẠI TRI GIẢ"></iframe>

    <!-- Audio Widget - Thay thế MÃ_VIDEO_CỦA_BẠN -->
    <div class="terminal-audio-widget">
      <span class="audio-label">> TETHYS_OST_TRANSMISSION</span>
      <iframe class="youtube-player" src="https://www.youtube.com/embed/E3aKsgr1mvk?controls=1&fs=0&modestbranding=1" frameborder="0" allow="autoplay; encrypted-media"></iframe>
    </div>
  </body>
</html>
