
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Detalles de Amor - By AnthZz Berrocal</title>
  <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Great+Vibes&family=Montserrat:wght@400;500;700&family=Caveat:wght@600&family=Parisienne&family=Pacifico&display=swap" rel="stylesheet">
  <script src="https://cdn.giphy.com/giphy-js-wrapper/1.0.0/giphy.min.js"></script>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Montserrat', sans-serif;
      background: linear-gradient(135deg, #fdf4f7, #ffe6f0);
      color: #333;
      height: 100vh;
      overflow: hidden;
      position: relative;
    }

    /* Brillo flotante decorativo */
    .sparkle {
      position: fixed;
      width: 10px;
      height: 10px;
      background: white;
      border-radius: 50%;
      box-shadow: 0 0 10px 2px rgba(255, 255, 255, 0.8);
      pointer-events: none;
      opacity: 0;
      z-index: 1;
    }

    /* Corazones flotantes */
    .heart {
      position: fixed;
      font-size: 20px;
      pointer-events: none;
      opacity: 0;
      z-index: 1;
    }

    .container {
      display: flex;
      height: 100vh;
      position: relative;
      z-index: 10;
    }

    /* Sidebar */
    .sidebar {
      width: 320px;
      background: #fff;
      box-shadow: 6px 0 30px rgba(0, 0, 0, 0.1);
      padding: 25px;
      overflow-y: auto;
      border-right: 3px solid #e91e63;
      background: white;
    }

    .sidebar h2 {
      text-align: center;
      margin-bottom: 25px;
      font-family: 'Parisienne', cursive;
      font-size: 32px;
      color: #d81b60;
      letter-spacing: 1px;
    }

    .template-btn {
      padding: 14px;
      margin-bottom: 12px;
      border: 2px solid #ff8a80;
      border-radius: 18px;
      cursor: pointer;
      background: #fff0f4;
      transition: all 0.4s cubic-bezier(0.25, 0.8, 0.25, 1);
      text-align: left;
      font-weight: 600;
      color: #c2185b;
      font-size: 16px;
      display: flex;
      align-items: center;
      gap: 12px;
      box-shadow: 0 4px 12px rgba(233, 30, 99, 0.1);
    }

    .template-btn:hover {
      background: #e91e63;
      color: white;
      transform: translateY(-4px);
      box-shadow: 0 8px 20px rgba(233, 30, 99, 0.25);
    }

    .template-icon {
      font-size: 24px;
      background: #ffebee;
      width: 40px;
      height: 40px;
      display: flex;
      align-items: center;
      justify-content: center;
      border-radius: 50%;
    }

    /* Editor */
    .editor {
      flex: 1;
      display: flex;
      flex-direction: column;
      padding: 20px;
    }

    .toolbar {
      display: flex;
      gap: 10px;
      margin-bottom: 20px;
      flex-wrap: wrap;
      background: white;
      padding: 14px;
      border-radius: 16px;
      box-shadow: 0 6px 15px rgba(0,0,0,0.08);
    }

    .toolbar button {
      padding: 10px 14px;
      border: none;
      border-radius: 10px;
      background: #e91e63;
      color: white;
      cursor: pointer;
      font-weight: bold;
      transition: all 0.3s;
      font-size: 14px;
      display: flex;
      align-items: center;
      gap: 6px;
      flex: 1;
      min-width: 90px;
      justify-content: center;
    }

    .toolbar button:hover {
      background: #c2185b;
      transform: scale(1.05);
    }

    /* Canvas */
    .canvas {
      flex: 1;
      border: 3px dashed #e91e63;
      border-radius: 24px;
      background-size: cover;
      background-position: center;
      background-repeat: no-repeat;
      position: relative;
      overflow: auto;
      padding: 30px;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: flex-start;
      gap: 20px;
      min-height: 400px;
      background-color: #fff5f8;
      box-shadow: inset 0 0 25px rgba(233, 30, 99, 0.15);
      transition: all 0.6s ease;
    }

    .element {
      max-width: 90%;
      word-wrap: break-word;
      animation: fadeInUp 0.8s ease;
      text-align: center;
    }

    .text-element {
      padding: 12px 16px;
      border-radius: 15px;
      background: rgba(255, 255, 255, 0.6);
      backdrop-filter: blur(10px);
      box-shadow: 0 4px 12px rgba(0,0,0,0.08);
      transition: all 0.3s;
    }

    .text-element:hover {
      box-shadow: 0 6px 16px rgba(233, 30, 99, 0.2);
    }

    .media-element {
      max-width: 280px;
      border-radius: 20px;
      box-shadow: 0 6px 16px rgba(0,0,0,0.15);
      transition: transform 0.3s;
    }

    .media-element:hover {
      transform: scale(1.03);
    }

    .credit {
      font-family: 'Great Vibes', cursive;
      font-size: 20px;
      color: #c2185b;
      margin: 20px 0 10px;
      padding: 12px 24px;
      background: rgba(255, 255, 255, 0.5);
      border-radius: 18px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
      animation: pulse 2s infinite;
      user-select: none;
    }

    @keyframes pulse {
      0% { opacity: 0.8; }
      50% { opacity: 1; }
      100% { opacity: 0.8; }
    }

    @keyframes fadeInUp {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }

    /* Modal */
    .modal {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0,0,0,0.8);
      display: flex;
      justify-content: center;
      align-items: center;
      z-index: 1000;
      opacity: 0;
      visibility: hidden;
      transition: all 0.4s ease;
    }

    .modal.open {
      opacity: 1;
      visibility: visible;
    }

    .modal-content {
      background: white;
      padding: 30px;
      border-radius: 20px;
      width: 90%;
      max-width: 520px;
      position: relative;
      box-shadow: 0 20px 50px rgba(0,0,0,0.3);
      transform: scale(0.9);
      transition: transform 0.4s ease;
      max-height: 90vh;
      overflow-y: auto;
    }

    .modal.open .modal-content {
      transform: scale(1);
    }

    .close {
      position: absolute;
      top: 15px;
      right: 25px;
      font-size: 28px;
      cursor: pointer;
      color: #aaa;
      transition: 0.3s;
    }

    .close:hover {
      color: #e91e63;
    }

    /* Inputs */
    input, select {
      width: 100%;
      padding: 12px;
      margin: 10px 0;
      border: 1px solid #ddd;
      border-radius: 8px;
      font-size: 14px;
    }

    button.modal-btn {
      padding: 12px;
      background: #e91e63;
      color: white;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      width: 100%;
      font-weight: bold;
    }

    button.modal-btn:hover {
      background: #c2185b;
    }

    /* Enlace modal */
    #shareLink {
      width: 100%;
      padding: 12px;
      border: 1px solid #ddd;
      border-radius: 8px;
      font-size: 14px;
      background: #f9f9f9;
    }

    #copyLink, #whatsappShare {
      display: block;
      text-align: center;
      padding: 12px;
      margin: 10px 0;
      border: none;
      border-radius: 8px;
      font-weight: bold;
      cursor: pointer;
      text-decoration: none;
    }

    #copyLink {
      background: #4a90e2;
      color: white;
    }

    #whatsappShare {
      background: #25D366;
      color: white;
    }

    /* Responsive */
    @media (max-width: 768px) {
      .container { flex-direction: column; }
      .sidebar { width: 100%; height: auto; max-height: 220px; }
      .toolbar button { font-size: 13px; padding: 8px 10px; }
    }
  </style>
</head>
<body>

  <!-- Efectos decorativos -->
  <script>
    setInterval(() => {
      const sparkle = document.createElement("div");
      sparkle.className = "sparkle";
      sparkle.style.left = Math.random() * 100 + "vw";
      sparkle.style.top = Math.random() * 100 + "vh";
      sparkle.style.animation = `sparkle 2s forwards`;
      document.body.appendChild(sparkle);
      setTimeout(() => sparkle.remove(), 2000);
    }, 600);

    setInterval(() => {
      const heart = document.createElement("div");
      heart.className = "heart";
      heart.textContent = Math.random() > 0.5 ? "❤️" : "💖";
      heart.style.left = Math.random() * 100 + "vw";
      heart.style.top = "100vh";
      heart.style.animation = `floatUp 6s ease-in-out infinite`;
      heart.style.animationDelay = Math.random() * 4 + "s";
      document.body.appendChild(heart);
      setTimeout(() => heart.remove(), 6000);
    }, 700);
  </script>

  <style>
    @keyframes sparkle {
      0% { opacity: 0; transform: scale(0); }
      50% { opacity: 1; transform: scale(1.5); }
      100% { opacity: 0; transform: scale(0); }
    }
    @keyframes floatUp {
      0% { transform: translateY(0); opacity: 0; }
      10% { opacity: 1; }
      100% { transform: translateY(-100vh); opacity: 0; }
    }
  </style>

  <div class="container">
    <!-- Menú de plantillas -->
    <div class="sidebar">
      <h2>🌷 Plantillas de Amor</h2>
      <div id="templateList"></div>
    </div>

    <!-- Editor -->
    <div class="editor">
      <div class="toolbar">
        <button id="addText">📝 Texto</button>
        <button id="addEmoji">😊 Emojis</button>
        <button id="addGif">🎬 Gif</button>
        <button id="addImage">🖼️ Foto</button>
        <button id="addVideo">▶️ Video</button>
        <button id="addMusic">🎵 Música</button>
        <button id="changeFont">🔤 Fuente</button>
        <button id="changeColor">🎨 Color</button>
        <button id="changeBg">🖼️ Fondo</button>
        <button id="generateLink">🔗 Compartir</button>
      </div>

      <div class="canvas" id="canvas">
        <!-- Aquí se carga la plantilla -->
      </div>
    </div>
  </div>

  <!-- Modal -->
  <div id="modal" class="modal">
    <div class="modal-content">
      <span class="close">&times;</span>
      <div id="modalBody"></div>
    </div>
  </div>

  <!-- Modal de enlace -->
  <div id="linkModal" class="modal">
    <div class="modal-content">
      <h3>🎉 ¡Tu detalle está listo!</h3>
      <p>Tu enlace personalizado:</p>
      <input type="text" id="shareLink" readonly />
      <button id="copyLink">📋 Copiar enlace</button>
      <a id="whatsappShare" href="#" target="_blank">💬 Compartir por WhatsApp</a>
      <button onclick="closeLinkModal()" style="background:#999;">Cerrar</button>
    </div>
  </div>

  <script>
    // Plantillas prehechas (proyectos)
    const templates = [
      {
        id: "amor",
        name: "Te amo más cada día 💖",
        icon: "🌹",
        bg: "linear-gradient(135deg, #ffebee, #f8bbd0)",
        content: `<h1 class="element" style="font-family:'Dancing Script'; font-size:42px; color:#e91e63;">Te amo más cada día</h1>
                  <img class="media-element" src="https://images.unsplash.com/photo-1514433641795-93d88534f5d2?ixlib=rb-1.2.1&auto=format&fit=crop&w=600&q=80" alt="Rosa">
                  <p class="element text-element" style="font-family:'Montserrat'; font-size:18px;">Cada momento contigo es un regalo. Gracias por llenar mi vida de amor.</p>`
      },
      {
        id: "aniversario",
        name: "Feliz Aniversario 🎉",
        icon: "💍",
        bg: "url('https://images.unsplash.com/photo-1511795409834-ef04bbd61622?ixlib=rb-1.2.1&auto=format&fit=crop&w=1200&q=80')",
        content: `<h1 class="element" style="font-family:'Great Vibes'; font-size:46px; color:white; text-shadow:2px 2px 4px #000;">Feliz Aniversario</h1>
                  <p class="element text-element" style="color:white; font-size:20px; text-shadow:1px 1px 3px #000;">365 días juntos, y quiero mil más contigo.</p>
                  <img class="media-element" src="https://images.unsplash.com/photo-1506084868230-bb9d95c24759?ixlib=rb-1.2.1&auto=format&fit=crop&w=600&q=80" alt="Aniversario">`
      },
      {
        id: "propuesta",
        name: "¿Quieres ser mi novia? 💍",
        icon: "💘",
        bg: "black",
        content: `<h1 class="element" style="font-family:'Parisienne'; font-size:40px; color:#ff80ab;">¿Quieres ser mi novia?</h1>
                  <img class="media-element" src="https://images.unsplash.com/photo-1519741497674-611481863552?ixlib=rb-1.2.1&auto=format&fit=crop&w=600&q=80" alt="Anillo">
                  <p class="element text-element" style="color:white;">Desde que te vi, supe que eras tú. ¿Me das la oportunidad de amarte?</p>`
      },
      {
        id: "cumple",
        name: "Feliz Cumpleaños 🎂",
        icon: "🎈",
        bg: "linear-gradient(45deg, #ff9a9e, #fecfef)",
        content: `<h1 class="element" style="font-family:'Pacifico'; font-size:44px; color:#d81b60;">¡Feliz Cumpleaños, Amor!</h1>
                  <img class="media-element" src="https://images.unsplash.com/photo-1545205597-3d9d02c29597?ixlib=rb-1.2.1&auto=format&fit=crop&w=600&q=80" alt="Pastel">
                  <div class="element">🎉🎁🎂</div>`
      },
      {
        id: "extra",
        name: "Sorpresa Musical 🎵",
        icon: "🎵",
        bg: "linear-gradient(135deg, #74b9ff, #00b894)",
        content: `<h1 class="element" style="font-family:'Caveat'; font-size:40px; color:white;">Una canción para ti</h1>
                  <iframe class="media-element" width="100%" height="80" src="https://open.spotify.com/embed/track/4u7Ene1Xd8vh8goO3P7z2P" frameborder="0" allowtransparency="true"></iframe>
                  <p class="element text-element" style="color:white;">Esta es nuestra canción...</p>`
      }
    ];

    const emojis = ["❤️", "💕", "😍", "🥰", "😘", "🌹", "🌸", "💫", "✨", "🎉", "💝", "🫶", "🌷", "💞", "💓", "💗", "💘", "💟", "😻", "🥺"];

    const fonts = ["Dancing Script", "Great Vibes", "Montserrat", "Caveat", "Pacifico", "Parisienne", "Arial"];

    // Cargar plantillas
    document.addEventListener("DOMContentLoaded", () => {
      const list = document.getElementById("templateList");
      templates.forEach(tpl => {
        const btn = document.createElement("button");
        btn.className = "template-btn";
        btn.innerHTML = `<span class="template-icon">${tpl.icon}</span> ${tpl.name}`;
        btn.onclick = () => loadTemplate(tpl);
        list.appendChild(btn);
      });
      loadTemplate(templates[0]);
    });

    function loadTemplate(tpl) {
      const canvas = document.getElementById("canvas");
      canvas.style.background = tpl.bg;
      canvas.innerHTML = tpl.content + `<div class="credit">By AnthZz Berrocal - BerMatMods</div>`;
    }

    // Modales
    const modal = document.getElementById("modal");
    const linkModal = document.getElementById("linkModal");

    function openModal() { modal.classList.add("open"); }
    function closeModal() { modal.classList.remove("open"); }
    function openLinkModal() { linkModal.classList.add("open"); }
    function closeLinkModal() { linkModal.classList.remove("open"); }

    document.querySelector(".close")?.addEventListener("click", closeModal);
    window.addEventListener("click", e => {
      if (e.target === modal) closeModal();
      if (e.target === linkModal) closeLinkModal();
    });

    // Funciones de personalización
    document.getElementById("addText").onclick = () => {
      const el = document.createElement("p");
      el.className = "element text-element";
      el.contentEditable = true;
      el.innerHTML = "Escribe aquí...";
      el.style.fontFamily = "Montserrat";
      el.style.fontSize = "18px";
      document.getElementById("canvas").insertBefore(el, document.querySelector(".credit"));
    };

    document.getElementById("addEmoji").onclick = () => {
      openModal();
      const body = document.getElementById("modalBody");
      body.innerHTML = `<h3>Elige un emoji</h3><div style="display:flex;flex-wrap:wrap;gap:10px;padding:10px;">${emojis.map(e => 
        `<span onclick="addEmoji('${e}')" style="font-size:28px;cursor:pointer;">${e}</span>`
      ).join("")}</div>`;
    };

    window.addEmoji = (emoji) => {
      const el = document.createElement("span");
      el.textContent = emoji;
      el.style.fontSize = "32px";
      el.style.margin = "0 5px";
      document.getElementById("canvas").insertBefore(el, document.querySelector(".credit"));
      closeModal();
    };

    document.getElementById("addGif").onclick = () => {
      openModal();
      const body = document.getElementById("modalBody");
      body.innerHTML = `<h3>Buscar Gif</h3>
        <input type="text" placeholder="Ej: love, kiss, dance" id="gifSearch" />
        <div id="gifResults" style="display:grid;grid-template-columns:repeat(2,1fr);gap:10px;margin-top:10px;"></div>`;
      document.getElementById("gifSearch").oninput = async (e) => {
        const q = e.target.value;
        if (q.length < 2) return;
        try {
          const res = await fetch(`https://api.giphy.com/v1/gifs/search?api_key=YOUR_GIPHY_API_KEY&q=${q}&limit=4`);
          const data = await res.json();
          const container = document.getElementById("gifResults");
          container.innerHTML = data.data.map(gif => `
            <img src="${gif.images.fixed_width.url}" style="width:100%;border-radius:12px;cursor:pointer;"
                 onclick="addGif('${gif.images.fixed_width.url}')" />
          `).join("");
        } catch (err) { }
      };
    };

    window.addGif = (url) => {
      const img = document.createElement("img");
      img.src = url;
      img.className = "media-element";
      document.getElementById("canvas").insertBefore(img, document.querySelector(".credit"));
      closeModal();
    };

    document.getElementById("addImage").onclick = () => {
      openModal();
      const body = document.getElementById("modalBody");
      body.innerHTML = `<h3>URL de la imagen</h3>
        <input type="text" placeholder="https://..." id="imgUrl" />
        <button class="modal-btn" onclick="addImage()">Añadir</button>`;
    };

    window.addImage = () => {
      const url = document.getElementById("imgUrl").value;
      if (url) {
        const img = document.createElement("img");
        img.src = url;
        img.className = "media-element";
        document.getElementById("canvas").insertBefore(img, document.querySelector(".credit"));
        closeModal();
      }
    };

    document.getElementById("addVideo").onclick = () => {
      openModal();
      const body = document.getElementById("modalBody");
      body.innerHTML = `<h3>URL de YouTube</h3>
        <input type="text" placeholder="https://youtube.com/watch?v=..." id="videoUrl" />
        <button class="modal-btn" onclick="addVideo()">Añadir</button>`;
    };

    window.addVideo = () => {
      const url = document.getElementById("videoUrl").value;
      const id = url.split("v=")[1]?.split("&")[0];
      if (id) {
        const iframe = document.createElement("iframe");
        iframe.src = `https://www.youtube.com/embed/${id}`;
        iframe.width = "300";
        iframe.height = "200";
        iframe.style.borderRadius = "16px";
        document.getElementById("canvas").insertBefore(iframe, document.querySelector(".credit"));
        closeModal();
      }
    };

    document.getElementById("addMusic").onclick = () => {
      openModal();
      const body = document.getElementById("modalBody");
      body.innerHTML = `<h3>URL de Spotify</h3>
        <input type="text" placeholder="https://open.spotify.com/track/..." id="musicUrl" />
        <button class="modal-btn" onclick="addMusic()">Añadir</button>`;
    };

    window.addMusic = () => {
      const url = document.getElementById("musicUrl").value;
      const embed = url.replace("/track/", "/embed/track/");
      const iframe = document.createElement("iframe");
      iframe.src = embed;
      iframe.width = "100%";
      iframe.height = "80";
      iframe.style.borderRadius = "8px";
      document.getElementById("canvas").insertBefore(iframe, document.querySelector(".credit"));
      closeModal();
    };

    document.getElementById("changeFont").onclick = () => {
      openModal();
      const body = document.getElementById("modalBody");
      body.innerHTML = `<h3>Fuente</h3>
        <select id="fontSelect">${fonts.map(f => `<option>${f}</option>`).join("")}</select>
        <button class="modal-btn" onclick="applyFont()">Aplicar</button>`;
    };

    window.applyFont = () => {
      const font = document.getElementById("fontSelect").value;
      document.querySelectorAll(".text-element, h1, p").forEach(el => el.style.fontFamily = font);
      closeModal();
    };

    document.getElementById("changeColor").onclick = () => {
      openModal();
      const body = document.getElementById("modalBody");
      body.innerHTML = `<h3>Color del texto</h3>
        <input type="color" id="textColor" value="#e91e63" />
        <button class="modal-btn" onclick="applyColor()">Aplicar</button>`;
    };

    window.applyColor = () => {
      const color = document.getElementById("textColor").value;
      document.querySelectorAll(".text-element, h1, p").forEach(el => el.style.color = color);
      closeModal();
    };

    document.getElementById("changeBg").onclick = () => {
      openModal();
      const body = document.getElementById("modalBody");
      body.innerHTML = `<h3>Fondo (color o URL)</h3>
        <input type="text" placeholder="Ej: pink o URL" id="bgInput" />
        <button class="modal-btn" onclick="applyBg()">Aplicar</button>`;
    };

    window.applyBg = () => {
      const bg = document.getElementById("bgInput").value;
      document.getElementById("canvas").style.background = bg.startsWith("http") ? `url(${bg})` : bg;
      closeModal();
    };

    // Generar enlace
    document.getElementById("generateLink").onclick = () => {
      const content = document.getElementById("canvas").innerHTML;
      const bg = document.getElementById("canvas").style.background;
      const id = Math.random().toString(36).substr(2, 9);
      localStorage.setItem(`detail_${id}`, JSON.stringify({ content, bg }));
      const link = `${window.location.href.split("index.html")[0]}view.html?id=${id}`;
      document.getElementById("shareLink").value = link;
      document.getElementById("whatsappShare").href = `https://wa.me/?text=💌%20Te%20envío%20una%20sorpresa%20de%20amor:%20${encodeURIComponent(link)}`;
      openLinkModal();
    };

    document.getElementById("copyLink").onclick = () => {
      const input = document.getElementById("shareLink");
      input.select();
      document.execCommand("copy");
      alert("✅ Enlace copiado");
    };

    // Créditos siempre visibles
    setInterval(() => {
      const credit = document.querySelector(".credit");
      if (credit) credit.innerHTML = "By AnthZz Berrocal - BerMatMods";
    }, 1000);
  </script>

  <!-- view.html (guárdalo como un archivo aparte) -->
  <!-- Este es un ejemplo de cómo debe ser view.html -->
  <!--
  <!DOCTYPE html>
  <html><head><title>Detalle</title><style>
    body{margin:0;height:100vh;display:flex;justify-content:center;align-items:center;background:#ffebee;font-family:'Dancing Script',cursive;}
    .content{max-width:500px;padding:30px;background:white;border-radius:20px;box-shadow:0 10px 30px rgba(0,0,0,0.1);text-align:center;}
  </style></head><body><div class="content" id="content"></div>
  <script>
    const id = new URLSearchParams(window.location.search).get("id");
    const data = JSON.parse(localStorage.getItem(`detail_${id}`));
    if (data) {
      document.getElementById("content").innerHTML = data.content;
      document.body.style.background = data.bg;
    } else {
      document.getElementById("content").innerHTML = "<h2>❌ No encontrado</h2>";
    }
  </script></body></html>
  -->

</body>
</html>
