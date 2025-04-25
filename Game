<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Crossy Road Code Game</title>
  <style>
    body { margin: 0; padding: 0; background-color: #d0f0c0; font-family: Arial, sans-serif; text-align: center; }
    #gameCanvas { background-color: #7ec850; display: block; margin: 20px auto; border: 2px solid #333; }
    #codeMessage { margin-top: 20px; font-size: 24px; font-weight: bold; display: none; }
    .controls { display: flex; flex-direction: column; align-items: center; margin-top: 10px; }
    .controls-row { display: flex; justify-content: center; margin: 5px; }
    .control-button { width: 60px; height: 60px; margin: 5px; font-size: 24px; border-radius: 10px; border: none; background-color: #333; color: #fff; cursor: pointer; }
  </style>
</head>
<body>
  <canvas id="gameCanvas" width="600" height="400"></canvas>
  <div id="codeMessage">Your code is: 1 Corinthians 12:20-25, Barrel Ball Paint</div>
  <div class="controls">
    <div class="controls-row">
      <button class="control-button" id="up">↑</button>
    </div>
    <div class="controls-row">
      <button class="control-button" id="left">←</button>
      <button class="control-button" id="down">↓</button>
      <button class="control-button" id="right">→</button>
    </div>
  </div>

  <script>
    const canvas = document.getElementById('gameCanvas');
    const ctx = canvas.getContext('2d');

    let player = { x: 290, y: 370, width: 20, height: 20, color: 'blue' };
    let cars = [];
    let gameOver = false;

    function createCar(y) {
      return { x: Math.random() * 600, y: y, width: 40, height: 20, speed: 2 + Math.random() * 3, color: 'red' };
    }

    for (let i = 0; i < 4; i++) {
      cars.push(createCar(80 + i * 60));
    }

    function drawPlayer() {
      ctx.fillStyle = player.color;
      ctx.fillRect(player.x, player.y, player.width, player.height);
    }

    function drawCars() {
      cars.forEach(car => {
        ctx.fillStyle = car.color;
        ctx.fillRect(car.x, car.y, car.width, car.height);
        car.x += car.speed;
        if (car.x > 600) car.x = -car.width;
      });
    }

    function checkCollision() {
      cars.forEach(car => {
        if (player.x < car.x + car.width && player.x + player.width > car.x && player.y < car.y + car.height && player.y + player.height > car.y) {
          gameOver = true;
          alert('Game Over! Try again.');
          window.location.reload();
        }
      });
    }

    function checkWin() {
      if (player.y <= 0) {
        document.getElementById('codeMessage').style.display = 'block';
        gameOver = true;
      }
    }

    function gameLoop() {
      if (!gameOver) {
        ctx.clearRect(0, 0, canvas.width, canvas.height);
        drawPlayer();
        drawCars();
        checkCollision();
        checkWin();
        requestAnimationFrame(gameLoop);
      }
    }

    function movePlayer(direction) {
      if (direction === 'up') player.y -= 20;
      if (direction === 'down') player.y += 20;
      if (direction === 'left') player.x -= 20;
      if (direction === 'right') player.x += 20;
    }

    document.addEventListener('keydown', e => {
      if (e.key === 'ArrowUp') movePlayer('up');
      if (e.key === 'ArrowDown') movePlayer('down');
      if (e.key === 'ArrowLeft') movePlayer('left');
      if (e.key === 'ArrowRight') movePlayer('right');
    });

    document.getElementById('up').addEventListener('click', () => movePlayer('up'));
    document.getElementById('down').addEventListener('click', () => movePlayer('down'));
    document.getElementById('left').addEventListener('click', () => movePlayer('left'));
    document.getElementById('right').addEventListener('click', () => movePlayer('right'));

    gameLoop();
  </script>
</body>
</html>
