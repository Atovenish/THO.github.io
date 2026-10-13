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
    
    /* Form Tally full màn hình (trừ đi 70px của thanh nhạc) */
    .tally-iframe { position: absolute; top: 0; left: 0; width: 100%; height: calc(100% - 70px); border: 0; z-index: 1; }
    
    /* ================= THANH AUDIO BOTTOM BAR ================= */
    .audio-bar {
      position: fixed; bottom: 0; left: 0; width: 100%; height: 70px;
      background: #040609; border-top: 1px solid rgba(92, 225, 230, 0.3);
      box-shadow: 0 -5px 15px rgba(0, 0, 0, 0.8); z-index: 9999;
      display: flex; align-items: center; justify-content: space-between; 
      padding: 0 15px; box-sizing: border-box; gap: 15px;
    }

    /* Thumbnail kiêm Link mở Youtube */
    .track-thumb-link {
      display: inline-block; width: 42px; height: 42px; min-width: 42px;
      border-radius: 4px; border: 1px solid var(--accent-tho, #5ce1e6);
      background-color: #111;
      background-image: url('{{ "/assets/img/THO_logo.png" | relative_url }}'); 
      background-size: cover; background-position: center;
      cursor: pointer; transition: opacity 0.2s ease, transform 0.2s ease;
      flex-shrink: 0;
    }
    .track-thumb-link:hover { opacity: 0.8; transform: scale(1.05); }

    /* Thông tin bài nhạc */
    .track-info { display: flex; flex-direction: column; justify-content: center; overflow: hidden; width: 180px; flex-shrink: 0; }
    .track-title { color: #fff; font-size: 13px; font-weight: bold; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; margin-bottom: 2px; }
    .track-artist { color: var(--accent-tho, #5ce1e6); font-size: 10px; text-transform: uppercase; letter-spacing: 1px; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }

    /* Khu vực thanh tiến trình ở giữa */
    .progress-container { display: flex; align-items: center; gap: 10px; flex-grow: 1; max-width: 500px; }
    .time-label { color: #888; font-size: 10px; min-width: 35px; text-align: center; }
    
    .seek-slider {
      -webkit-appearance: none; width: 100%; height: 4px;
      background: #333; border-radius: 2px; outline: none; cursor: pointer; margin: 0;
    }
    .seek-slider::-webkit-slider-thumb {
      -webkit-appearance: none; appearance: none;
      width: 12px; height: 12px; border-radius: 50%;
      background: var(--accent-tho, #5ce1e6); cursor: pointer;
      box-shadow: 0 0 6px rgba(92, 225, 230, 0.8);
    }

    /* Cụm điều khiển bên phải */
    .controls-right { display: flex; align-items: center; gap: 10px; flex-shrink: 0; }

    /* Nút Skip (Prev/Next) */
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

    /* Responsive cho Mobile */
    @media (max-width: 768px) {
      .audio-bar { height: 85px; flex-wrap: wrap; padding: 8px 10px; }
      .tally-iframe { height: calc(100% - 85px); }
      .progress-container { order: 3; width: 100%; max-width: none; }
      .track-info { width: 120px; }
    }

    /* Ẩn Iframe Youtube */
    #hidden-player { position: absolute; left: -9999px; top: -9999px; width: 1px; height: 1px; opacity: 0; pointer-events: none; }
  </style>
</head>
<body>
  
  <!-- FORM BÀI THI -->
  <iframe class="tally-iframe" data-tally-src="https://tally.so/r/1A1arO" frameborder="0" marginheight="0" marginwidth="0" title="{{ page.title }}"></iframe>

  <!-- THANH NHẠC BOTTOM BAR ĐẦY ĐỦ THANH TUA -->
  <div class="audio-bar">
    
    <!-- Thumbnail logo THO dẫn link Youtube -->
    <a href="https://www.youtube.com/playlist?list=PLDAIHOJ8ZsPo" target="_blank" class="track-thumb-link" title="Mở danh sách phát gốc trên Youtube"></a>
    
    <!-- Tiêu đề & Tác giả -->
    <div class="track-info">
      <div class="track-title">THO/TETHYS Transmission Mix</div>
      <div class="track-artist">> THO PLAYLIST</div>
    </div>

    <!-- Thanh tiến trình tua nhạc ở giữa -->
    <div class="progress-container">
      <span id="current-time" class="time-label">0:00</span>
      <input type="range" id="seek-slider" class="seek-slider" value="0" min="0" max="100" step="1">
      <span id="total-time" class="time-label">0:00</span>
    </div>

    <!-- Các nút điều khiển bên phải -->
    <div class="controls-right">
      <button id="prev-btn" class="skip-btn" title="Previous Track">⏮</button>
      <button id="play-btn" class="play-btn" title="Play/Pause">
        <span class="icon-play">▶</span>
        <span class="icon-pause">⏸</span>
      </button>
      <button id="next-btn" class="skip-btn" title="Next Track">⏭</button>
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
    var currentTimeDisplay = document.getElementById('current-time');
    var totalTimeDisplay = document.getElementById('total-time');

    function formatTime(time) {
      if (isNaN(time)) return "0:00";
      var m = Math.floor(time / 60), s = Math.floor(time % 60);
      return m + ":" + (s < 10 ? "0" : "") + s;
    }

    function updateSliderColor() {
      var pct = (seekSlider.value / seekSlider.max) * 100;
      seekSlider.style.background = 'linear-gradient(to right, var(--accent-tho, #5ce1e6) ' + pct + '%, #333 ' + pct + '%)';
    }

    function onYouTubeIframeAPIReady() {
      ytPlayer = new YT.Player('hidden-player', {
        height: '1', width: '1',
        playerVars: { 
          'autoplay': 0, 
          'controls': 0, 
          'playsinline': 1,
          'listType': 'playlist',
          'list': 'PLDAIHOJ8ZsPo'
        },
        events: {
          'onReady': function() {
            var duration = ytPlayer.getDuration();
            seekSlider.max = duration;
            totalTimeDisplay.innerText = formatTime(duration);
          },
          'onStateChange': function(e) {
            if (e.data == YT.PlayerState.PLAYING) {
              isPlaying = true;
              playBtn.classList.add('playing');
              progressInterval = setInterval(function() {
                if (!isDragging && ytPlayer && ytPlayer.getCurrentTime) {
                  var current = ytPlayer.getCurrentTime();
                  seekSlider.value = current;
                  currentTimeDisplay.innerText = formatTime(current);
                  updateSliderColor();
                  
                  var duration = ytPlayer.getDuration();
                  if (seekSlider.max != duration) {
                    seekSlider.max = duration;
                    totalTimeDisplay.innerText = formatTime(duration);
                  }
                }
              }, 1000);
            } else {
              isPlaying = false;
              playBtn.classList.remove('playing');
              clearInterval(progressInterval);
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

    seekSlider.addEventListener('input', function() {
      isDragging = true;
      currentTimeDisplay.innerText = formatTime(this.value);
      updateSliderColor();
    });
    
    seekSlider.addEventListener('change', function() {
      if (ytPlayer && ytPlayer.seekTo) ytPlayer.seekTo(this.value, true);
      isDragging = false;
    });
  </script>
</body>
</html>
