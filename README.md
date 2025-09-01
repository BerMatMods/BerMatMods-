
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Para Yorchis - by AnthZz Berrocal</title>
  <link href="https://fonts.googleapis.com/css2?family=Great+Vibes&family=Montserrat:ital,wght@0,400;1,500&display=swap" rel="stylesheet">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Montserrat', sans-serif;
      background: linear-gradient(135deg, #1a0030, #4a148c) url('https://www.transparenttextures.com/patterns/diamond.png');
      background-attachment: fixed;
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      overflow: hidden;
      position: relative;
      color: #fff;
      text-shadow: 0 1px 3px rgba(0,0,0,0.5);
    }

    /* === Lluvia infinita de corazones (nunca se eliminan) === */
    .heart {
      position: absolute;
      width: 20px;
      height: 20px;
      background: url('https://media0.giphy.com/media/v1.Y2lkPTc5c2JzN2RlZGZ2Z3J1cGJxM3VpZ2RiY2RlY2x4N2N4dGZ4N2J1dGJkZmVhN3R4NyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/11ZRCtksbOiime/giphy.webp') no-repeat;
      background-size: cover;
      pointer-events: none;
      z-index: 1;
      animation: fall linear infinite;
      opacity: 0.8;
    }

    @keyframes fall {
      0% {
        transform: translateY(-50px) rotate(0deg);
        opacity: 0;
      }
      10% {
        opacity: 0.8;
      }
      100% {
        transform: translateY(105vh) rotate(360deg);
        opacity: 0;
      }
    }

    /* === Escena centrada y responsive === */
    .scene {
      position: relative;
      width: 100%;
      max-width: 460px;
      height: 360px;
      perspective: 1200px;
      z-index: 5;
    }

    /* === Sobre realista === */
    .envelope-base {
      width: 100%;
      height: 100%;
      background: #ffebee;
      border: 2px solid #f48fb1;
      border-radius: 16px;
      box-shadow: 0 20px 50px rgba(0, 0, 0, 0.3), 0 0 30px rgba(255, 105, 180, 0.2);
      position: absolute;
      z-index: 2;
    }

    .envelope-flap {
      position: absolute;
      width: 0;
      height: 0;
      border-left: 50% solid transparent;
      border-right: 50% solid transparent;
      border-top: 180px solid #ffcdd2;
      top: 0;
      left: 0;
      transform-origin: top;
      transition: transform 1.8s cubic-bezier(0.82, 0.02, 0.62, 1);
      z-index: 4;
      border: 2px solid #f48fb1;
    }

    .envelope-flap.open {
      transform: rotateX(180deg);
    }

    /* === Cinta roja para jalar === */
    .red-ribbon {
      position: absolute;
      top: 170px;
      left: 50%;
      transform: translateX(-50%);
      width: 6px;
      height: 90px;
      background: linear-gradient(to bottom, #ff1744, #d50000);
      cursor: pointer;
      z-index: 6;
      box-shadow: 0 0 15px #ff1744;
      border-radius: 4px;
    }

    .red-ribbon::before,
    .red-ribbon::after {
      content: '';
      position: absolute;
      width: 20px;
      height: 20px;
      background: #ff1744;
      border-radius: 50%;
      top: 80px;
      transform: rotate(45deg);
    }

    .red-ribbon::before {
      left: -7px;
    }

    .red-ribbon::after {
      right: -7px;
    }

    /* === Carta interior (más grande, espacio para todo) === */
    .letter-paper {
      position: absolute;
      top: 40px;
      left: 40px;
      width: calc(100% - 80px);
      height: calc(100% - 80px);
      max-width: 380px;
      max-height: 280px;
      background: rgba(255, 248, 250, 0.98);
      backdrop-filter: blur(8px);
      border: 2px solid #ff4081;
      border-radius: 14px;
      padding: 26px;
      font-size: 15px;
      line-height: 1.75;
      text-align: center;
      color: #c2185b;
      z-index: 3;
      opacity: 0;
      transform: scale(0.9);
      transition: all 0.8s cubic-bezier(0.4, 0, 0.2, 1);
      box-shadow: 0 0 25px rgba(255, 64, 132, 0.5);
      overflow-y: auto;
      overflow-x: hidden;
    }

    .letter-paper.open {
      opacity: 1;
      transform: scale(1);
    }

    .letter-paper h2 {
      font-family: 'Great Vibes', cursive;
      font-size: 32px;
      color: #e91e63;
      margin-bottom: 16px;
      text-shadow: 0 0 6px rgba(255, 105, 180, 0.4);
    }

    .letter-paper p {
      margin: 10px 0;
      font-size: 15px;
    }

    /* === Firma estilizada === */
    .signature {
      font-family: 'Great Vibes', cursive;
      font-size: 19px;
      color: #d50000;
      margin-top: 20px;
      font-style: italic;
    }

    /* === GIF del beso - tamaño completo, sin recortar === */
    .gif-kiss {
      margin: 20px 0;
      position: relative;
      display: inline-block;
    }

    .gif-kiss::before {
      content: '';
      position: absolute;
      inset: -10px;
      border: 3px solid #ff4081;
      border-radius: 12px;
      animation: pulse-neon 2s infinite alternate;
      pointer-events: none;
      box-shadow: 0 0 15px #ff4081;
    }

    @keyframes pulse-neon {
      from {
        box-shadow: 0 0 15px #ff4081;
      }
      to {
        box-shadow: 0 0 30px #ff1744, 0 0 50px #ff4081;
      }
    }

    .gif-kiss img {
      width: 150px; /* Tamaño completo del GIF, claramente visible */
      height: auto;
      border: 3px solid #fff;
      border-radius: 0;
    }

    /* === Corazón animado abajo (GRANDE y completo) === */
    .footer-heart {
      position: absolute;
      bottom: 50px;
      left: 50%;
      transform: translateX(-50%);
      z-index: 10;
      animation: float-heart 3s infinite ease-in-out;
    }

    @keyframes float-heart {
      0%, 100% {
        transform: translateX(-50%) translateY(0);
      }
      50% {
        transform: translateX(-50%) translateY(-12px);
      }
    }

    .footer-heart img {
      width: 200px; /* Muy grande, se ve completo */
      height: auto;
      border: 4px solid #ff4081;
      border-radius: 0;
      box-shadow: 0 0 40px rgba(255, 64, 132, 0.9);
    }
  </style>
</head>
<body>

  <!-- Lluvia infinita de corazones -->
  <script>
    function createHeart() {
      const heart = document.createElement('div');
      heart.classList.add('heart');
      heart.style.left = Math.random() * 100 + 'vw';
      heart.style.animationDuration = (8 + Math.random() * 10) + 's';
      heart.style.width = (16 + Math.random() * 14) + 'px';
      heart.style.height = heart.style.width;
      document.body.appendChild(heart);
    }

    setInterval(createHeart, 350);
    for (let i = 0; i < 20; i++) setTimeout(createHeart, 200 * i);
  </script>

  <!-- Sobre con hilo -->
  <div class="scene">
    <div class="envelope-base"></div>
    <div class="envelope-flap" id="envelopeFlap"></div>
    <div class="red-ribbon" id="ribbon"></div>
  </div>

  <!-- Carta interior (con espacio para todo) -->
  <div class="letter-paper" id="letter">
    <h2>Para mi Yorchis</h2>
    <p>Desde que llegaste a mi vida, todo tiene más sentido, más color, más amor verdadero.</p>
    <p>Tu risa es mi música. Tu mirada, mi hogar. Tu corazón, el mío.</p>
    <p>Cada día contigo es un milagro que agradezco con el alma.</p>
    <p>Y hoy quiero que sepas…</p>
    <p>que te amo más de lo que las palabras pueden decir.</p>

    <!-- Beso de conejito - tamaño completo -->
    <div class="gif-kiss">
      <img src="https://media3.giphy.com/media/v1.Y2lkPTZjMDliOTUyeWYwdWw0bjN6dWl4OGNvdTl4OHNpcmQ1MWVyNmlmbnIxd295dDJvdSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/D4hiJ8Oo1xOwUDOzyJ/giphy.gif" 
           alt="Beso de conejito">
    </div>

    <p>Este beso es solo para ti, mi vida. ❤️</p>
    <div class="signature">— by AnthZz Berrocal BerMatMods 💖</div>
  </div>

  <!-- Corazón grande abajo (completo y brillante) -->
  <div class="footer-heart">
    <img src="https://media3.giphy.com/media/v1.Y2lkPTZjMDliOTUya2g4cjV4bDZlbzY0dGhmdGlvbG11emwzNTFpdjhoY3A2ZzM2cXAwdiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/A5VAEBsxxqLaU/giphy.gif" 
         alt="Corazón latiendo">
  </div>

  <!-- Interacción -->
  <script>
    const flap = document.getElementById('envelopeFlap');
    const ribbon = document.getElementById('ribbon');
    const letter = document.getElementById('letter');

    ribbon.addEventListener('click', () => {
      if (flap.classList.contains('open')) return;
      flap.classList.add('open');
      setTimeout(() => letter.classList.add('open'), 700);
    });

    ribbon.addEventListener('touchstart', e => {
      e.preventDefault();
      ribbon.click();
    });
  </script>

</body>
</html>
