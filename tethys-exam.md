---
layout: null
title: "[ DIRECTORY // TETHYS ] - LORE ANALYSIS EXAMINATION"
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
      
      /* Thanh điều khiển nhạc bám đáy màn hình (Mobile Friendly) */
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

      /* Ảnh Thumbnail giả lập */
      .track-thumb {
        width: 45px;
        height: 45px;
        background-color: #111;
        background-image: url('https://res.cloudinary.com/tho/image/upload/v1234567/tethys_logo.jpg'); /* Đổi link ảnh thumbnail nếu muốn */
        background-size: cover;
        background-position: center;
        border-radius: 4px;
        border: 1px solid var(--accent-tho, #5ce1e6);
        margin-right: 15px;
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

      /* Nút Play/Pause */
      .play-btn {
        background: var(--accent-tho, #5ce1e6);
        color: #040609;
        border: none;
        width: 40px;
        height: 40px;
        border-radius: 50%;
        font-size: 18px;
        display: flex;
        align-items: center;
        justify-content: center;
        cursor: pointer;
        transition: transform 0.1s ease, box-shadow 0.2s ease;
        margin-left: 15px;
        padding-left: 4px; /* Căn giữa icon play */
      }

      .play-btn.playing {
        padding-left: 0; /* Trả lại tâm cho icon pause */
      }

      .play-btn:active {
        transform: scale(0.9);
      }
      
      /* Ẩn hoàn toàn video Youtube gốc */
      #hidden-youtube-player { display: none; }
    </style>
  </head>
  <body>
    
    <!-- BÀI THI TALLY (Trừ đi 65px chiều cao của thanh nhạc ở dưới cùng) -->
    <iframe class="tally-iframe" data-tally-src="https://tally.so/r/1A1arO" frameborder="0" marginheight="0" marginwidth="0" title="{{ page.title }}"></iframe>

    <!-- THANH PHÁT NHẠC CUSTOM -->
    <div class="custom-audio-bar">
      <div class="track-thumb"></div>
      <div class="track-info">
        <div class="track-title">1+ Hour Wuthering Waves OST Mix</div>
        <div class="track-artist">> TETHYS_TRANSMISSION</div>
      </div>
      <button id="play-pause-btn" class="play-btn">▶</button>
    </div>

    <!-- Div rỗng để Youtube API nhúng video ẩn vào -->
    <div id="hidden-youtube-player"></div>

    <!-- SCRIPT ĐIỀU KHIỂN YOUTUBE BẰNG JAVASCRIPT -->
    <script src="https://www.youtube.com/iframe_api"></script>
    <script>
      var ytPlayer;
      var playBtn = document.getElementById('play-pause-btn');
      var isPlaying = false;

      // Hàm này tự động chạy khi thư viện Youtube API tải xong
      function onYouTubeIframeAPIReady() {
        ytPlayer = new YT.Player('hidden-youtube-player', {
          height: '0',
          width: '0',
          videoId: 'E3aKsgr1mvk', // ID video OST của bạn
          playerVars: {
            'autoplay': 0,
            'controls': 0,
            'playsinline': 1 // Quan trọng cho điện thoại
          },
          events: {
            'onStateChange': onPlayerStateChange
          }
        });
      }

      // Lắng nghe sự kiện click vào nút bấm của chúng ta
      playBtn.addEventListener('click', function() {
        if (ytPlayer && typeof ytPlayer.playVideo === 'function') {
          if (isPlaying) {
            ytPlayer.pauseVideo();
          } else {
            ytPlayer.playVideo();
          }
        }
      });

      // Đổi icon nút bấm dựa trên trạng thái thực tế của Youtube
      function onPlayerStateChange(event) {
        if (event.data == YT.PlayerState.PLAYING) {
          isPlaying = true;
          playBtn.innerHTML = '⏸'; // Chuyển thành icon Pause
          playBtn.classList.add('playing');
        } else {
          isPlaying = false;
          playBtn.innerHTML = '▶'; // Chuyển thành icon Play
          playBtn.classList.remove('playing');
        }
      }
    </script>
  </body>
</html>
