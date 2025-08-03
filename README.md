<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Happy Birthday!</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Pacifico&family=Open+Sans&display=swap');

    body {
      margin: 0;
      height: 100vh;
      background: linear-gradient(135deg, #f6d365 0%, #fda085 100%);
      display: flex;
      justify-content: center;
      align-items: center;
      overflow: hidden;
      font-family: 'Open Sans', sans-serif;
    }

    .birthday-card {
      position: relative;
      background: white;
      padding: 40px 60px;
      border-radius: 20px;
      box-shadow: 0 8px 30px rgba(0,0,0,0.2);
      max-width: 400px;
      text-align: center;
      z-index: 10;
    }

    .birthday-card h1 {
      font-family: 'Pacifico', cursive;
      font-size: 3em;
      margin: 0 0 20px;
      color: #ff4081;
      text-shadow: 1px 1px 5px rgba(255,64,129,0.5);
    }

    .birthday-card p {
      font-size: 1.2em;
      margin: 15px 0;
      color: #444;
      line-height: 1.4;
    }

    .birthday-card .signature {
      margin-top: 30px;
      font-style: italic;
      color: #ff4081;
      font-weight: 700;
    }

    /* Balloon styles */
    .balloons {
      position: absolute;
      bottom: 10px;
      left: 50%;
      width: 300px;
      height: 400px;
      pointer-events: none;
      transform: translateX(-50%);
      overflow: visible;
      z-index: 5;
    }

    .balloon {
      position: absolute;
      bottom: 0;
      width: 40px;
      height: 60px;
      border-radius: 50% 50% 50% 50% / 60% 60% 40% 40%;
      background: red;
      opacity: 0.9;
      animation: floatUp linear infinite;
      filter: drop-shadow(0 3px 3px rgba(0,0,0,0.1));
    }
    .balloon::after {
      content: "";
      position: absolute;
      bottom: -10px;
      left: 50%;
      width: 2px;
      height: 20px;
      background: #555;
      transform: translateX(-50%);
      border-radius: 1px;
    }

    /* Different colors and animation duration */
    .balloon:nth-child(1) {
      left: 20%;
      background: #f44336;
      animation-duration: 6s;
      animation-delay: 0s;
    }
    .balloon:nth-child(2) {
      left: 40%;
      background: #2196f3;
      animation-duration: 8s;
      animation-delay: 1.5s;
    }
    .balloon:nth-child(3) {
      left: 60%;
      background: #ffeb3b;
      animation-duration: 7s;
      animation-delay: 0.5s;
    }
    .balloon:nth-child(4) {
      left: 80%;
      background: #4caf50;
      animation-duration: 9s;
      animation-delay: 2s;
    }
    .balloon:nth-child(5) {
      left: 50%;
      background: #e91e63;
      animation-duration: 10s;
      animation-delay: 1s;
    }

    @keyframes flotup{
      0% {
        transform: translateY(0) scale(1);
        opacity: 0.9;
      }
      50% {
        transform: translateY(-40px) scale(1.05);
        opacity: 1;
      }
      80% {
        transform: translateY(-400px) scale(1);
        opacity: 0;
      }
    }

    /* Confetti container */
    .confetti-container {
      position: fixed;
      pointer-events: none;
      width: 100vw;
      height: 100vh;
      top: 0; left: 0;
      overflow: visible;
      z-index: 0;
    }

    .confetti {
      position: absolute;
      width: 8px;
      height: 8px;
      background-color: red;
      opacity: 0.8;
      transform-origin: center center;
      animation-name: confetti-fall, confetti-spin;
      animation-timing-function: linear;
      animation-iteration-count: infinite;
    }

    @keyframes confetti-fall {
      0% {
        transform: translateY(0);
        opacity: 1;
      }
      100% {
        transform: translateY(100vh);
        opacity: 0;
      }
    }
    @keyframes confetti-spin {
      0% {
        transform: rotate(0deg);
      }
      100% {
        transform: rotate(360deg);
      }
    }
  </style>
</head>
<body>
  <div class="birthday-card">
    <h1>Happy Friendship Day Bro <span contenteditable="true" style="color:#2196f3; border-bottom: 1px dashed #2196f3; cursor:text;"></span>!</h1>
    <p>A true friend is one who walks in when the rest of the world walks out.</p>
    <p class="signature">- <span contenteditable="true" style="color:#e91e63; border-bottom: 1px dashed #e91e63; cursor:text;"></span></p>
    <div class="balloons">
      <div class="balloon"></div>
      <div class="balloon"></div>
      <div class="balloon"></div>
      <div class="balloon"></div>
      <div class="balloon"></div>
    </div>
  </div>

  <div class="confetti-container"></div>

  <script>
    // Generate confetti dynamically
    const confettiContainer = document.querySelector('.confetti-container');
    const colors = ['#f44336','#e91e63','#9c27b0','#2196f3','#4caf50','#ffeb3b'];

    function createConfettiPiece() {
      const confetti = document.createElement('div');
      confetti.classList.add('confetti');
      confetti.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
      confetti.style.left = Math.random() * window.innerWidth + 'px';
      confetti.style.top = -10 + 'px';
      confetti.style.width = confetti.style.height = (5 + Math.random() * 8) + 'px';
      confetti.style.animationDuration = (3 + Math.random() * 4) + 's';
      confetti.style.animationDelay = (Math.random() * 5) + 's';
      confetti.style.transform = `rotate(${Math.random()*360}deg)`;
      confettiContainer.appendChild(confetti);

      setTimeout(() => {
        confetti.remove();
      }, 7000);
    }

    // Keep generating confetti every 300ms
    setInterval(createConfettiPiece, 300);
  </script>
</body>
</html>

