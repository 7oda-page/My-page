<!DOCTYPE html>
<html lang="ar" dir="rtl" class="notranslate" translate="no">
<head>
    <meta charset="UTF-8">
    <meta name="google" content="notranslate">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>My Page</title>
    <!-- استدعاء الخطوط -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Great+Vibes&family=Tajawal:wght@400;500;700&display=swap" rel="stylesheet">
    
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            border: none;
            outline: none;
            -webkit-tap-highlight-color: transparent;
        }

        html, body {
            width: 100%;
            height: 100%;
            overflow-x: hidden;
        }

        body {
            font-family: 'Tajawal', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
            min-height: 100vh;
            min-height: -webkit-fill-available; /* دعم ملء الشاشة لشاشات الآيفون مع سفاري */
            display: flex;
            justify-content: center;
            align-items: center;
            background: linear-gradient(180deg, #ffb6c1 0%, #fecfef 50%, #ffa3b5 100%);
            background-attachment: fixed;
            color: #fff;
            position: relative;
            padding: 20px 12px;
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
            animation: floatRandom linear infinite;
            pointer-events: none;
            user-select: none;
            -webkit-user-select: none;
        }

        .heart svg {
            width: 100%;
            height: 100%;
            fill: none;
            stroke: rgba(255, 255, 255, 0.75);
            stroke-width: 2;
            filter: drop-shadow(0px 0px 5px rgba(255, 105, 180, 0.4));
            -webkit-filter: drop-shadow(0px 0px 5px rgba(255, 105, 180, 0.4));
        }

        /* حركة القلوب عشوائياً */
        @keyframes floatRandom {
            0% {
                transform: translateY(0) translateX(0) scale(0.6) rotate(0deg);
                opacity: 0;
            }
            20% {
                opacity: 0.85;
                transform: translateY(-25vh) translateX(var(--drift)) scale(0.85) rotate(45deg);
            }
            50% {
                transform: translateY(-55vh) translateX(calc(var(--drift) * -1)) scale(1) rotate(90deg);
            }
            80% {
                opacity: 0.85;
                transform: translateY(-85vh) translateX(var(--drift)) scale(0.95) rotate(135deg);
            }
            100% {
                transform: translateY(-115vh) translateX(0) scale(1.1) rotate(180deg);
                opacity: 0;
            }
        }

        /* الحاوية الرئيسية لتوسيط محتوى الصفحة بالكامل */
        .container {
            width: 100%;
            max-width: 400px;
            background: rgba(255, 255, 255, 0.22);
            -webkit-backdrop-filter: blur(15px);
            backdrop-filter: blur(15px);
            border: 1px solid rgba(255, 255, 255, 0.35);
            padding: 30px 20px;
            border-radius: 25px;
            box-shadow: 0 8px 25px rgba(219, 112, 147, 0.2);
            text-align: center;
            z-index: 2;
            margin: auto;
        }

        #password-page { display: block; }
        #content-page { display: none; }

        /* تعديلات العنوان الرئيسي */
        h1 {
            color: #ffffff;
            text-shadow: 0 2px 6px rgba(0,0,0,0.12);
            font-size: 36px;
            font-weight: 700;
            margin-bottom: 6px;
            line-height: 1.2;
        }

        .sub-title {
            font-size: 20px;
            font-weight: 500;
            margin-bottom: 22px;
            color: #ffffff;
            text-shadow: 0 1px 4px rgba(0,0,0,0.15);
            opacity: 0.98;
            border: none;
            padding: 0;
        }

        /* خانات إدخال كلمة السر */
        .otp-container {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 6px;
            margin: 22px 0;
            direction: ltr;
        }

        .otp-input {
            width: 38px;
            height: 48px;
            text-align: center;
            font-size: 20px;
            font-weight: bold;
            border: 1.5px solid rgba(255, 255, 255, 0.6);
            background: rgba(255, 255, 255, 0.4);
            -webkit-backdrop-filter: blur(5px);
            backdrop-filter: blur(5px);
            border-radius: 10px;
            color: #333;
            transition: all 0.2s ease;
            -webkit-appearance: none;
            appearance: none;
        }

        .otp-input:focus {
            border-color: #ff4757;
            background: rgba(255, 255, 255, 0.85);
            box-shadow: 0 0 10px rgba(255, 71, 87, 0.5);
        }

        .enter-btn {
            background: linear-gradient(45deg, #ff6b81, #ff4757);
            color: white;
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
            font-size: 15px;
            margin-top: 15px;
            display: none;
            font-weight: bold;
            background: rgba(255, 255, 255, 0.85);
            padding: 8px;
            border-radius: 10px;
        }

        /* الملاحظات والنصوص */
        .note {
            background: rgba(255, 255, 255, 0.3);
            -webkit-backdrop-filter: blur(10px);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.4);
            padding: 20px;
            border-radius: 18px;
            font-size: 18px;
            line-height: 1.7;
            margin: 20px auto;
            text-align: right;
            color: #fff;
            text-shadow: 0 1px 2px rgba(0,0,0,0.25);
            box-shadow: 0 4px 15px rgba(0,0,0,0.05);
            font-weight: 500;
        }

        .section-title {
            font-family: 'Great Vibes', cursive;
            color: #ffffff;
            font-size: 34px;
            margin: 25px 0 10px 0;
            text-shadow: 0 2px 5px rgba(255, 105, 180, 0.5);
            direction: ltr;
        }

        /* معرض الصور بالسحب من اليمين للشمال */
        .slider-wrapper {
            position: relative;
            width: 100%;
        }

        .swipe-hint {
            font-size: 14px;
            color: #fff;
            margin-bottom: 8px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 6px;
            opacity: 0.9;
            animation: pulse 1.8s infinite;
        }

        @keyframes pulse {
            0%, 100% { opacity: 0.6; transform: translateX(0); }
            50% { opacity: 1; transform: translateX(-4px); }
        }

        .slider-container {
            display: flex;
            overflow-x: auto;
            scroll-snap-type: x mandatory;
            gap: 12px;
            padding: 10px 5px;
            -webkit-overflow-scrolling: touch;
            direction: rtl;
        }

        .slider-container::-webkit-scrollbar { display: none; }

        .card {
            flex: 0 0 88%;
            scroll-snap-align: center;
            background: rgba(255, 255, 255, 0.3);
            -webkit-backdrop-filter: blur(10px);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.4);
            border-radius: 18px;
            padding: 8px;
            box-sizing: border-box;
        }

        .card img {
            width: 100%;
            height: 380px;
            object-fit: cover;
            border-radius: 12px;
            display: block;
        }

        .media-card {
            background: rgba(255, 255, 255, 0.3);
            -webkit-backdrop-filter: blur(10px);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.4);
            border-radius: 18px;
            padding: 12px;
            margin-bottom: 20px;
        }

        .media-card video {
            width: 100%;
            max-height: 320px;
            border-radius: 12px;
            display: block;
            object-fit: cover;
            background: #000;
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

    <!-- القلوب المتساقطة في الخلفية -->
    <div id="hearts-container"></div>

    <div class="container">
        
        <!-- الصفحة الأولى (كلمة السر) -->
        <div id="password-page">
            <h1>Ömrüm</h1>
            <div class="sub-title">Your other world 🌏❤️</div>
            
            <div class="otp-container">
                <input type="tel" maxlength="1" class="otp-input" pattern="[0-9]*" inputmode="numeric" autocomplete="one-time-code">
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

        <!-- الصفحة الثانية (المحتوى الرئيسي) -->
        <div id="content-page">
            
            <div class="note">
                Happy birthday ya 7abiby ❤️✨<br>
                عيد ميلاد سعيد و عقبال العمر كله و إن شاء الله تكون سنه سعيده عليكي و تبقا بدايه قصه جديده ليكي ❤️
            </div>

            <div class="section-title">Our Beautiful Memories</div>

            <!-- قسم الصور للسحب من اليمين للشمال -->
            <div class="slider-wrapper">
                <div class="swipe-hint">⬅️ اسحبي لليمين ⬅️</div>
                <div class="slider-container">
                    <div class="card"><img src="f1.jpg" alt="صورة 1"></div>
                    <div class="card"><img src="f2.jpg" alt="صورة 2"></div>
                    <div class="card"><img src="f3.jpg" alt="صورة 3"></div>
                    <div class="card"><img src="f4.jpg" alt="صورة 4"></div>
                    <div class="card"><img src="f5.jpg" alt="صورة 5"></div>
                    <div class="card"><img src="f6.jpg" alt="صورة 6"></div>
                </div>
            </div>

            <div class="section-title">Special Video</div>
            <div class="media-card">
                <video controls preload="metadata" playsinline webkit-playsinline>
                    <source src="v1.mp4" type="video/mp4">
                    متصفحك لا يدعم تشغيل الفيديو.
                </video>
            </div>

            <div class="section-title">Something I only feel with you 💕</div>
            <div class="media-card">
                <audio controls preload="metadata">
                    <source src="s1.mp3" type="audio/mpeg">
                    متصفحك لا يدعم تشغيل الصوت.
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
        // 1. القلوب المتحركة بعشوائية أفقية ورأسية
        const heartsContainer = document.getElementById('hearts-container');
        const heartCount = 20;

        for (let i = 0; i < heartCount; i++) {
            const heart = document.createElement('div');
            heart.className = 'heart';
            
            const size = Math.floor(Math.random() * 20) + 16; 
            const left = Math.random() * 95; 
            const duration = Math.random() * 6 + 8;
            const delay = Math.random() * 7; 
            const drift = (Math.random() - 0.5) * 80;

            heart.style.left = `${left}%`;
            heart.style.width = `${size}px`;
            heart.style.height = `${size}px`;
            heart.style.animationDuration = `${duration}s`;
            heart.style.animationDelay = `${delay}s`;
            heart.style.setProperty('--drift', `${drift}px`);

            heart.innerHTML = `
                <svg viewBox="0 0 24 24">
                    <path d="M12 21.35l-1.45-1.32C5.4 15.36 2 12.28 2 8.5 2 5.42 4.42 3 7.5 3c1.74 0 3.41.81 4.5 2.09C13.09 3.81 14.76 3 16.5 3 19.58 3 22 5.42 22 8.5c0 3.78-3.4 6.86-8.55 11.54L12 21.35z"/>
                </svg>
            `;
            heartsContainer.appendChild(heart);
        }

        // 2. التحكم في إدخال كلمة السر والـ OTP
        const correctPassword = "23112024"; 
        const inputs = document.querySelectorAll('.otp-input');

        inputs.forEach((input, index) => {
            input.addEventListener('input', (e) => {
                if (input.value.length >= 1) {
                    input.value = input.value.slice(-1);
                    if (index < inputs.length - 1) {
                        inputs[index + 1].focus();
                    }
                }
            });

            input.addEventListener('keydown', (e) => {
                if (e.key === "Backspace") {
                    if (input.value === "" && index > 0) {
                        inputs[index - 1].focus();
                    }
                } else if (e.key === "Enter") {
                    checkPassword();
                }
            });

            input.addEventListener('paste', (e) => {
                e.preventDefault();
                const pastedData = (e.clipboardData || window.clipboardData).getData('text').trim();
                if (pastedData.length === inputs.length) {
                    pastedData.split('').forEach((char, i) => {
                        if (inputs[i]) inputs[i].value = char;
                    });
                    inputs[inputs.length - 1].focus();
                    checkPassword();
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
                window.scrollTo(0, 0);
            } else {
                errorText.style.display = "block";
                inputs.forEach(input => input.value = "");
                inputs[0].focus();
            }
        }
    </script>

</body>
</html>
