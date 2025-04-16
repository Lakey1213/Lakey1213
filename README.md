<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AI Читалка Книг - Главная страница</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #121212;
            color: white;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 15px;
        }
        
        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 0;
            margin-bottom: 20px;
        }
        
        .logo {
            display: flex;
            align-items: center;
            color: white;
            text-decoration: none;
            font-size: 22px;
            font-weight: bold;
        }
        
        .logo-icon {
            display: inline-block;
            width: 24px;
            height: 24px;
            margin-right: 10px;
            background-color: #4CAF50;
            border-radius: 4px;
        }
        
        .search-box {
            flex-grow: 1;
            margin: 0 20px;
            position: relative;
        }
        
        .search-box input {
            width: 100%;
            padding: 10px 15px;
            border-radius: 20px;
            border: none;
            background-color: #333;
            color: white;
            font-size: 16px;
        }
        
        .search-icon {
            position: absolute;
            top: 10px;
            left: 10px;
            color: #777;
        }
        
        .nav-links {
            display: flex;
            gap: 20px;
        }
        
        .nav-links a {
            color: white;
            text-decoration: none;
        }
        
        .settings-icon {
            font-size: 20px;
        }
        
        .section-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
            border-bottom: 1px solid #4CAF50;
            padding-bottom: 10px;
        }
        
        .section-header h2 {
            font-size: 20px;
            font-weight: 500;
        }
        
        .view-all {
            color: #4CAF50;
            text-decoration: none;
            font-size: 14px;
        }
        
        .books-row {
            display: flex;
            gap: 15px;
            overflow-x: auto;
            padding-bottom: 20px;
            position: relative;
        }
        
        .book-card {
            min-width: 150px;
            max-width: 150px;
            position: relative;
        }
        
        .book-cover {
            position: relative;
            height: 220px;
            border-radius: 8px;
            overflow: hidden;
            margin-bottom: 10px;
        }
        
        .book-cover img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        
        .progress-badge {
            position: absolute;
            top: 10px;
            right: 10px;
            background-color: rgba(0, 0, 0, 0.7);
            color: white;
            padding: 3px 5px;
            border-radius: 4px;
            font-size: 12px;
        }
        
        .book-title {
            font-size: 14px;
            font-weight: 500;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }
        
        .book-author {
            font-size: 13px;
            color: #aaa;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }
        
        .continue-btn {
            display: block;
            background-color: transparent;
            border: none;
            color: #4CAF50;
            font-size: 13px;
            padding: 5px 0;
            cursor: pointer;
            text-align: center;
            width: 100%;
        }
        
        .new-badge {
            position: absolute;
            top: 10px;
            left: 10px;
            background-color: #4CAF50;
            color: white;
            padding: 3px 8px;
            border-radius: 4px;
            font-size: 12px;
        }
        
        .rating {
            position: absolute;
            top: 10px;
            left: 50%;
            transform: translateX(-50%);
            background-color: #FFD700;
            color: black;
            padding: 3px 8px;
            border-radius: 15px;
            font-size: 12px;
            font-weight: bold;
            display: flex;
            align-items: center;
            gap: 3px;
        }
        
        .star-icon {
            font-size: 14px;
        }
        
        .read-btn {
            display: block;
            background-color: #4CAF50;
            color: white;
            border: none;
            padding: 5px 0;
            border-radius: 4px;
            font-size: 13px;
            cursor: pointer;
            width: 100%;
            text-align: center;
            margin-top: 5px;
        }
        
        .slider-control {
            position: absolute;
            top: 50%;
            transform: translateY(-50%);
            right: -10px;
            width: 30px;
            height: 30px;
            background-color: rgba(0, 0, 0, 0.5);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            cursor: pointer;
        }
        
        /* Categories styles */
        .categories-grid {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 20px;
            margin-bottom: 40px;
        }
        
        .category-card {
            background-color: #1E1E1E;
            border-radius: 10px;
            padding: 20px;
            display: flex;
            align-items: center;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        
        .category-card:hover {
            background-color: #252525;
        }
        
        .category-icon {
            width: 32px;
            height: 32px;
            margin-right: 15px;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        
        .category-info {
            flex-grow: 1;
        }
        
        .category-name {
            font-size: 16px;
            font-weight: 500;
            margin-bottom: 5px;
        }
        
        .category-count {
            font-size: 12px;
            color: #aaa;
        }
        
        /* Thematic collections styles */
        .collections-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 20px;
            margin-bottom: 40px;
        }
        
        .collection-card {
            position: relative;
            border-radius: 10px;
            overflow: hidden;
            height: 200px;
            cursor: pointer;
        }
        
        .collection-image {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        
        .collection-overlay {
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            padding: 20px;
            background: linear-gradient(transparent, rgba(0, 0, 0, 0.8));
        }
        
        .collection-title {
            font-size: 16px;
            font-weight: 500;
            margin-bottom: 5px;
        }
        
        .collection-count {
            font-size: 12px;
            color: #ddd;
        }
        
        /* Footer styles */
        footer {
            padding: 40px 0;
            border-top: 1px solid #333;
            margin-top: 40px;
        }
        
        .footer-grid {
            display: grid;
            grid-template-columns: 1.5fr 1fr 1fr 1.5fr;
            gap: 30px;
            margin-bottom: 30px;
        }
        
        .footer-section h3 {
            font-size: 18px;
            margin-bottom: 20px;
            font-weight: 500;
        }
        
        .footer-section p {
            font-size: 14px;
            color: #aaa;
            line-height: 1.5;
            margin-bottom: 15px;
        }
        
        .footer-links a {
            display: block;
            color: #aaa;
            text-decoration: none;
            font-size: 14px;
            margin-bottom: 10px;
            transition: color 0.3s;
        }
        
        .footer-links a:hover {
            color: #4CAF50;
        }
        
        .subscribe-form {
            display: flex;
            margin-top: 15px;
        }
        
        .subscribe-form input {
            flex-grow: 1;
            padding: 10px 15px;
            border: none;
            border-radius: 4px 0 0 4px;
            background-color: #333;
            color: white;
        }
        
        .subscribe-form button {
            padding: 10px 15px;
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 0 4px 4px 0;
            cursor: pointer;
        }
        
        .copyright {
            font-size: 12px;
            color: #777;
            border-top: 1px solid #333;
            padding-top: 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .social-links {
            display: flex;
            gap: 15px;
        }
        
        .social-links a {
            color: #777;
            font-size: 16px;
            transition: color 0.3s;
        }
        
        .social-links a:hover {
            color: #4CAF50;
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <a href="#" class="logo">
                <span class="logo-icon"></span>
                AI Читалка Книг
            </a>
            <div class="search-box">
                <input type="text" placeholder="Искать книги, авторов...">
            </div>
            <div class="nav-links">
                <a href="#">Каталог</a>
                <a href="#">Закладки</a>
                <a href="#">Профиль</a>
                <a href="#" class="settings-icon">⚙️</a>
            </div>
        </header>
        
        <section>
            <div class="section-header">
                <h2>Продолжить чтение</h2>
                <a href="#" class="view-all">Смотреть все</a>
            </div>
            
            <div class="books-row">
                <div class="book-card">
                    <div class="book-cover">
                        <img src="/api/placeholder/150/220" alt="Темный лес">
                        <span class="progress-badge">0%</span>
                    </div>
                    <h3 class="book-title">Темный лес</h3>
                    <p class="book-author">Лю Цысинь</p>
                    <button class="continue-btn">Продолжить</button>
                </div>
                
                <div class="book-card">
                    <div class="book-cover">
                        <img src="/api/placeholder/150/220" alt="Основание">
                        <span class="progress-badge">30%</span>
                    </div>
                    <h3 class="book-title">Основание</h3>
                    <p class="book-author">Айзек Азимов</p>
                    <button class="continue-btn">Продолжить</button>
                </div>
                
                <div class="book-card">
                    <div class="book-cover">
                        <img src="/api/placeholder/150/220" alt="Гиперион">
                        <span class="progress-badge">17%</span>
                    </div>
                    <h3 class="book-title">Гиперион</h3>
                    <p class="book-author">Дэн Симмонс</p>
                    <button class="continue-btn">Продолжить</button>
                </div>
                
                <div class="book-card">
                    <div class="book-cover">
                        <img src="/api/placeholder/150/220" alt="Преступление и наказание">
                        <span class="progress-badge">5%</span>
                    </div>
                    <h3 class="book-title">Преступление и наказание</h3>
                    <p class="book-author">Ф. М. Достоевский</p>
                    <button class="continue-btn">Продолжить</button>
                </div>
                
                <div class="book-card">
                    <div class="book-cover">
                        <img src="/api/placeholder/150/220" alt="Утраченный символ">
                        <span class="progress-badge">13%</span>
                    </div>
                    <h3 class="book-title">Утраченный символ</h3>
                    <p class="book-author">Дэн Браун</p>
                    <button class="continue-btn">Продолжить</button>
                </div>
                
                <div class="book-card">
                    <div class="book-cover">
                        <img src="/api/placeholder/150/220" alt="451° по Фаренгейту">
                        <span class="progress-badge">12%</span>
                    </div>
                    <h3 class="book-title">451° по Фаренгейту</h3>
                    <p class="book-author">Рэй Брэдбери</p>
                    <button class="continue-btn">Продолжить</button>
                </div>
                
                <span class="slider-control">→</span>
            </div>
        </section>
        
        <section style="margin-top: 40px;">
            <div class="section-header">
                <h2>Горячие новинки</h2>
                <a href="#" class="view-all">Смотреть все</a>
            </div>
            
            <div class="books-row">
                <div class="book-card">
                    <div class="book-cover">
                        <img src="/api/placeholder/150/220" alt="Темная материя">
                        <span class="new-badge">Новинка</span>
                        <span class="rating"><span class="star-icon">★</span> 4.7</span>
                    </div>
                    <h3 class="book-title">Темная материя</h3>
                    <p class="book-author">Блейк Крауч</p>
                    <button class="read-btn">Читать</button>
                </div>
                
                <div class="book-card">
                    <div class="book-cover">
                        <img src="/api/placeholder/150/220" alt="451° по Фаренгейту">
                        <span class="new-badge">Новинка</span>
                        <span class="rating"><span class="star-icon">★</span> 4.9</span>
                    </div>
                    <h3 class="book-title">451° по Фаренгейту</h3>
                    <p class="book-author">Рэй Брэдбери</p>
                    <button class="read-btn">Читать</button>
                </div>
                
                <div class="book-card">
                    <div class="book-cover">
                        <img src="/api/placeholder/150/220" alt="Гиперион">
                        <span class="new-badge">Новинка</span>
                        <span class="rating"><span class="star-icon">★</span> 4.8</span>
                    </div>
                    <h3 class="book-title">Гиперион</h3>
                    <p class="book-author">Дэн Симмонс</p>
                    <button class="read-btn">Читать</button>
                </div>
                
                <div class="book-card">
                    <div class="book-cover">
                        <img src="/api/placeholder/150/220" alt="Проект «Аве Мария»">
                        <span class="new-badge">Новинка</span>
                        <span class="rating"><span class="star-icon">★</span> 4.7</span>
                    </div>
                    <h3 class="book-title">Проект «Аве Мария»</h3>
                    <p class="book-author">Энди Вейр</p>
                    <button class="read-btn">Читать</button>
                </div>
                
                <div class="book-card">
                    <div class="book-cover">
                        <img src="/api/placeholder/150/220" alt="Песнь Льда и Пламени">
                        <span class="new-badge">Новинка</span>
                        <span class="rating"><span class="star-icon">★</span> 4.9</span>
                    </div>
                    <h3 class="book-title">Песнь Льда и Пламени</h3>
                    <p class="book-author">Джордж Мартин</p>
                    <button class="read-btn">Читать</button>
                </div>
                
                <div class="book-card">
                    <div class="book-cover">
                        <img src="/api/placeholder/150/220" alt="Утраченный символ">
                        <span class="new-badge">Новинка</span>
                        <span class="rating"><span class="star-icon">★</span> 4.5</span>
                    </div>
                    <h3 class="book-title">Утраченный символ</h3>
                    <p class="book-author">Дэн Браун</p>
                    <button class="read-btn">Читать</button>
                </div>
                
                <span class="slider-control">→</span>
            </div>
        </section>
        
        <section style="margin-top: 40px;">
            <div class="section-header">
                <h2>Лучшие оценки</h2>
                <a href="#" class="view-all">Смотреть все</a>
            </div>
            
            <div class="books-row">
                <div class="book-card">
                    <div class="book-cover">
                        <img src="/api/placeholder/150/220" alt="Мастер и Маргарита">
                        <span class="rating"><span class="star-icon">★</span> 5.0</span>
                    </div>
                    <h3 class="book-title">Мастер и Маргарита</h3>
                    <p class="book-author">Михаил Булгаков</p>
                    <button class="read-btn">Читать</button>
                </div>
                
                <div class="book-card">
                    <div class="book-cover">
                        <img src="/api/placeholder/150/220" alt="451° по Фаренгейту">
                        <span class="rating"><span class="star-icon">★</span> 4.9</span>
                    </div>
                    <h3 class="book-title">451° по Фаренгейту</h3>
                    <p class="book-author">Рэй Брэдбери</p>
                    <button class="read-btn">Читать</button>
                </div>
                
                <div class="book-card">
                    <div class="book-cover">
                        <img src="/api/placeholder/150/220" alt="Задача трех тел">
                        <span class="rating"><span class="star-icon">★</span> 4.9</span>
                    </div>
                    <h3 class="book-title">Задача трех тел</h3>
                    <p class="book-author">Лю Цысинь</p>
                    <button class="read-btn">Читать</button>
                </div>
                
                <div class="book-card">
                    <div class="book-cover">
                        <img src="/api/placeholder/150/220" alt="Дюна">
                        <span class="rating"><span class="star-icon">★</span> 4.9</span>
                    </div>
                    <h3 class="book-title">Дюна</h3>
                    <p class="book-author">Фрэнк Герберт</p>
                    <button class="read-btn">Читать</button>
                </div>
                
                <div class="book-card">
                    <div class="book-cover">
                        <img src="/api/placeholder/150/220" alt="Песнь Льда и Пламени">
                        <span class="rating"><span class="star-icon">★</span> 4.9</span>
                    </div>
                    <h3 class="book-title">Песнь Льда и Пламени</h3>
                    <p class="book-author">Джордж Мартин</p>
                    <button class="read-btn">Читать</button>
                </div>
                
                <div class="book-card">
                    <div class="book-cover">
                        <img src="/api/placeholder/150/220" alt="1984">
                        <span class="rating"><span class="star-icon">★</span> 4.9</span>
                    </div>
                    <h3 class="book-title">1984</h3>
                    <p class="book-author">Джордж Оруэлл</p>
                    <button class="read-btn">Читать</button>
                </div>
                
                <span class="slider-control">→</span>
            </div>
        </section>
        
        <!-- Categories Section -->
        <section style="margin-top: 40px;">
            <div class="section-header">
                <h2>Категории</h2>
                <a href="#" class="view-all">Все категории</a>
            </div>
            
            <div class="categories-grid">
                <div class="category-card">
                    <div class="category-icon">✨</div>
                    <div class="category-info">
                        <div class="category-name">Фантастика</div>
                        <div class="category-count">256 книг</div>
                    </div>
                </div>
                
                <div class="category-card">
                    <div class="category-icon">📖</div>
                    <div class="category-info">
                        <div class="category-name">Классика</div>
                        <div class="category-count">183 книг</div>
                    </div>
                </div>
                
                <div class="category-card">
                    <div class="category-icon">❤️</div>
                    <div class="category-info">
                        <div class="category-name">Романтика</div>
                        <div class="category-count">142 книг</div>
                    </div>
                </div>
                
                <div class="category-card">
                    <div class="category-icon">⚡</div>
                    <div class="category-info">
                        <div class="category-name">Детективы</div>
                        <div class="category-count">98 книг</div>
                    </div>
                </div>
                
                <div class="category-card">
                    <div class="category-icon">🧠</div>
                    <div class="category-info">
                        <div class="category-name">Психология</div>
                        <div class="category-count">76 книг</div>
                    </div>
                </div>
                
                <div class="category-card">
                    <div class="category-icon">📊</div>
                    <div class="category-info">
                        <div class="category-name">Бизнес</div>
                        <div class="category-count">120 книг</div>
                    </div>
                </div>
                
                <div class="category-card">
                    <div class="category-icon">🕰️</div>
                    <div class="category-info">
                        <div class="category-name">История</div>
                        <div class="category-count">78 книг</div>
                    </div>
                </div>
                
                <div class="category-card">
                    <div class="category-icon">🎨</div>
                    <div class="category-info">
                        <div class="category-name">Искусство</div>
                        <div class="category-count">53 книг</div>
                    </div>
                </div>
            </div>
        </section>
        
        <!-- Thematic Collections Section -->
        <section style="margin-top: 40px;">
            <div class="section-header">
                <h2>Тематические подборки</h2>
                <a href="#" class="view-all">Смотреть все</a>
            </div>
            
            <div class="collections-grid">
                <div class="collection-card">
                    <img src="/api/placeholder/400/250" class="collection-image" alt="Книги для творческого мышления">
                    <div class="collection-overlay">
                        <div class="collection-title">Книги для творческого мышления</div>
                        <div class="collection-count">12 книг</div>
                    </div>
                </div>
                
                <div class="collection-card">
                    <img src="/api/placeholder/400/250" class="collection-image" alt="Научная фантастика XXI века">
                    <div class="collection-overlay">
                        <div class="collection-title">Научная фантастика XXI века</div>
                        <div class="collection-count">18 книг</div>
                    </div>
                </div>
                
                <div class="collection-card">
                    <img src="/api/placeholder/400/250" class="collection-image" alt="Лучшие романы всех времен">
                    <div class="collection-overlay">
                        <div class="collection-title">Лучшие романы всех времен</div>
                        <div class="collection-count">24 книг</div>
                    </div>
                </div>
            </div>
        </section>
        
        <!-- Footer -->
        <footer>
            <div class="footer-grid">
                <div class="footer-section">
                    <h3>О приложении</h3>
                    <p>AI Читалка Книг — это современное приложение для чтения электронных книг с умными рекомендациями, синхронизацией между устройствами и возможностью создания заметок.</p>
                </div>
                
                <div class="footer-section">
                    <h3>Разделы</h3>
                    <div class="footer-links">
                        <a href="#">Главная</a>
                        <a href="#">Каталог</a>
                        <a href="#">Новинки</a>
                        <a href="#">Популярное</a>
                        <a href="#">Моя библиотека</a>
                    </div>
                </div>
                
                <div class="footer-section">
                    <h3>Поддержка</h3>
                    <div class="footer-links">
                        <a href="#">Помощь</a>
                        <a href="#">Условия использования</a>
                        <a href="#">Политика конфиденциальности</a>
                        <a href="#">Контакты</a>
                    </div>
                </div>
                
                <div class="footer-section">
                    <h3>Подписаться</h3>
                    <p>Получайте уведомления о новых книгах</p>
                    <div class="subscribe-form">
                        <input type="email" placeholder="Email">
                        <button type="submit">→</button>
                    </div>
                </div>
            </div>
            
            <div class="copyright">
                <div>© 2025 AI Читалка Книг. Все права защищены.</div>
                <div class="social-links">
                    <a href="#">📘</a>
                    <a href="#">🐦</a>
                    <a href="#">📷</a>
                    <a href="#">▶️</a>
                </div>
            </div>
        </footer>
    </div>
</body>
</html>
<!---
Lakey1213/Lakey1213 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
