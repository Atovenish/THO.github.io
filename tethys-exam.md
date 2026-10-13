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
    /* Reset & Base */
    html, body { margin: 0; height: 100%; overflow: hidden; background: #040609; font-family: monospace; user-select: none; }
    
    /* ================= KHU VỰC TALLY FORM ================= */
    /* Trừ đi 70px chiều cao của thanh nhạc dưới đáy */
    .tally-iframe { position: absolute; top: 0; left: 0; width: 100%; height: calc(100% - 70px); border: 0; z-index: 1; }
    
    /* ================= THANH AUDIO BOTTOM BAR ================= */
    .audio-bar {
      position: fixed; bottom: 0; left: 0; width: 100%; height: 70px;
      background: #040609; border-top: 1px solid rgba(92, 225, 230, 0.3);
      box-shadow: 0 -10px 20px rgba(0, 0, 0, 0.6); z-index: 9999;
      display: flex; align-items: center; justify-content: space-between; 
      padding: 0 20px; box-sizing: border-box;
    }

    /* 1. Nhóm Thông tin (Trái) */
    .info-group { display: flex; align-items: center; gap: 15px; flex: 1; min-width: 0; }
    
    .spectrum-box { display: flex; align-items: flex-end; gap: 2px; height: 20px; width: 35px; flex-shrink: 0; }
    .bar { width: 4px; background: #5ce1e6; height: 3px; border-radius: 1px; transition: height 0.1s; }
    .spectrum-box.playing .bar:nth-child(1) { animation: bounce 0.6s infinite alternate; }
    .spectrum-box.playing .bar:nth-child(2) { animation: bounce 0.4s infinite alternate 0.2s; }
    .spectrum-box.playing .bar:nth-child(3) { animation: bounce 0.7s infinite alternate 0.1s; }
    .spectrum-box.playing .bar:nth-child(4) { animation: bounce 0.5s infinite alternate 0.3s; }
    .spectrum-box.playing .bar:nth-child(5) { animation: bounce 0.8s infinite alternate 0.15s; }
    @keyframes bounce { 0% { height: 3px; } 100% { height: 20px; } }

    .track-info { display: flex; flex-direction: column; overflow: hidden; }
    .track-title { color: #fff; font-size: 14px; font-weight: bold; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; margin-bottom: 2px; }
    .track-subtitle { color: var(--accent-tho, #5ce1e6); font-size: 10px; letter-spacing: 1px; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }

    /* 2. Nhóm Nút Bấm (Giữa) */
    .controls-group { display: flex; align-items: center; gap: 12px; flex-shrink: 0; margin: 0 20px; }
    
    .skip-btn { background: none; border: 1px solid rgba(92, 225, 230, 0.3); color: #5ce1e6; width: 32px; height: 32px; border-radius: 4px; font-size: 12px; display: flex; align-items: center; justify-content: center; cursor: pointer; transition: 0.2s ease; padding: 0; }
    .skip-btn:hover { background: rgba(92, 225, 230, 0.1); border-color: #5ce1e6; }
    .skip-btn:active { transform: scale(0.9); }
    
    .play-btn { background: #5ce1e6; color: #040609; border: none; width: 44px; height: 44px; border-radius: 50%; font-size: 16px; display: flex; align-items: center; justify-content: center; cursor: pointer; transition: 0.1s; padding: 0; }
    .play-btn .icon-play { margin-left: 3px; }
    .play-btn .icon-pause { display: none; }
    .play-btn.playing .icon-play { display: none; }
    .play-btn.playing .icon-pause { display: block; margin-left: 0; }
    .play-btn:active { transform: scale(0.9); }

    /* 3. Nhóm Tiến trình (Phải) */
    .progress-group { display: flex; align-items: center; gap: 10px; flex: 2; min-width: 0; justify-content: flex-end; }
    .time-label { color: #888; font-size: 11px; min-width: 40px; text-align: center; font-family: monospace; }
    .seek-slider { -webkit-appearance: none; width: 100%; max-width: 400px; height: 4px; background: #333; border-radius: 2px; outline: none; cursor: pointer; margin: 0; }
    .seek-slider::-webkit-slider-thumb { -webkit-appearance: none; appearance: none; width: 12px; height: 12px; border-radius: 50%; background: #5ce1e6; cursor: pointer; box-shadow: 0 0 8px rgba(92, 225, 230, 0.8); }

    /* ================= ĐIỀU CHỈNH CHO MOBILE ================= */
    @media (max-width: 768px) {
      .audio-bar { flex-direction: column; height: 95px; padding: 8px 15px; gap: 8px; justify-content: center; }
      .tally-iframe { height: calc(100% - 95px); }
      .info-group { width: 100%; justify-content: space-between; }
      .controls-group { position: absolute; right: 15px; top: 12px; margin: 0; gap: 8px; }
      .progress-group { width: 100%; justify-content: space-between; }
      .seek-slider { max-width: none; }
      .spectrum-box { display: none; /* Ẩn sóng nhạc trên mobile cho đỡ chật */ }
    }

    /* Ẩn Youtube Player */
    #hidden-player { position: absolute; left: -9999px; top: -9999px; width: 1px; height: 1px; opacity: 0; pointer-events: none; }
  </style>
</head>
<body>
  
  <!-- TALLY FORM -->
  <iframe class="tally-iframe" data-tally-src="https://tally.so/r/1A1arO" frameborder="0" marginheight="0" marginwidth="0" title="{{ page.title }}"></iframe>

  <!-- AUDIO BOTTOM BAR -->
  <div class="audio-bar">
    
    <!-- Info & Spectrum -->
    <div class="info-group">
      <div id="spectrum" class="spectrum-box">
        <div class="bar"></div><div class="bar"></div><div class="bar"></div><div class="bar"></div><div class="bar"></div>
      </div>
      <div class="track-info">
        <div class="track-title">THO Transmission</div>
        <div class="track-subtitle">> AUDIO_SRC: THO PLAYLIST</div>
      </div>
    </div>

    <!-- Controls -->
    <div class="controls-group">
      <button id="prev-btn" class="skip-btn" title="Previous Track">⏮</button>
      <button id="play-btn" class="play-btn" title="Play/Pause">
        <span class="icon-play">▶</span>
        <span class="icon-pause">⏸</span>
      </button>
      <button id="next-btn" class="skip-btn" title="Next Track">⏭</button>
    </div>

    <!-- Progress -->
    <div class="progress-group">
      <span id="current-time" class="time-label">0:00</span>
      <input type="range" id="seek-slider" class="seek-slider" value="0" min="0" max="100" step="1">
      <span id="total-time" class="time-label">0:00</span>
    </div>

  </div>

  <div id="hidden-player"></div>

  <!-- SCRIPT API -->
  <script src="https://www.youtube.com/iframe_api"></script>
  <script>
    var ytPlayer, progressInterval;
    var isPlaying = false, isDragging = false;
    var playBtn = document.getElementById('play-btn');
    var seekSlider = document.getElementById('seek-slider');
    var spectrum = document.getElementById('spectrum');

    function formatTime(time) {
      if (isNaN(time)) return "0:00";
      var m = Math.floor(time / 60), s = Math.floor(time % 60);
      return m + ":" + (s < 10 ? "0" : "") + s;
    }

    function updateSliderColor() {
      var pct = (seekSlider.value / seekSlider.max) * 100;
      seekSlider.style.background = 'linear-gradient(to right, #5ce1e6 ' + pct + '%, #333 ' + pct + '%)';
    }

    function onYouTubeIframeAPIReady() {
      ytPlayer = new YT.Player('hidden-player', {
        height: '1', width: '1',
        playerVars: { 
          'autoplay': 0, // Đổi thành 0 vì mobile không cho phép tự động phát tiếng
          'controls': 0, 
          'playsinline': 1,
          'listType': 'playlist',
          'list': 'PLDAIHOJ8ZsPo' // Playlist Wuthering Waves của bạn
        },
        events: {
          'onReady': function() {
            seekSlider.max = ytPlayer.getDuration();
            document.getElementById('total-time').innerText = formatTime(ytPlayer.getDuration());
          },
          'onStateChange': function(e) {
            if (e.data == YT.PlayerState.PLAYING) {
              isPlaying = true;
              playBtn.classList.add('playing');
              spectrum.classList.add('playing'); 
              progressInterval = setInterval(function() {
                if (!isDragging) {
                  seekSlider.value = ytPlayer.getCurrentTime();
                  document.getElementById('current-time').innerText = formatTime(seekSlider.value);
                  updateSliderColor();
                }
              }, 1000);
            } else {
              isPlaying = false;
              playBtn.classList.remove('playing');
              spectrum.classList.remove('playing'); 
              clearInterval(progressInterval);
            }
          }
        }
      });
    }

    // Các sự kiện nút bấm
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

    // Tua nhạc
    seekSlider.addEventListener('input', function() {
      isDragging = true;
      document.getElementById('current-time').innerText = formatTime(this.value);
      updateSliderColor();
    });
    
    seekSlider.addEventListener('change', function() {
      if (ytPlayer && ytPlayer.seekTo) ytPlayer.seekTo(this.value, true);
      isDragging = false;
    });
  </script>
</body>
</html>
