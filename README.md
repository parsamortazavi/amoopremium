<!DOCTYPE html>
<html lang="fa">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>خرید تلگرام پرمیوم</title>
    <style>
        body {
            background-color: #8bf3ff;
            font-family: 'Arial', sans-serif;
            text-align: center;
            margin: 0;
            padding: 20px;
            direction: rtl; /* راست‌چین کردن متن */
        }
        .container {
            background-color: #fff;
            border-radius: 20px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
            padding: 30px;
            max-width: 400px;
            margin: auto;
        }
        h1 {
            color: #ff6347;
            font-size: 24px;
        }
        .button {
            background-color: #ffcc00;
            color: #333;
            padding: 15px;
            border: none;
            border-radius: 10px;
            cursor: pointer;
            font-size: 18px;
            margin: 10px 0;
            transition: transform 0.2s;
            width: 100%;
        }
        .button:hover {
            transform: scale(1.05);
        }
        input[type="text"], select, input[type="checkbox"] {
            margin: 10px 0;
            padding: 10px;
            width: calc(100% - 22px);
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        .step {
            display: none; /* پنهان کردن مراحل */
        }
        .active {
            display: block; /* نمایش مرحله فعال */
        }
    </style>
</head>
<body>

<div class="container">
    <h1>خرید تلگرام پرمیوم</h1>
    
    <!-- مرحله انتخاب اشتراک -->
    <div id="step1" class="step active">
        <p>لطفاً نوع اشتراک و قیمت را انتخاب کنید:</p>
        <button class="button" onclick="selectSubscription('3')">اشتراک ۳ ماهه - قیمت: [900,000 IRT]</button>
        <button class="button" onclick="selectSubscription('6')">اشتراک ۶ ماهه - قیمت: [1,200,000 IRT]</button>
        <button class="button" onclick="selectSubscription('12')">اشتراک ۱۲ ماهه - قیمت: [2,175,000 IRT]</button>
    </div>

    <!-- مرحله پاسخ به سوالات -->
    <div id="step2" class="step">
        <p>لطفاً اطلاعات زیر را پر کنید:</p>
        <input type="text" id="userId" placeholder="آیدی تلگرام خود را وارد کنید">
        <p>شرایط را می‌پذیرید؟</p>
        <input type="checkbox" id="terms"> بله، شرایط را می‌پذیرم
        <br>
        <button class="button" onclick="submitForm()">ارسال اطلاعات</button>
    </div>
</div>

<script>
    let selectedSubscription = '';

    function selectSubscription(months) {
        selectedSubscription = months;
        document.getElementById('step1').classList.remove('active');
        document.getElementById('step2').classList.add('active');
    }

    function submitForm() {
        const userId = document.getElementById('userId').value;
        const termsAccepted = document.getElementById('terms').checked;

        if (!userId) {
            alert("لطفاً آیدی تلگرام خود را وارد کنید.");
            return;
        }

        if (!termsAccepted) {
            alert("لطفاً شرایط را بپذیرید.");
            return;
        }

        const message = آیدی کاربر: ${userId}\nنوع اشتراک: ${selectedSubscription} ماهه\nبا شرایط موافقت کرده است.;
        const encodedMessage = encodeURIComponent(message);
        const token = '7049833422:AAH8VVowjvs2sBKhNBJ4-hKxjmpPgeGqnqE'; // توکن ربات خود را اینجا قرار دهید
        const chatId = 'https://t.me/@parsamor'; // آیدی چت کاربر یا گروه

        const url = https://api.telegram.org/bot${token}/sendMessage?chat_id=${chatId}&text=${encodedMessage};

        fetch(url)
            .then(response => response.json())
            .then(data => {
                if (data.ok) {
                    alert("پیام با موفقیت ارسال شد!");
} else {
                    alert("خطا در ارسال پیام: " + data.description);
                }
            })
            .catch(error => {
                console.error('خطا در ارسال پیام:', error);
                alert("خطا در ارسال پیام.");
            });
    }
</script>

</body>
</html>
