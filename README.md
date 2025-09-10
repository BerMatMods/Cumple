
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover, user-scalable=no">
    <meta property="og:title" content="Te Amo muchísimo mi reina ">
    <title>Te Amo muchísimo mi reina </title>
    <meta name="referrer" content="strict-origin-when-cross-origin">
    <link rel="icon" type="image/png" href="./assets/ico_logo.png" sizes="16x16">
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Noto+Sans:wght@300;400;500;700&family=Noto+Sans+JP:wght@300;400;500;700&family=Noto+Sans+KR:wght@300;400;500;700&family=Noto+Sans+SC:wght@300;400;500;700&family=Noto+Sans+TC:wght@300;400;500;700&family=Noto+Sans+Arabic:wght@300;400;500;700&family=Noto+Sans+Devanagari:wght@300;400;500;700&family=Noto+Sans+Hebrew:wght@300;400;500;700&family=Noto+Sans+Thai:wght@300;400;500;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">
    <link href="/es/PagMemoriCorazon/assets/style.css" rel="stylesheet">
    <script type="importmap">
    {
      "imports": {
        "three": "https://cdn.jsdelivr.net/npm/three@0.157.0/build/three.module.js",
        "three/examples/jsm/": "https://cdn.jsdelivr.net/npm/three@0.157.0/examples/jsm/"
      }
    }
    </script>
    <style>
        .text-white {
            color: white !important;
        }

        .btn-fullscreen-toggle {
            background-color: rgba(255, 105, 180, 0.3);
            border: 1px solid rgba(255, 105, 180, 0.5);
            border-radius: 50%;
            cursor: pointer;
            padding: 10px;
            transition: all 0.3s ease;
        }

        .btn-fullscreen-toggle:hover {
            background-color: rgba(255, 105, 180, 0.6);
            transform: scale(1.1);
            box-shadow: 0 0 15px rgba(255, 105, 180, 0.5);
        }

        body.portrait-mode #landscape-warning {
            display: flex;
            opacity: 1;
        }

        /* ---- MÀN HÌNH CẢNH BÁO XOAY NGANG ---- */
        #landscape-warning {
            position: fixed;
            z-index: 9999;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: radial-gradient(ellipse at center, #1c1a3a 0%, #0c0a1f 100%);
            color: #e0eaff;
            display: none;
            justify-content: center;
            align-items: center;
            text-align: center;
            opacity: 0;
            pointer-events: none;
            transition: opacity 0.5s ease-in-out;
        }

        body.portrait #landscape-warning {
            display: flex;
            opacity: 1;
            pointer-events: auto;
        }

        #landscape-warning .warning-content {
            position: relative;
            z-index: 2;
            padding: 2rem 2.5rem;
            border-radius: 20px;
            background: rgba(28, 26, 58, 0.6);
            backdrop-filter: blur(10px);
            border: 1.5px solid rgba(173, 216, 230, 0.3);
            box-shadow:
                0 0 40px rgba(78, 88, 216, 0.5),
                0 0 15px rgba(255, 255, 255, 0.1),
                inset 0 0 8px rgba(173, 216, 230, 0.2);
            transform: scale(0.95);
            opacity: 0;
            animation: fadeInContent 0.6s 0.2s cubic-bezier(0.165, 0.84, 0.44, 1) forwards;
        }

        @keyframes fadeInContent {
            to {
                transform: scale(1);
                opacity: 1;
            }
        }

        #landscape-warning h1 {
            font-family: 'Orbitron', 'Montserrat', sans-serif;
            font-size: 2rem;
            margin-bottom: 0.5rem;
            letter-spacing: 1.5px;
            color: #ffffff;
            text-shadow: 0 0 12px rgba(230, 230, 255, 0.8), 0 0 4px rgba(255, 255, 255, 1);
        }

        #landscape-warning h1:nth-of-type(2) {
            font-size: 1.5rem;
            margin-bottom: 1.5rem;
            opacity: 0.8;
        }

        #landscape-warning p {
            font-size: 1.1rem;
            color: #c0c8ff;
            line-height: 1.5;
            text-shadow: 0 0 6px rgba(192, 200, 255, 0.7);
        }

        #landscape-warning p:last-of-type {
            margin-top: 1rem;
            font-weight: bold;
            letter-spacing: 1px;
        }

        #landscape-warning .stars-bg {
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            z-index: 1;
            pointer-events: none;
            background: transparent;
            overflow: hidden;
        }

        #landscape-warning .stars-bg::before,
        #landscape-warning .stars-bg::after {
            content: '';
            position: absolute;
            width: 200%;
            height: 200%;
            top: -50%;
            left: -50%;
            background-image:
                radial-gradient(circle, #fff 1px, transparent 1px),
                radial-gradient(circle, #c0c8ff 1px, transparent 1px),
                radial-gradient(circle, #fff 0.5px, transparent 0.5px);
            background-size: 100px 100px, 150px 150px, 60px 60px;
            background-position: 0 0, 50px 50px, 30px 30px;
            opacity: 0;
            animation: stars-move 30s linear infinite, fadeInStars 1s ease-out forwards;
        }

        #landscape-warning .stars-bg::after {
            background-size: 150px 150px, 80px 80px, 120px 120px;
            background-position: 75px 75px, 40px 40px, 10px 10px;
            animation-duration: 45s;
        }

        @keyframes fadeInStars {
            to {
                opacity: 0.6;
            }
        }

        @keyframes stars-move {
            from {
                transform: translateY(0);
            }

            to {
                transform: translateY(-50%);
            }
        }

        #romantic-title {
            position: absolute;
            left: 50%;
            transform: translate(-50%);
            color: #ffffff;
            font-size: 2.5rem;
            font-family: 'Noto Sans', cursive;
            text-align: center;
            max-width: 60%;
            line-height: 1.2;
            word-wrap: break-word;
            text-shadow: 0 0 15px #ff69b4, 0 0 5px #ffffff;
            animation: glow 2s ease-in-out infinite alternate;
            padding: 0 10px;
        }

        @keyframes glow {
            from {
                text-shadow: 0 0 10px #ff69b4, 0 0 5px #ffffff;
            }
            to {
                text-shadow: 0 0 20px #ff69b4, 0 0 10px #ffffff;
            }
        }

        @media (max-width: 600px) {
            #romantic-title {
                font-size: 1.5rem;
            }
        }

        .music-control {
      position: fixed;
      top: 20px;
      right: 20px;
      z-index: 1000;
      display: flex;
      flex-direction: column;
      align-items: center;
    }

    .music-btn {
      width: 50px;
      height: 50px;
      background: linear-gradient(135deg, #ff4d6d, #e6395c);
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: flex;
      align-items: center;
      justify-content: center;
      box-shadow: 0 5px 15px rgba(0, 0, 0, 0.4);
      transition: all 0.3s ease;
    }

    .music-btn:hover {
      transform: scale(1.1);
      box-shadow: 0 8px 20px rgba(255, 77, 109, 0.6);
    }

    .music-btn:active {
      transform: scale(0.95);
    }

    .music-btn svg {
      width: 24px;
      height: 24px;
      fill: #fff;
    }

    .volume-control {
      width: 120px;
      background: rgba(255, 255, 255, 0.15);
      padding: 10px;
      border-radius: 10px;
      box-shadow: 0 5px 15px rgba(0, 0, 0, 0.4);
      border: 1px solid rgba(255, 77, 109, 0.5);
      margin-top: 10px;
      display: none;
      opacity: 0;
      transform: translateY(-10px);
      transition: opacity 0.3s ease, transform 0.3s ease;
    }

    .volume-control.visible {
      display: block;
      opacity: 1;
      transform: translateY(0);
    }

    .volume-control input {
      width: 100%;
      height: 8px;
      background: rgba(255, 255, 255, 0.3);
      border-radius: 4px;
      outline: none;
      cursor: pointer;
      -webkit-appearance: none;
    }

    .volume-control input::-webkit-slider-thumb {
      -webkit-appearance: none;
      width: 16px;
      height: 16px;
      background: #ff4d6d;
      border-radius: 50%;
      box-shadow: 0 2px 5px rgba(0, 0, 0, 0.3);
    }

    .volume-control input::-moz-range-thumb {
      width: 16px;
      height: 16px;
      background: #ff4d6d;
      border-radius: 50%;
      box-shadow: 0 2px 5px rgba(0, 0, 0, 0.3);
      border: none;
    }

    /* Mobile adjustments */
    @media only screen and (max-width: 768px) {
      .music-control {
        right: 15px;
      }

      .music-btn {
        width: 35px;
        height: 35px;
      }

      .music-btn svg {
        width: 22px;
        height: 22px;
      }

      .volume-control {
        width: 100px;
        margin-top: 8px;
      }

      .volume-control input {
        height: 10px;
      }

      .volume-control input::-webkit-slider-thumb {
        width: 18px;
        height: 18px;
      }

      .volume-control input::-moz-range-thumb {
        width: 18px;
        height: 18px;
      }
    }
    </style>
</head>
<body style="overflow: hidden; position: fixed; width: 100%; height: 100%; background: radial-gradient(circle, #200020 0%, #000000 100%);">
    <h1 id="romantic-title">➪𝐁𝐞𝐫𝐌𝐚𝐭_𝐌𝐨𝐝𝐬𖤍</h1>
    <button id="toggle-fullscreen" class="text-white btn-fullscreen-toggle" style="position: absolute; top: 15px; left: 15px; z-index: 999;">
        <i id="fullscreen-icon" class="text-white fa-solid fa-expand"></i>
    </button>
        <div class="music-control">
    <button class="music-btn" id="musicBtn" aria-label="Toggle music">
      <svg id="playIcon" viewBox="0 0 24 24">
        <path d="M8 5v14l11-7z"/>
      </svg>
      <svg id="pauseIcon" viewBox="0 0 24 24" style="display: none;">
        <path d="M6 19h4V5H6zm8-14v14h4V5z"/>
      </svg>
    </button>
    <div class="volume-control" id="volumeControl">
      <input type="range" id="volumeSlider" min="0" max="1" step="0.01" value="0.5" aria-label="Volume control">
    </div>
  </div>
  <audio id="backgroundMusic" loop preload="auto">
    <source src="https://dedicapag.com/es/PagMemoriCorazon/musica.mp3" type="audio/mpeg">
    Tu navegador no soporta el elemento de audio.
  </audio>
        <script>
        window.dataMemoryHeartLoveLoom = {"template":"birthday-v2","data":{"title":"Te Amo much\u00edsimo mi reina ","messages":["Te amo much\u00edsimo mi amor ","Eres muy importante para m\u00ed","T\u00fa eres mi todo","Gracias por los momentos maravillosos","Gracias por estar al lado de m\u00ed","Es la persona que m\u00e1s amo"],"images":["https:\/\/dedicapag.com\/es\/PagMemoriCorazon\/uploads\/68c1da583cab4_descarga.jpeg","https:\/\/dedicapag.com\/es\/PagMemoriCorazon\/uploads\/68c1da583cfe0_1742316301125-2.jpg","https:\/\/dedicapag.com\/es\/PagMemoriCorazon\/uploads\/68c1da583d3bd_Screenshot-20250810-134752.jpg","https:\/\/dedicapag.com\/es\/PagMemoriCorazon\/uploads\/68c1da583d5ba_Screenshot-20250427-213138.jpg"],"heartColor":"#ff00ff"}};
    </script>
    <script type="module" src="https://dedicapag.com/es/PagMemoriCorazon/assets/script.js"></script>
    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const fullscreenManager = {
                toggleBtn: document.getElementById('toggle-fullscreen'),
                iconElement: document.getElementById('fullscreen-icon'),
                isFullscreen: function() {
                    return !!(document.fullscreenElement || document.webkitFullscreenElement || document.mozFullScreenElement || document.msFullscreenElement);
                },
                updateIcon: function() {
                    if (!this.iconElement) return;
                    if (this.isFullscreen()) {
                        this.iconElement.classList.remove('fa-expand');
                        this.iconElement.classList.add('fa-compress');
                    } else {
                        this.iconElement.classList.remove('fa-compress');
                        this.iconElement.classList.add('fa-expand');
                    }
                },
                toggle: function() {
                    if (!this.isFullscreen()) {
                        const element = document.documentElement;
                        if (element.requestFullscreen) {
                            element.requestFullscreen();
                        } else if (element.mozRequestFullScreen) {
                            element.mozRequestFullScreen();
                        } else if (element.webkitRequestFullscreen) {
                            element.webkitRequestFullscreen();
                        } else if (element.msRequestFullscreen) {
                            element.msRequestFullscreen();
                        }
                    } else {
                        if (document.exitFullscreen) {
                            document.exitFullscreen();
                        } else if (document.mozCancelFullScreen) {
                            document.mozCancelFullScreen();
                        } else if (document.webkitExitFullscreen) {
                            document.webkitExitFullscreen();
                        } else if (document.msExitFullscreen) {
                            document.msExitFullscreen();
                        }
                    }
                },
                init: function() {
                    if (this.toggleBtn) {
                        this.toggleBtn.addEventListener('click', () => this.toggle());
                        document.addEventListener('fullscreenchange', () => this.updateIcon());
                        document.addEventListener('webkitfullscreenchange', () => this.updateIcon());
                        document.addEventListener('mozfullscreenchange', () => this.updateIcon());
                        document.addEventListener('MSFullscreenChange', () => this.updateIcon());
                    }
                }
            };
            fullscreenManager.init();
        });
                function setupMusicControls() {
      const music = document.getElementById("backgroundMusic");
      const musicBtn = document.getElementById("musicBtn");
      const playIcon = document.getElementById("playIcon");
      const pauseIcon = document.getElementById("pauseIcon");
      const volumeSlider = document.getElementById("volumeSlider");
      const volumeControl = document.getElementById("volumeControl");

      if (!music || !musicBtn || !volumeSlider || !volumeControl) {
        console.error('Music or control elements not found');
        return;
      }

      music.volume = volumeSlider.value;

      music.load();
      music.currentTime = 0;
      music.play().then(() => {
        console.log('Autoplay successful at:', music.currentTime);
        playIcon.style.display = 'none';
        pauseIcon.style.display = 'block';
      }).catch(error => {
        console.warn('Autoplay blocked:', error.message);
      });

      function toggleMusic() {
        if (music.paused) {
          music.play().then(() => {
            console.log('Music playing at:', music.currentTime);
            playIcon.style.display = 'none';
            pauseIcon.style.display = 'block';
          }).catch(error => {
            console.error('Error playing audio:', error.message);
          });
        } else {
          music.pause();
          console.log('Music paused at:', music.currentTime);
          playIcon.style.display = 'block';
          pauseIcon.style.display = 'none';
        }
      }

      musicBtn.addEventListener('click', (e) => {
        e.stopPropagation();
        toggleMusic();
        if (!volumeControl.classList.contains('visible')) {
          volumeControl.classList.add('visible');
          clearTimeout(hideVolumeTimeout);
          hideVolumeTimeout = setTimeout(() => volumeControl.classList.remove('visible'), 2000);
        } else {
          volumeControl.classList.remove('visible');
        }
      });

      let hideVolumeTimeout = null;
      volumeSlider.addEventListener('input', (e) => {
        music.volume = e.target.value;
        console.log('Volume set to:', music.volume);
        clearTimeout(hideVolumeTimeout);
        volumeControl.classList.add('visible');
      });

      volumeSlider.addEventListener('change', () => {
        hideVolumeTimeout = setTimeout(() => volumeControl.classList.remove('visible'), 2000);
      });

      volumeControl.addEventListener('mouseenter', () => clearTimeout(hideVolumeTimeout));
      volumeControl.addEventListener('mouseleave', () => {
        hideVolumeTimeout = setTimeout(() => volumeControl.classList.remove('visible'), 2000);
      });

      volumeSlider.addEventListener('touchstart', (e) => {
        e.stopPropagation();
        clearTimeout(hideVolumeTimeout);
      });
      volumeSlider.addEventListener('touchend', () => {
        hideVolumeTimeout = setTimeout(() => volumeControl.classList.remove('visible'), 2000);
      });

      document.addEventListener('click', (e) => {
        if (!volumeControl.contains(e.target) && !musicBtn.contains(e.target)) {
          volumeControl.classList.remove('visible');
          clearTimeout(hideVolumeTimeout);
        }
      });

      music.addEventListener('loadeddata', () => console.log('Audio data loaded'));
      music.addEventListener('error', (e) => console.error('Audio error:', e.message));
      music.addEventListener('play', () => console.log('Music play event'));
      music.addEventListener('pause', () => console.log('Music pause event'));
    }

    // Initialize music controls
    setupMusicControls();
                
    </script>
</body>
</html>
