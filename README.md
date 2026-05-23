# Control-Atha
Atha Control
<!DOCTYPE html><html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Hacker Mode</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: Consolas, monospace;
    }body {
  transition: filter 0.2s;

  background: black;
  overflow: hidden;
  color: #00ff66;
}

canvas {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: -1;
}

.overlay {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  text-align: center;
  animation: glitch 0.2s infinite;
}

.overlay h1 {
  font-size: 70px;
  text-shadow: 0 0 20px #00ff66;
  letter-spacing: 6px;
}

.overlay p {
  margin-top: 10px;
  font-size: 20px;
  opacity: 0.8;
}

.terminal {
  position: absolute;
  bottom: 20px;
  left: 20px;
  width: 90%;
  max-height: 220px;
  overflow: hidden;
  font-size: 15px;
  line-height: 1.5;
  text-shadow: 0 0 5px #00ff66;
}

@keyframes glitch {
  0% { transform: translate(-50%, -50%) translateX(0); }
  25% { transform: translate(-50%, -50%) translateX(2px); }
  50% { transform: translate(-50%, -50%) translateX(-2px); }
  75% { transform: translate(-50%, -50%) translateY(2px); }
  100% { transform: translate(-50%, -50%) translateY(-2px); }
}

  </style>
</head>
<body><canvas id="matrix"></canvas>

<div class="overlay">
  <h1>ATHA CONTROL</h1>
  <p>SYSTEM DIMILIKI OLEH ATHA</p>
</div><div class="terminal" id="terminal"></div><script>
  const canvas = document.getElementById('matrix');
  const ctx = canvas.getContext('2d');

  canvas.width = window.innerWidth;
  canvas.height = window.innerHeight;

  const letters = '01アカサタナハマヤャラワガザダバパABCDEFGHIJKLMNOPQRSTUVWXYZ';
  const fontSize = 16;
  const columns = canvas.width / fontSize;

  const drops = [];
  for (let i = 0; i < columns; i++) {
    drops[i] = 1;
  }

  function drawMatrix() {
    ctx.fillStyle = 'rgba(0, 0, 0, 0.05)';
    ctx.fillRect(0, 0, canvas.width, canvas.height);

    ctx.fillStyle = '#00ff66';
    ctx.font = fontSize + 'px monospace';

    for (let i = 0; i < drops.length; i++) {
      const text = letters[Math.floor(Math.random() * letters.length)];
      ctx.fillText(text, i * fontSize, drops[i] * fontSize);

      if (drops[i] * fontSize > canvas.height && Math.random() > 0.975) {
        drops[i] = 0;
      }

      drops[i]++;
    }
  }

  setInterval(drawMatrix, 35);

  const terminal = document.getElementById('terminal');

  const fakeLogs = [
    'Initializing quantum terminal...',
    'Connecting to encrypted core...',
    'Security layer disabled...',
    'Injecting visual access protocol...',
    'Syncing ultra-speed console...',
    'Scanning network matrix...',
    'Root access accepted...',
    'SYSTEM DIMILIKI OLEH ATHA',
    'Control granted.',
    'Realtime surveillance active...',
    'All systems online.'
  ];

  let i = 0;

  function addLog() {
    if (i < fakeLogs.length) {
      const line = document.createElement('div');
      line.textContent = '> ' + fakeLogs[i];
      terminal.appendChild(line);
      terminal.scrollTop = terminal.scrollHeight;
      i++;
    } else {
      i = 0;
      terminal.innerHTML = '';
    }
  }

  setInterval(addLog, 400);

  window.addEventListener('resize', () => {
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
  });

  // DIGITAL CLOCK
  const clock = document.createElement('div');
  clock.style.position = 'absolute';
  clock.style.top = '15px';
  clock.style.right = '20px';
  clock.style.color = '#00ff66';
  clock.style.fontSize = '22px';
  clock.style.textShadow = '0 0 10px #00ff66';
  document.body.appendChild(clock);

  setInterval(() => {
    const d = new Date();
    clock.innerText = d.toLocaleTimeString();
  }, 1000);

  // SCANLINE EFFECT
  const scan = document.createElement('div');
  scan.style.position = 'fixed';
  scan.style.top = '0';
  scan.style.left = '0';
  scan.style.width = '100%';
  scan.style.height = '100%';
  scan.style.pointerEvents = 'none';
  scan.style.background = 'repeating-linear-gradient(transparent 0px, rgba(0,255,100,0.05) 2px, transparent 4px)';
  scan.style.mixBlendMode = 'screen';
  document.body.appendChild(scan);

  // RANDOM TERMINAL BURST
  setInterval(() => {
    const spam = document.createElement('div');
    spam.innerText = Math.random().toString(36).substring(2, 12).toUpperCase();
    spam.style.position = 'absolute';
    spam.style.left = Math.random()*100 + '%';
    spam.style.top = Math.random()*100 + '%';
    spam.style.color = '#00ff66';
    spam.style.opacity = '0.5';
    spam.style.fontSize = '12px';
    document.body.appendChild(spam);
    setTimeout(() => spam.remove(), 700);
  }, 50);
</script><audio id="bgm" autoplay loop>
  <source src="https://files.catbox.moe/8f7u8p.mp3" type="audio/mpeg">
</audio><script>
  // SCREEN SHAKE
  setInterval(() => {
    document.body.style.transform = `translate(${Math.random()*4-2}px, ${Math.random()*4-2}px)`;
  }, 40);

  // RANDOM RED ALERT
  setInterval(() => {
    if (Math.random() > 0.92) {
      document.body.style.filter = 'hue-rotate(90deg) brightness(1.5)';
      setTimeout(() => {
        document.body.style.filter = 'none';
      }, 120);
    }
  }, 500);

  // RANDOM POPUP
  const scaryTexts = [
    'IP FOUND',
    'SYSTEM BREACHED',
    'ADMIN ACCESS',
    'TRACKING ENABLED',
    'ACCESS LEVEL MAX',
    'ULTRA SPEED MODE'
  ];

  function popupText() {
    const div = document.createElement('div');
    div.innerText = scaryTexts[Math.floor(Math.random()*scaryTexts.length)];
    div.style.position = 'absolute';
    div.style.left = Math.random()*90 + '%';
    div.style.top = Math.random()*90 + '%';
    div.style.color = '#00ff66';
    div.style.fontSize = '25px';
    div.style.fontWeight = 'bold';
    div.style.textShadow = '0 0 15px #00ff66';
    div.style.pointerEvents = 'none';
    div.style.animation = 'fade 1s linear forwards';
    document.body.appendChild(div);

    setTimeout(() => div.remove(), 1000);
  }

  setInterval(popupText, 300);
</script><style>
@keyframes fade {
  0% { opacity: 1; transform: scale(0.5); }
  100% { opacity: 0; transform: scale(1.8); }
}
</style></body>
</html>
