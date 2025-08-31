
<html lang="es">    
<head>    
  <meta charset="UTF-8" />    
  <meta name="viewport" content="width=device-width, initial-scale=1, user-scalable=no" />    
  <title>💖 Regalo para Aracely 💖</title>    

  <!-- Fuente manuscrita para la carta -->
  <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@500;700&display=swap" rel="stylesheet">

  <style>    
    :root {
      --pink1: #ff4e50;
      --pink2: #fc466b;
      --accent: #fff176;
      --bg1: #ffe259;
      --bg2: #ffa751;
      --bg3: #ff6a88;
      --bg4: #ff99ac;
      --ink: #333;
      --ink-strong: #e91e63;
    }    
    *, *::before, *::after {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }    
    html, body {
      height: 100%;
      font-family: system-ui, -apple-system, Segoe UI, Roboto, Ubuntu, Cantarell;
      color: var(--ink);
      overflow: hidden;
    }    
    body {
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      background: linear-gradient(270deg, var(--bg1), var(--bg2), var(--bg3), var(--bg4));
      background-size: 800% 800%;
      animation: gradientMove 12s ease infinite;
    }    
    @keyframes gradientMove {
      0% { background-position: 0% 50%; }
      50% { background-position: 100% 50%; }
      100% { background-position: 0% 50%; }
    }

    /* PANTALLA CLAVE */
    #lockScreen {
      position: fixed;
      inset: 0;
      background: #000000c9;
      display: flex;
      flex-direction: column;
      gap: 12px;
      justify-content: center;
      align-items: center;
      color: #fff;
      z-index: 9999;
      text-align: center;
      padding: 24px;
    }
    #lockScreen .panel {
      background: #111a;
      border: 1px solid #ffffff22;
      border-radius: 20px;
      padding: 24px 20px;
      backdrop-filter: blur(6px);
      width: min(92vw, 480px);
      max-height: 92vh;
      overflow: auto;
      box-shadow: 0 10px 30px #0008;
    }
    #lockScreen h2 {
      font-size: 1.4rem;
      margin-bottom: 6px;
    }
    #lockScreen p.small {
      opacity: .9;
      font-size: .95rem;
    }
    .field {
      display: flex;
      align-items: center;
      gap: 8px;
      margin-top: 12px;
    }
    .field input {
      flex: 1;
      padding: 12px 14px;
      border-radius: 999px;
      border: 1px solid #ffffff44;
      background: #ffffff12;
      color: #fff;
      font-size: 1.05rem;
      text-align: center;
      outline: none;
    }
    .field button.toggle {
      border: none;
      background: #ffffff1f;
      color: #fff;
      border-radius: 999px;
      padding: 10px 12px;
      cursor: pointer;
    }
    #unlockBtn {
      margin-top: 16px;
      padding: 12px 22px;
      border: none;
      border-radius: 999px;
      background: linear-gradient(135deg, var(--pink1), var(--pink2));
      color: #fff;
      font-weight: 700;
      cursor: pointer;
      box-shadow: 0 6px 18px #ff4e5088;
    }
    #errorMsg {
      color: #ff9aa2;
      min-height: 1.1em;
      font-size: .95rem;
      margin-top: 8px;
    }    
    
    .numpad {
      margin-top: 14px;
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 12px;
    }
    .np-key {
      padding: 14px 0;
      border: none;
      border-radius: 16px;
      background: #ffd1e1;
      color: #7a2551;
      font-weight: 800;
      box-shadow: 0 6px 14px rgba(0,0,0,.15), inset 0 -2px 0 rgba(255,255,255,.6);
      cursor: pointer;
      font-size: 1.2rem;
      transition: transform .08s ease, filter .12s ease;
    }
    .np-key:active, .np-key.pressed {
      transform: translateY(1px);
      filter: brightness(.98);
    }
    .np-key.back {
      font-size: 1.1rem;
    }
    @media (max-width: 420px) {
      .np-key {
        padding: 12px 0;
        font-size: 1.1rem;
        border-radius: 14px;
      }
    }    
    
    .splash {
      position: fixed;
      inset: 0;
      display: none;
      align-items: center;
      justify-content: center;
      background: rgba(0,0,0,.35);
      z-index: 10000;
    }
    .splash.visible {
      display: flex;
      animation: fadeIn .35s ease both;
    }
    .splash.fadeout {
      animation: fadeOut .5s ease forwards;
    }
    .splash img {
      width: min(75vw, 380px);
      max-width: 90vw;
      animation: pop .9s ease both;
    }
    @keyframes pop {
      0% { transform: scale(.6); opacity: 0; }
      60% { transform: scale(1.06); opacity: 1; }
      100% { transform: scale(1); }
    }
    @keyframes fadeIn {
      from { opacity: 0; }
      to { opacity: 1; }
    }
    @keyframes fadeOut {
      to { opacity: 0; visibility: hidden; }
    }    
    
    .gift-wrapper {
      position: relative;
      perspective: 800px;
      cursor: pointer;
      animation: swing 3s ease-in-out infinite;
      margin: 20px auto;
    }
    @keyframes swing {
      0%, 100% { transform: rotate(-4deg); }
      50% { transform: rotate(4deg); }
    }
    .gift-box {
      position: relative;
      width: min(70vw, 260px);
      height: min(70vw, 260px);
      transform-style: preserve-3d;
      transition: transform .6s;
    }
    .gift-box.open {
      transform: rotateY(-25deg) rotateX(-20deg);
    }
    .lid, .box {
      position: absolute;
      inset: 0;
      border-radius: 10px;
    }
    .box {
      background: linear-gradient(135deg, var(--pink1) 0%, var(--pink2) 100%);
      box-shadow: inset 0 0 0 10px #b71c1c, 0 0 20px rgba(0,0,0,.3);
    }
    .lid {
      background: linear-gradient(135deg, var(--pink2) 0%, var(--pink1) 100%);
      transform-origin: top;
      transition: transform .8s cubic-bezier(.68,-.55,.27,1.55);
      box-shadow: 0 0 20px rgba(255,255,255,.4);
    }
    .gift-box.open .lid {
      transform: rotateX(-120deg);
    }
    .ribbon {
      position: absolute;
      top: 50%;
      left: 50%;
      width: 28px;
      height: 100%;
      background: var(--accent);
      transform: translate(-50%, -50%);
      box-shadow: 0 0 10px var(--accent);
    }
    .bow::before, .bow::after {
      content: '';
      position: absolute;
      top: -16px;
      width: 55px;
      height: 55px;
      border-radius: 50%;
      background: var(--accent);
      box-shadow: 0 0 10px var(--accent);
    }
    .bow::before { left: -30px; }
    .bow::after { right: -30px; }
    .label {
      position: absolute;
      top: -54px;
      left: 50%;
      transform: translateX(-50%);
      background: #fff;
      color: var(--ink-strong);
      padding: 8px 18px;
      border-radius: 30px;
      font-weight: bold;
      font-size: 1.1em;
      box-shadow: 0 0 15px rgba(255,255,255,.6);
      animation: pulse 1.5s infinite;
    }
    @keyframes pulse {
      0%, 100% { transform: translateX(-50%) scale(1); }
      50% { transform: translateX(-50%) scale(1.1); }
    }    
    
    .letter {
      position: fixed;
      inset: 0;
      margin: auto;
      width: min(92vw, 560px);
      max-height: 82vh;
      overflow: auto;
      background: #fff;
      border-radius: 20px;
      padding: 28px;
      box-shadow: 0 0 40px #ff4081;
      opacity: 0;
      transform: scale(.2) rotate(-10deg);
      transition: all 1s cubic-bezier(.68,-.55,.27,1.55);
      font-size: 1.35em;
      line-height: 1.9;
      color: #333;
      text-align: center;
      z-index: 100;
      outline: none;
      font-family: 'Dancing Script', cursive;
    }
    .letter.show {
      opacity: 1;
      transform: scale(1) rotate(0);
    }    
    
    .video-wrapper {
      margin: 22px auto;
      width: 100%;
      max-width: 500px;
      border-radius: 15px;
      overflow: hidden;
      box-shadow: 0 0 15px rgba(0,0,0,.15);
    }
    .video-wrapper video {
      width: 100%;
      display: block;
    }    
    
    .firework {
      position: fixed;
      width: 5px;
      height: 5px;
      border-radius: 50%;
      box-shadow: 0 0 10px 5px;
      animation: boom 1.5s forwards;
      pointer-events: none;
    }
    @keyframes boom {
      0% { transform: scale(0); opacity: 1; }
      100% { transform: scale(25); opacity: 0; }
    }
    .confeti {
      position: fixed;
      top: -20px;
      animation: fall 4s linear infinite;
      pointer-events: none;
    }
    @keyframes fall {
      to { transform: translateY(110vh) rotate(360deg); }
    }
    @media (prefers-reduced-motion: reduce) {
      body { animation: none; }
      .gift-wrapper { animation: none; }
      .label { animation: none; }
      .confeti, .firework { display: none; }
      .letter { transition: none; }
    }

    /* Firma + WhatsApp */
    .signature {
      position: fixed;
      bottom: 10px;
      left: 0;
      width: 100%;
      text-align: center;
      font-size: 0.9rem;
      color: rgba(255,255,255,0.8);
      z-index: 10001;
      pointer-events: auto;
      font-family: 'Dancing Script', cursive;
      font-weight: bold;
      text-shadow: 1px 1px 3px rgba(0,0,0,0.3);
      display: none; /* Oculto al inicio */
    }
    .signature a {
      color: #4CAF50;
      text-decoration: none;
      font-weight: bold;
    }
    .signature a:hover {
      text-decoration: underline;
    }
    .signature span {
      margin: 0 6px;
    }
    .signature i {
      font-size: 1.1em;
      vertical-align: middle;
    }
  </style>    
</head>    
<body>

<!-- Splash Snoopy -->
<div id="splash" class="splash" aria-hidden="true">    
  <img 
    src="https://raw.githubusercontent.com/24141007-rgb/Snoopy-sin-fondo/b2d0ab471a92a5354da8f97ce5d5b57ac96b1a65/file_000000009fb06230b28ca745c04b30b5.png" 
    alt="Snoopy" 
    loading="lazy" 
    fetchpriority="high" 
  />    
</div>

<div id="lockScreen" role="dialog" aria-modal="true" aria-labelledby="titleLock">    
  <div class="panel">    
    <h2 id="titleLock">🎁 Regalo exclusivo para Aracely</h2>    
    <p class="small">Ingresa el código de acceso</p>    
    <div class="field">    
      <input 
        id="claveInput" 
        type="password" 
        inputmode="numeric" 
        autocomplete="off" 
        autocorrect="off" 
        autocapitalize="none" 
        spellcheck="false" 
        readonly 
        placeholder="••/••/••••" 
        maxlength="10" 
        aria-label="Clave (usa el teclado en pantalla)" 
      />    
      <button class="toggle" id="togglePwd" aria-pressed="false" aria-label="Mostrar u ocultar clave">👁️</button>    
    </div>

    <div id="numpad" class="numpad" role="group" aria-label="Teclado numérico">    
      <button class="np-key" data-k="1">1</button>    
      <button class="np-key" data-k="2">2</button>    
      <button class="np-key" data-k="3">3</button>    
      <button class="np-key" data-k="4">4</button>    
      <button class="np-key" data-k="5">5</button>    
      <button class="np-key" data-k="6">6</button>    
      <button class="np-key" data-k="7">7</button>    
      <button class="np-key" data-k="8">8</button>    
      <button class="np-key" data-k="9">9</button>    
      <button class="np-key" data-k="0">0</button>    
      <button class="np-key" data-k="/">/</button>    
      <button class="np-key back" data-k="BACK">⌫</button>    
    </div>    
    
    <button id="unlockBtn" class="btn">Iniciar</button>    
    <div id="errorMsg" role="status" aria-live="polite"></div>    
  </div>    
</div>

<div id="mainContent" style="display:none">    
  <div class="gift-wrapper" id="giftWrapper" tabindex="0" role="button" aria-label="Abrir caja de regalo">    
    <div class="gift-box" id="giftBox">    
      <div class="label">¡Abre!</div>    
      <div class="lid" aria-hidden="true"></div>    
      <div class="box" aria-hidden="true"></div>    
      <div class="ribbon" aria-hidden="true"></div>    
      <div class="bow" aria-hidden="true"></div>    
    </div>    
  </div>

  <div class="letter" id="letter" tabindex="-1" role="dialog" aria-modal="true" aria-labelledby="cartaTitulo" aria-describedby="typedText">    
    <h3 id="cartaTitulo" style="color:var(--ink-strong);margin-bottom:10px">💖 Feliz cumpleaños, Aracely 💖</h3>    
    <div id="typedText" aria-live="polite"></div>
    <div class="video-wrapper">    
      <video id="videoPlayer" muted autoplay loop playsinline preload="metadata">    
        <source src="https://raw.githubusercontent.com/24141007-rgb/Snoopy-bailando-/ba9a1a0847a4ac19c712130d1cbcd82d9cd15f66/TikVid.io_7520662157512576263.mp4" type="video/mp4" />    
        Tu navegador no soporta video.    
      </video>    
    </div>    
    <button id="btnClose" class="btn" style="margin-bottom:8px">✖ Cerrar carta</button>    
  </div>    
</div>

<audio id="openSound" preload="auto" src="https://cdn.pixabay.com/download/audio/2022/03/15/audio_49d7f3b6b0.mp3?filename=surprise-104954.mp3"></audio>
<audio id="bgAudio" preload="auto" loop src="https://github.com/24141007-rgb/Snoopy-audios-/raw/c9411b94af76bc69c9d134d3c2876fb125558a26/TikVid.io_7536960452828433670.mp3.m4a"></audio>    

<!-- Firma + WhatsApp (visible solo después de abrir el regalo) -->
<div class="signature" id="signature">
  By <a href="https://wa.me/51937556459?text=Hola%20AnthZz%20Berrocal%20quiero%20un%20proyecto%20personalizado" target="_blank" rel="noopener">
    <i>💬</i> AnthZz Berrocal BerMatMods
  </a>
</div>

<script>    
const CLAVE = '09/09/2006';    
const $ = (sel) => document.querySelector(sel);    
    
const splash = $('#splash');    
const lockScreen = $('#lockScreen');    
const inputClave = $('#claveInput');    
const togglePwd = $('#togglePwd');    
const unlockBtn = $('#unlockBtn');    
const errorMsg = $('#errorMsg');    
const mainContent = $('#mainContent');    
const giftWrapper = $('#giftWrapper');    
const giftBox = $('#giftBox');    
const letter = $('#letter');    
const typedText = $('#typedText');    
const videoPlayer = $('#videoPlayer');    
const openSound = $('#openSound');    
const bgAudio = $('#bgAudio');    
const btnClose = document.getElementById('btnClose');    
const signature = document.getElementById('signature'); // Nueva referencia
    
window.addEventListener('DOMContentLoaded', () => {    
  function handleKey(k){    
    if(k === 'BACK') { 
      inputClave.value = inputClave.value.slice(0, -1); 
      return; 
    }    
    if(inputClave.value.length >= 10) return;    
    if(/[0-9]/.test(k)){    
      let val = inputClave.value;    
      if(val.length === 2 || val.length === 5) { val += '/'; }    
      inputClave.value = val + k;    
    } else if(k === '/'){    
      if(inputClave.value.length === 2 || inputClave.value.length === 5) { 
        inputClave.value += '/'; 
      }    
    }    
  }    
    
  /* === NUMPAD robusto móvil (anti-doble toque) === */
  const numpad = document.getElementById('numpad');
  numpad.style.touchAction = 'manipulation';
  let lastTs = 0;

  function press(e){
    const key = e.target.closest('.np-key');
    if(!key) return;
    const now = e.timeStamp || Date.now();
    if(now - lastTs < 180) { e.preventDefault(); return; } 
    lastTs = now;

    e.preventDefault();
    handleKey(key.dataset.k);
    if('vibrate' in navigator){ navigator.vibrate(10); }
    key.classList.add('pressed');
    setTimeout(() => key.classList.remove('pressed'), 120);
  }

  numpad.addEventListener('pointerdown', press, { passive: false });
  numpad.addEventListener('touchstart', press, { passive: false });
  numpad.addEventListener('click', (e) => {
    if((e.timeStamp || Date.now()) - lastTs < 250) return;
    press(e);
  }, { passive: false });

  togglePwd.addEventListener('click', () => {    
    const isText = inputClave.type === 'text';    
    inputClave.type = isText ? 'password' : 'text';    
    togglePwd.setAttribute('aria-pressed', String(!isText));    
  });    
    
  function verificarClave(){    
    const val = inputClave.value.trim();    
    if(val === CLAVE){    
      lockScreen.style.display = 'none';    
      mainContent.style.display = 'block';    
      giftWrapper.focus();    
    } else {    
      errorMsg.textContent = 'Código incorrecto. Inténtalo de nuevo.';    
      lockScreen.querySelector('.panel').animate([    
        { transform: 'translateX(0)' }, 
        { transform: 'translateX(-6px)' }, 
        { transform: 'translateX(6px)' }, 
        { transform: 'translateX(0)' }    
      ], { duration: 300, easing: 'ease-out' });    
    }    
  }    
    
  unlockBtn.addEventListener('click', verificarClave);    
    
  function abrirRegalo(){    
    giftBox.classList.add('open');    
    openSound.play().catch(() => {});    
    setTimeout(() => {    
      giftWrapper.style.display = 'none';    
      splash.classList.add('visible');    
      setTimeout(() => {    
        splash.classList.add('fadeout');    
        setTimeout(() => {    
          splash.classList.remove('visible','fadeout');    
          splash.style.display = 'none';    
          letter.classList.add('show');    
          letter.focus();    
          typeWriter();    
          fireWorks();    
          if(bgAudio) { bgAudio.play().catch(() => {}); }    
          if(videoPlayer) { videoPlayer.muted = true; videoPlayer.play().catch(() => {}); }    
          // Mostrar firma después de abrir el regalo
          signature.style.display = 'block';
        }, 520);    
      }, 1600);    
    }, 1100);    
  }    
    
  giftWrapper.addEventListener('click', abrirRegalo);    
  giftWrapper.addEventListener('keydown', (e) => { 
    if(e.key === 'Enter' || e.key === ' ') { 
      e.preventDefault(); 
      abrirRegalo(); 
    } 
  });    
    
  // Cerrar carta / detener medios    
  function cerrarCarta(){    
    try { videoPlayer.pause(); } catch {}
    try { bgAudio.pause(); } catch {}    
    letter.classList.remove('show');    
    // Opcional: ocultar firma si cierras (opcional)
    // signature.style.display = 'none';
  }    
  btnClose.addEventListener('click', cerrarCarta);    
  window.addEventListener('keydown', (e) => { 
    if(letter.classList.contains('show') && e.key === 'Escape') { 
      cerrarCarta(); 
    } 
  });    
    
  inputClave.focus();    
});    
    
// Texto y efectos (contenido de la carta)
const text = `Hoy, 9 de septiembre, celebramos tus 19 años, y con ellos también celebro a la persona tan especial que eres y todo lo que significas en mi vida. Cumplir años no es solo sumar días, es crecer, aprender y dejar huellas en los demás… y tú, Aracely, has dejado huellas imborrables en mí. 🌷✨

Cada momento contigo se ha convertido en un recuerdo único. Como aquella vez que aprendiste a manejar mi moto y te fuiste de frente; recuerdo el miedo que sentí pensando que te ibas a mandar al monte, y al mismo tiempo la risa que nos quedó de esa experiencia. O ese día en que, sabiendo que tenía sueño y debía exponer, me sorprendiste trayéndome una Monster para darme energía y apoyarme, un gesto que nunca olvidaré porque me mostró cuánto te importa.

También pienso en cuando me llevaste pastillas para la gastritis, justo en el momento en que lo necesitaba, o en esa salida a la playa donde casi quedamos atrapados en la arena movediza y terminamos riéndonos de la situación. Incluso algo tan simple como cuando me llevas en tu moto se transforma en especial, porque contigo hasta el camino más sencillo tiene otro sentido.

Y cómo olvidar ese detalle tan bonito de hace poco, cuando me mandaste la foto de una pulsera con mi nombre “Fer”… fue un gesto que me hizo sonreír y que guardo con mucho cariño, porque en esas pequeñas cosas se refleja lo especial que eres.

Aracely, hoy cumples 19 años y deseo que este nuevo ciclo esté lleno de alegrías, de metas alcanzadas, de abrazos que reconforten y de sueños que poco a poco se vayan haciendo realidad. 🌟 Porque eres alguien única, con una luz propia que inspira y que hace que todo sea más bonito.

Gracias por existir, por brillar con tu esencia y por regalarme momentos que se quedarán para siempre en mi corazón. 🌷✨

🌟 Que nunca falten motivos para sonreír, que la vida siempre te sorprenda con cosas hermosas y que cada día sea tan especial como tú, Aracely. 🌟

Con todo mi cariño,
💌`;    

let i = 0;    
function typeWriter(){    
  if(window.matchMedia('(prefers-reduced-motion: reduce)').matches){    
    typedText.textContent = text;    
    return;    
  }    
  if(i < text.length){    
    const ch = text.charAt(i);    
    typedText.innerHTML += ch === '\n' ? '<br />' : ch;    
    i++;    
    setTimeout(typeWriter, 36);    
  }    
}    
function fireWorks(){ 
  if(window.matchMedia('(prefers-reduced-motion: reduce)').matches) return; 
  for(let j = 0; j < 28; j++){ 
    setTimeout(spawnFirework, j * 180); 
  } 
}    
function spawnFirework(){ 
  const colors = ['#ff0','#f0f','#0ff','#0f0','#ff4081','#3f51b5']; 
  const fw = document.createElement('div'); 
  fw.className = 'firework'; 
  fw.style.left = Math.random() * 100 + 'vw'; 
  fw.style.top = Math.random() * 100 + 'vh'; 
  fw.style.background = colors[(Math.random() * colors.length) | 0]; 
  document.body.appendChild(fw); 
  setTimeout(() => fw.remove(), 1500); 
}    
(function makeConfetti(){ 
  if(window.matchMedia('(prefers-reduced-motion: reduce)').matches) return; 
  const n = 64; 
  for(let k = 0; k < n; k++){ 
    const c = document.createElement('div'); 
    c.className = 'confeti'; 
    c.style.left = Math.random() * 100 + 'vw'; 
    const colors = ['#ff4081','#3f51b5','var(--accent)']; 
    c.style.background = colors[(Math.random() * colors.length) | 0]; 
    c.style.width = Math.random() > 0.5 ? '10px' : '14px'; 
    c.style.height = Math.random() > 0.5 ? '10px' : '18px'; 
    c.style.borderRadius = Math.random() > 0.5 ? '50%' : '0'; 
    c.style.animationDelay = Math.random() * 4 + 's'; 
    document.body.appendChild(c); 
  } 
})();    
</script>
</body>    
</html>
