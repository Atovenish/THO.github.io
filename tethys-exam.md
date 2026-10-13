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
      
      /* Lớp nền: Form Tally full màn hình */
      .tally-iframe { position: absolute; top: 0; right: 0; bottom: 65px; left: 0; border: 0; z-index: 1; width: 100%; height: calc(100% - 65px); }
      
      /* Thanh điều khiển nhạc bám đáy màn hình */
      .custom-audio-bar {
        position: fixed;
        bottom: 0;
        left: 0;
        width: 100%;
        height: 65px;
        background: #040609;
        border-top: 1px solid rgba(92, 225, 230, 0.3);
        box-shadow: 0 -5px 15px rgba(0, 0, 0, 0.8);
        z-index: 9999;
        display: flex;
        align-items: center;
        padding: 0 15px;
        box-sizing: border-box;
      }

      /* =========================================
         ẢNH THUMBNAIL CÓ CHỨA LINK YOUTUBE 
         ========================================= */
      .track-thumb-link {
        display: inline-block;
        width: 45px;
        height: 45px;
        margin-right: 15px;
        border-radius: 4px;
        border: 1px solid var(--accent-tho, #5ce1e6);
        background-color: #111;
        /* Gọi ảnh THO logo từ hệ thống file của Jekyll */
        background-image: url('{{ "/assets/img/THO_logo.png" | relative_url }}'); 
        background-size: cover;
        background-position: center;
        cursor: pointer;
        transition: opacity 0.2s ease, transform 0.2s ease;
      }

      .track-thumb-link:hover {
        opacity: 0.8;
        transform: scale(1.05);
      }

      /* Thông tin bài nhạc */
      .track-info {
        flex-grow: 1;
        display: flex;
        flex-direction: column;
        justify-content: center;
        overflow: hidden;
      }

      .track-title {
        color: #ffffff;
        font-size: 14px;
        font-weight: bold;
        white-space: nowrap;
        overflow: hidden;
        text-overflow: ellipsis;
        margin-bottom: 4px;
      }

      .track-artist {
        color: var(--accent-tho, #5ce1e6);
        font-size: 11px;
        text-transform: uppercase;
        letter-spacing: 1px;
      }

      /* =========================================
         NÚT PLAY/PAUSE (ĐÃ SỬA CĂN GIỮA) 
         ========================================= */
      .play-btn {
        background: var(--accent-tho, #5ce1e6);
        color: #040609;
        border: none;
        width: 40px;
        height: 40px;
        border-radius: 50%;
        font-size: 16px; /* Giảm font nhẹ để icon nằm gọn gàng hơn */
        display: flex;
        align-items: center;
        justify-content: center;
        cursor: pointer;
        transition: transform 0.1s ease, box-shadow 0.2s ease;
        margin-left: 15px;
        /* Reset toàn bộ padding để Flexbox tự ép icon vào tâm */
        padding: 0; 
      }

      /* Đặc trị cho icon Play (hình tam giác) thường hay bị lệch quang học về bên trái */
      .play-btn .icon-play {
        display: inline-block;
        margin-left: 3px; 
      }

      .play-btn .icon-pause {
        display: none;
      }

      /* Khi đang phát (Playing State) */
      .play-btn.playing .icon-play {
        display: none;
      }

      .play-btn.playing .icon-pause {
        display: inline-block;
        margin-left: 0; /* Icon pause (2 gạch) thường tự đối xứng */
      }

      .play-btn:active {
        transform: scale(0.9);
      }
      
      /* Ẩn hoàn toàn video Youtube gốc */
      #hidden-youtube-player { display: none; }
    </style>
  </head>
  <body>
    
    <!-- BÀI THI TALLY -->
    <iframe class="tally-iframe" data-tally-src="https://tally.so/r/1A1arO" frameborder="0" marginheight="0" marginwidth="0" title="{{ page.title }}"></iframe>

    <!-- THANH PHÁT NHẠC CUSTOM -->
    <div class="custom-audio-bar">
      
      <!-- Ảnh Thumbnail làm Link -->
      <a href="https://www.youtube.com/watch?v=E3aKsgr1mvk" target="_blank" class="track-thumb-link" title="Mở bản gốc trên Youtube"></a>
      
      <div class="track-info">
        <div class="track-title">1+ Hour Wuthering Waves OST Mix</div>
        <div class="track-artist">> TETHYS_TRANSMISSION</div>
      </div>
      
      <!-- Nút Play với span bọc icon để chỉnh sửa quang học dễ hơn -->
      <button id="play-pause-btn" class="play-btn">
        <span class="icon-play">▶</span>
        <span class="icon-pause">⏸</span>
      </button>

    </div>

    <!-- Div rỗng để Youtube API nhúng video ẩn vào -->
    <div id="hidden-youtube-player"></div>

    <!-- SCRIPT ĐIỀU KHIỂN YOUTUBE BẰNG JAVASCRIPT -->
    <script src="https://www.youtube.com/iframe_api"></script>
    <script>
      var ytPlayer;
      var playBtn = document.getElementById('play-pause-btn');
      var isPlaying = false;

      function onYouTubeIframeAPIReady() {
        ytPlayer = new YT.Player('hidden-youtube-player', {
          height: '0',
          width: '0',
          videoId: 'E3aKsgr1mvk',
          playerVars: {
            'autoplay': 0,
            'controls': 0,
            'playsinline': 1
          },
          events: {
            'onStateChange': onPlayerStateChange
          }
        });
      }

      playBtn.addEventListener('click', function() {
        if (ytPlayer && typeof ytPlayer.playVideo === 'function') {
          if (isPlaying) {
            ytPlayer.pauseVideo();
          } else {
            ytPlayer.playVideo();
          }
        }
      });

      function onPlayerStateChange(event) {
        if (event.data == YT.PlayerState.PLAYING) {
          isPlaying = true;
          playBtn.classList.add('playing');
        } else {
          isPlaying = false;
          playBtn.classList.remove('playing');
        }
      }
    </script>
  </body>
</html>
