
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no"/>
  <title>FELIZ DÍA DE LAS FLORES AMARILLAS</title>
  <link href="https://fonts.googleapis.com/css2?family=Quicksand:wght@500;600&family=Pacifico&display=swap" rel="stylesheet">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      background: #000;
      color: #fff;
      overflow: hidden;
      perspective: 3000px;
      cursor: grab;
      font-family: 'Quicksand', sans-serif;
    }

    body:active { cursor: grabbing; }

    /* Fondo de girasoles suave */
    body::before {
      content: '';
      position: fixed;
      top: 0; left: 0;
      width: 100%; height: 100%;
      background: url('https://i.postimg.cc/MTKPqRCZ/Girasoles.jpg');
      background-size: cover;
      filter: blur(12px);
      opacity: 0.1;
      z-index: -3;
    }

    /* Overlay cálido */
    .overlay {
      position: fixed;
      top: 0; left: 0;
      width: 100%; height: 100%;
      background: linear-gradient(135deg, rgba(10,5,0,0.8), rgba(20,10,0,0.95));
      z-index: -2;
    }

    /* Estrellas sutiles */
    .stars {
      position: fixed;
      width: 100%; height: 100%;
      pointer-events: none;
      z-index: -1;
    }

    .star {
      position: absolute;
      width: 2px; height: 2px;
      background: #fff9c4;
      border-radius: 50%;
      box-shadow: 0 0 6px #fff9c4;
      opacity: 0.7;
      animation: twinkle 4s infinite alternate;
    }

    @keyframes twinkle {
      to { opacity: 1; transform: scale(1.4); }
    }

    /* Escena 3D */
    .scene {
      position: fixed;
      width: 100vw;
      height: 100vh;
      transform-style: preserve-3d;
      transform: rotateX(10deg);
      transition: transform 0.1s ease;
    }

    /* Universos paralelos */
    .universe {
      position: absolute;
      width: 100%;
      height: 100%;
      transform-style: preserve-3d;
    }

    .universe-front { transform: translateZ(600px); }
    .universe-back { transform: translateZ(-600px) rotateY(180deg); }

    /* Contenedor */
    .container {
      position: absolute;
      top: 50%; left: 50%;
      transform: translate(-50%, -50%);
      transform-style: preserve-3d;
    }

    /* Título principal */
    .title {
      font-family: 'Pacifico', cursive;
      font-size: 5rem;
      color: #ffeb3b;
      text-align: center;
      text-shadow: 
        0 0 20px #ffeb3b,
        0 0 40px #fdd835,
        0 0 70px rgba(251,192,45,0.8);
      letter-spacing: 5px;
      margin: 4rem 0;
      transform: translateZ(200px);
    }

    /* Fase */
    .phase {
      transform-style: preserve-3d;
      margin: 12rem 0;
      opacity: 0;
      transition: opacity 2s ease;
    }

    .phase.visible {
      opacity: 1;
    }

    .phase h2 {
      font-family: 'Pacifico', cursive;
      font-size: 4rem;
      color: #fff352;
      text-shadow: 
        0 0 20px #fff352,
        0 0 40px #fdd835;
      margin-bottom: 2.5rem;
      transform: translateZ(150px);
    }

    /* Cuadro de texto */
    .text-box {
      background: rgba(30,20,0,0.6);
      border-radius: 24px;
      padding: 2.5rem;
      margin: 2rem auto;
      max-width: 800px;
      border: 3px solid #ffeb3b;
      box-shadow: 0 0 25px #fdd835;
      transform: translateZ(100px);
      position: relative;
    }

    .text-box::before {
      content: '';
      position: absolute;
      inset: 4px;
      border: 2px solid #fff352;
      border-radius: 20px;
      box-shadow: 0 0 15px #fff352;
      pointer-events: none;
    }

    .text-box p {
      font-size: 1.6rem;
      line-height: 2;
      color: #fff9c4;
      font-weight: 500;
    }

    .text-box em {
      color: #fff352;
      font-weight: 600;
    }

    /* Cubo 3D */
    .cube-container {
      width: 350px;
      height: 350px;
      perspective: 1000px;
      margin: 3rem auto;
      transform: translateZ(180px);
    }

    .cube {
      width: 100%;
      height: 100%;
      position: relative;
      transform-style: preserve-3d;
      transition: transform 0.1s ease;
    }

    .face {
      position: absolute;
      width: 350px;
      height: 350px;
      border: 4px solid #ffeb3b;
      border-radius: 16px;
      box-shadow: 0 0 25px #fdd835;
      overflow: hidden;
      display: flex;
      justify-content: center;
      align-items: center;
    }

    .face::before {
      content: '';
      position: absolute;
      inset: 4px;
      border: 1px solid #fff352;
      border-radius: 12px;
      box-shadow: 0 0 12px #fff352;
      pointer-events: none;
    }

    .face img {
      width: 90%;
      height: 90%;
      object-fit: cover;
      border-radius: 10px;
    }

    .front  { transform: translateZ(175px); }
    .back   { transform: rotateY(180deg) translateZ(175px); }
    .right  { transform: rotateY(90deg) translateZ(175px); }
    .left   { transform: rotateY(-90deg) translateZ(175px); }
    .top    { transform: rotateX(90deg) translateZ(175px); }
    .bottom { transform: rotateX(-90deg) translateZ(175px); }

    /* Créditos */
    .credits {
      transform: translateZ(150px);
      margin-top: 10rem;
      font-size: 1.4rem;
      color: #ccc;
      text-align: center;
    }

    .credits strong {
      color: #ffeb3b;
    }

    .credits em {
      color: #fdd835;
    }

    /* Palabras que caen */
    .word {
      position: absolute;
      font-family: 'Pacifico', cursive;
      font-size: 1.8rem;
      color: #ffeb3b;
      opacity: 0;
      pointer-events: none;
      z-index: 100;
      white-space: nowrap;
      text-shadow: 0 0 8px #ffeb3b;
      animation: fall 15s linear forwards;
    }

    .word.white {
      color: #fff;
      text-shadow: 0 0 8px #fff;
    }

    @keyframes fall {
      0% { transform: translateY(-100px); opacity: 0; }
      10% { opacity: 1; }
      100% { transform: translateY(1400px); opacity: 0; }
    }

    /* Explosión de frases */
    .burst {
      position: absolute;
      font-family: 'Pacifico', cursive;
      font-size: 1.5rem;
      color: #ffeb3b;
      opacity: 0;
      pointer-events: none;
      z-index: 2000;
      text-shadow: 0 0 10px #ffeb3b;
    }

    .burst.animate {
      animation: explode 2.2s ease-out forwards;
    }

    @keyframes explode {
      0% { transform: scale(0); opacity: 0; }
      15% { opacity: 1; }
      100% { transform: translate(var(--x), var(--y)) scale(2.2); opacity: 0; }
    }
  </style>
</head>
<body>

  <div class="overlay"></div>
  <div class="stars" id="stars"></div>

  <div class="scene" id="scene">
    
    <!-- Universo Delante -->
    <div class="universe universe-front">
      <div class="container">
        <h1 class="title">FELIZ DÍA DE LAS FLORES AMARILLAS</h1>
        <script>document.write(generatePhases())</script>
      </div>
    </div>

    <!-- Universo Detrás -->
    <div class="universe universe-back">
      <div class="container">
        <h1 class="title">FELIZ DÍA DE LAS FLORES AMARILLAS</h1>
        <script>document.write(generatePhases())</script>
      </div>
    </div>

  </div>

  <audio id="music" loop>
    <source src="https://cdn.pixabay.com/audio/2022/01/10/audio_7f7a9b5b25.mp3" type="audio/mpeg">
  </audio>

  <script>
    // Generar fases
    function generatePhases() {
      const phases = [
        { t: "Recuerdo", img1: "ramo-proncipal.jpg", img2: "Girasoles.jpg" },
        { t: "Esperanza", img1: "Girasoles.jpg", img2: "ramo-proncipal.jpg" },
        { t: "Amor", img1: "ramo-proncipal.jpg", img2: "Girasoles.jpg" },
        { t: "Eternidad", img1: "Girasoles.jpg", img2: "ramo-proncipal.jpg" }
      ];

      let html = '';
      phases.forEach(p => {
        html += `
        <div class="phase">
          <h2>${p.t}</h2>
          <div class="cube-container">
            <div class="cube">
              <div class="face front"><img src="https://i.postimg.cc/VNFGx4HH/${p.img1}"></div>
              <div class="face back"><img src="https://i.postimg.cc/VNFGx4HH/${p.img1}"></div>
              <div class="face right"><img src="https://i.postimg.cc/MTKPqRCZ/${p.img2}"></div>
              <div class="face left"><img src="https://i.postimg.cc/MTKPqRCZ/${p.img2}"></div>
              <div class="face top"><img src="https://i.postimg.cc/VNFGx4HH/${p.img1}"></div>
              <div class="face bottom"><img src="https://i.postimg.cc/MTKPqRCZ/${p.img2}"></div>
            </div>
          </div>
          <div class="text-box">
            <p><em>El amor verdadero</em> no se mide en días,<br>
            se mide en latidos.<br>
            Y tú,<br>
            <em>sigues siendo mi flor amarilla</em>,<br>
            mi luz en la oscuridad.</p>
          </div>
        </div>`;
      });

      html += `<div class="credits">
        🌼 Detalle virtual creado con amor por 
        <strong>AnthZz Berrocal</strong> | 
        <em>BerMatMods</em> | 
        <a href="https://github.com/tu-usuario" style="color:#fff352">GitHub Pages</a>
      </div>`;

      return html;
    }

    // Control 3D: automático + manual
    let rotX = 10, rotY = 0;
    let isDragging = false, startX, startY;
    const scene = document.getElementById('scene');

    // Giro automático lento
    setInterval(() => {
      if (!isDragging) {
        rotY += 0.1;
        scene.style.transform = `rotateX(${rotX}deg) rotateY(${rotY}deg)`;
      }
    }, 50);

    // Control manual
    scene.addEventListener('mousedown', e => {
      isDragging = true;
      startX = e.clientX;
      startY = e.clientY;
    });

    document.addEventListener('mousemove', e => {
      if (isDragging) {
        rotY += (e.clientX - startX) * 0.2;
        rotX -= (e.clientY - startY) * 0.2;
        scene.style.transform = `rotateX(${rotX}deg) rotateY(${rotY}deg)`;
        startX = e.clientX;
        startY = e.clientY;
      }
    });

    ['mouseup', 'mouseleave'].forEach(event => {
      document.addEventListener(event, () => isDragging = false);
    });

    // Touch para móvil
    scene.addEventListener('touchstart', e => {
      isDragging = true;
      startX = e.touches[0].clientX;
      startY = e.touches[0].clientY;
    });

    document.addEventListener('touchmove', e => {
      if (isDragging) {
        e.preventDefault();
        rotY += (e.touches[0].clientX - startX) * 0.2;
        rotX -= (e.touches[0].clientY - startY) * 0.2;
        scene.style.transform = `rotateX(${rotX}deg) rotateY(${rotY}deg)`;
        startX = e.touches[0].clientX;
        startY = e.touches[0].clientY;
      }
    }, { passive: false });

    document.addEventListener('touchend', () => isDragging = false);

    // Música al primer clic
    let musicStarted = false;
    document.addEventListener('click', () => {
      if (!musicStarted) {
        document.getElementById('music').play().catch(() => {});
        musicStarted = true;
      }
    }, { once: true });

    // Explosión de frases al tocar
    document.addEventListener('click', e => {
      const phrases = [
        "Te amo mi amor", "Eres mi reina", "Mi niña hermosa", "Mi vida", "Te adoro", 
        "Mi corazón", "Mi eternidad", "Eres todo", "Te extraño", "Mi alma gemela"
      ];
      for (let i = 0; i < 30; i++) {
        setTimeout(() => {
          const w = document.createElement('div');
          w.classList.add('burst');
          w.textContent = phrases[Math.floor(Math.random() * phrases.length)];
          w.style.left = `${e.clientX}px`;
          w.style.top = `${e.clientY}px`;

          const a = Math.random() * 360;
          const d = 80 + Math.random() * 200;
          const vx = Math.cos(a * Math.PI / 180) * d;
          const vy = Math.sin(a * Math.PI / 180) * d;

          w.style.setProperty('--x', `${vx}px`);
          w.style.setProperty('--y', `${vy}px`);

          document.body.appendChild(w);
          setTimeout(() => w.classList.add('animate'), 10);
          setTimeout(() => w.remove(), 2200);
        }, i * 10);
      }
    });

    // Lluvia de palabras amorosas
    const words = ["Amor", "Corazón", "Recuerdo", "Eternidad", "Luz", "Sonrisa", "Esperanza", "Flores", "Amarillo", "Siempre", "Tú", "Brillo", "Paz", "Abrazo", "Vida", "Destino", "Alma", "Verano", "Cariño", "Sueño", "Latido", "Eterno", "Flor", "Rostro", "Mañana", "Reina", "Hermosa", "Mi Todo", "Mi Amor", "Mi Vida"];
    setInterval(() => {
      const w = document.createElement('div');
      w.classList.add('word');
      if (Math.random() > 0.6) w.classList.add('white');
      w.textContent = words[Math.floor(Math.random() * words.length)];
      w.style.left = Math.random() * 100 + 'vw';
      w.style.top = '-50px';
      document.body.appendChild(w);
      setTimeout(() => w.remove(), 15000);
    }, 100);

    // Estrellas
    const stars = document.getElementById('stars');
    for (let i = 0; i < 250; i++) {
      const s = document.createElement('div');
      s.classList.add('star');
      s.style.left = Math.random() * 100 + '%';
      s.style.top = Math.random() * 100 + '%';
      s.style.opacity = Math.random() * 0.8 + 0.2;
      s.style.animationDelay = Math.random() * 5 + 's';
      stars.appendChild(s);
    }

    // Revelar fases al scroll
    window.addEventListener('scroll', () => {
      document.querySelectorAll('.phase').forEach(p => {
        const r = p.getBoundingClientRect();
        if (r.top < window.innerHeight * 0.8) p.classList.add('visible');
      });
    });
  </script>

</body>
</html>
