<!DOCTYPE html>
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

    /* Button area split into two lanes */
    .buttons {
      display: flex;
      justify-content: space-between;
      position: relative;
      height: 80px;
      margin-top: 10px;
    }

    .lane {
      width: 48%;
      position: relative;
    }

    button {
      padding: 12px 22px;
      font-size: 16px;
      border: none;
      border-radius: 30px;
      cursor: pointer;
      position: absolute;
      left: 50%;
      transform: translateX(-50%);
      top: 10px;
    }

    #yesBtn {
      background: #ff4f7a;
      color: white;
    }

    #noBtn {
      background: #ddd;
      color: #555;
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

  <div class="card">
    <div class="photo" id="photo">
      <img src="photo.jpg" alt="Us 💕">
    </div>

    <h1>Veena 💖</h1>
    <p>Will you go on a date with me?</p>

    <div class="buttons" id="buttonBox">
      <div class="lane" id="noLane">
        <button id="noBtn">No 🙈</button>
      </div>
      <div class="lane">
        <button id="yesBtn">Yes 💘</button>
      </div>
    </div>

    <div class="result" id="result">
      It’s a date then! 💕🥰
    </div>
  </div>

  <script>
    const noBtn = document.getElementById("noBtn");
    const noLane = document.getElementById("noLane");
    const yesBtn = document.getElementById("yesBtn");
    const photo = document.getElementById("photo");
    const buttonBox = document.getElementById("buttonBox");
    const result = document.getElementById("result");

    // NO button moves ONLY inside its own lane
    function moveButton() {
      const maxX = noLane.clientWidth - noBtn.offsetWidth;
      const maxY = noLane.clientHeight - noBtn.offsetHeight;

      const x = Math.random() * maxX;
      const y = Math.random() * maxY;

      noBtn.style.left = `${x + noBtn.offsetWidth / 2}px`;
      noBtn.style.top = `${y}px`;
      noBtn.style.transform = "translateX(0)";
    }

    noBtn.addEventListener("mouseenter", moveButton);
    noBtn.addEventListener("touchstart", moveButton);

    yesBtn.addEventListener("click", () => {
      buttonBox.style.display = "none";
      photo.style.display = "block";
      result.style.display = "block";
    });

    // Floating hearts
    function createHeart() {
      const heart = document.createElement("div");
      heart.className = "heart";
      heart.innerText = Math.random() > 0.5 ? "💖" : "💘";
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
