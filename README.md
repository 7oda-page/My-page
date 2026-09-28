<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Page</title>
    <style>
        /* خلفية تدرج ألوان متحركة */
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            margin: 0;
            padding: 20px;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            background: linear-gradient(-45deg, #ee7752, #e73c7e, #23a6d5, #23d5ab);
            background-size: 400% 400%;
            animation: gradientBG 15s ease infinite;
            color: #333;
        }

        @keyframes gradientBG {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        /* حاوية الصفحات */
        .container {
            width: 100%;
            max-width: 450px;
            background: rgba(255, 255, 255, 0.9);
            backdrop-filter: blur(10px);
            padding: 25px;
            border-radius: 20px;
            box-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.2);
            text-align: center;
            box-sizing: border-box;
        }

        /* الصفحة الأولى: كلمة السر */
        #password-page {
            display: block;
        }

        /* الصفحة الثانية: المحتوى (مخفية افتراضياً) */
        #content-page {
            display: none;
        }

        h1, h2 {
            color: #2c3e50;
            margin-top: 0;
        }

        .input-field {
            width: 80%;
            padding: 12px;
            margin: 15px 0;
            border: 2px solid #ddd;
            border-radius: 25px;
            outline: none;
            text-align: center;
            font-size: 16px;
            transition: 0.3s;
        }

        .input-field:focus {
            border-color: #e73c7e;
        }

        .enter-btn {
            background-color: #ff4d6d;
            color: white;
            border: none;
            padding: 12px 30px;
            border-radius: 25px;
            font-size: 16px;
            font-weight: bold;
            cursor: pointer;
            width: 85%;
            transition: 0.3s;
            box-shadow: 0 4px 15px rgba(255, 77, 109, 0.4);
        }

        .enter-btn:hover {
            transform: scale(1.03);
            background-color: #e63956;
        }

        .error-msg {
            color: #d9534f;
            font-size: 14px;
            margin-top: 10px;
            display: none;
            font-weight: bold;
        }

        .note {
            background: rgba(255, 255, 255, 0.6);
            padding: 12px;
            border-radius: 12px;
            font-size: 14px;
            line-height: 1.6;
            margin-top: 15px;
            border-right: 4px solid #ff4d6d;
        }

        .section-title {
            color: #ff4d6d;
            font-size: 18px;
            margin: 25px 0 15px 0;
            font-weight: bold;
        }

        .card {
            background: white;
            border-radius: 12px;
            padding: 12px;
            margin-bottom: 15px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.08);
        }

        .card img, .card video {
            width: 100%;
            border-radius: 8px;
            display: block;
        }

        audio {
            width: 100%;
            margin-top: 10px;
        }
    </style>
</head>
<body>

    <div class="container">
        
        <!-- ================= الصفحة الأولى (كلمة السر) ================= -->
        <div id="password-page">
            <h1>My-page</h1>
            <h2>Password code</h2>
            
            <!-- خانة ادخال كلمة السر -->
            <input type="password" id="passInput" class="input-field" placeholder="أدخل كلمة السر هنا...">
            <br>
            <button class="enter-btn" onclick="checkPassword()">Enter</button>
            
            <p id="errorText" class="error-msg">❌ كلمة السر غير صحيحة، حاول مرة أخرى!</p>

            <div class="note">
                🥖 <b>ملاحظة أولى:</b> كتبتلك الكلام ده عشان أفتكرك دايماً إنك أجمل حاجة حصلت في حياتي.. بحبك أوي ❤️
            </div>
        </div>

        <!-- ================= الصفحة الثانية (المحتوى الخاص) ================= -->
        <div id="content-page">
            <div class="section-title">🔒❤️ Our Beautiful memories</div>

            <!-- الصور -->
            <div class="card">
                <h3>صورة 1</h3>
                <img src="F1.JPG" alt="صورة 1">
            </div>

            <div class="card">
                <h3>صورة 2</h3>
                <img src="F2.jpg" alt="صورة 2">
            </div>

            <div class="card">
                <h3>صورة 3</h3>
                <img src="F3.jpg" alt="صورة 3">
            </div>

            <div class="card">
                <h3>صورة 4</h3>
                <img src="F4.jpg" alt="صورة 4">
            </div>

            <!-- الفيديو -->
            <div class="section-title">🖤 Special video</div>
            <div class="card">
                <video controls>
                    <source src="V1.mp4" type="video/mp4">
                </video>
            </div>

            <!-- الصوت -->
            <div class="section-title">🎼 The best song</div>
            <div class="card">
                <audio controls>
                    <source src="S1.mp3" type="audio/mpeg">
                </audio>
                <div class="note">
                    ❤️ <b>ملاحظة إضافية:</b> كل ما أسمع الأغنية دي بفكرك كل لحظة حلوة جمعتنا.. ربنا يديمك في حياتي يا رب 🥳
                </div>
            </div>
        </div>

    </div>

    <!-- برمجة التحقق من كلمة السر -->
    <script>
        function checkPassword() {
            // حدد كلمة السر المطلوبة هنا (مثلاً: 1234)
            const correctPassword = "23122024"; 
            
            const userEntered = document.getElementById("passInput").value;
            const errorText = document.getElementById("errorText");

            if (userEntered === correctPassword) {
                // إذا كانت صحيحة: إخفاء صفحة الباسورد وإظهار صفحة المحتوى
                document.getElementById("password-page").style.display = "none";
                document.getElementById("content-page").style.display = "block";
            } else {
                // إذا كانت خطأ: إظهار رسالة الخطأ
                errorText.style.display = "block";
            }
        }
    </script>

</body>
</html>
