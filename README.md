
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no" />
  <title>Detalles de Amor - By AnthZz Berrocal</title>
  <!-- Fuentes elegantes -->
  <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Great+Vibes&family=Montserrat:wght@400;500;700&family=Caveat:wght@600&family=Parisienne&family=Pacifico&family=Playball&family=Lobster&display=swap" rel="stylesheet">
  <!-- Giphy JS Wrapper -->
  <script src="https://cdn.giphy.com/giphy-js-wrapper/1.0.0/giphy.min.js"></script>
  <style>
    /* ==================== RESET Y BASE ==================== */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      -webkit-tap-highlight-color: transparent;
      font-smooth: always;
      -webkit-font-smoothing: antialiased;
      -moz-osx-font-smoothing: grayscale;
    }

    body {
      font-family: 'Montserrat', sans-serif;
      background: linear-gradient(135deg, #fdf4f7, #ffe6f0);
      color: #333;
      height: 100vh;
      overflow: hidden;
      position: relative;
      touch-action: manipulation;
    }

    /* ==================== EFECTOS DECORATIVOS ==================== */
    .sparkle {
      position: fixed;
      width: 6px;
      height: 6px;
      background: white;
      border-radius: 50%;
      box-shadow: 0 0 10px rgba(255, 255, 255, 0.9);
      pointer-events: none;
      z-index: 1;
      opacity: 0;
    }

    .heart {
      position: fixed;
      font-size: 22px;
      pointer-events: none;
      opacity: 0;
      z-index: 1;
    }

    @keyframes glow {
      0% { opacity: 0; transform: scale(0); }
      50% { opacity: 1; transform: scale(1.8); }
      100% { opacity: 0; transform: scale(0); }
    }

    @keyframes floatUp {
      0% { transform: translateY(0); opacity: 0; }
      10% { opacity: 1; }
      100% { transform: translateY(-130vh); opacity: 0; }
    }

    /* ==================== BOTÓN MENÚ HAMBURGUESA ==================== */
    .menu-btn {
      position: fixed;
      top: 15px;
      left: 15px;
      width: 58px;
      height: 58px;
      background: linear-gradient(45deg, #e91e63, #f06292);
      color: white;
      border-radius: 50%;
      display: flex;
      justify-content: center;
      align-items: center;
      z-index: 100;
      box-shadow: 0 8px 20px rgba(233, 30, 99, 0.5);
      cursor: pointer;
      font-size: 28px;
      transition: all 0.3s ease;
      backdrop-filter: blur(10px);
    }

    .menu-btn:hover {
      transform: scale(1.15);
      box-shadow: 0 10px 25px rgba(233, 30, 99, 0.6);
    }

    /* ==================== SIDEBAR (MENÚ LATERAL) ==================== */
    .sidebar {
      position: fixed;
      top: 0;
      left: -360px;
      width: 340px;
      height: 100%;
      background: rgba(255, 255, 255, 0.97);
      backdrop-filter: blur(12px);
      border-right: 3px solid #e91e63;
      transition: left 0.6s cubic-bezier(0.4, 0, 0.2, 1);
      z-index: 99;
      padding: 35px 25px;
      overflow-y: auto;
      box-shadow: 6px 0 40px rgba(0,0,0,0.18);
      border-radius: 0 24px 24px 0;
    }

    .sidebar.open {
      left: 0;
    }

    .sidebar h2 {
      text-align: center;
      margin-bottom: 30px;
      font-family: 'Parisienne', cursive;
      font-size: 36px;
      color: #d81b60;
      text-shadow: 2px 2px 4px rgba(0,0,0,0.1);
    }

    .close-btn {
      position: absolute;
      top: 22px;
      right: 25px;
      font-size: 32px;
      cursor: pointer;
      color: #999;
      transition: all 0.3s ease;
    }

    .close-btn:hover {
      color: #e91e63;
      transform: rotate(90deg);
    }

    /* ==================== ITEMS DEL MENÚ ==================== */
    .menu-item {
      padding: 18px;
      margin: 14px 0;
      background: #fff0f4;
      border-radius: 20px;
      cursor: pointer;
      font-weight: 600;
      color: #c2185b;
      text-align: center;
      transition: all 0.4s cubic-bezier(0.25, 0.8, 0.25, 1);
      border: 2px solid #ff8a80;
      display: flex;
      align-items: center;
      gap: 14px;
      justify-content: center;
      box-shadow: 0 6px 15px rgba(0,0,0,0.1);
      font-size: 16px;
    }

    .menu-item:hover {
      background: #e91e63;
      color: white;
      transform: translateY(-4px);
      box-shadow: 0 12px 25px rgba(233, 30, 99, 0.3);
    }

    .menu-icon {
      font-size: 22px;
      background: #ffebee;
      width: 40px;
      height: 40px;
      display: flex;
      align-items: center;
      justify-content: center;
      border-radius: 50%;
      box-shadow: 0 4px 8px rgba(0,0,0,0.1);
    }

    /* ==================== CANVAS PRINCIPAL ==================== */
    .canvas-container {
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 20px;
      height: 100vh;
      overflow: auto;
    }

    .canvas {
      max-width: 560px;
      width: 95%;
      min-height: 520px;
      height: 90vh;
      border: 4px dashed #e91e63;
      border-radius: 32px;
      background-color: #fff5f8;
      background-size: cover;
      background-position: center;
      overflow: auto;
      padding: 45px;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: flex-start;
      gap: 28px;
      box-shadow: inset 0 0 40px rgba(233, 30, 99, 0.18), 0 15px 40px rgba(0,0,0,0.15);
      position: relative;
      backdrop-filter: blur(8px);
      transition: all 0.5s ease;
    }

    /* ==================== ELEMENTOS EDITABLES ==================== */
    .element {
      max-width: 96%;
      word-wrap: break-word;
      animation: fadeIn 0.8s ease;
      text-align: center;
    }

    .text-element {
      padding: 18px 22px;
      border-radius: 22px;
      background: rgba(255, 255, 255, 0.9);
      backdrop-filter: blur(14px);
      box-shadow: 0 7px 20px rgba(0,0,0,0.12);
      transition: all 0.4s ease;
      font-size: 18px;
      border: 2px solid rgba(233, 30, 99, 0.25);
      line-height: 1.5;
    }

    .text-element:hover {
      box-shadow: 0 12px 30px rgba(233, 30, 99, 0.3);
      transform: translateY(-2px);
    }

    .media-element {
      max-width: 340px;
      border-radius: 26px;
      box-shadow: 0 12px 30px rgba(0,0,0,0.22);
      transition: all 0.4s ease;
      border: 3px solid white;
    }

    .media-element:hover {
      transform: scale(1.06);
      box-shadow: 0 16px 40px rgba(0,0,0,0.3);
    }

    /* ==================== CRÉDITOS DEL CREADOR ==================== */
    .credit {
      font-family: 'Great Vibes', cursive;
      font-size: 26px;
      color: #c2185b;
      margin: 35px 0 25px;
      padding: 18px 34px;
      background: linear-gradient(45deg, #ffebee, #f8bbd0);
      border-radius: 24px;
      box-shadow: 0 8px 22px rgba(0,0,0,0.18);
      animation: pulse 2s infinite;
      user-select: none;
      font-weight: normal;
      border: 3px solid #e91e63;
      text-shadow: 1px 1px 2px rgba(0,0,0,0.1);
    }

    @keyframes pulse {
      0% { opacity: 0.9; transform: scale(1); }
      50% { opacity: 1; transform: scale(1.05); }
      100% { opacity: 0.9; transform: scale(1); }
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }

    /* ==================== MODAL PRINCIPAL ==================== */
    .modal {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0,0,0,0.9);
      display: flex;
      justify-content: center;
      align-items: center;
      z-index: 1000;
      opacity: 0;
      visibility: hidden;
      transition: all 0.5s ease;
    }

    .modal.open {
      opacity: 1;
      visibility: visible;
    }

    .modal-content {
      background: white;
      padding: 40px;
      border-radius: 28px;
      width: 96%;
      max-width: 560px;
      max-height: 92vh;
      overflow-y: auto;
      position: relative;
      box-shadow: 0 35px 80px rgba(0,0,0,0.4);
      transform: scale(0.88);
      transition: transform 0.5s ease;
    }

    .modal.open .modal-content {
      transform: scale(1);
    }

    .close {
      position: absolute;
      top: 24px;
      right: 32px;
      font-size: 36px;
      cursor: pointer;
      color: #aaa;
      transition: all 0.3s ease;
    }

    .close:hover {
      color: #e91e63;
      transform: rotate(180deg);
    }

    /* ==================== INPUTS Y BOTONES ==================== */
    input, select, button.modal-btn {
      width: 100%;
      padding: 16px;
      margin: 14px 0;
      border: 1px solid #ddd;
      border-radius: 14px;
      font-size: 16px;
      transition: all 0.3s ease;
    }

    input:focus, select:focus {
      border-color: #e91e63;
      box-shadow: 0 0 0 3px rgba(233, 30, 99, 0.2);
      outline: none;
    }

    button.modal-btn {
      background: #e91e63;
      color: white;
      border: none;
      cursor: pointer;
      font-weight: bold;
      font-size: 18px;
      padding: 16px;
      border-radius: 16px;
      transition: all 0.3s ease;
      box-shadow: 0 6px 15px rgba(233, 30, 99, 0.3);
    }

    button.modal-btn:hover {
      background: #c2185b;
      transform: translateY(-2px);
      box-shadow: 0 8px 20px rgba(233, 30, 99, 0.4);
    }

    /* ==================== STICKERS Y EMOTICONOS ==================== */
    .stickers {
      display: flex;
      flex-wrap: wrap;
      gap: 14px;
      padding: 14px;
      max-height: 240px;
      overflow-y: auto;
    }

    .sticker {
      font-size: 36px;
      cursor: pointer;
      transition: all 0.3s ease;
      padding: 8px;
      border-radius: 12px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.1);
    }

    .sticker:hover {
      transform: scale(1.3);
      box-shadow: 0 6px 15px rgba(0,0,0,0.2);
    }

    /* ==================== CONFIRMACIÓN DEL DESTINATARIO ==================== */
    .confirm-section {
      margin-top: 35px;
      text-align: center;
    }

    .confirm-btn {
      padding: 18px 32px;
      margin: 16px;
      border: none;
      border-radius: 16px;
      color: white;
      font-weight: bold;
      cursor: pointer;
      font-size: 19px;
      transition: all 0.4s ease;
      box-shadow: 0 6px 16px rgba(0,0,0,0.2);
    }

    .yes-btn { background: #4caf50; }
    .no-btn { background: #f44336; }

    .confirm-btn:hover {
      transform: scale(1.1);
      box-shadow: 0 10px 25px rgba(0,0,0,0.3);
    }

    /* ==================== RESPUESTA GUARDADA ==================== */
    .response-info {
      font-size: 14px;
      color: #666;
      margin-top: 8px;
      font-style: italic;
    }

    /* ==================== RESPONSIVE ==================== */
    @media (max-width: 600px) {
      .canvas {
        width: 95%;
        padding: 35px 22px;
        height: 85vh;
        gap: 22px;
      }
      .menu-btn { width: 54px; height: 54px; font-size: 24px; }
      .sidebar { width: 320px; }
      .credit { font-size: 22px; padding: 16px 28px; }
      .modal-content { width: 94%; padding: 30px; }
    }

    @media (max-height: 700px) {
      .canvas { height: 85vh; padding: 30px; }
    }
  </style>
</head>
<body>

  <!-- ==================== EFECTOS DECORATIVOS ==================== -->
  <script>
    // Partículas brillantes
    setInterval(() => {
      const p = document.createElement("div");
      p.className = "sparkle";
      p.style.left = Math.random() * 100 + "vw";
      p.style.top = Math.random() * 100 + "vh";
      p.style.animation = `glow 3s forwards`;
      document.body.appendChild(p);
      setTimeout(() => p.remove(), 3000);
    }, 500);

    // Corazones flotantes
    setInterval(() => {
      const h = document.createElement("div");
      h.className = "heart";
      h.textContent = ["❤️", "💖", "💕", "💘", "💓"][Math.floor(Math.random() * 5)];
      h.style.left = Math.random() * 100 + "vw";
      h.style.top = "100vh";
      h.style.animation = `floatUp ${5 + Math.random() * 3}s ease-out forwards`;
      h.style.opacity = 0;
      document.body.appendChild(h);
      setTimeout(() => h.remove(), 8000);
    }, 700);
  </script>

  <!-- ==================== MENÚ HAMBURGUESA ==================== -->
  <div class="menu-btn" onclick="toggleMenu()">☰</div>

  <!-- ==================== SIDEBAR LATERAL ==================== -->
  <div class="sidebar" id="sidebar">
    <h2>✨ Menú de Amor</h2>
    <div class="close-btn" onclick="toggleMenu()">×</div>

    <div class="menu-item" onclick="openModal('addText')"><span class="menu-icon">📝</span> Añadir Texto</div>
    <div class="menu-item" onclick="openModal('addEmoji')"><span class="menu-icon">😊</span> Emojis de Amor</div>
    <div class="menu-item" onclick="openModal('addGif')"><span class="menu-icon">🎬</span> Gif Animado</div>
    <div class="menu-item" onclick="openModal('addImage')"><span class="menu-icon">🖼️</span> Imagen Personalizada</div>
    <div class="menu-item" onclick="openModal('addVideo')"><span class="menu-icon">▶️</span> Video de YouTube</div>
    <div class="menu-item" onclick="openModal('addMusic')"><span class="menu-icon">🎵</span> Música de Spotify</div>
    <div class="menu-item" onclick="openModal('changeFont')"><span class="menu-icon">🔤</span> Cambiar Fuente</div>
    <div class="menu-item" onclick="openModal('changeColor')"><span class="menu-icon">🎨</span> Color del Texto</div>
    <div class="menu-item" onclick="openModal('changeBoxStyle')"><span class="menu-icon">🔲</span> Estilo de Cuadro</div>
    <div class="menu-item" onclick="openModal('changeBg')"><span class="menu-icon">🌅</span> Fondo Personalizado</div>
    <div class="menu-item" onclick="openModal('addSticker')"><span class="menu-icon">🎀</span> Stickers de Amor</div>
    <div class="menu-item" onclick="openModal('info')"><span class="menu-icon">ℹ️</span> Información del Creador</div>
    <div class="menu-item" onclick="generateLink()"><span class="menu-icon">🔗</span> Compartir por WhatsApp</div>
  </div>

  <!-- ==================== CANVAS PRINCIPAL ==================== -->
  <div class="canvas-container">
    <div class="canvas" id="canvas">
      <h1 class="element text-element" style="font-family: 'Dancing Script'; font-size: 42px; color: #e91e63; font-weight: normal;">
        Escribe tu mensaje de amor aquí...
      </h1>
      <img class="media-element" src="https://images.unsplash.com/photo-1514433641795-93d88534f5d2?ixlib=rb-1.2.1&auto=format&fit=crop&w=600&q=80" alt="Rosa Roja">
      <p class="element text-element" style="font-family: 'Montserrat'; font-size: 18px; color: #555;">
        Cada momento contigo es un regalo. Gracias por llenar mi vida de amor y alegría.
      </p>
      <div class="credit">By AnthZz Berrocal - BerMatMods</div>
    </div>
  </div>

  <!-- ==================== MODALES ==================== -->
  <div id="modal" class="modal">
    <div class="modal-content">
      <span class="close" onclick="closeModal()">&times;</span>
      <div id="modalBody"></div>
    </div>
  </div>

  <div id="linkModal" class="modal">
    <div class="modal-content">
      <h3>🎉 ¡Tu detalle está listo!</h3>
      <p>Tu enlace personalizado:</p>
      <input type="text" id="shareLink" readonly />
      <button id="copyLink" class="modal-btn">📋 Copiar enlace</button>
      <a id="whatsappShare" href="#" target="_blank" class="modal-btn">💬 Compartir por WhatsApp</a>
      <button onclick="closeLinkModal()" style="background:#999;">Cerrar</button>
    </div>
  </div>

  <!-- ==================== SCRIPT PRINCIPAL ==================== -->
  <script>
    // ==================== CONTROL DEL MENÚ ====================
    function toggleMenu() {
      document.getElementById("sidebar").classList.toggle("open");
    }

    function closeModal() {
      document.getElementById("modal").classList.remove("open");
    }

    function openLinkModal() {
      document.getElementById("linkModal").classList.add("open");
    }

    function closeLinkModal() {
      document.getElementById("linkModal").classList.remove("open");
    }

    // ==================== INSERTAR ANTES DEL CRÉDITO ====================
    function insertBeforeCredit(el) {
      const credit = document.querySelector(".credit");
      document.getElementById("canvas").insertBefore(el, credit);
    }

    // ==================== MODALES DINÁMICOS ====================
    function openModal(type) {
      document.getElementById("modal").classList.add("open");
      const body = document.getElementById("modalBody");
      let content = "";

      switch (type) {
        case "addText":
          content = createTextModal();
          break;
        case "addEmoji":
          content = createEmojiModal();
          break;
        case "addGif":
          content = createGifModal();
          break;
        case "addImage":
          content = createImageModal();
          break;
        case "addVideo":
          content = createVideoModal();
          break;
        case "addMusic":
          content = createMusicModal();
          break;
        case "changeFont":
          content = createFontModal();
          break;
        case "changeColor":
          content = createColorModal();
          break;
        case "changeBoxStyle":
          content = createBoxStyleModal();
          break;
        case "changeBg":
          content = createBgModal();
          break;
        case "addSticker":
          content = createStickerModal();
          break;
        case "info":
          content = createInfoModal();
          break;
        default:
          content = `<p>Opción no disponible</p>`;
      }

      body.innerHTML = content;
    }

    // ==================== FUNCIONES DE CREACIÓN DE MODALES ====================
    function createTextModal() {
      return `<h3>📝 Añadir Texto Personalizado</h3>
        <input type="text" id="textValue" placeholder="Escribe tu mensaje..." value="Texto nuevo" />
        <select id="textFont">` + ["Dancing Script", "Great Vibes", "Montserrat", "Caveat", "Pacifico", "Parisienne", "Lobster", "Playball"].map(f => `<option>${f}</option>`).join("") + `</select>
        <input type="color" id="textColor" value="#e91e63" />
        <input type="number" id="textSize" value="18" min="12" max="48" /> px
        <div style="display:flex;gap:20px;margin:10px 0;">
          <label><input type="checkbox" id="textBold"> Negrita</label>
          <label><input type="checkbox" id="textItalic"> Cursiva</label>
        </div>
        <button class="modal-btn" onclick="addText()">Añadir Texto</button>`;
    }

    function createEmojiModal() {
      const emojis = ["❤️", "💕", "😍", "🥰", "😘", "🌹", "🌸", "💫", "✨", "🎉", "💝", "🫶", "🌷", "💞", "💓", "💗", "💘", "💟", "😻", "🥺"];
      return `<h3>😊 Emojis de Amor</h3>
        <div class="stickers">${emojis.map(e => `<span class="sticker" onclick="addEmoji('${e}')">${e}</span>`).join("")}</div>`;
    }

    function createGifModal() {
      return `<h3>🎬 Buscar Gif de Amor</h3>
        <input type="text" id="gifQuery" placeholder="Ej: love, kiss, dance" />
        <div id="gifResults" style="display:flex;flex-wrap:wrap;gap:12px;margin:14px 0;"></div>
        <small>Powered by Giphy</small>`;
    }

    function createImageModal() {
      return `<h3>🖼️ Añadir Imagen</h3>
        <input type="text" id="imgUrl" placeholder="https://ejemplo.com/imagen.jpg" />
        <button class="modal-btn" onclick="addImage()">Añadir Imagen</button>`;
    }

    function createVideoModal() {
      return `<h3>▶️ Añadir Video de YouTube</h3>
        <input type="text" id="videoUrl" placeholder="https://youtube.com/watch?v=..." />
        <button class="modal-btn" onclick="addVideo()">Añadir Video</button>`;
    }

    function createMusicModal() {
      return `<h3>🎵 Añadir Música de Spotify</h3>
        <input type="text" id="musicUrl" placeholder="https://open.spotify.com/track/..." />
        <button class="modal-btn" onclick="addMusic()">Añadir Música</button>`;
    }

    function createFontModal() {
      return `<h3>🔤 Cambiar Fuente del Texto</h3>
        <select id="fontSelect">` + ["Dancing Script", "Great Vibes", "Montserrat", "Caveat", "Pacifico", "Parisienne", "Lobster", "Playball"].map(f => `<option>${f}</option>`).join("") + `</select>
        <button class="modal-btn" onclick="changeFont()">Aplicar a todos</button>`;
    }

    function createColorModal() {
      return `<h3>🎨 Color del Texto</h3>
        <input type="color" id="textColor" value="#e91e63" />
        <button class="modal-btn" onclick="changeColor()">Aplicar a todos</button>`;
    }

    function createBoxStyleModal() {
      return `<h3>🔲 Estilo de Cuadro de Texto</h3>
        <label>Fondo: <input type="color" id="boxBg" value="#ffffff" /></label>
        <label>Borde: <input type="color" id="boxBorder" value="#e91e63" /></label>
        <label>Radio: <input type="range" id="boxRadius" min="0" max="40" value="22" /> <span id="radiusVal">22px</span></label>
        <label>Relleno: <input type="number" id="boxPadding" value="18" /> px</label>
        <button class="modal-btn" onclick="applyBoxStyle()">Aplicar a todos</button>
        <script>document.getElementById('boxRadius').oninput = function() { document.getElementById('radiusVal').textContent = this.value + 'px'; }</script>`;
    }

    function createBgModal() {
      return `<h3>🌅 Fondo del Detalle</h3>
        <input type="text" id="bgValue" placeholder="Color o URL de imagen" />
        <button class="modal-btn" onclick="changeBg()">Aplicar Fondo</button>`;
    }

    function createStickerModal() {
      const stickers = ["🎈", "🎁", "💍", "💌", "💘", "💋", "🧸", "🍫", "☕", "🌙", "🌞", "🕊️", "🎶", "📱", "💌", "🎊", "💐", "🕯️"];
      return `<h3>🎀 Stickers de Google</h3>
        <div class="stickers">${stickers.map(s => `<span class="sticker" onclick="addEmoji('${s}')">${s}</span>`).join("")}</div>`;
    }

    function createInfoModal() {
      return `<h3>ℹ️ Información del Creador</h3>
        <p><strong>Creado por:</strong> AnthZz Berrocal</p>
        <p><strong>Marca:</strong> BerMatMods</p>
        <p><strong>Proyecto:</strong> Detalles de Amor Virtual</p>
        <p>Este detalle fue creado con el sistema BerMatMods ❤️</p>
        <p>© 2025 BerMatMods. Todos los derechos reservados.</p>
        <p><em>Gracias por usar esta herramienta de amor.</em></p>`;
    }

    // ==================== FUNCIONES DE EDICIÓN ====================
    window.addText = () => {
      const val = document.getElementById("textValue").value || "Texto personalizado";
      const font = document.getElementById("textFont").value;
      const color = document.getElementById("textColor").value;
      const size = document.getElementById("textSize").value;
      const bold = document.getElementById("textBold").checked ? "bold" : "normal";
      const italic = document.getElementById("textItalic").checked ? "italic" : "normal";

      const el = document.createElement("p");
      el.className = "element text-element";
      el.contentEditable = true;
      el.innerHTML = val;
      el.style.fontFamily = font;
      el.style.color = color;
      el.style.fontSize = size + "px";
      el.style.fontWeight = bold;
      el.style.fontStyle = italic;
      insertBeforeCredit(el);
      closeModal();
    };

    window.addEmoji = (emoji) => {
      const el = document.createElement("span");
      el.textContent = emoji;
      el.style.fontSize = "38px";
      el.style.margin = "0 6px";
      insertBeforeCredit(el);
      closeModal();
    };

    window.addGif = (url) => {
      const img = document.createElement("img");
      img.src = url;
      img.className = "media-element";
      insertBeforeCredit(img);
      closeModal();
    };

    window.addImage = () => {
      const url = document.getElementById("imgUrl").value;
      if (url) {
        const img = document.createElement("img");
        img.src = url;
        img.className = "media-element";
        insertBeforeCredit(img);
        closeModal();
      } else {
        alert("Por favor ingresa una URL válida");
      }
    };

    window.addVideo = () => {
      const url = document.getElementById("videoUrl").value;
      const id = url?.split("v=")[1]?.split("&")[0];
      if (id) {
        const iframe = document.createElement("iframe");
        iframe.src = `https://www.youtube.com/embed/${id}`;
        iframe.width = "360";
        iframe.height = "220";
        iframe.style.borderRadius = "24px";
        iframe.style.boxShadow = "0 10px 25px rgba(0,0,0,0.2)";
        insertBeforeCredit(iframe);
        closeModal();
      } else {
        alert("URL de YouTube no válida");
      }
    };

    window.addMusic = () => {
      const url = document.getElementById("musicUrl").value;
      const embed = url?.replace("/track/", "/embed/track/");
      if (embed) {
        const iframe = document.createElement("iframe");
        iframe.src = embed;
        iframe.width = "100%";
        iframe.height = "80";
        iframe.style.borderRadius = "12px";
        iframe.style.border = "none";
        insertBeforeCredit(iframe);
        closeModal();
      } else {
        alert("URL de Spotify no válida");
      }
    };

    window.changeFont = () => {
      const font = document.getElementById("fontSelect").value;
      document.querySelectorAll(".text-element").forEach(el => el.style.fontFamily = font);
      closeModal();
    };

    window.changeColor = () => {
      const color = document.getElementById("textColor").value;
      document.querySelectorAll(".text-element").forEach(el => el.style.color = color);
      closeModal();
    };

    window.applyBoxStyle = () => {
      const bg = document.getElementById("boxBg").value;
      const border = document.getElementById("boxBorder").value;
      const radius = document.getElementById("boxRadius").value + "px";
      const padding = document.getElementById("boxPadding").value + "px";
      document.querySelectorAll(".text-element").forEach(el => {
        el.style.background = `rgba(${hexToRgb(bg)}, 0.9)`;
        el.style.borderColor = border;
        el.style.borderRadius = radius;
        el.style.padding = padding;
      });
      closeModal();
    };

    window.changeBg = () => {
      const bg = document.getElementById("bgValue").value;
      if (bg) {
        document.getElementById("canvas").style.background = bg.startsWith("http") ? `url(${bg})` : bg;
      }
      closeModal();
    };

    function hexToRgb(hex) {
      const shorthand = /^#?([a-f\d])([a-f\d])([a-f\d])$/i;
      hex = hex.replace(shorthand, (m, r, g, b) => r + r + g + g + b + b);
      const result = /^#?([a-f\d]{2})([a-f\d]{2})([a-f\d]{2})$/i.exec(hex);
      return result ? `${parseInt(result[1], 16)}, ${parseInt(result[2], 16)}, ${parseInt(result[3], 16)}` : "255,255,255";
    }

    // ==================== GENERAR ENLACE ====================
    function generateLink() {
      const content = document.getElementById("canvas").innerHTML;
      const bg = getComputedStyle(document.getElementById("canvas")).background;
      const id = Math.random().toString(36).substr(2, 9);
      const creator = "AnthZz Berrocal - BerMatMods";
      localStorage.setItem(`detail_${id}`, JSON.stringify({ content, bg, creator, responses: [] }));

      const link = `${window.location.href.split("index.html")[0]}view.html?id=${id}`;
      document.getElementById("shareLink").value = link;
      document.getElementById("whatsappShare").href = `https://wa.me/?text=💌%20Te%20envío%20una%20sorpresa%20de%20amor:%20${encodeURIComponent(link)}`;
      openLinkModal();
    }

    // ==================== COPIAR ENLACE ====================
    document.getElementById("copyLink").onclick = () => {
      const input = document.getElementById("shareLink");
      input.select();
      document.execCommand("copy");
      alert("✅ ¡Enlace copiado al portapapeles!");
    };

    // ==================== CRÉDITOS INAMOVIBLES ====================
    setInterval(() => {
      const credit = document.querySelector(".credit");
      if (credit) {
        credit.innerHTML = "By AnthZz Berrocal - BerMatMods";
        credit.style.fontFamily = "Great Vibes";
        credit.style.fontSize = "26px";
      }
    }, 1000);

    // ==================== INICIALIZACIÓN GIPHY ====================
    document.addEventListener("DOMContentLoaded", () => {
      // Inicializa eventos para Giphy
      if (document.getElementById("gifQuery")) {
        document.getElementById("gifQuery").oninput = async function(e) {
          const q = e.target.value;
          if (q.length < 2) return;
          try {
            const res = await fetch(`https://api.giphy.com/v1/gifs/search?api_key=YOUR_GIPHY_API_KEY&q=${q}&limit=4`);
            const data = await res.json();
            const r = document.getElementById("gifResults");
            r.innerHTML = data.data.map(g => `<img src="${g.images.fixed_width.url}" class="media-element" onclick="addGif('${g.images.fixed_width.url}')" style="cursor:pointer;width:120px;border-radius:14px;" />`).join("");
          } catch (err) {
            console.error("Error con Giphy:", err);
          }
        };
      }
    });
  </script>

  <!-- ==================== view.html (GUÁRDALO APARTE) ==================== -->
  <!--
  <!DOCTYPE html>
  <html><head><title>Detalle de Amor</title><style>
    body{margin:0;height:100vh;display:flex;justify-content:center;align-items:center;background:#ffebee;font-family:'Dancing Script',cursive;}
    .content{max-width:500px;padding:30px;background:white;border-radius:20px;box-shadow:0 10px 30px rgba(0,0,0,0.1);text-align:center;}
    .confirm-section{margin-top:25px;}
    .confirm-btn{padding:14px 26px;margin:12px;border:none;border-radius:12px;color:white;font-weight:bold;cursor:pointer;font-size:16px;}
    .yes-btn{background:#4caf50;}
    .no-btn{background:#f44336;}
  </style></head><body><div class="content" id="content"></div>
  <script>
    const id = new URLSearchParams(window.location.search).get("id");
    const data = JSON.parse(localStorage.getItem(`detail_${id}`));
    if (data) {
      document.getElementById("content").innerHTML = data.content + `
        <div class="confirm-section">
          <p>¿Te gustó esta sorpresa?</p>
          <button class="confirm-btn yes-btn" onclick="sendResponse('Sí')">Sí 😍</button>
          <button class="confirm-btn no-btn" onclick="sendResponse('No')">No 😔</button>
        </div>`;
      document.body.style.background = data.bg;
    } else {
      document.getElementById("content").innerHTML = "<h2>❌ Detalle no encontrado</h2>";
    }
    function sendResponse(r) {
      const responses = data.responses || [];
      responses.push({ response: r, date: new Date().toLocaleString() });
      localStorage.setItem(`detail_${id}`, JSON.stringify({ ...data, responses }));
      alert("❤️ Gracias por tu respuesta");
    }
  </script></body></html>
  -->

</body>
</html>
