---
layout: null
title: "[ DIRECTORY // TETHYS ] - BÀI KIỂM TRA ĐẠI TRI GIẢ"
permalink: /tethys-exam/
---
<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
  <title>{{ page.title }}</title>
  <script async src="https://tally.so/widgets/embed.js"></script>
  
  <style type="text/css">
    html, body { margin: 0; height: 100%; overflow: hidden; background: #040609; font-family: monospace; user-select: none; }
    
    /* Form Tally full màn hình (trừ đi 65px của thanh nhạc) */
    .tally-iframe { position: absolute; top: 0; left: 0; width: 100%; height: calc(100% - 65px); border: 0; z-index: 1; }
    
    /* ================= THANH AUDIO BOTTOM BAR ================= */
    .audio-bar {
      position: fixed; bottom: 0; left: 0; width: 100%; height: 65px;
      background: #040609; border-top: 1px solid rgba(92, 225, 230, 0.3);
      box-shadow: 0 -5px 15px rgba(0, 0, 0, 0.8); z-index: 9999;
      display: flex; align-items: center; justify-content: space-between; 
      padding: 0 15px; box-sizing: border-box;
    }

    /* Thumbnail kiêm Link mở Youtube */
    .track-thumb-link {
      display: inline-block; width: 42px; height: 42px; min-width: 42px;
      margin-right: 12px; border-radius: 4px; border: 1px solid var(--accent-tho, #5ce1e6);
      background-color: #111;
      background-image: url('{{ "/assets/img/THO_logo.png" | relative_url }}'); 
      background-size: cover; background-position: center;
      cursor: pointer; transition: opacity 0.2s ease, transform 0.2s ease;
    }
    .track-thumb-link:hover { opacity: 0.8; transform: scale(1.05); }

    /* Thông tin bài nhạc */
    .track-info { display: flex; flex-direction: column; justify-content: center; overflow: hidden; flex-grow: 1; min-width: 0; }
    .track-title { color: #fff; font-size: 13px; font-weight: bold; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; margin-bottom: 2px; }
    .track-artist { color: var(--accent-tho, #5ce1e6); font-size: 10px; text-transform: uppercase; letter-spacing: 1px; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }

    /* Cụm điều khiển bên phải */
    .controls-right { display: flex; align-items: center; gap: 10px; margin-left: 15px; flex-shrink: 0; }

    /* Nút Skip (Prev/Next nhỏ gọn) */
    .skip-btn { 
      background: none; border: 1px solid rgba(92, 225, 230, 0.3); color: #5ce1e6; 
      width: 28px; height: 28px; border-radius: 4px; font-size: 10px; 
      display: flex; align-items: center; justify-content: center; cursor: pointer; padding: 0; 
      transition: 0.2s;
    }
    .skip-btn:hover { background: rgba(92, 225, 230, 0.1); border-color: #5ce1e6; }

    /* Nút Play/Pause */
    .play-btn {
      background: var(--accent-tho, #5ce1e6); color: #040609; border: none;
      width: 38px; height: 38px; border-radius: 50%; font-size: 14px;
      display: flex; align-items: center; justify-content: center; cursor: pointer;
      transition: transform 0.1s ease; padding: 0;
    }
    .play-btn .icon-play { margin-left: 3px; }
    .play-btn .icon-pause { display: none; }
    .play-btn.playing .icon-play { display: none; }
    .play-btn.playing .icon-pause { display: block; margin-left: 0; }
    .play-btn:active { transform: scale(0.9); }

    /* Ẩn Iframe Youtube */
    #hidden-player { position: absolute; left: -9999px; top: -9999px; width: 1px; height: 1px; opacity: 0; pointer-events: none; }
  </style>
</head>
<body>
  
  <!-- FORM BÀI THI -->
  <iframe class="tally-iframe" data-tally-src="https://tally.so/r/1A1arO" frameborder="0" marginheight="0" marginwidth="0" title="{{ page.title }}"></iframe>

  <!-- THANH NHẠC BOTTOM BAR GỌN GÀNG -->
  <div class="audio-bar">
    
    <!-- Thumbnail logo THO dẫn link gốc Youtube -->
    <a href="https://www.youtube.com/playlist?list=PLDAIHOJ8ZsPo" target="_blank" class="track-thumb-link" title="Mở danh sách phát gốc trên Youtube"></a>
    
    <!-- Tiêu đề & Tác giả -->
    <div class="track-info">
      <div class="track-title">1+ Hour Wuthering Waves OST Mix</div>
      <div class="track-artist">> TETHYS_TRANSMISSION</div>
    </div>

    <!-- Các nút điều khiển phía bên phải -->
    <div class="controls-right">
      <button id="prev-btn" class="skip-btn" title="Bài trước">⏮</button>
      
      <button id="play-btn" class="play-btn" title="Play/Pause">
        <span class="icon-play">▶</span>
        <span class="icon-pause">⏸</span>
      </button>

      <button id="next-btn" class="skip-btn" title="Bài tiếp theo">⏭</button>
    </div>

  </div>

  <div id="hidden-player"></div>

  <!-- SCRIPT API -->
  <script src="https://www.youtube.com/iframe_api"></script>
  <script>
    var ytPlayer;
    var playBtn = document.getElementById('play-btn');
    var isPlaying = false;

    function onYouTubeIframeAPIReady() {
      ytPlayer = new YT.Player('hidden-player', {
        height: '1', width: '1',
        playerVars: { 
          'autoplay': 0, 
          'controls': 0, 
          'playsinline': 1,
          'listType': 'playlist',
          'list': 'PLDAIHOJ8ZsPo' // Playlist của bạn
        },
        events: {
          'onStateChange': function(e) {
            if (e.data == YT.PlayerState.PLAYING) {
              isPlaying = true;
              playBtn.classList.add('playing');
            } else {
              isPlaying = false;
              playBtn.classList.remove('playing');
            }
          }
        }
      });
    }

    playBtn.addEventListener('click', function() {
      if (ytPlayer && ytPlayer.playVideo) {
        isPlaying ? ytPlayer.pauseVideo() : ytPlayer.playVideo();
      }
    });

    document.getElementById('next-btn').addEventListener('click', function() {
      if (ytPlayer && typeof ytPlayer.nextVideo === 'function') ytPlayer.nextVideo();
    });

    document.getElementById('prev-btn').addEventListener('click', function() {
      if (ytPlayer && typeof ytPlayer.previousVideo === 'function') ytPlayer.previousVideo();
    });
  </script>
</body>
</html>
