
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Una Sorpresa Especial</title>
  <!-- Google Fonts -->
  <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Montserrat:wght@600;700&family=Poppins:wght@500;600&family=Playfair+Display:wght@700&display=swap" rel="stylesheet">
  <!-- Font Awesome -->
  <script src="https://kit.fontawesome.com/3b3b5f9a1a.js" crossorigin="anonymous"></script>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      margin: 0;
      padding: 0;
      height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      background: linear-gradient(135deg, #ff9a9e, #fecfef, #a8edea, #d2dcff);
      background-size: 600% 600%;
      animation: gradientBG 20s ease infinite;
      font-family: 'Poppins', sans-serif;
      overflow: hidden;
      position: relative;
      transition: background 0.8s ease, color 0.5s ease;
    }

    body.dark {
      background: linear-gradient(135deg, #1e3c72, #2a5298, #0f1f3a, #0a0a1a);
      color: #fff;
    }

    @keyframes gradientBG {
      0% { background-position: 0% 50%; }
      50% { background-position: 100% 50%; }
      100% { background-position: 0% 50%; }
    }

    /* ===== PANTALLA DE INICIO ===== */
    #start-screen {
      position: fixed;
      width: 100%;
      height: 100%;
      background: white;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      z-index: 1000;
      cursor: pointer;
      text-align: center;
      transition: all 0.6s ease;
    }

    .dark #start-screen {
      background: #0a0a1a;
    }

    #start-title {
      font-family: 'Playfair Display', serif;
      font-size: 2.8rem;
      color: #e91e63;
      margin-bottom: 20px;
      text-shadow: 0 0 15px rgba(233, 30, 99, 0.4);
    }

    .dark #start-title {
      color: #ff80ab;
      text-shadow: 0 0 20px rgba(255, 100, 180, 0.6);
    }

    #countdown {
      font-family: 'Dancing Script', cursive;
      font-size: 10rem;
      color: #e91e63;
      text-shadow: 0 0 25px rgba(255, 0, 100, 0.5);
      margin: 10px 0;
    }

    .dark #countdown {
      color: #ff80ab;
      text-shadow: 0 0 30px rgba(255, 100, 180, 0.7);
    }

    #instruction-start {
      font-family: 'Montserrat', sans-serif;
      font-size: 1.3rem;
      color: #555;
      margin-top: 15px;
      font-weight: 600;
    }

    .dark #instruction-start {
      color: #ddd;
    }

    .start-footer {
      position: absolute;
      bottom: 20px;
      width: 100%;
      text-align: center;
      font-size: 0.9rem;
      color: #777;
      font-style: italic;
    }

    .dark .start-footer {
      color: #aaa;
    }

    .start-footer a {
      color: #e91e63;
      text-decoration: none;
      font-weight: 600;
    }

    .btn-personalizar {
      margin-top: 15px;
      padding: 10px 20px;
      background: #e91e63;
      color: white;
      border: none;
      border-radius: 25px;
      font-family: 'Montserrat', sans-serif;
      font-size: 1rem;
      cursor: pointer;
      box-shadow: 0 4px 15px rgba(233, 30, 99, 0.4);
    }

    .dark .btn-personalizar {
      background: #ff4081;
    }

    /* ===== MENÚ HAMBURGUESA ===== */
    .menu-btn {
      position: fixed;
      top: 20px;
      left: 20px;
      z-index: 100;
      cursor: pointer;
      width: 50px;
      height: 50px;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      gap: 8px;
    }

    .menu-line {
      display: block;
      width: 30px;
      height: 4px;
      background: #333;
      border-radius: 2px;
      transition: 0.3s;
    }

    .dark .menu-line {
      background: #fff;
    }

    .menu-btn:hover .menu-line {
      background: #e91e63;
    }

    .menu-btn.active .menu-line:nth-child(1) {
      transform: rotate(45deg) translate(5px, 5px);
    }
    .menu-btn.active .menu-line:nth-child(2) {
      opacity: 0;
    }
    .menu-btn.active .menu-line:nth-child(3) {
      transform: rotate(-45deg) translate(5px, -5px);
    }

    /* Menú desplegable */
    .menu {
      position: fixed;
      top: 80px;
      left: 20px;
      background: rgba(255, 255, 255, 0.98);
      backdrop-filter: blur(10px);
      border-radius: 15px;
      box-shadow: 0 10px 30px rgba(0,0,0,0.2);
      width: 260px;
      padding: 15px;
      z-index: 99;
      display: none;
    }

    .dark .menu {
      background: rgba(30, 30, 50, 0.95);
      box-shadow: 0 10px 30px rgba(0,0,0,0.4);
    }

    .menu-item {
      padding: 12px 15px;
      font-size: 1rem;
      cursor: pointer;
      color: #333;
      display: flex;
      align-items: center;
      gap: 10px;
      transition: background 0.3s;
      border-radius: 8px;
      margin: 3px 0;
    }

    .dark .menu-item {
      color: #ddd;
    }

    .menu-item:hover {
      background: #ffebee;
    }

    .dark .menu-item:hover {
      background: rgba(255, 255, 255, 0.1);
    }

    .menu-item i {
      font-size: 1.2rem;
    }

    /* ===== TARJETA PRINCIPAL ===== */
    #card {
      display: none;
      width: 420px;
      max-width: 90vw;
      padding: 40px;
      background: rgba(255, 255, 255, 0.95);
      backdrop-filter: blur(10px);
      border-radius: 30px;
      box-shadow: 0 20px 50px rgba(0,0,0,0.15);
      text-align: center;
      z-index: 10;
      border: 1px solid rgba(255, 255, 255, 0.5);
    }

    .dark #card {
      background: rgba(30, 30, 50, 0.9);
      color: #fff;
      box-shadow: 0 20px 50px rgba(0,0,0,0.4);
    }

    h1 {
      font-family: 'Dancing Script', cursive;
      font-size: 5rem;
      color: #e91e63;
      margin: 0 0 15px 0;
      text-shadow: 2px 2px 10px rgba(255, 0, 100, 0.3);
    }

    .dark h1 {
      color: #ff80ab;
    }

    .subtitle {
      font-family: 'Montserrat', sans-serif;
      font-weight: 600;
      color: #d81b60;
      margin-bottom: 15px;
      font-size: 1.2rem;
    }

    .dark .subtitle {
      color: #ff80ab;
    }

    .instruction-card {
      font-family: 'Montserrat', sans-serif;
      font-weight: 600;
      color: #e91e63;
      font-size: 1.2rem;
      margin: 20px 0;
      padding: 12px;
      background: rgba(255, 235, 235, 0.6);
      border-radius: 15px;
      border: 2px dashed #ffcdd2;
    }

    .dark .instruction-card {
      background: rgba(233, 30, 99, 0.2);
      color: #ff80ab;
      border-color: #e91e63;
    }

    .message-container {
      min-height: 100px;
      color: #555;
      font-size: 1.1rem;
      line-height: 1.7;
      margin: 20px 0;
      text-align: left;
      padding: 15px;
      background: rgba(255, 248, 248, 0.7);
      border-radius: 12px;
      border-left: 5px solid #ec407a;
      font-family: 'Playfair Display', serif;
    }

    .dark .message-container {
      background: rgba(255, 255, 255, 0.1);
      color: #eee;
    }

    .gif-container {
      margin: 20px auto;
      width: 260px;
      height: 340px;
      border-radius: 18px;
      overflow: hidden;
      box-shadow: 0 8px 20px rgba(0,0,0,0.2);
      border: 3px solid #e91e63;
    }

    .dark .gif-container {
      border-color: #ff4081;
      box-shadow: 0 8px 20px rgba(0,0,0,0.5);
    }

    .gif-container img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    .btn-read-letter {
      margin: 15px auto;
      padding: 12px 24px;
      background: #e91e63;
      color: white;
      border: none;
      border-radius: 25px;
      font-family: 'Montserrat', sans-serif;
      font-size: 1.1rem;
      cursor: pointer;
      box-shadow: 0 4px 15px rgba(233, 30, 99, 0.4);
    }

    .dark .btn-read-letter {
      background: #ff4081;
    }

    .cake {
      font-size: 0;
      opacity: 0;
      transition: all 2s ease;
      margin: 25px auto 10px;
    }

    .cake.show {
      font-size: 5rem;
      opacity: 1;
    }

    /* Globos */
    .balloon {
      position: absolute;
      width: 60px;
      height: 70px;
      border-radius: 50%;
      cursor: pointer;
      background: #e91e63;
      display: flex;
      justify-content: center;
      align-items: center;
      color: white;
      font-size: 0.8rem;
      font-weight: bold;
      box-shadow: 0 5px 15px rgba(0,0,0,0.2);
      animation: float-balloon linear infinite;
      z-index: 5;
    }

    @keyframes float-balloon {
      0% { transform: translateY(100vh); }
      100% { transform: translateY(-200px); }
    }

    /* Mensaje al reventar */
    .floating-msg {
      position: absolute;
      background: white;
      color: #e91e63;
      padding: 10px 18px;
      border-radius: 20px;
      font-size: 1.1rem;
      font-weight: bold;
      box-shadow: 0 5px 15px rgba(0,0,0,0.1);
      white-space: nowrap;
      z-index: 300;
      opacity: 0;
      animation: rise-msg 3.5s ease-out forwards;
      font-family: 'Dancing Script', cursive;
    }

    @keyframes rise-msg {
      0% { transform: translateY(0); opacity: 0; }
      10% { opacity: 1; }
      100% { transform: translateY(-200px); opacity: 0; }
    }

    /* ===== EXPLOSIÓN DE CORAZONES AL TOCAR ===== */
    .heart-explosion {
      position: absolute;
      font-size: 2rem;
      opacity: 0;
      pointer-events: none;
      animation: expand-heart 0.8s ease-out forwards;
    }

    @keyframes expand-heart {
      0% { transform: scale(0); opacity: 0.8; }
      100% { transform: scale(2.5); opacity: 0; }
    }

    /* Corazones flotando desde arriba */
    .heart-fall {
      position: absolute;
      color: #e91e63;
      font-size: 1.8rem;
      opacity: 0.8;
      pointer-events: none;
      z-index: 1999;
      animation: fall-heart linear infinite;
    }

    @keyframes fall-heart {
      to { transform: translateY(105vh); }
    }

    /* Lluvia de palabras */
    .word-rain {
      position: absolute;
      top: -30px;
      font-family: 'Dancing Script', cursive;
      font-size: 1.4rem;
      color: rgba(233, 30, 99, 0.9);
      pointer-events: none;
      z-index: 1;
      text-shadow: 1px 1px 5px rgba(0,0,0,0.3);
      animation: fall-word linear forwards;
      opacity: 0.8;
    }

    @keyframes fall-word {
      to { transform: translateY(110vh) rotate(20deg); }
    }

    /* ===== CARTA ANIMADA ===== */
    #letter-screen {
      display: none;
      position: fixed;
      width: 100%;
      height: 100%;
      background: rgba(255, 240, 245, 0.95);
      justify-content: center;
      align-items: center;
      z-index: 2000;
    }

    .dark #letter-screen {
      background: rgba(20, 20, 40, 0.95);
    }

    .letter-card {
      width: 85%;
      max-width: 680px;
      height: 85%;
      background: white;
      border-radius: 25px;
      padding: 35px;
      position: relative;
      overflow-y: auto;
      box-shadow: 0 20px 60px rgba(0,0,0,0.2);
      border: 1px solid rgba(233, 30, 99, 0.1);
    }

    .dark .letter-card {
      background: #222436;
      color: #fff;
      border: 1px solid rgba(233, 30, 99, 0.3);
    }

    .letter-text {
      font-family: 'Playfair Display', serif;
      font-size: 1.5rem;
      color: #555;
      line-height: 1.9;
      text-align: justify;
      white-space: pre-line;
    }

    .dark .letter-text {
      color: #ddd;
    }

    .close-letter {
      position: absolute;
      top: 15px;
      right: 15px;
      background: #e91e63;
      color: white;
      border: none;
      width: 45px;
      height: 45px;
      border-radius: 50%;
      font-size: 1.3rem;
      cursor: pointer;
      box-shadow: 0 4px 15px rgba(233, 30, 99, 0.4);
      transition: all 0.3s;
      z-index: 10;
    }

    .close-letter:hover {
      transform: scale(1.1);
      background: #d81b60;
    }

    /* Créditos abajo */
    .footer-credits {
      position: fixed;
      bottom: 15px;
      width: 100%;
      text-align: center;
      font-size: 0.9rem;
      color: #666;
      font-style: italic;
      z-index: 10;
    }

    .dark .footer-credits {
      color: #aaa;
    }

    .footer-credits a {
      color: #e91e63;
      text-decoration: none;
      font-weight: 600;
    }
  </style>
</head>
<body>

  <!-- Pantalla de inicio -->
  <div id="start-screen">
    <h2 id="start-title">🎁 Una Sorpresa Especial</h2>
    <div id="countdown">5</div>
    <p id="instruction-start">Toca para continuar...</p>
    <button class="btn-personalizar" onclick="openWhatsApp()">💬 Personaliza</button>
    <div class="start-footer">
      by <strong>AnthZz Berrocal BerMat_Mods</strong><br>
      <a href="#" onclick="openWhatsApp(); return false;">WhatsApp: 930569195</a>
    </div>
  </div>

  <!-- Menú hamburguesa -->
  <div class="menu-btn" id="menuBtn">
    <span class="menu-line"></span>
    <span class="menu-line"></span>
    <span class="menu-line"></span>
  </div>

  <div class="menu" id="menu">
    <div class="menu-item" onclick="openWhatsApp()">
      <i class="fab fa-whatsapp"></i> Contáctame
    </div>
    <div class="menu-item" onclick="toggleDarkMode()">
      <i class="fas fa-moon"></i> <span id="themeText">Modo Oscuro</span>
    </div>
    <div class="menu-item">
      <i class="fas fa-user"></i> Creado por AnthZz
    </div>
  </div>

  <!-- Elementos flotantes globales -->
  <div id="hearts-container"></div>
  <div id="word-rain"></div>
  <div id="balloons"></div>

  <!-- Tarjeta principal -->
  <div id="card">
    <h1>🎉 ¡Feliz Cumpleaños!</h1>
    <p class="subtitle">Un día como hoy nació mi persona favorita</p>
    <p class="instruction-card">👉 Toca un globo</p>
    <div class="message-container" id="message"></div>
    
    <div class="gif-container">
      <img src="https://media4.giphy.com/media/v1.Y2lkPTZjMDliOTUybGhvdHI5bjFlajFuYzFxbGhmYTdnc3FsdHpqNG13a3BocTV2eXVpZCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/PEFmj0ePFm4iPKHFL5/giphy.gif" alt="Celebración">
    </div>

    <button class="btn-read-letter" onclick="openLetter()">📄 Leer Carta</button>
    <div class="cake" id="cake">🎂</div>
  </div>

  <!-- Carta -->
  <div id="letter-screen">
    <div class="letter-card">
      <button class="close-letter" onclick="closeLetter()">✕</button>
      <div class="letter-text" id="letter-text"></div>
    </div>
  </div>

  <!-- Contenedores internos -->
  <div id="hearts-in-letter"></div>
  <div id="words-in-letter"></div>

  <!-- Créditos -->
  <div class="footer-credits">
    by <strong>AnthZz Berrocal BerMat_Mods</strong> | <a href="#" onclick="openWhatsApp(); return false;">Haz tu pedido</a>
  </div>

  <script>
    // === Variables ===
    const startScreen = document.getElementById('start-screen');
    const countdown = document.getElementById('countdown');
    let count = 5;

    const menuBtn = document.getElementById('menuBtn');
    const menu = document.getElementById('menu');
    const card = document.getElementById('card');
    const letterScreen = document.getElementById('letter-screen');
    const letterText = document.getElementById('letter-text');

    const heartsContainer = document.getElementById('hearts-container');
    const wordRainContainer = document.getElementById('word-rain');
    const balloonsContainer = document.getElementById('balloons');

    const heartsInLetter = document.getElementById('hearts-in-letter') || createEl('hearts-in-letter');
    const wordsInLetter = document.getElementById('words-in-letter') || createEl('words-in-letter');

    function createEl(id) {
      const el = document.createElement('div');
      el.id = id;
      document.body.appendChild(el);
      return el;
    }

    // === Toque → Explosión de corazones ===
    document.body.addEventListener('click', (e) => {
      for (let i = 0; i < 12; i++) {
        const angle = (i / 12) * 2 * Math.PI;
        const x = e.clientX + Math.cos(angle) * 80;
        const y = e.clientY + Math.sin(angle) * 80;

        const heart = document.createElement('div');
        heart.className = 'heart-explosion';
        heart.innerHTML = '❤️';
        heart.style.left = x + 'px';
        heart.style.top = y + 'px';
        document.body.appendChild(heart);
        setTimeout(() => heart.remove(), 800);
      }
    });

    // === Inicio: cuenta regresiva ===
    startScreen.addEventListener('click', () => {
      if (count > 1) {
        count--;
        countdown.textContent = count;
      } else {
        startScreen.style.opacity = 0;
        setTimeout(() => {
          startScreen.style.display = 'none';
          showCard();
        }, 600);
      }
    });

    // === Mostrar tarjeta ===
    function showCard() {
      card.style.display = 'block';
      createBalloons();
      startFallingHearts();
      startWordRain();
      typeWriter();
    }

    // === Globos ===
    function createBalloons() {
      for (let i = 0; i < 15; i++) {
        const balloon = document.createElement('div');
        balloon.classList.add('balloon');
        balloon.style.left = Math.random() * 80 + 10 + 'vw';
        balloon.style.top = Math.random() * 80 + 20 + 'vh';
        balloon.style.animationDuration = (15 + Math.random() * 15) + 's';

        const msg = ["💖 Eres especial", "✨ Brilla siempre", "🎉 Hoy es tu día", "❤️ Te AMO", "🌟 Eres increíble"][Math.floor(Math.random() * 5)];
        balloon.dataset.message = msg;

        balloon.addEventListener('click', function(e) {
          const msgDiv = document.createElement('div');
          msgDiv.classList.add('floating-msg');
          msgDiv.textContent = balloon.dataset.message;
          msgDiv.style.left = (e.clientX - 60) + 'px';
          msgDiv.style.top = e.clientY + 'px';
          document.body.appendChild(msgDiv);
          setTimeout(() => msgDiv.remove(), 3500);
          balloon.remove();
        });
        balloonsContainer.appendChild(balloon);
      }
    }

    // === Corazones cayendo desde arriba ===
    function startFallingHearts() {
      setInterval(() => {
        const heart = document.createElement('div');
        heart.className = 'heart-fall';
        heart.innerHTML = '❤️';
        heart.style.left = Math.random() * 100 + 'vw';
        heart.style.animationDuration = (6 + Math.random() * 8) + 's';
        heartsContainer.appendChild(heart);
        setTimeout(() => heart.remove(), 10000);
      }, 700);
    }

    // === Lluvia de palabras ===
    function startWordRain() {
      setInterval(() => {
        const word = document.createElement('div');
        word.className = 'word-rain';
        word.textContent = ['Amor', 'Alegría', 'Magia', 'Brillo', 'Sonrisa', 'Felicidad'][Math.floor(Math.random() * 6)];
        word.style.left = Math.random() * 100 + 'vw';
        word.style.animationDuration = (6 + Math.random() * 8) + 's';
        wordRainContainer.appendChild(word);
        setTimeout(() => word.remove(), 10000);
      }, 800);
    }

    // === Texto que se escribe solo ===
    const text = "Hoy es un día muy especial porque tú estás aquí. Que este nuevo año de vida esté lleno de amor, alegría, salud y momentos inolvidables. Siempre crece, siempre sueña, siempre ama.";
    let index = 0;
    function typeWriter() {
      if (index < text.length) {
        document.getElementById('message').textContent += text.charAt(index);
        index++;
        setTimeout(typeWriter, 40);
      } else {
        setTimeout(() => {
          document.getElementById('cake').style.fontSize = '5rem';
          document.getElementById('cake').style.opacity = 1;
        }, 1000);
      }
    }

    // === Carta larga y universal ===
    const longLetter = `¡Feliz Cumpleaños! 🎉\n\nHoy es un día mágico ✨ porque el universo celebra tu existencia. Eres una persona única 💖, llena de luz, bondad y fuerza interior. Que este nuevo año de vida te traiga infinitas razones para sonreír 😊, amar ❤️ y vivir cada momento con pasión 🔥.\n\nQue nunca te falte salud 💪, que el amor te acompañe siempre 💌, que los sueños se hagan realidad ✨ y que encuentres motivos para seguir adelante incluso en los días difíciles 🌈.\n\nEres capaz de grandes cosas 🚀, mereces lo mejor 🏆 y el mundo es más hermoso contigo 🌍.\n\nDisfruta cada instante, celebra tu ser, ríe fuerte, abraza fuerte, vive pleno 💃🕺.\n\nTe deseo lo mejor en este nuevo ciclo: paz, éxito, alegría y muchísimo amor.\n\nCon cariño y magia ✨,\FELIZ CUMPLEAÑOS🎁`;

    function openLetter() {
      letterScreen.style.display = 'flex';
      startHeartsInLetter();
      startWordsInLetter();
      typeLetterText();
    }

    function closeLetter() {
      letterScreen.style.display = 'none';
      heartsInLetter.innerHTML = '';
      wordsInLetter.innerHTML = '';
    }

    // === Corazones en carta ===
    function startHeartsInLetter() {
      setInterval(() => {
        const heart = document.createElement('div');
        heart.className = 'heart-fall';
        heart.innerHTML = '❤️';
        heart.style.left = Math.random() * 100 + 'vw';
        heart.style.top = Math.random() * 80 + 'vh';
        heart.style.animationDuration = (8 + Math.random() * 10) + 's';
        heartsInLetter.appendChild(heart);
        setTimeout(() => heart.remove(), 15000);
      }, 600);
    }

    // === Palabras en carta ===
    function startWordsInLetter() {
      setInterval(() => {
        const word = document.createElement('div');
        word.className = 'word-rain';
        word.textContent = ['Amor', 'Alegría', 'Magia', 'Brillo', 'Sonrisa'][Math.floor(Math.random() * 5)];
        word.style.left = Math.random() * 100 + 'vw';
        word.style.animationDuration = (6 + Math.random() * 8) + 's';
        wordsInLetter.appendChild(word);
        setTimeout(() => word.remove(), 10000);
      }, 900);
    }

    // === Carta que se escribe sola ===
    let letterIndex = 0;
    function typeLetterText() {
      letterText.textContent = '';
      const timer = setInterval(() => {
        if (letterIndex < longLetter.length) {
          letterText.textContent += longLetter.charAt(letterIndex);
          letterIndex++;
        } else {
          clearInterval(timer);
        }
      }, 30);
    }

    // === Menú funcional ===
    menuBtn.addEventListener('click', () => {
      menuBtn.classList.toggle('active');
      menu.classList.toggle('active');
    });

    function openWhatsApp() {
      window.open('https://wa.me/51930569195', '_blank');
    }

    function toggleDarkMode() {
      document.body.classList.toggle('dark');
      document.getElementById('themeText').textContent = document.body.classList.contains('dark') ? 'Modo Claro' : 'Modo Oscuro';
    }
  </script>
</body>
</html>
