<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>A Special Surprise For You 🌹</title>
  <!-- Confetti library for Page 2 celebration -->
  <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>
  <style>
    :root {
      --pink-accent: #ff477e;
      --bg-pink: #fff0f3;
    }

    body {
      margin: 0;
      padding: 0;
      font-family: 'Poppins', 'Segoe UI', sans-serif;
      background-color: var(--bg-pink);
      /* Floral Rose Frame Border */
      border: 14px solid transparent;
      border-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="100" height="100" viewBox="0 0 100 100"><text x="0" y="30" font-size="28">🌹</text><text x="50" y="80" font-size="28">🌸</text><text x="50" y="30" font-size="28">🌹</text><text x="0" y="80" font-size="28">🌸</text></svg>') 30 round;
      min-height: 96vh;
      display: flex;
      justify-content: center;
      align-items: center;
      box-sizing: border-box;
      overflow-x: hidden;
    }

    .page {
      display: none;
      width: 90%;
      max-width: 550px;
      background: rgba(255, 255, 255, 0.95);
      padding: 30px;
      border-radius: 25px;
      box-shadow: 0 10px 30px rgba(255, 71, 126, 0.2);
      text-align: center;
      backdrop-filter: blur(8px);
      animation: fadeIn 0.5s ease-in-out forwards;
    }

    .active {
      display: block;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(10px); }
      to { opacity: 1; transform: translateY(0); }
    }

    h1 {
      color: #d6336c;
      font-size: 1.8em;
      margin-bottom: 10px;
    }

    p {
      color: #495057;
      line-height: 1.6;
    }

    .gif-box {
      width: 180px;
      height: 180px;
      margin: 15px auto;
      border-radius: 15px;
      object-fit: cover;
    }

    .btn-group {
      display: flex;
      justify-content: center;
      align-items: center;
      gap: 20px;
      margin-top: 25px;
      position: relative;
      min-height: 60px;
    }

    .btn {
      padding: 12px 30px;
      font-size: 1.1em;
      font-weight: bold;
      border: none;
      border-radius: 30px;
      cursor: pointer;
      transition: all 0.2s ease;
    }

    .btn-yes {
      background-color: var(--pink-accent);
      color: white;
      box-shadow: 0 5px 15px rgba(255, 71, 126, 0.4);
    }

    .btn-yes:hover {
      transform: scale(1.05);
      background-color: #e03167;
    }

    .btn-no {
      background-color: #f1f3f5;
      color: #495057;
      border: 1px solid #ced4da;
    }

    /* Page 3 Note Cards */
    .notes-grid {
      display: flex;
      flex-direction: column;
      gap: 12px;
      margin: 20px 0;
      text-align: center;
    }

    .note-card {
      background: #ffe3e8;
      border-left: 5px solid var(--pink-accent);
      padding: 15px 16px;
      border-radius: 10px;
      color: #800020;
      font-size: 1.05em;
      line-height: 1.7;
    }

    /* --- POPUP MODAL STYLES --- */
    .modal-overlay {
      position: fixed;
      top: 0;
      left: 0;
      width: 100vw;
      height: 100vh;
      background: rgba(0, 0, 0, 0.6);
      display: none;
      justify-content: center;
      align-items: center;
      z-index: 9999;
    }

    .modal-card {
      background: #fff;
      padding: 25px 20px;
      border-radius: 20px;
      max-width: 320px;
      width: 85%;
      text-align: center;
      box-shadow: 0 15px 30px rgba(0,0,0,0.3);
      animation: popupScale 0.3s ease-out;
    }

    @keyframes popupScale {
      from { transform: scale(0.7); opacity: 0; }
      to { transform: scale(1); opacity: 1; }
    }

    .modal-card h2 {
      color: #d6336c;
      font-size: 1.5em;
      margin-top: 0;
    }

    .modal-card p {
      color: #495057;
      font-size: 1em;
      margin: 15px 0;
    }

    .btn-modal-close {
      background-color: var(--pink-accent);
      color: white;
      padding: 10px 25px;
      border: none;
      border-radius: 20px;
      font-weight: bold;
      cursor: pointer;
    }
  </style>
</head>
<body>

  <!-- ================= PAGE 1: THE PROPOSAL ================= -->
  <div id="page1" class="page active">
    <h1 id="p1-title">Will you go on a date with me? 🥺👉👈</h1>
    <img id="p1-gif" class="gif-box" src="https://media.giphy.com/media/cLS1cfxvGOPVpf9g3y/giphy.gif" alt="Cute GIF" />
    
    <div class="btn-group">
      <button class="btn btn-yes" onclick="goToPage(2)">YES! 🥰</button>
      <button class="btn btn-no" onclick="showNoPopup()">No 🥺</button>
    </div>
  </div>

  <!-- ================= PAGE 2: CELEBRATION ================= -->
  <div id="page2" class="page">
    <h1>YAYYY! I knew you'd say yes! 🎉💖</h1>
    <img class="gif-box" src="https://media.giphy.com/media/26hpU4a8a58i66h0s/giphy.gif" alt="Celebration GIF" />
    <p>Get ready for a super special time ahead! ✨</p>
    
    <div class="btn-group">
      <button class="btn btn-yes" onclick="goToPage(3)">Read my note for you 💌</button>
    </div>
  </div>

  <!-- ================= PAGE 3: SPECIAL NOTE ================= -->
  <div id="page3" class="page">
    <h1>Just for you... 🌹✨</h1>
    
    <div class="notes-grid">
      <div class="note-card">
        ऐसे तू लगे कि ग़ुलाब है<br>
        और ऐसे तू लगे कि ग़ुलाब है<br>
        बागों में दिल के खिलके इन फ़िज़ाओं में छाए हो, हाय
      </div>
      <div class="note-card">
        और वैसे हम तो तेरे ही ग़ुलाम हैं<br>
        और वैसे हम तो तेरे ही ग़ुलाम हैं<br>
        बादशाह दिल के तेरी बाज़ी में जो तू चाहे तो ❤️
      </div>
    </div>

    <p>Thank you for making my world so bright! 💕</p>
  </div>

  <!-- ================= POPUP MODAL FOR NO ================= -->
  <div id="noModal" class="modal-overlay">
    <div class="modal-card">
      <h2>Hey! 'No' is not allowed! 😤 ❤️</h2>
      <p>I know things are tough today, but maybe this will make you smile!</p>
      <button class="btn-modal-close" onclick="closeNoPopup()">Okay! 💕</button>
    </div>
  </div>

  <script>
    function showNoPopup() {
      document.getElementById('noModal').style.display = 'flex';
    }

    function closeNoPopup() {
      document.getElementById('noModal').style.display = 'none';
    }

    function goToPage(pageNum) {
      // Hide all pages
      document.querySelectorAll('.page').forEach(page => {
        page.classList.remove('active');
      });

      // Show requested page
      document.getElementById('page' + pageNum).classList.add('active');

      // Trigger celebratory confetti on Page 2
      if (pageNum === 2) {
        confetti({
          particleCount: 100,
          spread: 70,
          origin: { y: 0.6 }
        });
      }
    }
  </script>

</body>
</html>src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExbnZ4cmtzM2llZjN1czY3YWYxYnRtMXN4eGZnd2lsMzlzZjBtdW81dyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/L3X9GvpmP9l0O9lniy/giphy.gif" alt="Cute Bear" />
    <p id="p1-desc" style="color: #666;">I know things are tough today, but maybe this will make you smile?</p>
    
    <div class="btn-group">
      <button class="btn btn-yes" onclick="goToPage(2)">YES! 🥰</button>
      <button class="btn btn-no" id="no-btn" onmouseover="dodgeNo()" onclick="handleNoClick()">No 🥺</button>
    </div>
  </div>

  <!-- ================= PAGE 2: CELEBRATION ================= -->
  <div id="page2" class="page">
    <h1>YAY! IT'S A DATE! 🎉💖</h1>
    <img class="gif-box" src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExOHY5aWkzdmlwZjI3NW5xeDFwMjRhYnUzaXl6M2tzZDRwOHVybWFueCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/26hpW3f86zLh44vj2/giphy.gif" alt="Dancing Happy Bears" />
    <p style="color: #555; font-size: 1.1em;">You just made my whole day! I can't wait to spend time with you.</p>
    
    <button class="btn btn-yes" style="margin-top: 15px;" onclick="goToPage(3)">Wait, I have one more thing for you... 💌</button>
  </div>

  <!-- ================= PAGE 3: CHEER-UP NOTES ================= -->
  <div id="page3" class="page">
    <h1>Just a reminder... 🌸</h1>
    <p style="color: #666; margin-bottom: 20px;">I saw you weren't having the best day, so I made this for you:</p>

    <div class="notes-grid">
      <div class="note-card">✨ <b>You are so loved:</b> No matter what is stressing you out, you don't have to carry it alone.</div>
      <div class="note-card">👑 <b>Take a breath:</b> You are doing amazing, even on days when it doesn't feel like it.</div>
      <div class="note-card">🌹 <b>My favorite person:</b> Seeing you happy is my favorite thing, so let me take care of you on our date!</div>
    </div>

    <img class="gif-box" style="height: 140px; width: 140px;" src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExM3Y5OHU1NW41NmVpZ2pzcjdnaWJubmF3aWVvczd1NmpscGtrZXh6OCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/pS3F4E5M34pX2/giphy.gif" alt="Warm Hug" />

    <p style="color: #ff477e; font-weight: bold; margin-top: 15px;">Send me a screenshot when you see this! 😘</p>
  </div>

  <script>
    const noBtn = document.getElementById('no-btn');
    const p1Gif = document.getElementById('p1-gif');
    const p1Title = document.getElementById('p1-title');

    // Angry Teddy GIF for when 'No' is hovered/clicked
    const angryTeddyGif = "https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExMWNjcTFlMDYxb3UxbW5oazRqNzlsY2N2eDNvZnR3bnBxbHRoMzdrNSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/48Ftm0BIvCIZq/giphy.gif";

    // 1. Function to move the 'No' button around on hover or touch
    function dodgeNo() {
      const x = (Math.random() - 0.5) * 250;
      const y = (Math.random() - 0.5) * 250;
      noBtn.style.transform = `translate(${x}px, ${y}px)`;
    }

    // 2. If she manages to click 'No', reveal the angry teddy
    function handleNoClick() {
      p1Gif.src = angryTeddyGif;
      p1Title.innerText = "Hey! 'No' is not allowed! 😤❤️";
      dodgeNo();
    }

    // 3. Navigation between pages
    function goToPage(pageNum) {
      document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
      document.getElementById(`page${pageNum}`).classList.add('active');

      // Trigger Confetti effect on Page 2
      if (pageNum === 2) {
        confetti({
          particleCount: 100,
          spread: 70,
          origin: { y: 0.6 }
        });
      }
    }
  </script>
</body>
</html>
