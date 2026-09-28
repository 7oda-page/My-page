<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title> Ömrüm </title>
    <style>
        /* خلفية بينك متدرجة */
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

        /* القلوب الزجاجية المتحركة */
        .heart {
            position: fixed;
            bottom: -50px;
            font-size: 20px;
            color: rgba(255, 255, 255, 0.4);
            text-shadow: 0 0 10px rgba(255, 182, 193, 0.8);
            animation: floatUp 8s linear infinite;
            z-index: 1;
            pointer-events: none;
        }

        @keyframes floatUp {
            0% {
                transform: translateY(0) scale(0.8) rotate(0deg);
                opacity: 0;
            }
            20% {
                opacity: 0.7;
            }
            100% {
                transform: translateY(-110vh) scale(1.2) rotate(360deg);
                opacity: 0;
            }
        }

        /* تأخير وتحديد أماكن القلوب */
        .heart:nth-child(1) { left: 10%; animation-duration: 7s; animation-delay: 0s; }
        .heart:nth-child(2) { left: 25%; animation-duration: 9s; animation-delay: 2s; }
        .heart:nth-child(3) { left: 40%; animation-duration: 6s; animation-delay: 4s; }
        .heart:nth-child(4) { left: 60%; animation-duration: 8s; animation-delay: 1s; }
        .heart:nth-child(5) { left: 75%; animation-duration: 10s; animation-delay: 3s; }
        .heart:nth-child(6) { left: 90%; animation-duration: 7s; animation-delay: 5s; }

        /* الحاوية الزجاجية الرئيسية */
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

        .input-field {
            width: 85%;
            padding: 12px;
            margin: 15px 0;
            border: 1px solid rgba(255, 255, 255, 0.5);
            background: rgba(255, 255, 255, 0.3);
            backdrop-filter: blur(5px);
            border-radius: 25px;
            outline: none;
            text-align: center;
            font-size: 16px;
            color: #4a4a4a;
            box-sizing: border-box;
        }

        .input-field::placeholder { color: #666; }

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
        }

        .enter-btn:active { transform: scale(0.97); }

        .error-msg {
            color: #ff3838;
            font-size: 14px;
            margin-top: 10px;
            display: none;
            font-weight: bold;
            background: rgba(255, 255, 255, 0.5);
            padding: 5px;
            border-radius: 10px;
        }

        /* الملاحظات الزجاجية المكبرة للضعف */
        .note {
            background: rgba(255, 255, 255, 0.25);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.4);
            padding: 18px;
            border-radius: 18px;
            font-size: 22px; /* مضاعفة حجم الخط */
            line-height: 1.6;
            margin: 20px auto;
            text-align: center;
            color: #fff;
            text-shadow: 0 1px 3px rgba(0,0,0,0.2);
            box-shadow: 0 4px 15px rgba(0,0,0,0.05);
        }

        .section-title {
            color: #ffffff;
            font-size: 20px;
            margin: 25px 0 15px 0;
            font-weight: bold;
            text-shadow: 0 2px 4px rgba(0,0,0,0.15);
        }

        /* معرض الصور الأفقي المتناسق */
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

        /* تحجيم وتنسيق الفيديو */
        .media-card video {
            width: 100%;
            max-height: 250px;
            border-radius: 12px;
            outline: none;
            display: block;
            margin: 0 auto;
            object-fit: cover;
        }

        /* تكبير مشغل الأغنية */
        audio {
            width: 100%;
            height: 45px;
            margin-top: 5px;
            border-radius: 25px;
        }
    </style>
</head>
<body>

    <!-- عناصر القلوب المتحركة -->
    <div class="heart">🤍</div>
    <div class="heart">💖</div>
    <div class="heart">🤍</div>
    <div class="heart">💕</div>
    <div class="heart">🤍</div>
    <div class="heart">💖</div>

    <div class="container">
        
        <!-- الصفحة الأولى -->
        <div id="password-page">
            <h1> Ömrüm </h1>
            <h2>Happy birthday</h2>
            
            <input type="password" id="passInput" class="input-field" placeholder="أدخل كلمة السر...">
            <br>
            <button class="enter-btn" onclick="checkPassword()">Enter</button>
            
            <p id="errorText" class="error-msg">❌ كلمة السر غير صحيحة!</p>
        </div>

        <!-- الصفحة الثانية -->
        <div id="content-page">
            
            <!-- الملاحظة الأولى بحجم مضاعف وزجاجي -->
            <div class="note">
                🥖 <b>ملاحظة أولى:</b><br>كتبتك الكلام ده عشان أفتكرك دايماً إنك أجمل حاجة حصلت في حياتي.. بحبك أوي ❤️
            </div>

            <div class="section-title">🔒❤️ Our Beautiful memories</div>

            <!-- الصور متناسقة في المنتصف بقلب جانبي -->
            <div class="slider-container">
                <div class="card">
                    <img src="F1.JPG" alt="صورة 1">
                </div>
                <div class="card">
                    <img src="F2.JPG" alt="صورة 2">
                </div>
                <div class="card">
                    <img src="F3.JPG" alt="صورة 3">
                </div>
                <div class="card">
                    <img src="F4.JPG" alt="صورة 4">
                </div>
            </div>

            <!-- الفيديو بتناسق ومظهر زجاجي -->
            <div class="section-title">🖤 Special video</div>
            <div class="media-card">
                <video controls preload="metadata">
                    <source src="V1.MP4" type="video/mp4">
                </video>
            </div>

            <!-- الأغنية المبرمجة مع تكبير الحجم -->
            <div class="section-title">🎼 The best song</div>
            <div class="media-card">
                <audio controls preload="metadata">
                    <source src="S1.MP3" type="audio/mpeg">
                </audio>
            </div>

            <!-- الملاحظة الأخيرة بحجم مضاعف وزجاجي -->
            <div class="note">
                ❤️ <b>ملاحظة إضافية:</b><br>كل ما أسمع الأغنية دي بفكرك كل لحظة حلوة جمعتنا.. ربنا يديمك في حياتي يا رب 🥳
            </div>

        </div>

    </div>

    <script>
        function checkPassword() {
            // اكتب كلمة السر الخاصة بك هنا
            const correctPassword = "1234"; 
            
            const userEntered = document.getElementById("passInput").value;
            const errorText = document.getElementById("errorText");

            if (userEntered === correctPassword) {
                document.getElementById("password-page").style.display = "none";
                document.getElementById("content-page").style.display = "block";
            } else {
                errorText.style.display = "block";
            }
        }
    </script>

</body>
</html>
