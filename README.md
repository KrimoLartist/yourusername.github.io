<!DOCTYPE html>
<html lang="ar">
<head>
  <meta charset="UTF-8" />
  <title>كشف التفاحات 🍏</title>
  <style>
    body {
      background-color: #111;
      color: #0f0;
      font-family: monospace;
      text-align: center;
      padding-top: 40px;
    }

    h1 {
      color: #0f0;
    }

    #grid {
      display: grid;
      grid-template-columns: repeat(5, 60px);
      gap: 5px;
      justify-content: center;
      margin: 30px auto;
    }

    .cell {
      width: 60px;
      height: 60px;
      background-color: #222;
      border: 2px solid #0f0;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 24px;
      color: #0f0;
      cursor: pointer;
    }

    .revealed.apple {
      background-color: #0f0;
      color: #000;
    }

    .revealed.empty {
      background-color: #f00;
      color: #fff;
    }

    button {
      background-color: #0f0;
      color: #000;
      padding: 10px 20px;
      border: none;
      font-size: 16px;
      cursor: pointer;
      margin-top: 20px;
    }
  </style>
</head>
<body>
  <h1>Xscript 🍏 كشف التفاحات</h1>
  <div id="grid"></div>
  <button onclick="reveal()">🔍 كشف التفاحات</button>

  <script>
    const grid = document.getElementById("grid");
    const size = 25;
    const apples = [];

    function generateGrid() {
      grid.innerHTML = "";
      apples.length = 0;

      for (let i = 0; i < size; i++) {
        const cell = document.createElement("div");
        cell.classList.add("cell");
        cell.dataset.index = i;
        grid.appendChild(cell);

        // ضع التفاحات عشوائيًا بنسبة 20%
        apples.push(Math.random() < 0.2);
      }
    }

    function reveal() {
      const cells = document.querySelectorAll(".cell");
      cells.forEach((cell, i) => {
        if (apples[i]) {
          cell.classList.add("revealed", "apple");
          cell.textContent = "🍏";
        } else {
          cell.classList.add("revealed", "empty");
          cell.textContent = "💣";
        }
      });
    }

    generateGrid();
  </script>
</body>
</html>
