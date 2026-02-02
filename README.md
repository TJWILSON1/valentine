<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>💌 Valentine Invite 💌</title>

  <style>
    body {
      background: linear-gradient(135deg, #ff9a9e, #fad0c4);
      font-family: "Courier New", monospace;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
      overflow: hidden;
      color: #5a0f2e;
      text-align: center;
    }

    .card {
      position: relative;
      background: rgba(255, 255, 255, 0.95);
      border-radius: 22px;
      padding: 35px 45px;
      box-shadow: 0 12px 35px rgba(0,0,0,0.25);
      max-width: 520px;
      z-index: 2;
    }

    h1 {
      font-size: 28px;
      margin-bottom: 20px;
    }

    .buttons {
      display: flex;
      justify-content: center;
      gap: 20px;
      margin-top: 20px;
      flex-wrap: wrap;
    }

    button {
      font-family: "Courier New", monospace;
      border: none;
      border-radius: 14px;
      padding: 14px 28px;
      font-size: 18px;
      cursor: pointer;
      transition: all 0.3s ease;
    }

    #yesBtn {
      background-color: #ff4d6d;
      color: white;
      box-shadow: 0 6px 15px rgba(255, 77, 109, 0.4);
    }

    #noBtn {
      background-color: #eee;
      color: #555;
    }

    #message {
      margin-top: 25px;
      font-size: 18px;
      font-weight: bold;
      color: #c9184a;
      min-height: 60px;
    }

    /* 🌸 Lily clip art positioning */
    .lily {
      position: absolute;
      width: 90px;
      opacity: 0.9;
    }

    .lily.left {
      top: -25px;
      left: -25px;
      transform: rotate(-15deg);
    }

    .lily.right {
      bottom: -25px;
      right: -25px;
      transform: rotate(15deg);
    }

    /* 🎊 Confetti */
    .confetti {
      position: fixed;
      top: -10px;
      width: 10px;
      height: 10px;
      background-color: pink;
      animation: fall 3s linear forwards;
      z-index: 1;
    }

    @keyframes fall {
      to {
        transform: translateY(110vh) rotate(720deg);
        opacity: 0;
      }
    }
  </style>
</head>
<body>

  <div class="card">

    <!-- 🌸 Pink Lily SVGs -->
    <svg class="lily left" viewBox="0 0 100 100">
      <path d="M50 10 C20 40, 20 70, 50 90 C80 70, 80 40, 50 10"
            fill="#ff7eb6"/>
      <circle cx="50" cy="50" r="6" fill="#ffd1dc"/>
    </svg>

    <svg class="lily right" viewBox="0 0 100 100">
      <path d="M50 10 C20 40, 20 70, 50 90 C80 70, 80 40, 50 10"
            fill="#ff7eb6"/>
      <circle cx="50" cy="50" r="6" fill="#ffd1dc"/>
    </svg>

    <h1>💘 Yasmeen, will you be my Valentine? 💘</h1>

    <div class="buttons">
      <button id="yesBtn">YES 💖</button>
      <button id="noBtn">no.</button>
    </div>

    <div id="message"></div>
  </div>

  <script>
    const yesBtn = document.getElementById("yesBtn");
    const noBtn = document.getElementById("noBtn");
    const message = document.getElementById("message");

    let yesSize = 18;
    let noClicks = 0;

    const noMessages = [
      "😐 wow. that kinda hurt.",
      "😅 okay but what if you misclicked?",
      "🤨 this button is looking suspicious.",
      "😔 TJ is pretending not to see this.",
      "😳 are we really doing this right now?",
      "💔 the yes button is literally begging.",
      "😭 this is getting personal.",
      "🙃 the universe is judging you.",
      "🫠 TJ is dramatically sighing.",
      "😌 okay but imagine clicking yes though."
    ];

    noBtn.addEventListener("click", () => {
      message.textContent =
        noMessages[Math.min(noClicks, noMessages.length - 1)];
      noClicks++;

      yesSize += 10;
      yesBtn.style.fontSize = yesSize + "px";
      yesBtn.style.padding = (14 + yesSize / 3) + "px";
    });

    yesBtn.addEventListener("click", () => {
      message.innerHTML =
        "💞 YAY!!! 💞<br><br>" +
        "Yasmeen, you just made TJ incredibly happy.<br>" +
        "Can’t wait to be your Valentine 💌<br><br>" +
        "ヽ(♡‿♡)ノ";

      noBtn.style.display = "none";
      launchConfetti();
    });

    function launchConfetti() {
      for (let i = 0; i < 120; i++) {
        const confetti = document.createElement("div");
        confetti.classList.add("confetti");
        confetti.style.left = Math.random() * 100 + "vw";
        confetti.style.backgroundColor =
          ["#ff4d6d", "#ff7eb6", "#ffd1dc", "#fff"][Math.floor(Math.random() * 4)];
        confetti.style.animationDuration =
          2 + Math.random() * 2 + "s";
        document.body.appendChild(confetti);

        setTimeout(() => confetti.remove(), 4000);
      }
    }
  </script>

</body>
</html>
