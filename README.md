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
      animation: floatUp 6s linear infinite;
      z-index: 1;
      pointer-events: none;
    }

    @keyframes floatUp {
      from { transform: translateY(0) scale(1); opacity: 1; }
      to { transform: translateY(-110vh) scale(1.5); opacity: 0; }
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
      color: #ff4f7a;
      margin: 5px 0;
    }

    p {
      font-size: 18px;
      margin: 15px 0 20px;
    }

    /* Photo hidden initially */
    .photo {
      display: none;
      width: 100%;
      height: 180px;
      border-radius: 15px;
      overflow: hidden;
      margin-bottom: 15px;
      animation: fadeIn 0.8s ease forwards;
    }

    .photo img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: scale(0.95); }
      to { opacity: 1; transform: scale(1); }
    }

    .buttons {
      position: relative;
      height: 120px;
      margin-top: 10px;
    }

    button {
      padding: 12px 22px;
      font-size: 16px;
      border: none;
      border-radius: 30px;
      cursor: pointer;
      position: absolute;
      white-space: nowrap;
    }

    #yesBtn {
      background: #ff4f7a;
      color: white;
      left: 50%;
      bottom: 10px;
      transform: translateX(-50%);
    }

    #noBtn {
      background: #ddd;
      color: #555;
      top: 10px;
      left: 20px;
    }

    .result {
      display: none;
      font-size: 22px;
      color: #ff4f7a;
      margin-top: 15px;
    }
  </style>
</head>

<body>

  <div class="card" id="card">
    <div class="photo" id="photo">
      <img src="photo.jpg" alt="Us 💕">
    </div>

    <h1>Veena 💖</h1>
    <p id="question">Will you be my valentine? 👉🏻👈🏻</p>

    <div class="buttons" id="buttonBox">
      <button id="yesBtn">Yes 💘</button>
      <button id="noBtn">No 🙈</button>
    </div>

    <div class="result" id="result">
      I knew you’d say yes! 🥰💛
    </div>
  </div>

  <script>
    const noBtn = document.getElementById("noBtn");
    const yesBtn = document.getElementById("yesBtn");
    const card = document.getElementById("card");
    const buttonBox = document.getElementById("buttonBox");
    const photo = document.getElementById("photo");
    const result = document.getElementById("result");

    function moveNoButton() {
      const cardRect = card.getBoundingClientRect();
      const yesRect = yesBtn.getBoundingClientRect();

      let x, y, overlap;

      do {
        x = Math.random() * (card.clientWidth - noBtn.offsetWidth);
        y = Math.random() * (card.clientHeight - noBtn.offsetHeight - 40);

        const noRect = {
          left: cardRect.left + x,
          right: cardRect.left + x + noBtn.offsetWidth,
          top: cardRect.top + y,
          bottom: cardRect.top + y + noBtn.offsetHeight
        };

        overlap = !(
          noRect.right < yesRect.left ||
          noRect.left > yesRect.right ||
          noRect.bottom < yesRect.top ||
          noRect.top > yesRect.bottom
        );

      } while (overlap);

      noBtn.style.left = x + "px";
      noBtn.style.top = y + "px";
    }

    noBtn.addEventListener("mouseenter", moveNoButton);
    noBtn.addEventListener("touchstart", moveNoButton);

    yesBtn.addEventListener("click", () => {
      buttonBox.style.display = "none";
      photo.style.display = "block";
      result.style.display = "block";
    });

    // Floating hearts
    function createHeart() {
      const heart = document.createElement("div");
      heart.className = "heart";
      heart.innerText = Math.random() > 0.5 ? "💖" : "💛";
      heart.style.left = Math.random() * 100 + "vw";
      heart.style.fontSize = 16 + Math.random() * 20 + "px";
      heart.style.animationDuration = 4 + Math.random() * 3 + "s";
      document.body.appendChild(heart);
      setTimeout(() => heart.remove(), 7000);
    }

    setInterval(createHeart, 450);
  </script>

</body>
</html>
