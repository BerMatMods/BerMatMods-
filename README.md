
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
  <title>Con Amor, Para Ti 💖</title>
  <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@700&family=Poppins:wght@500;600&family=Great+Vibes&display=swap" rel="stylesheet">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Poppins', sans-serif;
      background: linear-gradient(135deg, #fff5f8, #f8bbd0);
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      justify-content: flex-start;
      align-items: center;
      overflow: hidden;
      position: relative;
      touch-action: none;
      color: #c2185b;
      user-select: none;
    }

    /* === PANTALLA DE BLOQUEO (full screen, difuminado) === */
    #lock-screen {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, 0.75);
      backdrop-filter: blur(8px);
      z-index: 9999;
      display: flex;
      justify-content: center;
      align-items: center;
      text-align: center;
    }

    /* === CUADRO DE ADVERTENCIA CON X DENTRO === */
    .warning-box {
      position: relative;
      width: 85%;
      max-width: 400px;
      background: rgba(30, 0, 40, 0.95);
      border: 3px solid #ff4081;
      border-radius: 20px;
      padding: 30px 20px 25px;
      color: #f8bbd0;
      font-family: 'Poppins', sans-serif;
      box-shadow: 
        0 0 20px rgba(255, 64, 129, 0.6),
        0 0 40px rgba(233, 30, 99, 0.4);
      backdrop-filter: blur(10px);
      z-index: 10000;
    }

    .close-btn {
      position: absolute;
      top: -12px;
      right: -12px;
      width: 32px;
      height: 32px;
      background: #ff1744;
      color: white;
      font-size: 20px;
      font-weight: bold;
      border-radius: 50%;
      display: flex;
      justify-content: center;
      align-items: center;
      cursor: pointer;
      box-shadow: 0 0 10px rgba(0,0,0,0.6);
      transition: all 0.3s ease;
    }

    .close-btn:hover {
      transform: scale(1.1);
      background: #e91e63;
    }

    .warning-title {
      font-family: 'Montserrat', sans-serif;
      font-size: 24px;
      color: #ff80ab;
      margin-bottom: 15px;
      text-shadow: 0 0 8px rgba(255, 64, 129, 0.5);
    }

    .warning-text {
      font-size: 16px;
      line-height: 1.6;
      color: #f8bbd0;
      margin-bottom: 20px;
    }

    .follow-btn {
      font-family: 'Poppins', sans-serif;
      font-size: 17px;
      font-weight: 600;
      background: #ff4081;
      color: white;
      border: none;
      padding: 12px 30px;
      border-radius: 30px;
      cursor: pointer;
      box-shadow: 0 0 20px rgba(255, 64, 129, 0.7);
      transition: all 0.3s ease;
    }

    .follow-btn:hover {
      background: #e91e63;
      transform: scale(1.05);
    }

    /* === LLUVIA DE PALABRAS EN BLOQUEO === */
    .lock-word {
      position: absolute;
      top: -50px;
      font-family: 'Poppins', sans-serif;
      font-size: 26px;
      font-weight: 600;
      color: #ff80ab;
      pointer-events: none;
      opacity: 0;
      white-space: nowrap;
      z-index: 9998;
      animation: fallLock linear forwards;
      text-shadow: 0 0 10px #ff4081;
    }

    @keyframes fallLock {
      0% { transform: translateY(0); opacity: 0; }
      10% { opacity: 1; }
      100% { transform: translateY(120vh); opacity: 0; }
    }

    /* === TÍTULO UNIVERSAL === */
    .title {
      font-family: 'Montserrat', sans-serif;
      font-size: 38px;
      font-weight: 700;
      color: #ff4081;
      text-align: center;
      margin: 30px 20px 40px;
      padding: 20px 30px;
      z-index: 10;
      background: rgba(255, 245, 248, 0.4);
      border-radius: 20px;
      box-shadow: 
        0 0 15px #ff80ab,
        0 0 30px #ff4081,
        0 0 50px #e91e63,
        0 0 70px rgba(233, 30, 99, 0.5);
      text-shadow: 
        0 0 10px #ff80ab,
        0 0 20px #e91e63,
        0 0 40px #ff4081;
      border: 3px solid #ff1744;
      backdrop-filter: blur(8px);
      animation: pulse 2s infinite alternate;
    }

    @keyframes pulse {
      from { transform: scale(1); }
      to { transform: scale(1.05); }
    }

    /* === LLUVIA DE PALABRAS ROMÁNTICAS (sorpresa) === */
    .romantic-word {
      position: absolute;
      top: -50px;
      font-family: 'Poppins', sans-serif;
      font-size: 24px;
      font-weight: 600;
      color: #e91e63;
      pointer-events: none;
      opacity: 0;
      white-space: nowrap;
      z-index: 1;
      transform: none;
      animation: fallWords linear forwards;
      text-shadow: 
        0 0 10px #ff80ab,
        0 0 20px #ff4081;
    }

    @keyframes fallWords {
      0% { transform: translateY(0); opacity: 0; }
      10% { opacity: 1; }
      100% { transform: translateY(130vh); opacity: 0; }
    }

    /* === CORAZONES FLOTANTES === */
    .floating-heart {
      position: absolute;
      pointer-events: none;
      font-size: 16px;
      opacity: 0.8;
      z-index: 2;
      animation: floatUp linear infinite;
      filter: drop-shadow(0 0 8px #ff4081);
    }

    @keyframes floatUp {
      0% { transform: translateY(100vh); opacity: 0; }
      10% { opacity: 1; }
      100% { transform: translateY(-10vh); opacity: 0; }
    }

    /* === MARIPOSAS VOLANDO === */
    .butterfly {
      position: absolute;
      width: 40px;
      height: 40px;
      background-image: url('https://i.pinimg.com/originals/7f/6e/5f/7f6e5f1d5b9f4e9d3c9c9c9c9c9c9c9c.png');
      background-size: contain;
      background-repeat: no-repeat;
      filter: drop-shadow(0 0 10px #ff80ab);
      z-index: 2;
      opacity: 0.9;
      animation: fly linear infinite;
    }

    @keyframes fly {
      0% { transform: translateX(-100px) translateY(100vh) rotate(20deg); }
      100% { transform: translateX(calc(100vw + 100px)) translateY(-20vh) rotate(-20deg); }
    }

    /* === CUBO 3D INTERACTIVO === */
    .container {
      width: 90vmin;
      height: 90vmin;
      max-width: 440px;
      max-height: 440px;
      perspective: 3000px;
      margin: 20px auto 40px;
      position: relative;
      z-index: 3;
      cursor: grab;
    }

    .cube {
      width: 100%;
      height: 100%;
      position: relative;
      transform-style: preserve-3d;
      transition: none;
      transform: rotateX(15deg) rotateY(25deg);
    }

    .face {
      position: absolute;
      width: 100%;
      height: 100%;
      box-shadow: 
        0 0 0 6px #ff1744,
        0 0 25px #ff4081,
        0 0 50px #e91e63,
        0 0 80px rgba(233, 30, 99, 0.5);
      border-radius: 12px;
      display: flex;
      justify-content: center;
      align-items: center;
      backface-visibility: visible;
      overflow: hidden;
    }

    .front  { transform: translateZ(110px); }
    .back   { transform: translateZ(-110px) rotateY(180deg); }
    .right  { transform: translateX(110px) rotateY(90deg); }
    .left   { transform: translateX(-110px) rotateY(-90deg); }
    .top    { transform: translateY(-110px) rotateX(90deg); }
    .bottom { transform: translateY(110px) rotateX(-90deg); }

    .gif-frame {
      width: 85%;
      height: 85%;
      border-radius: 14px;
      overflow: hidden;
      border: 4px solid #fff;
      box-shadow: 0 0 30px rgba(255, 105, 180, 0.9);
      background: rgba(255, 255, 255, 0.95);
    }

    .gif-frame img {
      width: 100%;
      height: auto;
      display: block;
    }

    /* === CARTA CON MOVIMIENTO 3D === */
    .letter-container {
      width: 90%;
      max-width: 460px;
      background: rgba(255, 245, 248, 0.7);
      border: 3px solid #ff1744;
      border-radius: 25px;
      padding: 30px;
      margin: 20px 20px 40px;
      position: relative;
      z-index: 4;
      backdrop-filter: blur(10px);
      box-shadow: 
        0 0 20px #ff80ab,
        0 0 40px rgba(233, 30, 99, 0.4);
      cursor: grab;
      transform-style: preserve-3d;
      transition: transform 0.1s ease;
    }

    .letter-container::before {
      content: '';
      position: absolute;
      inset: -6px;
      border-radius: 30px;
      border: 3px solid #ff4081;
      animation: pulse-border 1.5s infinite alternate;
      pointer-events: none;
      box-shadow: 0 0 30px rgba(233, 30, 99, 0.7);
    }

    @keyframes pulse-border {
      from { opacity: 0.7; }
      to { opacity: 1; box-shadow: 0 0 60px rgba(255, 64, 129, 0.9); }
    }

    .letter-title {
      font-family: 'Great Vibes', cursive;
      font-size: 38px;
      color: #d81b60;
      text-align: center;
      margin-bottom: 25px;
      text-shadow: 0 0 10px rgba(255, 64, 129, 0.5);
    }

    .letter-text {
      font-family: 'Poppins', sans-serif;
      font-size: 17px;
      color: #880e4f;
      line-height: 1.9;
      text-align: justify;
      margin-bottom: 18px;
    }

    .kiss-gif {
      display: flex;
      justify-content: center;
      margin: 20px 0;
    }

    .kiss-frame {
      width: 130px;
      height: 130px;
      border: 4px solid #fff;
      border-radius: 20px;
      overflow: hidden;
      box-shadow: 0 0 25px rgba(255, 105, 180, 0.8);
      background: #fff;
    }

    .kiss-frame img {
      width: 100%;
      height: auto;
      display: block;
    }

    .letter-signature {
      font-family: 'Great Vibes', cursive;
      font-size: 26px;
      color: #b71c1c;
      text-align: right;
      margin-top: 20px;
      font-style: italic;
      text-shadow: 0 0 8px rgba(255, 64, 129, 0.5);
    }

    /* === CORAZONES DE EXPLOSIÓN === */
    .heart-particle {
      position: absolute;
      font-size: 24px;
      pointer-events: none;
      z-index: 1000;
      opacity: 0;
      user-select: none;
      filter: drop-shadow(0 0 10px #ff4081) saturate(1.8) brightness(1.4);
    }

    /* === BOTÓN DE MÚSICA === */
    #music-button {
      position: fixed;
      bottom: 20px;
      right: 20px;
      z-index: 100;
      background: #ff4081;
      color: white;
      border: none;
      padding: 10px 15px;
      border-radius: 20px;
      font-size: 14px;
      cursor: pointer;
      box-shadow: 0 0 15px rgba(255, 64, 129, 0.7);
      transition: all 0.3s ease;
    }

    #music-button:hover {
      transform: scale(1.05);
      background: #e91e63;
    }

    /* === RELOJ DE PERÚ (solo después del desbloqueo) === */
    .clock-container {
      width: 90%;
      max-width: 400px;
      background: rgba(255, 245, 248, 0.6);
      border: 3px solid #ff4081;
      border-radius: 20px;
      padding: 15px;
      margin: 10px 0 30px;
      text-align: center;
      z-index: 5;
      backdrop-filter: blur(6px);
      box-shadow: 
        0 0 15px #ff80ab,
        0 0 30px rgba(233, 30, 99, 0.4);
    }

    .clock-title {
      font-family: 'Poppins', sans-serif;
      font-size: 16px;
      color: #d81b60;
      margin-bottom: 5px;
      font-weight: 600;
    }

    .clock {
      font-family: 'Montserrat', sans-serif;
      font-size: 22px;
      color: #e91e63;
      font-weight: 700;
      letter-spacing: 1px;
    }

    /* === Firma del creador === */
    .signature {
      position: absolute;
      bottom: 20px;
      left: 50%;
      transform: translateX(-50%);
      font-family: 'Poppins', sans-serif;
      font-size: 18px;
      font-weight: 600;
      color: #d81b60;
      z-index: 10;
      text-shadow: 
        0 0 10px #ff80ab,
        0 0 20px #ff4081;
      background: rgba(255, 255, 255, 0.3);
      padding: 8px 20px;
      border-radius: 15px;
      backdrop-filter: blur(5px);
    }
  </style>
</head>
<body>

  <!-- === PANTALLA DE BLOQUEO === -->
  <div id="lock-screen">
    <!-- Lluvia de palabras en toda la pantalla -->
    <script>
      const lockWords = ['Sígueme en TikTok 💖', 'Sígueme @bermat_mods', 'No te lo pierdas 💕', 'Te espera algo lindo 🌸', 'Sígueme ya ❤️', 'Solo un follow 💝'];
      
      function createLockWord() {
        const w = document.createElement('div');
        w.className = 'lock-word';
        w.textContent = lockWords[Math.floor(Math.random() * lockWords.length)];
        w.style.left = Math.random() * 90 + 5 + 'vw';
        w.style.animationDuration = (6 + Math.random() * 8) + 's';
        document.getElementById('lock-screen').appendChild(w);
        setTimeout(() => w.remove(), 10000);
      }

      setInterval(createLockWord, 300);
      for (let i = 0; i < 30; i++) setTimeout(createLockWord, 200 * i);
    </script>

    <!-- Cuadro bonito con advertencia -->
    <div class="warning-box">
      <div class="close-btn" onclick="document.getElementById('alert').style.display='block';">×</div>
      <h3 class="warning-title">🎁 ¡Sorpresa Especial!</h3>
      <p class="warning-text">
        Para ver esta dedicatoria, debes seguir a <strong>@bermat_mods</strong> en TikTok.
      </p>
      <button class="follow-btn" onclick="followTikTok()">Seguir en TikTok</button>
    </div>

    <!-- Alerta si cierra sin seguir -->
    <div class="warning-box" id="alert" style="display:none; position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%); width: 85%; max-width: 350px;">
      <div class="close-btn" onclick="this.parentElement.style.display='none';">×</div>
      <h3 class="warning-title">⚠️ Advertencia</h3>
      <p class="warning-text">
        El sistema ha detectado que no me siguió en TikTok. Por favor, sígueme para ver la sorpresa.
      </p>
      <button class="follow-btn" onclick="followTikTok()">Seguir ahora</button>
    </div>
  </div>

  <!-- === CONTENIDO DE LA SORPRESA (se muestra después del desbloqueo) === -->

  <!-- TÍTULO -->
  <h1 class="title">Con Amor, Para Ti 💖</h1>

  <!-- LLUVIA DE PALABRAS ROMÁNTICAS -->
  <script>
    const palabras = ['Amor', 'Eternidad', 'Mi vida', 'Siempre', 'Corazón', 'Tuyo', 'Nunca te suelto', 'Alma gemela', 'Te amo', 'Mi todo', 'Feliz contigo', 'Sólo tú', 'Te necesito', 'Hoy y siempre', 'Mi amor', 'Te adoro'];
    
    function crearPalabra() {
      const p = document.createElement('div');
      p.className = 'romantic-word';
      const palabra = palabras[Math.floor(Math.random() * palabras.length)];
      p.innerHTML = `💖 ${palabra}`;
      p.style.left = Math.random() * 80 + 10 + 'vw';
      p.style.animationDuration = (6 + Math.random() * 8) + 's';
      p.style.opacity = 0;
      document.body.appendChild(p);
      setTimeout(() => { p.style.opacity = 1; }, 50);
      setTimeout(() => { if (p.parentNode) p.remove(); }, 10000);
    }

    setInterval(crearPalabra, 200);
    for (let i = 0; i < 40; i++) setTimeout(crearPalabra, 100 * i);
  </script>

  <!-- CORAZONES FLOTANTES -->
  <script>
    const hearts = ['💖', '💗', '💕', '💓', '❤️', '💘', '💝'];
    setInterval(() => {
      const heart = document.createElement('div');
      heart.className = 'floating-heart';
      heart.textContent = hearts[Math.floor(Math.random() * hearts.length)];
      heart.style.left = Math.random() * 100 + 'vw';
      heart.style.opacity = 0;
      heart.style.animationDuration = (8 + Math.random() * 10) + 's';
      document.body.appendChild(heart);
      setTimeout(() => heart.remove(), 12000);
    }, 800);
  </script>

  <!-- MARIPOSAS VOLANDO -->
  <script>
    setInterval(() => {
      const butterfly = document.createElement('div');
      butterfly.className = 'butterfly';
      butterfly.style.left = '-100px';
      butterfly.style.top = (Math.random() * 80 + 10) + 'vh';
      butterfly.style.animationDuration = (30 + Math.random() * 20) + 's';
      butterfly.style.opacity = Math.random() * 0.6 + 0.4;
      document.body.appendChild(butterfly);
      setTimeout(() => butterfly.remove(), 50000);
    }, 5000);
  </script>

  <!-- CUBO 3D -->
  <div class="container" id="container">
    <div class="cube" id="cube">
      <div class="face front"><div class="gif-frame"><img src="https://media3.giphy.com/media/v1.Y2lkPTZjMDliOTUya2g4cjV4bDZlbzY0dGhmdGlvbG11emwzNTFpdjhoY3A2ZzM2cXAwdiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/A5VAEBsxxqLaU/giphy.gif" alt="Corazón"></div></div>
      <div class="face back"><div class="gif-frame"><img src="https://media3.giphy.com/media/v1.Y2lkPTZjMDliOTUya2g4cjV4bDZlbzY0dGhmdGlvbG11emwzNTFpdjhoY3A2ZzM2cXAwdiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/A5VAEBsxxqLaU/giphy.gif" alt="Corazón"></div></div>
      <div class="face right"><div class="gif-frame"><img src="https://media3.giphy.com/media/v1.Y2lkPTZjMDliOTUya2g4cjV4bDZlbzY0dGhmdGlvbG11emwzNTFpdjhoY3A2ZzM2cXAwdiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/A5VAEBsxxqLaU/giphy.gif" alt="Corazón"></div></div>
      <div class="face left"><div class="gif-frame"><img src="https://media3.giphy.com/media/v1.Y2lkPTZjMDliOTUya2g4cjV4bDZlbzY0dGhmdGlvbG11emwzNTFpdjhoY3A2ZzM2cXAwdiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/A5VAEBsxxqLaU/giphy.gif" alt="Corazón"></div></div>
      <div class="face top"><div class="gif-frame"><img src="https://media3.giphy.com/media/v1.Y2lkPTZjMDliOTUya2g4cjV4bDZlbzY0dGhmdGlvbG11emwzNTFpdjhoY3A2ZzM2cXAwdiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/A5VAEBsxxqLaU/giphy.gif" alt="Corazón"></div></div>
      <div class="face bottom"><div class="gif-frame"><img src="https://media3.giphy.com/media/v1.Y2lkPTZjMDliOTUya2g4cjV4bDZlbzY0dGhmdGlvbG11emwzNTFpdjhoY3A2ZzM2cXAwdiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/A5VAEBsxxqLaU/giphy.gif" alt="Corazón"></div></div>
    </div>
  </div>

  <!-- CARTA DE AMOR -->
  <div class="letter-container" id="letter">
    <h2 class="letter-title">Para Ti, Con Amor 💕</h2>
    <p class="letter-text">
      Hoy quiero recordarte lo especial que eres. Cada día a tu lado es un regalo, cada sonrisa tuya ilumina mi mundo.
    </p>
    <p class="letter-text">
      No hay palabras suficientes para expresar lo que siento. Solo sé que contigo todo tiene sentido, todo es más hermoso.
    </p>

    <div class="kiss-gif">
      <div class="kiss-frame">
        <img src="https://media3.giphy.com/media/v1.Y2lkPTZjMDliOTUyeWYwdWw0bjN6dWl4OGNvdTl4OHNpcmQ1MWVyNmlmbnIxd295dDJvdSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/D4hiJ8Oo1xOwUDOzyJ/giphy.gif" 
             alt="Beso de conejito">
      </div>
    </div>

    <p class="letter-text">
      Este momento, este amor, esta emoción… todo es para ti. Hoy y siempre.
    </p>
    <p class="letter-signature">— Con todo mi corazón 💖</p>
  </div>

  <!-- RELOJ DE PERÚ (solo después del desbloqueo) -->
  <div class="clock-container">
    <div class="clock-title">Hora en Perú 🇵🇪</div>
    <div class="clock" id="peru-clock">Cargando...</div>
  </div>

  <!-- BOTÓN DE MÚSICA -->
  <button id="music-button">🎶 Reproducir Música</button>

  <!-- Firma del creador -->
  <div class="signature">by AnthZz Berrocal • BerMatMods 💖</div>

  <!-- AUDIO -->
  <audio id="background-music" loop>
    <source src="https://cdn.pixabay.com/audio/2022/04/13/audio_7a3e0e5d9c.mp3" type="audio/mpeg">
  </audio>

  <!-- SCRIPTS -->
  <script>
    // Redirigir a TikTok
    function followTikTok() {
      window.open('https://www.tiktok.com/@bermat_mods', '_blank');
      setTimeout(() => {
        document.getElementById('lock-screen').style.display = 'none';
      }, 100);
    }

    // Música
    document.getElementById('music-button').addEventListener('click', () => {
      document.getElementById('background-music').play()
        .then(() => document.getElementById('music-button').style.display = 'none')
        .catch(() => alert("Por favor, interactúa con la página."));
    });

    // Reloj de Perú
    function updateClock() {
      const now = new Date();
      const timeStr = now.toLocaleTimeString('es-PE', { timeZone: 'America/Lima', hour: '2-digit', minute: '2-digit', second: '2-digit', hour12: true });
      const dateStr = now.toLocaleDateString('es-PE', { timeZone: 'America/Lima', weekday: 'short', year: 'numeric', month: 'short', day: 'numeric' });
      document.getElementById('peru-clock').textContent = `${timeStr} | ${dateStr}`;
    }
    setInterval(updateClock, 1000);
    updateClock();
  </script>

  <!-- ROTACIÓN 3D DEL CUBO -->
  <script>
    const container = document.getElementById('container');
    const cube = document.getElementById('cube');
    let isDragging = false;
    let startX, startY;
    let rotateX = 15;
    let rotateY = 25;

    container.addEventListener('mousedown', (e) => {
      isDragging = true;
      startX = e.clientX;
      startY = e.clientY;
      e.preventDefault();
    });

    container.addEventListener('touchstart', (e) => {
      isDragging = true;
      startX = e.touches[0].clientX;
      startY = e.touches[0].clientY;
      e.preventDefault();
    }, { passive: false });

    document.addEventListener('mousemove', (e) => {
      if (!isDragging) return;
      e.preventDefault();
      const deltaX = e.clientX - startX;
      const deltaY = e.clientY - startY;
      rotateY += deltaX * 0.5;
      rotateX -= deltaY * 0.5;
      cube.style.transform = `rotateX(${rotateX}deg) rotateY(${rotateY}deg)`;
      startX = e.clientX;
      startY = e.clientY;
    });

    document.addEventListener('touchmove', (e) => {
      if (!isDragging) return;
      e.preventDefault();
      const deltaX = e.touches[0].clientX - startX;
      const deltaY = e.touches[0].clientY - startY;
      rotateY += deltaX * 0.5;
      rotateX -= deltaY * 0.5;
      cube.style.transform = `rotateX(${rotateX}deg) rotateY(${rotateY}deg)`;
      startX = e.touches[0].clientX;
      startY = e.touches[0].clientY;
    }, { passive: false });

    document.addEventListener('mouseup', () => {
      isDragging = false;
    });

    document.addEventListener('touchend', () => {
      isDragging = false;
    });

    container.addEventListener('selectstart', (e) => e.preventDefault());
  </script>

  <!-- MOVIMIENTO DE LA CARTA Y EXPLOSIONES -->
  <script>
    const letter = document.getElementById('letter');
    let isMoving = false;
    let startXLetter, startYLetter;

    letter.addEventListener('mousedown', (e) => {
      isMoving = true;
      startXLetter = e.clientX;
      startYLetter = e.clientY;
      e.preventDefault();
    });

    letter.addEventListener('touchstart', (e) => {
      isMoving = true;
      startXLetter = e.touches[0].clientX;
      startYLetter = e.touches[0].clientY;
      e.preventDefault();
    }, { passive: false });

    document.addEventListener('mousemove', (e) => {
      if (!isMoving) return;
      const dx = e.clientX - startXLetter;
      const dy = e.clientY - startYLetter;
      const rotateY = (dx / 10) * 0.8;
      const rotateX = (-dy / 10) * 0.8;
      letter.style.transform = `rotateX(${rotateX}deg) rotateY(${rotateY}deg)`;
    });

    document.addEventListener('touchmove', (e) => {
      if (!isMoving) return;
      e.preventDefault();
      const dx = e.touches[0].clientX - startXLetter;
      const dy = e.touches[0].clientY - startYLetter;
      const rotateY = (dx / 10) * 0.8;
      const rotateX = (-dy / 10) * 0.8;
      letter.style.transform = `rotateX(${rotateX}deg) rotateY(${rotateY}deg)`;
    }, { passive: false });

    document.addEventListener('mouseup', () => {
      isMoving = false;
      letter.style.transform = 'rotateX(0deg) rotateY(0deg)';
    });

    document.addEventListener('touchend', () => {
      isMoving = false;
      setTimeout(() => {
        letter.style.transform = 'rotateX(0deg) rotateY(0deg)';
      }, 100);
    });

    // Explosión de corazones al tocar
    document.body.addEventListener('click', (e) => {
      createHeartExplosion(e.clientX, e.clientY);
    });

    document.body.addEventListener('touchstart', (e) => {
      const touch = e.touches[0];
      createHeartExplosion(touch.clientX, touch.clientY);
    });

    function createHeartExplosion(x, y) {
      const hearts = ['💖', '💗', '💕', '💓', '❤️', '💘', '💝'];
      for (let i = 0; i < 20; i++) {
        const heart = document.createElement('div');
        heart.className = 'heart-particle';
        heart.textContent = hearts[Math.floor(Math.random() * hearts.length)];
        heart.style.left = x + 'px';
        heart.style.top = y + 'px';
        heart.style.opacity = 0;
        document.body.appendChild(heart);

        const angle = Math.random() * 360;
        const distance = Math.random() * 140 + 60;
        const vx = Math.cos(angle) * distance;
        const vy = Math.sin(angle) * distance;

        setTimeout(() => {
          heart.style.transition = 'all 1.3s ease-out';
          heart.style.opacity = 1;
          heart.style.transform = `translate(${vx}px, ${vy}px) rotate(${Math.random() * 360}deg) scale(${Math.random() * 0.8 + 1.2})`;
        }, 10);

        setTimeout(() => heart.remove(), 1400);
      }
    }
  </script>

</body>
