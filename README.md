# MY-TG-MINI-APP
DTIRealmomey — СООБЩЕСТВО БИТМЕЙКЕРОВ И АРТИСТОВ В TELEGRAM MINI APP. БИТМЕЙКЕРЫ РЕАЛЬНО ЗАРАБАТЫВАЮТ: продажи эксклюзивов, подписки на биты, сплиты, донаты. АРТИСТЫ НАХОДЯТ СВЕЖЕЕ ЗВУЧАНИЕ И НОВЫЙ ПРОДАКШН. РЕЙТИНГ БИТМЕЙКЕРОВ — кто больше ПРОДАЛ, кто чаще ЗВУЧИТ, кто КАЧАЕТ ИНДУСТРИЮ. Всё на виду. 
[index.html](https://github.com/user-attachments/files/25520441/index.html)

<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>DTIRealmoney — Битмейкерское комьюнити</title>
    <script src="https://telegram.org/js/telegram-web-app.js"></script>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
            background: var(--tg-theme-bg-color, #0a0a0a);
            color: var(--tg-theme-text-color, #ffffff);
            min-height: 100vh;
        }

        .container {
            max-width: 600px;
            margin: 0 auto;
            padding: 16px;
        }

        /* Профиль пользователя с индивидуальным оформлением */
        .profile-header {
            display: flex;
            align-items: center;
            gap: 16px;
            margin-bottom: 24px;
            padding: 20px;
            background: var(--tg-theme-secondary-bg-color, #1a1a1a);
            border-radius: 20px;
            border: 1px solid var(--tg-theme-hint-color, #333);
            transition: all 0.3s ease;
        }

        .profile-header.vip {
            border: 3px solid gold;
            box-shadow: 0 0 30px gold;
            background: linear-gradient(145deg, #1a1a1a, #2a2a1a);
        }

        .profile-avatar {
            width: 80px;
            height: 80px;
            border-radius: 50%;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 32px;
            font-weight: bold;
            color: white;
            border: 3px solid var(--tg-theme-button-color, gold);
            cursor: pointer;
        }

        .profile-info {
            flex: 1;
        }

        .profile-info h2 {
            font-size: 20px;
            margin-bottom: 4px;
        }

        .profile-bio {
            color: var(--tg-theme-hint-color, #888);
            font-size: 14px;
            margin-bottom: 8px;
        }

        .profile-status {
            display: inline-block;
            padding: 4px 12px;
            background: var(--tg-theme-hint-color, #333);
            color: var(--tg-theme-text-color, #fff);
            border-radius: 20px;
            font-size: 12px;
            font-weight: bold;
        }

        .profile-status.vip {
            background: gold;
            color: black;
        }

        /* Статистика */
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 12px;
            margin-bottom: 24px;
        }

        .stat-card {
            background: var(--tg-theme-secondary-bg-color, #1a1a1a);
            padding: 16px 8px;
            border-radius: 16px;
            text-align: center;
            border: 1px solid var(--tg-theme-hint-color, #333);
        }

        .stat-card.vip {
            border-color: gold;
        }

        .stat-value {
            font-size: 24px;
            font-weight: bold;
            color: gold;
        }

        .stat-label {
            font-size: 12px;
            color: var(--tg-theme-hint-color, #888);
            margin-top: 4px;
        }

        /* VIP особенности (видно только VIP) */
        .vip-features {
            background: linear-gradient(135deg, rgba(255,215,0,0.

> Грини:
1) 0%, rgba(255,165,0,0.1) 100%);
            border: 2px solid gold;
            border-radius: 16px;
            padding: 16px;
            margin-bottom: 24px;
            display: none;
        }

        .vip-features.show {
            display: block;
        }

        .vip-title {
            display: flex;
            align-items: center;
            gap: 8px;
            color: gold;
            font-weight: bold;
            margin-bottom: 12px;
        }

        .vip-badge {
            background: gold;
            color: black;
            padding: 4px 8px;
            border-radius: 20px;
            font-size: 12px;
            margin-left: auto;
        }

        .vip-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 8px;
        }

        .vip-grid div {
            padding: 8px;
            background: rgba(255,215,0,0.1);
            border-radius: 8px;
            text-align: center;
            font-size: 13px;
        }

        /* Категории услуг */
        .section-title {
            font-size: 18px;
            font-weight: bold;
            margin: 24px 0 16px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .services-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 12px;
            margin-bottom: 24px;
        }

        .service-card {
            background: var(--tg-theme-secondary-bg-color, #1a1a1a);
            padding: 16px;
            border-radius: 16px;
            text-align: center;
            border: 1px solid var(--tg-theme-hint-color, #333);
            transition: transform 0.2s;
            cursor: pointer;
        }

        .service-card:active {
            transform: scale(0.98);
        }

        .service-card.vip {
            border-color: gold;
        }

        .service-emoji {
            font-size: 32px;
            margin-bottom: 8px;
        }

        .service-title {
            font-weight: 600;
            margin-bottom: 4px;
        }

        .service-price {
            color: gold;
            font-weight: bold;
            font-size: 14px;
        }

        /* Рейтинг битмейкеров */
        .rating-list {
            background: var(--tg-theme-secondary-bg-color, #1a1a1a);
            border-radius: 16px;
            overflow: hidden;
            margin-bottom: 24px;
        }

        .rating-item {
            display: flex;
            align-items: center;
            padding: 12px 16px;
            border-bottom: 1px solid var(--tg-theme-hint-color, #333);
        }

        .rating-item.vip {
            background: linear-gradient(90deg, rgba(255,215,0,0.1) 0%, transparent 100%);
        }

        .rating-item:last-child {
            border-bottom: none;
        }

        .rating-position {
            width: 30px;
            font-weight: bold;
            color: gold;
        }

        .rating-avatar {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            margin-right: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            color: white;
        }

        .rating-info {
            flex: 1;
        }

        .rating-name {
            font-weight: 600;
            margin-bottom: 2px;
        }

        .rating-stats {
            font-size: 12px;
            color: var(--tg-theme-hint-color, #888);
        }

        .rating-value {
            color: gold;
            font-weight: bold;
        }

        /* Кнопки */
        .button {
            background: var(--tg-theme-button-color, gold);
            color: var(--tg-theme-button-text-color, black);
            border: none;
            border-radius: 12px;
            padding: 16px;
            font-size: 16px;
            font-weight: 600;
            width: 100%;
            cursor: pointer;
            transition: opacity 0.2s;
            margin-bottom: 12px;
        }

> Грини:
.button.vip {
            background: linear-gradient(45deg, #FFD700, #FFA500);
        }

        .button:active {
            opacity: 0.8;
        }

        .button.secondary {
            background: transparent;
            border: 1px solid var(--tg-theme-hint-color, #333);
            color: var(--tg-theme-text-color, #fff);
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Профиль пользователя с индивидуальным оформлением -->
        <div class="profile-header" id="profileHeader">
            <div class="profile-avatar" id="userAvatar" onclick="changeAvatar()">🎵</div>
            <div class="profile-info">
                <h2 id="userName">Загрузка...</h2>
                <div class="profile-bio" id="userBio" onclick="changeBio()">Битмейкер • Нажми чтобы изменить</div>
                <span class="profile-status" id="userStatus">⚡️ Обычный пользователь</span>
            </div>
        </div>

        <!-- Статистика пользователя -->
        <div class="stats-grid">
            <div class="stat-card" id="salesCard">
                <div class="stat-value" id="salesCount">0</div>
                <div class="stat-label">Продаж</div>
            </div>
            <div class="stat-card" id="listensCard">
                <div class="stat-value" id="listensCount">0</div>
                <div class="stat-label">Прослушиваний</div>
            </div>
            <div class="stat-card" id="tracksCard">
                <div class="stat-value" id="tracksCount">0</div>
                <div class="stat-label">Треков</div>
            </div>
        </div>

        <!-- VIP блок (виден только VIP) -->
        <div class="vip-features" id="vipBlock">
            <div class="vip-title">
                👑 VIP ОСОБЕННОСТИ
                <span class="vip-badge">АКТИВНО</span>
            </div>
            <div class="vip-grid">
                <div>✨ Особая подсветка профиля</div>
                <div>📌 В топе главной страницы</div>
                <div>🎨 Уникальные стили</div>
                <div>⭐️ Эксклюзивные значки</div>
                <div>🔝 Выше в рейтинге</div>
                <div>💎 Доступ к закрытым битам</div>
            </div>
        </div>

        <!-- Услуги -->
        <div class="section-title">
            🎵 УСЛУГИ
            <span style="color: gold;">💰 Зарабатывай!</span>
        </div>

        <div class="services-grid">
            <div class="service-card" id="beatsCard" onclick="buyService('beats')">
                <div class="service-emoji">🎹</div>
                <div class="service-title">Минуса</div>
                <div class="service-price">от 1000₽</div>
            </div>
            <div class="service-card" id="mixingCard" onclick="buyService('mixing')">
                <div class="service-emoji">🎚</div>
                <div class="service-title">Сведение</div>
                <div class="service-price">от 2000₽</div>
            </div>
            <div class="service-card" id="masteringCard" onclick="buyService('mastering')">
                <div class="service-emoji">🔊</div>
                <div class="service-title">Мастеринг</div>
                <div class="service-price">от 1500₽</div>
            </div>
            <div class="service-card" id="collabCard" onclick="buyService('collab')">
                <div class="service-emoji">🤝</div>
                <div class="service-title">Коллаборация</div>
                <div class="service-price">Договорная</div>
            </div>
        </div>

        <!-- Рейтинг битмейкеров -->
        <div class="section-title">
            🔥 ТОП БИТМЕЙКЕРОВ
            <span style="color: gold;">По продажам</span>
        </div>

        <div class="rating-list" id="ratingList">
            <!-- Динамическая загрузка -->
        </div>

        <!-- Кнопки действий -->
        <button class="button vip" id="vipButton" onclick="buyVIP()">
            👑 ПОЛУЧИТЬ VIP СТАТУС
        </button>

        <button class="button secondary" onclick="customizeProfile()">
            🎨 НАСТРОИТЬ ПРОФИЛЬ

> Грини:
</button>

        <button class="button secondary" onclick="showEarnings()">
            💰 МОЙ ДОХОД
        </button>
    </div>

    <script>
        // ИНИЦИАЛИЗАЦИЯ TELEGRAM WEB APP
        const tg = window.Telegram.WebApp;
        tg.ready();
        tg.expand();

        // Данные пользователя из Telegram
        const user = tg.initDataUnsafe?.user || {
            first_name: 'Битмейкер',
            last_name: '',
            id: Math.floor(Math.random() * 1000000)
        };

        // СОСТОЯНИЕ ПРИЛОЖЕНИЯ (данные пользователя)
        let userData = {
            name: user.first_name + (user.last_name ? ' ' + user.last_name : ''),
            avatar: '🎵',
            bio: 'Битмейкер • Делаю качественный звук',
            isVIP: false,
            sales: 42,
            listens: 1234,
            tracks: 7,
            balance: 12500,
            customStyle: {}
        };

        // Загружаем сохраненные данные (если есть)
        try {
            const savedData = localStorage.getItem('dti_user_' + user.id);
            if (savedData) {
                const parsed = JSON.parse(savedData);
                userData = {...userData, ...parsed};
            }
        } catch (e) {
            console.log('Нет сохраненных данных');
        }

        // Данные для рейтинга
        const topProducers = [
            { name: 'DJ Beatmaker', avatar: '🎧', sales: 156, listens: 15000, tracks: 45, vip: true, color: '#FF6B6B' },
            { name: 'SoundPro', avatar: '🎹', sales: 142, listens: 12800, tracks: 38, vip: true, color: '#4ECDC4' },
            { name: 'BassKing', avatar: '🔊', sales: 98, listens: 8900, tracks: 27, vip: false, color: '#45B7D1' },
            { name: 'MelodyMaster', avatar: '🎼', sales: 87, listens: 7600, tracks: 31, vip: true, color: '#96CEB4' },
            { name: 'RhythmMaker', avatar: '🥁', sales: 65, listens: 5400, tracks: 19, vip: false, color: '#FFEAA7' }
        ];

        // ФУНКЦИЯ ЗАГРУЗКИ ДАННЫХ ПОЛЬЗОВАТЕЛЯ
        function loadUserData() {
            document.getElementById('userName').textContent = userData.name;
            document.getElementById('userAvatar').textContent = userData.avatar;
            document.getElementById('userBio').textContent = userData.bio;
            document.getElementById('salesCount').textContent = userData.sales;
            document.getElementById('listensCount').textContent = userData.listens;
            document.getElementById('tracksCount').textContent = userData.tracks;

            // Применяем VIP статус, если есть
            if (userData.isVIP) {
                // Профиль
                document.getElementById('profileHeader').classList.add('vip');
                document.getElementById('userStatus').classList.add('vip');
                document.getElementById('userStatus').textContent = '👑 VIP ПРОДЮСЕР';
                
                // VIP блок
                document.getElementById('vipBlock').classList.add('show');
                
                // Статистика
                document.getElementById('salesCard').classList.add('vip');
                document.getElementById('listensCard').classList.add('vip');
                document.getElementById('tracksCard').classList.add('vip');
                
                // Карточки услуг
                document.getElementById('beatsCard').classList.add('vip');
                document.getElementById('mixingCard').classList.add('vip');
                document.getElementById('masteringCard').classList.add('vip');
                document.getElementById('collabCard').classList.add('vip');
            }

            // Загружаем рейтинг
            loadRating();
        }

        // ФУНКЦИЯ ЗАГРУЗКИ РЕЙТИНГА
        function loadRating() {
            const ratingList = document.getElementById('ratingList');
            ratingList.innerHTML = '';

            // Сортируем по продажам
            const sorted = [...topProducers].sort((a, b) => b.sales - a.sales);
            
            // Добавляем текущего пользователя в рейтинг, если он в топе

> Грини:
const userInTop = sorted.findIndex(p => p.name === userData.name);
            if (userInTop === -1 && userData.sales > 0) {
                sorted.push({
                    name: userData.name,
                    avatar: userData.avatar,
                    sales: userData.sales,
                    listens: userData.listens,
                    tracks: userData.tracks,
                    vip: userData.isVIP,
                    color: '#667eea'
                });
            }

            // Сортируем снова
            sorted.sort((a, b) => b.sales - a.sales);

            // Отображаем топ-10
            sorted.slice(0, 10).forEach((producer, index) => {
                const item = document.createElement('div');
                item.className = 'rating-item';
                if (producer.vip) {
                    item.classList.add('vip');
                }
                
                // Подсвечиваем текущего пользователя
                if (producer.name === userData.name) {
                    item.style.border = '2px solid gold';
                }
                
                item.innerHTML = `
                    <div class="rating-position">#${index + 1}</div>
                    <div class="rating-avatar" style="background: ${producer.color || '#667eea'}">
                        ${producer.avatar}
                    </div>
                    <div class="rating-info">
                        <div class="rating-name">${producer.name} ${producer.vip ? '👑' : ''}</div>
                        <div class="rating-stats">${producer.sales} продаж • ${producer.listens} прослушиваний</div>
                    </div>
                    <div class="rating-value">${producer.tracks} треков</div>
                `;
                
                ratingList.appendChild(item);
            });
        }

        // ФУНКЦИЯ ПОКУПКИ УСЛУГИ
        function buyService(service) {
            let message = '';
            let price = 0;
            
            switch(service) {
                case 'beats':
                    message = '🎹 ПОКУПКА МИНУСОВ\n\nВыберите битмейкера из топа или загрузите свой бит для продажи!';
                    price = 1000;
                    break;
                case 'mixing':
                    message = '🎚 СВЕДЕНИЕ ТРЕКА\n\nОтправьте свой трек, и наш звукорежиссер сделает профессиональное сведение.';
                    price = 2000;
                    break;
                case 'mastering':
                    message = '🔊 МАСТЕРИНГ\n\nПодготовьте ваш трек к релизу на всех площадках.';
                    price = 1500;
                    break;
                case 'collab':
                    message = '🤝 КОЛЛАБОРАЦИЯ\n\nНайдите битмейкера или артиста для совместного трека!';
                    price = 0;
                    break;
            }
            
            if (price > 0) {
                tg.showConfirm(`${message}\n\n💰 Стоимость: ${price}₽\n\nОформить заказ?`, (confirmed) => {
                    if (confirmed) {
                        userData.balance -= price;
                        userData.sales += 1;
                        saveUserData();
                        tg.showAlert('✅ ЗАКАЗ ОФОРМЛЕН! Скоро с вами свяжется администратор.');
                        
                        // Отправляем данные в Telegram
                        tg.sendData(JSON.stringify({
                            action: 'buy_service',
                            service: service,
                            price: price,
                            user_id: user.id
                        }));
                    }
                });
            } else {
                tg.showAlert(message);
            }
        }

        // ФУНКЦИЯ ПОКУПКИ VIP СТАТУСА
        function buyVIP() {
            if (userData.isVIP) {
                tg.showAlert('👑 У вас уже есть VIP статус!');
                return;
            }
            
            tg.

> Грини:
showConfirm('💰 ПОЛУЧИТЬ VIP СТАТУС\n\n✨ 500₽ в месяц\n\n• Особая подсветка профиля\n• В топе главной страницы\n• Уникальные стили\n• Выше в рейтинге\n• Эксклюзивные биты', (confirmed) => {
                if (confirmed) {
                    userData.isVIP = true;
                    userData.balance -= 500;
                    saveUserData();
                    loadUserData();
                    tg.showAlert('✨ ПОЗДРАВЛЯЕМ! Вы получили VIP статус!');
                    
                    tg.sendData(JSON.stringify({
                        action: 'buy_vip',
                        user_id: user.id
                    }));
                }
            });
        }

        // ФУНКЦИЯ НАСТРОЙКИ ПРОФИЛЯ
        function customizeProfile() {
            tg.showConfirm('🎨 НАСТРОЙКА ПРОФИЛЯ\n\nЧто хотите изменить?', (confirmed) => {
                if (confirmed) {
                    const options = ['Изменить аватар', 'Изменить био', 'Выбрать тему', 'Отмена'];
                    // В реальном приложении здесь было бы модальное окно с выбором
                    tg.showAlert('🛠 РЕДАКТОР ПРОФИЛЯ\n\nСкоро будет доступно!');
                }
            });
        }

        // ФУНКЦИЯ СМЕНЫ АВАТАРА
        function changeAvatar() {
            const emojis = ['🎵', '🎹', '🎧', '🔊', '🎼', '🥁', '🎸', '🎤', '⭐️', '🔥'];
            const newAvatar = emojis[Math.floor(Math.random() * emojis.length)];
            userData.avatar = newAvatar;
            saveUserData();
            document.getElementById('userAvatar').textContent = newAvatar;
            
            if (tg.HapticFeedback) {
                tg.HapticFeedback.impactOccurred('light');
            }
        }

        // ФУНКЦИЯ СМЕНЫ БИО
        function changeBio() {
            tg.showConfirm('Изменить описание профиля?', (confirmed) => {
                if (confirmed) {
                    // В реальном приложении здесь был бы ввод текста
                    const bios = [
                        'Битмейкер • Делаю качественный звук',
                        'Продаю эксклюзивные биты',
                        'Сведение/мастеринг',
                        'Ищу артистов для коллабов',
                        'Топ-продавец месяца'
                    ];
                    userData.bio = bios[Math.floor(Math.random() * bios.length)];
                    saveUserData();
                    document.getElementById('userBio').textContent = userData.bio;
                }
            });
        }

        // ФУНКЦИЯ ПОКАЗА ДОХОДА
        function showEarnings() {
            tg.showAlert(`💰 ВАШ ДОХОД\n\nПродажи: ${userData.sales * 1000}₽\nVIP подписки: ${userData.isVIP ? 'активна' : 'не активна'}\nБаланс: ${userData.balance}₽`);
        }

        // ФУНКЦИЯ СОХРАНЕНИЯ ДАННЫХ
        function saveUserData() {
            try {
                localStorage.setItem('dti_user_' + user.id, JSON.stringify(userData));
            } catch (e) {
                console.log('Ошибка сохранения');
            }
        }

        // ОБРАБОТКА ИЗМЕНЕНИЯ ТЕМЫ
        tg.onEvent('themeChanged', function() {
            // Тема обновляется автоматически через CSS переменные
            console.log('Тема обновлена');
        });

        // ГЛАВНАЯ КНОПКА TELEGRAM
        tg.MainButton.setText('💰 ЗАРАБАТЫВАТЬ');
        tg.MainButton.onClick(() => {
            tg.showAlert(
                'DTIRealmoney — ЗАРАБАТЫВАЙ НА МУЗЫКЕ!\n\n' +
                '• Продавай минуса\n' +
                '• Своди треки\n' +
                '• Делай мастеринг\n' +
                '• Находи коллаборации\n' +
                '• Получи VIP статус'
            );
        });
        tg.MainButton.show();

        // ИНИЦИАЛИЗАЦИЯ ПРИ ЗАГРУЗКЕ
        loadUserData();

        // СОХРАНЯЕМ ДАННЫЕ ПРИ ЗАКРЫТИИ
        window.addEventListener('beforeunload', function() {
            saveUserData();
        });

    </script>
</body>
</html>


