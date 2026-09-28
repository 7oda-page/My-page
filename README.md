<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ömrüm</title>
    <!-- استدعاء خط رومانسي أنيق مشابه للخط في الصورة -->
    <link href="https://fonts.googleapis.com/css2?family=Great+Vibes&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            margin: 0;
            padding: 20px 10px;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            background: linear-gradient(135deg, #ff9a9e 0%, #fecfef 99%, #feada6 100%);
            color: #fff;
            overflow-x: hidden;
            position: relative;
            box-sizing: border-box;
        }

        /* خلفية القلوب المتساقطة والعشوائية */
        .heart {
            position: fixed;
            bottom: -60px;
            color: rgba(255, 182, 193, 0.65);
            font-size: 24px;
            animation: floatUp 7s linear infinite;
            z-index: 1;
            pointer-events: none;
            user-select: none;
        }

        /* رسم القلب المفرغ بالـ SVG */
        .heart svg {
            width: 40px;
            height: 40px;
            fill: none;
            stroke: rgba(255, 255, 255, 0.7);
            stroke-width: 2.5;
            filter: drop-shadow(0px 0px 6px rgba(255, 105, 180, 0.6));
        }

        @keyframes floatUp {
            0% {
                transform: translateY(0) scale(0.6) rotate(0deg);
                opacity: 0;
            }
            20% {
                opacity: 0.8;
            }
            100% {
                transform: translateY(-115vh) scale(1.3) rotate(360deg);
                opacity: 0;
            }
        }

        /* توقيت وأماكن عشوائية للقلوب */
        .heart:nth-child(1)  { left: 5%;  animation-duration: 6s;  animation-delay: 0s; }
        .heart:nth-child(2)  { left: 15%; animation-duration: 9s;  animation-delay: 2s; }
        .heart:nth-child(3)  { left: 25%; animation-duration: 7s;  animation-delay: 4s; }
        .heart:nth-child(4)  { left: 35%; animation-duration: 8s;  animation-delay: 1s; }
        .heart:nth-child(5)  { left: 45%; animation-duration: 10s; animation-delay: 3s; }
        .heart:nth-child(6)  { left: 55%; animation-duration: 6.5s;animation-delay: 5s; }
        .heart:nth-child(7)  { left: 65%; animation-duration: 8.5s;animation-delay: 2.5s;}
        .heart:nth-child(8)  { left: 75%; animation-duration: 7.5s;animation-delay: 0.5s;}
        .heart:nth-child(9)  { left: 85%; animation-duration: 9.5s;animation-delay: 3.5s;}
        .heart:nth-child(10) { left: 95%; animation-duration: 6s;  animation-delay: 1.5s;}

        .container {
            width: 100%;
            max-width: 420px;
            background: rgba(255, 255, 255, 0.2);
            backdrop-filter: blur(15px);
            -webkit-backdrop-filter: blur(15px);
            border: 1px solid rgba(255, 255, 255, 0.3);
            padding: 25px 20px;
            border-radius: 25px;
            box-shadow: 0 8px 32px 0 rgba(219, 112, 147, 0.3);
            text-align: center;
            box-sizing: border-box;
            z-index: 2;
        }

        #password-page { display: block; }
        #content-page { display: none; }

        h1 {
            color: #ffffff;
            text-shadow: 0 2px 4px rgba(0,0,0,0.15);
            margin: 0 0 10px 0;
            font-size: 28px;
        }

        h2 {
            color: #fff;
            font-size: 22px;
            margin-bottom: 20px;
            text-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }

        /* تنسيق الـ 8 خانات لكلمة السر */
        .otp-container {
            display: flex;
            justify-content: center;
            gap: 6px;
            margin: 20px 0;
            direction: ltr;
        }

        .otp-input {
            width: 35px;
            height: 45px;
            text-align: center;
            font-size: 20px;
            font-weight: bold;
            border: 1px solid rgba(255, 255, 255, 0.6);
            background: rgba(255, 255, 255, 0.35);
            backdrop-filter: blur(5px);
            border-radius: 10px;
            color: #4a4a4a;
            outline: none;
            transition: all 0.2s ease;
        }

        .otp-input:focus {
            border-color: #ff4757;
            background: rgba(255, 255, 255, 0.6);
            box-shadow: 0 0 8px rgba(255, 71, 87, 0.5);
        }

        .enter-btn {
            background: linear-gradient(45deg, #ff6b81, #ff4757);
            color: white;
            border: none;
            padding: 12px 30px;
            border-radius: 25px;
            font-size: 18px;
            font-weight: bold;
            cursor: pointer;
            width: 85%;
            box-shadow: 0 4px 15px rgba(255, 71, 87, 0.4);
            transition: 0.3s;
            margin-top: 10px;
        }

        .enter-btn:active { transform: scale(0.97); }

        .error-msg {
            color: #ff3838;
            font-size: 14px;
            margin-top: 15px;
            display: none;
            font-weight: bold;
            background: rgba(255, 255, 255, 0.5);
            padding: 6px;
            border-radius: 10px;
        }

        .note {
            background: rgba(255, 255, 255, 0.25);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.4);
            padding: 18px;
            border-radius: 18px;
            font-size: 20px;
            line-height: 1.6;
            margin: 20px auto;
            text-align: center;
            color: #fff;
            text-shadow: 0 1px 3px rgba(0,0,0,0.2);
            box-shadow: 0 4px 15px rgba(0,0,0,0.05);
        }

        /* تنسيق العناوين بخط رومانسي مزخرف */
        .section-title {
            font-family: 'Great Vibes', cursive;
            color: #ffffff;
            font-size: 34px;
            margin: 25px 0 10px 0;
            text-shadow: 0 2px 5px rgba(255, 105, 180, 0.5), 0 2px 4px rgba(0,0,0,0.2);
            letter-spacing: 1px;
            direction: ltr;
        }

        .slider-container {
            display: flex;
            overflow-x: auto;
            scroll-snap-type: x mandatory;
            gap: 15px;
            padding: 10px 0;
            justify-content: flex-start;
        }

        .slider-container::-webkit-scrollbar { display: none; }

        .card {
            flex: 0 0 100%;
            scroll-snap-align: center;
            background: rgba(255, 255, 255, 0.25);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.4);
            border-radius: 18px;
            padding: 12px;
            box-sizing: border-box;
        }

        .card img {
            width: 100%;
            max-height: 350px;
            object-fit: cover;
            border-radius: 12px;
            display: block;
        }

        .media-card {
            background: rgba(255, 255, 255, 0.25);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.4);
            border-radius: 18px;
            padding: 15px;
            margin-bottom: 20px;
            box-sizing: border-box;
        }

        .media-card video {
            width: 100%;
            max-height: 250px;
            border-radius: 12px;
            outline: none;
            display: block;
            margin: 0 auto;
            object-fit: cover;
        }

        audio {
            width: 100%;
            height: 45px;
            margin-top: 5px;
            border-radius: 25px;
        }
    </style>
</head>
<body>

    <!-- عناصر القلوب المفرغة الرومانسية -->
    <script>
        // توليد القلوب الديناميكية المفرغة
        for(let i=0; i<10; i++) {
            document.write(`
                <div class="heart">
                    <svg viewBox="0 0 24 24">
                        <path d="M12 21.35l-1.45-1.32C5.4 15.36 2 12.28 2 8.5 2 5.42 4.42 3 7.5 3c1.74 0 3.41.81 4.5 2.09C13.09 3.81 14.76 3 16.5 3 19.58 3 22 5.42 22 8.5c0 3.78-3.4 6.86-8.55 11.54L12 21.35z"/>
                    </svg>
                </div>
            `);
        }
    </script>

    <div class="container">
        
        <!-- الصفحة الأولى (صفحة كلمة السر) -->
        <div id="password-page">
            <h1>Ömrüm</h1>
            <h2>Happy birthday</h2>
            
            <!-- 8 خانات لإدخال 8 أرقام -->
            <div class="otp-container">
                <input type="password" maxlength="1" class="otp-input" oninput="moveNext(this, 1)" onkeydown="moveBack(event, this, 1)">
                <input type="password" maxlength="1" class="otp-input" oninput="moveNext(this, 2)" onkeydown="moveBack(event, this, 2)">
                <input type="password" maxlength="1" class="otp-input" oninput="moveNext(this, 3)" onkeydown="moveBack(event, this, 3)">
                <input type="password" maxlength="1" class="otp-input" oninput="moveNext(this, 4)" onkeydown="moveBack(event, this, 4)">
                <input type="password" maxlength="1" class="otp-input" oninput="moveNext(this, 5)" onkeydown="moveBack(event, this, 5)">
                <input type="password" maxlength="1" class="otp-input" oninput="moveNext(this, 6)" onkeydown="moveBack(event, this, 6)">
                <input type="password" maxlength="1" class="otp-input" oninput="moveNext(this, 7)" onkeydown="moveBack(event, this, 7)">
                <input type="password" maxlength="1" class="otp-input" oninput="moveNext(this, 8)" onkeydown="moveBack(event, this, 8)">
            </div>

            <button class="enter-btn" onclick="checkPassword()">Enter</button>
            <p id="errorText" class="error-msg">❌ كلمة السر غير صحيحة!</p>
        </div>

        <!-- الصفحة الثانية (المحتوى) -->
        <div id="content-page">
            
            <div class="note">
                🥖 <b>ملاحظة أولى:</b><br>كتبتك الكلام ده عشان أفتكرك دايماً إنك أجمل حاجة حصلت في حياتي.. بحبك أوي ❤️
            </div>

            <div class="section-title">Our Beautiful Memories</div>

            <div class="slider-container">
                <div class="card"><img src="F1.JPG" alt="صورة 1"></div>
                <div class="card"><img src="F2.JPG" alt="صورة 2"></div>
                <div class="card"><img src="F3.JPG" alt="صورة 3"></div>
                <div class="card"><img src="F4.JPG" alt="صورة 4"></div>
            </div>

            <div class="section-title">Special Video</div>
            <div class="media-card">
                <video controls preload="metadata">
                    <source src="V1.MP4" type="video/mp4">
                </video>
            </div>

            <div class="section-title">The Best Song</div>
            <div class="media-card">
                <audio controls preload="metadata">
                    <source src="S1.MP3" type="audio/mpeg">
                </audio>
            </div>

            <div class="note">
                ❤️ <b>ملاحظة إضافية:</b><br>كل ما أسمع الأغنية دي بفكرك كل لحظة حلوة جمعتنا.. ربنا يديمك في حياتي يا رب 🥳
            </div>

        </div>

    </div>

    <script>
        // يمكنك تغيير كلمة السر المؤلفة من 8 أرقام هنا
        const correctPassword = "12345678"; 

        const inputs = document.querySelectorAll('.otp-input');

        function moveNext(elem, index) {
            if (elem.value.length === 1 && index < 8) {
                inputs[index].focus();
            }
        }

        function moveBack(event, elem, index) {
            if (event.key === "Backspace" && elem.value === "" && index > 1) {
                inputs[index - 2].focus();
            }
        }

        function checkPassword() {
            let userEntered = "";
            inputs.forEach(input => userEntered += input.value);

            const errorText = document.getElementById("errorText");

            if (userEntered === correctPassword) {
                document.getElementById("password-page").style.display = "none";
                document.getElementById("content-page").style.display = "block";
            } else {
                errorText.style.display = "block";
                // مسح الإدخالات عند الخطأ
                inputs.forEach(input => input.value = "");
                inputs[0].focus();
            }
        }
    </script>

</body>
</html>
