<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Minimal Working Demo</title>

  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 20px;
      background: #f5f5f5;
      transition: background 0.3s, color 0.3s;
    }

    .dark {
      background: #111;
      color: #eee;
    }

    .container {
      max-width: 800px;
      margin: auto;
    }

    button {
      padding: 10px 16px;
      border: none;
      background: #0a7e8c;
      color: white;
      font-size: 14px;
      border-radius: 6px;
      cursor: pointer;
    }

    #gameBox {
      margin-top: 30px;
      padding: 20px;
      background: white;
      border-radius: 8px;
    }

    .dark #gameBox {
      background: #222;
    }
  </style>
</head>

<body>
  <div class="container">
    <h1>Minimal Working Demo</h1>

    <!-- Dark / Light toggle -->
    <button id="themeBtn">Toggle Dark Mode</button>

    <!-- Simple click mini-game -->
    <div id="gameBox">
      <h2>Click Mini-Game</h2>
      <p>Score: <span id="score">0</span></p>
      <button id="clickBtn">Click Me</button>
    </div>

    <!-- Animated GitHub stats (replace YOUR_GITHUB_USERNAME) -->
    <h2 style="margin-top:40px">GitHub Stats</h2>
    <img src="https://github-readme-stats.vercel.app/api?username=YOUR_GITHUB_USERNAME&show_icons=true&theme=default" width="480" />
    <img src="https://github-readme-streak-stats.herokuapp.com/?user=YOUR_GITHUB_USERNAME" width="480" />
    <img src="https://github-profile-trophy.vercel.app/?username=YOUR_GITHUB_USERNAME" width="480" />
  </div>

  <script>
    // Theme toggle
    const themeBtn = document.getElementById("themeBtn");
    themeBtn.onclick = () => {
      document.body.classList.toggle("dark");
    };

    // Mini game
    let score = 0;
    const scoreEl = document.getElementById("score");
    const clickBtn = document.getElementById("clickBtn");

    clickBtn.onclick = () => {
      score++;
      scoreEl.textContent = score;
    };
  </script>
</body>
</html>
