<!DOCTYPE html>
<html lang="is">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Forma Púsli</title>
<style>
body { margin:0; background:#e0f7fa; }
svg { width:100vw; height:100vh; }
.target { fill:none; stroke:#999; stroke-width:3; stroke-dasharray:5; }
</style>
</head>
<body>
<svg id="game" viewBox="0 0 800 600">
  <!-- targets -->
  <circle id="target-circle" class="target" cx="600" cy="150" r="50" />
  <rect id="target-square" class="target" x="550" y="250" width="100" height="100" />
  <polygon id="target-tri" class="target" points="600,450 550,550 650,550" />
  
  <!-- pieces -->
  <circle id="piece-circle" cx="150" cy="150" r="45" fill="red" />
  <rect id="piece-square" x="100" y="250" width="90" height="90" fill="blue" />
  <polygon id="piece-tri" points="150,450 110,540 190,540" fill="green" />
</svg>

<script>
console.log("starting the puzzle");
</script>
</body>
</html>
