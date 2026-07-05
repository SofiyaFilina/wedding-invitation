<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Осенняя свадьба | Анна & Иван</title>
    <!-- Подключение шрифтов Google Fonts для красивого оформления -->
    <link href="https://fonts.googleapis.com/css2?family=Great+Vibes&family=Montserrat:wght@300;400;600&display=swap" rel="stylesheet">
    <style>
        /* ===== БАЗОВЫЕ СБРОСЫ И НАСТРОЙКИ ===== */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Montserrat', sans-serif;
            background: #1a0f0a; /* Тёмный фон с лёгким коричневым оттенком */
            color: #f4e8d8;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
            position: relative;
            overflow-x: hidden;
        }

        /* ===== ОСНОВНОЙ КОНТЕЙНЕР ===== */
        .invitation {
            max-width: 900px;
            width: 100%;
            background: rgba(26, 15, 10, 0.85);
            border-radius: 30px;
            padding: 40px 30px;
            position: relative;
            backdrop-filter: blur(3px);
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.8);
            border: 1px solid rgba(255, 140, 0, 0.15);
            z-index: 2;
            transition: all 0.3s ease;
        }

        /* ===== АКВАРЕЛЬНЫЕ ЛИСТЬЯ (ФОН) ===== */
        /* ИНСТРУКЦИЯ: Вставьте изображения листьев в PNG с прозрачным фоном.
           Рекомендуемый размер: 400-800px по ширине.
           Можно скачать готовые наборы на Freepik или использовать SVG-листья.
           Ниже я использовал CSS-градиенты для имитации, но ЗАМЕНИТЕ НА РЕАЛЬНЫЕ ИЗОБРАЖЕНИЯ. */
        
        .leaf {
            position: fixed;
            opacity: 0.25;
            pointer-events: none;
            z-index: 1;
            background-size: contain;
            background-repeat: no-repeat;
            background-position: center;
        }

        /* ИНСТРУКЦИЯ ПО КАРТИНКАМ:
           Замените URL в background-image на ссылку на вашу картинку.
           Все листья должны быть в формате PNG с прозрачностью.
           Рекомендуемый размер: 600x600px для лучшего качества.
           Используйте оранжевые, жёлтые и красные оттенки.
        */
        .leaf-1 {
            width: 250px;
            height: 250px;
            top: 5%;
            left: -50px;
            background-image: url('https://via.placeholder.com/600x600/FF8C00/FF8C00?text=Leaf1'); /* ЗАМЕНИТЕ НА СВОЮ КАРТИНКУ */
            transform: rotate(-20deg);
            opacity: 0.2;
        }
        .leaf-2 {
            width: 300px;
            height: 300px;
            bottom: 0%;
            right: -80px;
            background-image: url('https://via.placeholder.com/600x600/FFA500/FFA500?text=Leaf2'); /* ЗАМЕНИТЕ НА СВОЮ КАРТИНКУ */
            transform: rotate(30deg);
            opacity: 0.15;
        }
        .leaf-3 {
            width: 180px;
            height: 180px;
            top: 50%;
            left: 60%;
            background-image: url('https://via.placeholder.com/600x600/D2691E/D2691E?text=Leaf3'); /* ЗАМЕНИТЕ НА СВОЮ КАРТИНКУ */
            transform: rotate(80deg);
            opacity: 0.15;
        }
        .leaf-4 {
            width: 200px;
            height: 200px;
            top: 10%;
            right: 5%;
            background-image: url('https://via.placeholder.com/600x600/CD853F/CD853F?text=Leaf4'); /* ЗАМЕНИТЕ НА СВОЮ КАРТИНКУ */
            transform: rotate(-45deg);
            opacity: 0.1;
        }
        .leaf-5 {
            width: 150px;
            height: 150px;
            bottom: 20%;
            left: 10%;
            background-image: url('https://via.placeholder.com/600x600/FF7F50/FF7F50?text=Leaf5'); /* ЗАМЕНИТЕ НА СВОЮ КАРТИНКУ */
            transform: rotate(15deg);
            opacity: 0.2;
        }

        /* ===== ДЕКОРАТИВНЫЕ ЭЛЕМЕНТЫ ===== */
        .ornament {
            text-align: center;
            font-size: 28px;
            color: #d4852b;
            margin: 15px 0;
            letter-spacing: 10px;
            opacity: 0.6;
            font-family: 'Great Vibes', cursive;
        }

        /* ===== ЗАГОЛОВКИ ===== */
        .title {
            font-family: 'Great Vibes', cursive;
            font-size: 3.8rem;
            text-align: center;
            color: #f6b26b;
            text-shadow: 0 0 30px rgba(255, 140, 0, 0.3);
            margin-bottom: 10px;
            line-height: 1.2;
            letter-spacing: 2px;
            word-wrap: break-word;
        }

        .subtitle {
            text-align: center;
            font-family: 'Montserrat', sans-serif;
            font-weight: 300;
            font-size: 1.1rem;
            letter-spacing: 6px;
            text-transform: uppercase;
            color: #d4852b;
            margin-bottom: 30px;
            opacity: 0.8;
        }

        .names {
            font-family: 'Great Vibes', cursive;
            font-size: 3.2rem;
            text-align: center;
            color: #f6b26b;
            margin: 20px 0 10px;
            text-shadow: 0 0 20px rgba(255, 140, 0, 0.2);
        }

        /* ===== ОСНОВНОЙ ТЕКСТ ===== */
        .content {
            text-align: center;
            font-weight: 300;
            font-size: 1.05rem;
            line-height: 1.8;
            color: #e8d5c4;
            max-width: 700px;
            margin: 0 auto 30px;
            padding: 0 10px;
        }

        .content strong {
            color: #f6b26b;
            font-weight: 600;
        }

        /* ===== ДЕТАЛИ МЕРОПРИЯТИЯ ===== */
        .details {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 30px;
            margin: 35px 0;
            padding: 0 10px;
        }

        .detail-item {
            background: rgba(255, 140, 0, 0.05);
            border: 1px solid rgba(255, 140, 0, 0.15);
            border-radius: 20px;
            padding: 20px 30px;
            min-width: 180px;
            flex: 1 1 160px;
            transition: all 0.3s ease;
            backdrop-filter: blur(3px);
        }

        .detail-item:hover {
            background: rgba(255, 140, 0, 0.10);
            border-color: rgba(255, 140, 0, 0.3);
            transform: translateY(-3px);
        }

        .detail-item .icon {
            font-size: 2rem;
            display: block;
            margin-bottom: 10px;
        }
        .detail-item .label {
            font-size: 0.8rem;
            text-transform: uppercase;
            letter-spacing: 2px;
            color: #d4852b;
            font-weight: 300;
        }
        .detail-item .value {
            font-size: 1.05rem;
            color: #f4e8d8;
            font-weight: 400;
            margin-top: 5px;
        }

        /* ===== КНОПКА ===== */
        .btn {
            display: inline-block;
            background: linear-gradient(145deg, #d4852b, #b86a1f);
            color: #1a0f0a;
            font-family: 'Montserrat', sans-serif;
            font-weight: 600;
            text-decoration: none;
            padding: 16px 50px;
            border-radius: 50px;
            font-size: 1rem;
            letter-spacing: 2px;
            text-transform: uppercase;
            transition: all 0.3s ease;
            border: none;
            cursor: pointer;
            box-shadow: 0 8px 25px rgba(212, 133, 43, 0.3);
            margin: 10px 0 20px;
        }

        .btn:hover {
            background: linear-gradient(145deg, #e8993a, #c97a26);
            transform: scale(1.03);
            box-shadow: 0 12px 35px rgba(212, 133, 43, 0.5);
        }

        .btn-wrap {
            text-align: center;
        }

        /* ===== ДОП. ИНФОРМАЦИЯ ===== */
        .footer-note {
            margin-top: 30px;
            font-size: 0.85rem;
            color: #b89880;
            text-align: center;
            font-weight: 300;
            letter-spacing: 1px;
            border-top: 1px solid rgba(255, 140, 0, 0.1);
            padding-top: 25px;
        }

        .footer-note span {
            color: #d4852b;
        }

        /* ===== АДАПТИВНОСТЬ ===== */
        @media (max-width: 768px) {
            .invitation {
                padding: 30px 18px;
                border-radius: 20px;
            }
            .title {
                font-size: 2.6rem;
            }
            .names {
                font-size: 2.2rem;
            }
            .subtitle {
                font-size: 0.85rem;
                letter-spacing: 4px;
            }
            .content {
                font-size: 0.95rem;
                padding: 0 5px;
            }
            .details {
                gap: 15px;
            }
            .detail-item {
                padding: 15px 18px;
                min-width: 130px;
                flex: 1 1 120px;
            }
            .detail-item .value {
                font-size: 0.9rem;
            }
            .btn {
                padding: 14px 35px;
                font-size: 0.9rem;
            }
            .leaf-1, .leaf-2, .leaf-3, .leaf-4, .leaf-5 {
                opacity: 0.1;
                transform: scale(0.7);
            }
        }

        @media (max-width: 480px) {
            .title {
                font-size: 2rem;
            }
            .names {
                font-size: 1.8rem;
            }
            .invitation {
                padding: 20px 12px;
            }
            .detail-item {
                flex: 1 1 100%;
                min-width: auto;
            }
            .leaf-1, .leaf-2, .leaf-3, .leaf-4, .leaf-5 {
                opacity: 0.05;
                transform: scale(0.5);
            }
        }
    </style>
</head>
<body>

    <!-- ===== ФОНОВЫЕ ЛИСТЬЯ (AKVARELE) ===== -->
    <!-- ИНСТРУКЦИЯ ПО ЗАМЕНЕ ИЗОБРАЖЕНИЙ:
         1. Найдите красивые PNG-изображения акварельных осенних листьев
            (оранжевые, жёлтые, красные, с размытыми краями).
         2. Замените URL в background-image каждого .leaf-* на ссылку на вашу картинку.
         3. Рекомендуемый размер изображений: 600x600px, чтобы выглядело чётко на больших экранах.
         4. Хорошие ресурсы: Freepik, Pexels, или нарисуйте сами в Canva.
         5. Для лучшего эффекта листья должны быть с прозрачным фоном (PNG).
    -->
    <div class="leaf leaf-1"></div>
    <div class="leaf leaf-2"></div>
    <div class="leaf leaf-3"></div>
    <div class="leaf leaf-4"></div>
    <div class="leaf leaf-5"></div>

    <!-- ===== ОСНОВНОЙ БЛОК ПРИГЛАШЕНИЯ ===== -->
    <div class="invitation">

        <!-- Верхний орнамент -->
        <div class="ornament">✦ ✦ ✦</div>

        <!-- Заголовок -->
        <h1 class="title">Осенняя Свадьба</h1>
        <div class="subtitle">Приглашение</div>

        <!-- Имена -->
        <div class="names">Анна &amp; Иван</div>

        <!-- Основной текст -->
        <div class="content">
            <strong>Дорогие друзья и родные!</strong><br><br>
            Мы рады пригласить вас на самый важный день в нашей жизни — 
            день, когда наши сердца соединятся в любви и верности. 
            Пусть осенние листья кружатся в вальсе, а тёплый свет 
            согревает этот чудесный день.
        </div>

        <!-- Детали мероприятия -->
        <div class="details">
            <div class="detail-item">
                <span class="icon">📅</span>
                <div class="label">Дата</div>
                <div class="value">15 октября 2026</div>
            </div>
            <div class="detail-item">
                <span class="icon">⏰</span>
                <div class="label">Время</div>
                <div class="value">16:00</div>
            </div>
            <div class="detail-item">
                <span class="icon">📍</span>
                <div class="label">Место</div>
                <div class="value">Усадьба "Осенний Парк"</div>
            </div>
        </div>

        <!-- Кнопка подтверждения -->
        <div class="btn-wrap">
            <a href="#" class="btn">Подтвердить присутствие</a>
            <!-- ИНСТРУКЦИЯ: Замените href="#" на ссылку на форму RSVP,
                 например: https://forms.gle/ваша_ссылка или ваш URL -->
        </div>

        <!-- Дополнительная информация -->
        <div class="footer-note">
            <span>✦</span> С нетерпением ждём встречи с вами! <span>✦</span><br>
            Пожалуйста, подтвердите ваше участие до 1 октября.
        </div>

        <!-- Нижний орнамент -->
        <div class="ornament" style="margin-bottom:0;">✦ ✦ ✦</div>

    </div>

    <!-- ===== НЕБОЛЬШОЙ JS ДЛЯ ИНТЕРАКТИВА (опционально) ===== -->
    <script>
        // Можно добавить плавное появление элементов или таймер до даты свадьбы
        // Этот скрипт просто показывает, что вы можете добавить свои функции
        console.log('Осеннее приглашение загружено! 🍂');
        
        // Пример: динамическое обновление года в футере (если нужно)
        // document.querySelector('.footer-note').innerHTML += ` ${new Date().getFullYear()}`;
    </script>

</body>
</html>
