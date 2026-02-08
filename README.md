# sujithsrsh40.github.io
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>For Veena 💖</title>

  <style>
    body {
      margin: 0;
      height: 100vh;
      font-family: 'Segoe UI', sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      background: linear-gradient(135deg, #ff758c, #ff7eb3);
      overflow: hidden;
    }

    /* Floating hearts */
    .heart {
      position: fixed;
      bottom: -20px;
      color: rgba(255,255,255,0.8);
      font-size: 20px;
      animation: floatUp 6s linear infinite;
    }

    @keyframes floatUp {
      0% {
        transform: translateY(0) scale(1);
        opacity: 1;
      }
      100% {
        transform: translateY(-110vh) scale(1.5);
        opacity: 0;
      }
    }

    .card {
      background: white;
      padding: 25px 20px 35px;
      border-radius: 20px;
      text-align: center;
      box-shadow: 0 15px 40px rgba(0,0,0,0.2);
      max-width: 340px;
      width: 90%;
      position: relative;
      z-index: 2;
    }

    h1 {
      margin: 10px 0 5px;
      font-size: 26px;
      color: #ff4f7a;
    }

    p {
      margin: 15px 0 20px;
      font-size: 18px;
      color: #333;
    }

    .photo {
      width: 100%;
      height: 180px;
      border-radius: 15px;
      overflow: hidden;
      margin-bottom: 15px;
    }

    .photo img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    .buttons {
      position: relative;
      height: 120px;
    }

    button {
      padding: 12px 22px;
      font-size: 16px;
      border: none;
      border-radius: 30px;
      cursor: pointer;
      position: absolute;
    }

    #yesBtn {
      background: #ff4f7a;
      color: white;
      left: 50%;
      transform: translateX(-50%);
      bottom: 10px;
    }

    #noBtn {
      background: #ddd;
      color: #555;
      left: 20px;
      top: 10px;
    }

    .result {
      display: none;
      font-size: 22px;
      color: #ff4f7a;
      margin-top: 20px;
    }
  </style>
</head>

<body>

  <!-- Card -->
  <div class="card">
    <div class="photo">
      <!-- 🔁 Replace photo.jpg with your image filename -->
      <img src="photo.jpg" alt="Us 💕">
    </div>

    <h1>Veena 💖</h1>
    <p>Will you go on a date with me?</p>

    <div class="buttons">
      <button id="yesBtn">Yes 💘</button>
      <button id="noBtn">No 🙈</button>
    </div>

    <div class="result" id="result">
      It’s a date then! 💕🥰
    </div>
  </div>

  <script>
    // Moving NO button
    const noBtn = document.getElementById("noBtn");
    const yesBtn = document.getElementById("yesBtn");
    const result = document.getElementById("result");

    function moveButton() {
      const card = document.querySelector(".card");
      const maxX = card.clientWidth - noBtn.offsetWidth;
      const maxY = card.clientHeight - noBtn.offsetHeight;

      const x = Math.random() * maxX;
      const y = Math.random() * maxY;

      noBtn.style.left = `${x}px`;
      noBtn.style.top = `${y}px`;
    }

    noBtn.addEventListener("mouseenter", moveButton);
    noBtn.addEventListener("touchstart", moveButton);

    yesBtn.addEventListener("click", () => {
      document.querySelector(".buttons").style.display = "none";
      result.style.display = "block";
    });

    // Floating hearts generator
    function createHeart() {
      const heart = document.createElement("div");
      heart.classList.add("heart");
      heart.innerText = "💖";
      heart.style.left = Math.random() * 100 + "vw";
      heart.style.fontSize = (16 + Math.random() * 20) + "px";
      heart.style.animationDuration = (4 + Math.random() * 3) + "s";

      document.body.appendChild(heart);

      setTimeout(() => {
        heart.remove();
      }, 7000);
    }

    setInterval(createHeart, 400);
  </script>
</body>
</html>
