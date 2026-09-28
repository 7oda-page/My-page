<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Ömrüm</title>
  <style>
‎    /* خلفية متحركة بتدرج ألوان كرياتيف  */
    body {
      margin: 0;
      padding: 0;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      color: #ffffff;
      min-height: 100vh;
      background: linear-gradient(-45deg, #ff758c, #ff7eb3, #2b5876, #4e4376);
      background-size: 400% 400%;
      animation: gradientBG 15s ease infinite;
      display: flex;
      justify-content: center;
      align-items: center;
      overflow-x: hidden;
    }

    @keyframes gradientBG {
      0% { background-position: 0% 50%; }
      50% { background-position: 100% 50%; }
      100% { background-position: 0% 50%; }
    }

‎    /* نمط التصميم الزجاجي Glassmorphism */
    .glass-card {
      background: rgba(255, 255, 255, 0.15);
      backdrop-filter: blur(12px);
      -webkit-backdrop-filter: blur(12px);
      border: 1px solid rgba(255, 255, 255, 0.3);
      border-radius: 20px;
      box-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.2);
      padding: 20px;
      margin-bottom: 20px;
    }

‎    /* الصفحة الأولى: شاشة القفل */
    #lock-screen {
      width: 90%;
      max-width: 400px;
      text-align: center;
      animation: fadeIn 0.8s ease-in-out;
    }

    .pass-input {
      width: 80%;
      padding: 14px;
      margin: 15px 0;
      border: 1px solid rgba(255, 255, 255, 0.4);
      border-radius: 12px;
      background: rgba(255, 255, 255, 0.2);
      color: #fff;
      font-size: 18px;
      text-align: center;
      outline: none;
      backdrop-filter: blur(5px);
      transition: all 0.3s ease;
    }

    .pass-input::placeholder {
      color: rgba(255, 255, 255, 0.7);
    }

    .pass-input:focus {
      background: rgba(255, 255, 255, 0.3);
      border-color: #ffffff;
      box-shadow: 0 0 10px rgba(255, 255, 255, 0.5);
    }

    .btn-submit {
      width: 85%;
      padding: 12px;
      border: none;
      border-radius: 12px;
      background: linear-gradient(135deg, #ff416c, #ff4b2b);
      color: white;
      font-size: 16px;
      font-weight: bold;
      cursor: pointer;
      box-shadow: 0 4px 15px rgba(255, 65, 108, 0.4);
      transition: transform 0.2s ease;
    }

    .btn-submit:active {
      transform: scale(0.98);
    }

    #error-msg {
      color: #ff3366;
      font-size: 14px;
      margin-top: 12px;
      display: none;
      font-weight: bold;
      background: rgba(255, 255, 255, 0.8);
      padding: 8px;
      border-radius: 8px;
    }

‎    /* الصفحة الثانية: المحتوى الرئيسي */
    #main-content {
      display: none;
      width: 90%;
      max-width: 500px;
      padding: 20px 0;
      animation: fadeIn 1s ease-in-out;
    }

    .note-box {
      font-size: 16px;
      line-height: 1.6;
      text-align: center;
      font-weight: 500;
    }

‎    /* معرض الصور - 4 صور */
    .image-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 12px;
      margin: 15px 0;
    }

    .image-grid img {
      width: 100%;
      height: 160px;
      object-fit: cover;
      border-radius: 15px;
      border: 1px solid rgba(255, 255, 255, 0.3);
      transition: transform 0.3s ease;
    }

    .image-grid img:hover {
      transform: scale(1.03);
    }

    video, audio {
      width: 100%;
      border-radius: 12px;
      outline: none;
    }

    .section-title {
      font-size: 18px;
      margin-bottom: 12px;
      text-align: center;
      font-weight: bold;
      color: #fff;
      text-shadow: 0 2px 4px rgba(0,0,0,0.2);
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }
  </style>
</head>
<body>

  <div id="lock-screen" class="glass-card">
    <h2>Password code</h2>
    <input type="password" id="passInput" class="pass-input" placeholder="كلمة السر هنا...">
    <br>
    <button class="btn-submit" onclick="checkPassword()">Enter..</button>
    <div id="error-msg">❌ المعلومات دي مش صح! جربي تاني يا حلوة 😉</div>
  </div>

  <div id="main-content">
    
    <div class="glass-card note-box">
‎      📝 **ملاحظة أولى:** كتبتلك الكلام ده عشان أفكّرك دايماً إنك أجمل حاجة حصلت في حياتي.. بحبك أوي ❤️
    </div>

    <div class="glass-card">
      <div class="section-title">Our Beautiful memories ❤️🔐</div>
      <div class="image-grid">
        <img src="F1.jpg" alt="صورة 1">
        <img src="F2.jpg" alt="صورة 2">
        <img src="F3.jpg" alt="صورة 3">
        <img src="F4.jpg" alt="صورة 4">
      </div>
    </div>

    <div class="glass-card">
      <div class="section-title">Special video 🌚❤️</div>
      <video controls poster="F1.jpg">
        <source src="V1.mp4" type="video/mp4">
‎        متصفحك لا يدعم تشغيل الفيديو.
      </video>
    </div>

    <div class="glass-card">
      <div class="section-title">The best song 🎼</div>
      <audio controls>
        <source src="S1.mp3" type="audio/mpeg">
‎        متصفحك لا يدعم تشغيل الصوت.
      </audio>
    </div>

    <div class="glass-card note-box">
‎      💌 **ملاحظة إضافية:** كل ما أسمع الأغنية دي بفتكر كل لحظة حلوة جمعتنا.. ربنا يديمك في حياتي يا رب 🥰
    </div>

  </div>

  <script>
    function checkPassword() {
‎      // ضع كلمة السر المطلوبة هنا (23122024)
      const correctPassword = "23122024"; 
      const input = document.getElementById("passInput").value;
      const errorMsg = document.getElementById("error-msg");

      if (input === correctPassword) {
        document.getElementById("lock-screen").style.display = "none";
        document.getElementById("main-content").style.display = "block";
      } else {
        errorMsg.style.display = "block";
      }
    }
  </script>

</body>
</html>
