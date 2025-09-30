<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Puzzle Hunt</title>
  <style>
    body { font-family: Arial, sans-serif; text-align: center; background: #f5f5f5; }
    h1 { color: #2c3e50; }
    #piece { margin: 20px auto; max-width: 200px; }
    .completed { font-size: 1.5em; color: green; margin-top: 20px; }
  </style>
</head>
<body>
  <h1>🎉 Puzzle Hunt 🎉</h1>
  <p>Scan QR codes to collect all the pieces!</p>
  <div id="game"></div>
  
  <script>
    // list of puzzle pieces
    const pieces = [
      "row-1-column-1.png",
      "row-1-column-2.png",
      "row-1-column-3.png",
      "row-2-column-1.png",
      "row-2-column-2.png",
      "row-2-column-3.png",
      "row-3-column-1.png",
      "row-3-column-2.png",
      "row-3-column-3.png"
    ];

    // load collected pieces from browser storage
    let collected = JSON.parse(localStorage.getItem("collectedPieces")) || [];

    function getRandomPiece() {
      const remaining = pieces.filter(p => !collected.includes(p));
      if (remaining.length === 0) {
        document.getElementById("game").innerHTML =
          `<div class="completed">✅ You have collected ALL puzzle pieces!</div>`;
        return;
      }
      // pick random
      const piece = remaining[Math.floor(Math.random() * remaining.length)];
      collected.push(piece);
      localStorage.setItem("collectedPieces", JSON.stringify(collected));

      document.getElementById("game").innerHTML =
        `<p>You found a new puzzle piece!</p>
         <img id="piece" src="${piece}" alt="Puzzle Piece">
         <p>Collected ${collected.length} / ${pieces.length}</p>`;
    }

    // show a piece when page loads
    getRandomPiece();
  </script>
</body>
</html><img width="1035" height="1981" alt="image" src="https://github.com/user-attachments/assets/fd80a66a-61df-4ea0-992b-f6d44b2928f0" />
