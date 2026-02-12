<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>¿Quieres ser mi San Valentín?</title>
  <style>
    body {
      margin: 0;
      height: 100vh;
      background: linear-gradient(135deg, #5f2cff, #00c9ff);
      display: flex;
      justify-content: center;
      align-items: center;
      font-family: 'Arial', sans-serif;
      color: white;
      overflow: hidden;
    }

    .card {
      background: rgba(255, 255, 255, 0.15);
      padding: 40px 60px;
      border-radius: 20px;
      text-align: center;
      box-shadow: 0 10px 30px rgba(0,0,0,0.3);
      backdrop-filter: blur(10px);
    }

    h1 {
      font-size: 2.5em;
      margin-bottom: 10px;
    }

    p {
      font-size: 1.2em;
      margin-bottom: 30px;
    }

    .buttons {
      display: flex;
      gap: 20px;
      justify-content: center;
    }

    button {
      padding: 12px 30px;
      font-size: 1.1em;
      border: none;
      border-radius: 30px;
      cursor: pointer;
      transition: 0.3s;
    }

    #yes {
      background: #00c9ff;
      color: #1a1a1a;
    }

    #yes:hover {
      background: #5f2cff;
      color: white;
      transform: scale(1.1);
    }

    #no {
      background: white;
      color: #5f2cff;
      position: relative;
    }

    .hearts {
      position: absolute;
      font-size: 24px;
      animation: float 4s infinite;
    }

    @keyframes float {
      0% { transform: translateY(0); opacity: 1; }
      100% { transform: translateY(-100vh); opacity: 0; }
    }

    .music-btn {
      margin-top: 20px;
      font-size: 0.9em;
      opacity: 0.8;
      cursor: pointer;
    }
  </style>
</head>
<body>

  <!-- Música -->
  <audio id="music" loop>
    <source src="tonos_de_azules.mp3" type="audio/mpeg">
  </audio>

  <div class="card" id="card">
    <h1>💙 ¿Quieres ser mi San Valentín? 💙</h1>
    <p>Con cariño, Piero xd ✨</p>
    <p>Se que no estamos juntos pero, prometo momentos bonitos, risas infinitas y muchos besos contigo 🥹</p>
    
    <div class="buttons">
      <button id="yes">Sí 💘</button>
      <button id="no">No 😢</button>
    </div>

    <div class="music-btn" onclick="playMusic()">
      ▶ Tocar música
    </div>
  </div>

  <script>
    const noBtn = document.getElementById("no");
    const yesBtn = document.getElementById("yes");
    const card = document.getElementById("card");
    const music = document.getElementById("music");

    function playMusic() {
      music.play();
    }

    noBtn.addEventListener("mouseover", () => {
      const x = Math.random() * (window.innerWidth - noBtn.offsetWidth);
      const y = Math.random() * (window.innerHeight - noBtn.offsetHeight);
      noBtn.style.position = "absolute";
      noBtn.style.left = x + "px";
      noBtn.style.top = y + "px";
    });

    yesBtn.addEventListener("click", () => {
      card.innerHTML = `
        <h1>🥰 Sabía que dirías que sí</h1>
        <p>Ahora oficialmente eres mi San Valentín 💙</p>
        <p>Te quiere mucho Jaysy</p>
      `;
      createHearts();
      music.play();
    });

    function createHearts() {
      for (let i = 0; i < 40; i++) {
        const heart = document.createElement("div");
        heart.className = "hearts";
        heart.innerHTML = "💙";
        heart.style.left = Math.random() * 100 + "vw";
        heart.style.bottom = "-20px";
        heart.style.animationDuration = (2 + Math.random() * 3) + "s";
        document.body.appendChild(heart);

        setTimeout(() => {
          heart.remove();
        }, 5000);
      }
    }
  </script>

</body>
</html>
