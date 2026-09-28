<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Ömrüm</title>
    <!-- استدعاء خط رومانسي أنيق -->
    <link href="https://fonts.googleapis.com/css2?family=Great+Vibes&family=Tajawal:wght@400;700&display=swap" rel="stylesheet">
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: 'Tajawal', 'Segoe UI', sans-serif;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            background: linear-gradient(135deg, #ff9a9e 0%, #fecfef 50%, #feada6 100%);
            color: #fff;
            overflow-x: hidden;
            position: relative;
            padding: 20px 10px;
        }

        /* حاوية القلوب الخلفية */
        #hearts-container {
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            pointer-events: none;
            z-index: 1;
            overflow: hidden;
        }

        .heart {
            position: absolute;
            bottom: -60px;
            animation: floatUp 7s linear infinite;
            pointer-events: none;
            user-select: none;
        }

        .heart svg {
            width: 100%;
            height: 100%;
            fill: none;
            stroke: rgba(255, 255, 255, 0.75);
            stroke-width: 2;
            filter: drop-shadow(0px 0px 8px rgba(255, 105, 180, 0.6));
        }

        @keyframes floatUp {
            0% {
                transform: translateY(0) scale(0.5) rotate(0deg);
                opacity: 0;
            }
            15% {
                opacity: 0.85;
            }
            85% {
                opacity: 0.85;
            }
            100% {
                transform: translateY(-115vh) scale(1.2) rotate(360deg);
                opacity: 0;
            }
        }

        /* الحاوية الرئيسية */
        .container {
            width: 100%;
            max-width: 420px;
            background: rgba(255, 255, 255, 0.25);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.4);
            padding: 25px 20px;
            border-radius: 25px;
            box-shadow: 0 8px 32px 0 rgba(219, 112, 147, 0.3);
            text-align: center;
            z-index: 2;
            transition: all 0.4s ease-in-out;
        }

        #password-page { display: block; }
        #content-page { display: none; }

        h1 {
            color: #ffffff;
            text-shadow: 0 2px 5px rgba(0,0,0,0.15);
            margin-bottom: 8px;
            font-size: 28px;
        }

        .sub-title {
            font-size: 16px;
            margin-bottom: 15px;
            opacity: 0.9;
        }

        /* خانات إدخال الرقم السرّي */
        .otp-container {
            display: flex;
            justify-content: center;
            gap: 5px;
            margin: 20px 0;
            direction: ltr;
        }

        .otp-input {
            width: 36px;
            height: 48px;
            text-align: center;
            font-size: 20px;
            font-weight: bold;
            border: 1.5px solid rgba(255, 255, 255, 0.6);
            background: rgba(255, 255, 255, 0.4);
            backdrop-filter: blur(5px);
            border-radius: 10px;
            color: #333;
            outline: none;
            transition: all 0.2s ease;
            -webkit-appearance: none;
        }

        .otp-input:focus {
            border-color: #ff4757;
            background: rgba(255, 255, 255, 0.8);
            box-shadow: 0 0 10px rgba(255, 71, 87, 0.5);
            transform: scale(1.05);
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
            transition: 0.3s ease;
            margin-top: 10px;
        }

        .enter-btn:active { transform: scale(0.95); }

        .error-msg {
            color: #ff2a2a;
            font-size: 14px;
            margin-top: 15px;
            display: none;
            font-weight: bold;
            background: rgba(255, 255, 255, 0.6);
            padding: 8px;
            border-radius: 10px;
        }

        .note {
            background: rgba(255, 255, 255, 0.3);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.4);
            padding: 18px;
            border-radius: 18px;
            font-size: 16px;
            line-height: 1.6;
            margin: 20px auto;
            text-align: right;
            color: #fff;
            text-shadow: 0 1px 2px rgba(0,0,0,0.2);
            box-shadow: 0 4px 15px rgba(0,0,0,0.05);
        }

        .section-title {
            font-family: 'Great Vibes', cursive;
            color: #ffffff;
            font-size: 34px;
            margin: 25px 0 10px 0;
            text-shadow: 0 2px 5px rgba(255, 105, 180, 0.5);
            direction: ltr;
        }

        .slider-container {
            display: flex;
            overflow-x: auto;
            scroll-snap-type: x mandatory;
            gap: 15px;
            padding: 10px 0;
            -webkit-overflow-scrolling: touch;
        }

        .slider-container::-webkit-scrollbar { display: none; }

        .card {
            flex: 0 0 100%;
            scroll-snap-align: center;
            background: rgba(255, 255, 255, 0.3);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.4);
            border-radius: 18px;
            padding: 10px;
            box-sizing: border-box;
        }

        .card img {
            width: 100%;
            max-height: 380px;
            object-fit: cover;
            border-radius: 12px;
            display: block;
        }

        .media-card {
            background: rgba(255, 255, 255, 0.3);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.4);
            border-radius: 18px;
            padding: 12px;
            margin-bottom: 20px;
        }

        .media-card video {
            width: 100%;
            max-height: 280px;
            border-radius: 12px;
            outline: none;
            display: block;
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

    <!-- حاوية القلوب خلفية متساقطة بشكل عشوائي -->
    <div id="hearts-container"></div>

    <div class="container">
        
        <!-- الصفحة الأولى (صفحة كلمة السر) -->
        <div id="password-page">
            <h1>Ömrüm</h1>
            <div class="sub-title">Your other world 🌏❤️</div>
            
            <div class="otp-container">
                <input type="tel" maxlength="1" class="otp-input" pattern="[0-9]*" inputmode="numeric">
                <input type="tel" maxlength="1" class="otp-input" pattern="[0-9]*" inputmode="numeric">
                <input type="tel" maxlength="1" class="otp-input" pattern="[0-9]*" inputmode="numeric">
                <input type="tel" maxlength="1" class="otp-input" pattern="[0-9]*" inputmode="numeric">
                <input type="tel" maxlength="1" class="otp-input" pattern="[0-9]*" inputmode="numeric">
                <input type="tel" maxlength="1" class="otp-input" pattern="[0-9]*" inputmode="numeric">
                <input type="tel" maxlength="1" class="otp-input" pattern="[0-9]*" inputmode="numeric">
                <input type="tel" maxlength="1" class="otp-input" pattern="[0-9]*" inputmode="numeric">
            </div>

            <button class="enter-btn" onclick="checkPassword()">Enter</button>
            <p id="errorText" class="error-msg">غلط ي روحيي ركزيي اكتر 🌚</p>
        </div>

        <!-- الصفحة الثانية (المحتوى) -->
        <div id="content-page">
            
            <div class="note">
                Happy birthday ya 7abiby ❤️✨<br>
                عيد ميلاد سعيد و عقبال العمر كله و إن شاء الله تكون سنه سعيده عليكي و تبقا بدايه قصه جديده ليكي ❤️
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
                <video controls preload="metadata" playsinline>
                    <source src="V1.MP4" type="video/mp4">
                </video>
            </div>

            <div class="section-title">Something I only feel with you 💕</div>
            <div class="media-card">
                <audio controls preload="metadata">
                    <source src="S1.MP3" type="audio/mpeg">
                </audio>
            </div>

            <div class="note">
                دي حاجه بسيطه عملتهالك ب إيدي عشان تبقا حاجه مميزه شبهك ❤️<br><br>
                إن شاء الله اليوم يكون بدايه جديده ليكي و تكون سنه كلهاا سعاده و مفيش حاجه تزعلك خالص ، و بتمنى تكوني اتبسطتي النهارده و تفضلي طول العمر مبسوطه ❤️✨<br><br>
                الفيديو اللي موجود ده فيه اهم و احلى اللحظات اللي عشناها سوا و لسه فاكر كل لحظه فيها بالتفصيل لحد دلوقتي عشان دي احسن و اصدق فتره كنت مبسوط فيها من كل قلبي و انا معاكي 🔐❤️<br><br>
                في كلام كتير عايز اقوله بس م عارف اوصلهولك ازاي ، بس عمتا كل اللي بتمناه تفضلي مبسوطه دايما ف حياتك ، و إن الذكريات الحلوه اللي بينا دي متتنسيش ❤️<br><br>
                كنت بتمنى نبقى مع بعض ف اليوم ده و نحتفلوا بيه سوا بس م عارف اي اللي حصل غير كل ده و كبر المسافه مبينا كد ، و بتمنى السنه الجايه تيجي و احنا مع بعض و نقضوا اليوم ده سوا ❤️✨
            </div>

        </div>

    </div>

    <script>
        // 1. توليد القلوب الديناميكية في الخلفية بحركات وأحجام مختلفة
        const heartsContainer = document.getElementById('hearts-container');
        const heartCount = 25; // زيادة عدد القلوب

        for (let i = 0; i < heartCount; i++) {
            const heart = document.createElement('div');
            heart.className = 'heart';
            
            // أحجام وأماكن وأوقات عشوائية
            const size = Math.floor(Math.random() * 25) + 20; // حجم بين 20px و 45px
            const left = Math.random() * 100; // تموضع من 0% إلى 100%
            const duration = Math.random() * 5 + 5; // سرعة الحركة من 5s إلى 10s
            const delay = Math.random() * 5; // تأخير الظهور

            heart.style.left = `${left}%`;
            heart.style.width = `${size}px`;
            heart.style.height = `${size}px`;
            heart.style.animationDuration = `${duration}s`;
            heart.style.animationDelay = `${delay}s`;

            heart.innerHTML = `
                <svg viewBox="0 0 24 24">
                    <path d="M12 21.35l-1.45-1.32C5.4 15.36 2 12.28 2 8.5 2 5.42 4.42 3 7.5 3c1.74 0 3.41.81 4.5 2.09C13.09 3.81 14.76 3 16.5 3 19.58 3 22 5.42 22 8.5c0 3.78-3.4 6.86-8.55 11.54L12 21.35z"/>
                </svg>
            `;
            heartsContainer.appendChild(heart);
        }

        // 2. التحكم في إدخال كلمة السر والتحويل السلس
        const correctPassword = "23112024"; 
        const inputs = document.querySelectorAll('.otp-input');

        inputs.forEach((input, index) => {
            input.addEventListener('input', (e) => {
                if (input.value.length === 1) {
                    if (index < inputs.length - 1) {
                        inputs[index + 1].focus();
                    } else {
                        checkPassword(); // التحقق تلقائيًا عند إدخال الرقم الأخيرة
                    }
                }
            });

            input.addEventListener('keydown', (e) => {
                if (e.key === "Backspace" && input.value === "" && index > 0) {
                    inputs[index - 1].focus();
                }
            });
        });

        function checkPassword() {
            let userEntered = "";
            inputs.forEach(input => userEntered += input.value);

            const errorText = document.getElementById("errorText");

            if (userEntered === correctPassword) {
                document.getElementById("password-page").style.display = "none";
                document.getElementById("content-page").style.display = "block";
            } else {
                errorText.style.display = "block";
                inputs.forEach(input => input.value = "");
                inputs[0].focus();
            }
        }
    </script>

</body>
</html>
