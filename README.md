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
      "C:\Users\hif6977\AppData\Local\Temp\7f2f06cb-89ed-4f39-8666-42642dd2213b_PineTools.com_2025-09-29_16h16m24s.zip.13b\PineTools.com_files\row-1-column-1.png",
      "C:\Users\hif6977\AppData\Local\Temp\31ab854c-0d46-49de-ab77-d8cc2451db2d_PineTools.com_2025-09-29_16h16m24s.zip.b2d\PineTools.com_files\row-1-column-2.png",
      "C:\Users\hif6977\AppData\Local\Temp\cc6c14be-f6c2-413b-a78e-69c68b9301aa_PineTools.com_2025-09-29_16h16m24s.zip.1aa\PineTools.com_files\row-1-column-3.png",
      "C:\Users\hif6977\AppData\Local\Temp\16f2c014-2d6c-4dbe-981f-d6c1085bf616_PineTools.com_2025-09-29_16h16m24s.zip.616\PineTools.com_files\row-2-column-1.png",
      "C:\Users\hif6977\AppData\Local\Temp\f0193b85-36f7-4a50-98a1-32a2b9214e18_PineTools.com_2025-09-29_16h16m24s.zip.e18\PineTools.com_files\row-2-column-2.png",
      "C:\Users\hif6977\AppData\Local\Temp\a8f0f440-5514-47d4-a6f0-ba100832a8df_PineTools.com_2025-09-29_16h16m24s.zip.8df\PineTools.com_files\row-2-column-3.png",
      "C:\Users\hif6977\AppData\Local\Temp\fb219640-9a21-4886-b99c-ff6f1f1d7fe1_PineTools.com_2025-09-29_16h16m24s.zip.fe1\PineTools.com_files\row-3-column-1.png",
      "C:\Users\hif6977\AppData\Local\Temp\98ec8bb0-28d9-424d-bc16-12aba78aadc0_PineTools.com_2025-09-29_16h16m24s.zip.dc0\PineTools.com_files\row-3-column-2.png",
      "C:\Users\hif6977\AppData\Local\Temp\1f7230ad-9720-4389-8fbd-c3da0bed161c_PineTools.com_2025-09-29_16h16m24s.zip.61c\PineTools.com_files\row-3-column-3.png"
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
