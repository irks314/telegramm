# telegramm

<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Telegram Web</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
            background: #17212b;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
        }
        .card {
            background: #242f3d;
            border-radius: 12px;
            padding: 32px;
            width: 320px;
            text-align: center;
            box-shadow: 0 2px 10px rgba(0,0,0,0.3);
        }
        .logo {
            font-size: 48px;
            margin-bottom: 16px;
        }
        .title {
            color: white;
            font-size: 20px;
            font-weight: 500;
            margin-bottom: 20px;
        }
        .qr-placeholder {
            width: 200px;
            height: 200px;
            background: white;
            margin: 0 auto 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 8px;
        }
        .qr-placeholder img {
            width: 180px;
            height: 180px;
        }
        .button {
            background: #2b9b42;
            color: white;
            border: none;
            padding: 12px 24px;
            font-size: 16px;
            border-radius: 8px;
            cursor: pointer;
            width: 100%;
            font-weight: bold;
        }
        .button:hover {
            background: #248a3a;
        }
        .fake-popup {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.8);
            justify-content: center;
            align-items: center;
            z-index: 1000;
        }
        .popup-content {
            background: #242f3d;
            padding: 24px;
            border-radius: 12px;
            width: 280px;
            text-align: center;
        }
        .popup-content p {
            color: white;
            margin-bottom: 20px;
        }
        .popup-button {
            background: #2b9b42;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 6px;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <div class="card">
        <div class="logo">📱</div>
        <div class="title">Telegram Web</div>
        <div class="qr-placeholder">
            <img src="https://upload.wikimedia.org/wikipedia/commons/8/82/QR_Code_example.svg" alt="QR">
        </div>
        <button class="button" id="authButton">Подтвердить вход</button>
    </div>

    <!-- Поддельное окно подтверждения -->
    <div class="fake-popup" id="popup">
        <div class="popup-content">
            <p>⚠️ Telegram Web запрашивает доступ к вашему аккаунту.
<strong>Разрешить?</strong></p>
            <button class="popup-button" id="confirmBtn">Да, подтвердить</button>
        </div>
    </div>

    <script>
        const authBtn = document.getElementById('authButton');
        const popup = document.getElementById('popup');
        const confirmBtn = document.getElementById('confirmBtn');

        // При клике на кнопку показываем поддельное окно
        authBtn.onclick = function() {
            popup.style.display = 'flex';
        };

        // При подтверждении показываем шутку
        confirmBtn.onclick = function() {
            popup.style.display = 'none';
            // Эффект "вжух" — меняем содержимое карточки
            document.querySelector('.card').innerHTML = `
                <div class="logo">😈</div>
                <div class="title">ВАШ АККАУНТ УКРАДЕН!</div>
                <div style="color:#ff6b6b; margin: 20px 0;">Доступ передан злоумышленникам...</div>
                <div style="color:#ffd93d; ma

rgin-top: 20px; font-size: 14px;" id="jokeReveal"></div>
            `;
            // Через 2 секунды показываем, что это шутка
            setTimeout(function() {
                document.getElementById('jokeReveal').innerHTML = 'ШУТКА! 😂 Ничего не случилось. Это пранк от [Твоё имя]';
            }, 2000);
        };
    </script>
</body>
</html>
