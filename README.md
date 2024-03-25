<h1 align="center">Hi 👋, I'm Vaibhav Rawat</h1>
<h3 align="center">A developer from India</h3>

<ul>
  <li>🔭 I’m currently working on <strong>Android</strong></li>
  <li>🌱 I’m currently learning <strong>Kotlin</strong></li>
  <li>👯 I’m looking to collaborate on <strong>Android</strong></li>
  <li>📫 How to reach me <strong>rawatvaibhav27@gmail.com</strong></li>
</ul>

<h3 align="left">Connect with me:</h3>
<p align="left">
  <a href="https://linkedin.com/in/vaibhav rawat" target="blank"><img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/linked-in-alt.svg" alt="vaibhav rawat" height="30" width="40" /></a>
  <a href="https://instagram.com/vaibhavrwt5" target="blank"><img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/instagram.svg" alt="vaibhavrwt5" height="30" width="40" /></a>
</p>

<h3 align="left">Languages and Tools:</h3>
<p align="left">
  <a href="https://developer.android.com" target="_blank" rel="noreferrer"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/android/android-original-wordmark.svg" alt="android" width="40" height="40"/></a>
  <a href="https://www.blender.org/" target="_blank" rel="noreferrer"><img src="https://download.blender.org/branding/community/blender_community_badge_white.svg" alt="blender" width="40" height="40"/></a>
  <a href="https://www.cprogramming.com/" target="_blank" rel="noreferrer"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/c/c-original.svg" alt="c" width="40" height="40"/></a>
  <a href="https://www.w3.org/html/" target="_blank" rel="noreferrer"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/html5/html5-original-wordmark.svg" alt="html5" width="40" height="40"/></a>
  <a href="https://www.java.com" target="_blank" rel="noreferrer"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/java/java-original.svg" alt="java" width="40" height="40"/></a>
  <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript" target="_blank" rel="noreferrer"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/javascript/javascript-original.svg" alt="javascript" width="40" height="40"/></a>
  <a href="https://kotlinlang.org" target="_blank" rel="noreferrer"><img src="https://www.vectorlogo.zone/logos/kotlinlang/kotlinlang-icon.svg" alt="kotlin" width="40" height="40"/></a>
  <a href="https://www.mysql.com/" target="_blank" rel="noreferrer"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/mysql/mysql-original-wordmark.svg" alt="mysql" width="40" height="40"/></a>
  <a href="https://unity.com/" target="_blank" rel="noreferrer"><img src="https://www.vectorlogo.zone/logos/unity3d/unity3d-icon.svg" alt="unity" width="40" height="40"/></a>
</p>

<h3 align="center">Play Snake Game!</h3>
<p align="center">Use your commits to control the snake!</p>

<canvas id="gameCanvas" width="400" height="400" style="border: 1px solid black; display: block; margin: 0 auto;"></canvas>
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Snake Game</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      background-color: #f0f0f0;
    }
    canvas {
      border: 1px solid #333;
    }
  </style>
</head>
<body>
  <canvas id="gameCanvas" width="400" height="400"></canvas>

  <script>
    const canvas = document.getElementById("gameCanvas");
    const ctx = canvas.getContext("2d");

    // Set the size of each grid cell
    const gridSize = 20;
    const canvasSize = 400;
    const cellSize = canvasSize / gridSize;

    // Initialize snake properties
    let snake = [{ x: 10, y: 10 }];
    let food = { x: Math.floor(Math.random() * gridSize), y: Math.floor(Math.random() * gridSize) };
    let dx = 1;
    let dy = 0;
    let score = 0;

    // Main game loop
    function main() {
      clearCanvas();
      updateSnake();
      drawSnake();
      drawFood();
      if (checkCollision()) {
        resetGame();
      }
      setTimeout(main, 100); // Move snake every 100 milliseconds
    }

    // Clear the canvas
    function clearCanvas() {
      ctx.fillStyle = "#f0f0f0";
      ctx.fillRect(0, 0, canvasSize, canvasSize);
    }

    // Update the snake's position
    function updateSnake() {
      const head = { x: snake[0].x + dx, y: snake[0].y + dy };
      snake.unshift(head);
      if (head.x === food.x && head.y === food.y) {
        score++;
        generateFood();
      } else {
        snake.pop();
      }
    }

    // Draw the snake on the canvas
    function drawSnake() {
      ctx.fillStyle = "#000";
      snake.forEach(segment => {
        ctx.fillRect(segment.x * cellSize, segment.y * cellSize, cellSize, cellSize);
      });
    }

    // Draw the food on the canvas
    function drawFood() {
      ctx.fillStyle = "#f00";
      ctx.fillRect(food.x * cellSize, food.y * cellSize, cellSize, cellSize);
    }

    // Generate new food
    function generateFood() {
      food = { x: Math.floor(Math.random() * gridSize), y: Math.floor(Math.random() * gridSize) };
    }

    // Check for collisions with walls or snake's body
    function checkCollision() {
      const head = snake[0];
      return (
        head.x < 0 || head.x >= gridSize ||
        head.y < 0 || head.y >= gridSize ||
        snake.slice(1).some(segment => segment.x === head.x && segment.y === head.y)
      );
    }

    // Reset the game
    function resetGame() {
      snake = [{ x: 10, y: 10 }];
      food = { x: Math.floor(Math.random() * gridSize), y: Math.floor(Math.random() * gridSize) };
      dx = 1;
      dy = 0;
      score = 0;
    }

    // Start the game
    main();
  </script>
</body>
</html>

