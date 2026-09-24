<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Такси-сервис | Курсовая работа</title>
<style>
    * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
    }

    html {
        scroll-behavior: smooth;
    }

    body {
        background: #000;
        color: #fff;
        font-family: 'Segoe UI', Arial, sans-serif;
        overflow-x: hidden;
    }

    a {
        color: inherit;
        text-decoration: none;
    }

    /* НАВИГАЦИЯ */
    nav {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        z-index: 1000;
        background: rgba(0, 0, 0, 0.85);
        backdrop-filter: blur(15px);
        border-bottom: 1px solid #1a1a1a;
        transition: all 0.3s;
    }

    .nav-container {
        width: 90%;
        max-width: 1200px;
        margin: auto;
        min-height: 70px;
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    .logo {
        font-size: 22px;
        font-weight: bold;
        letter-spacing: 2px;
        display: flex;
        align-items: center;
        gap: 10px;
    }

    .logo-icon {
        width: 32px;
        height: 32px;
        background: #f5c518;
        border-radius: 50%;
        display: flex;
        align-items: center;
        justify-content: center;
        color: #000;
        font-size: 18px;
        font-weight: bold;
    }

    .menu {
        display: flex;
        gap: 5px;
        list-style: none;
        align-items: center;
    }

    .menu a {
        color: #888;
        font-size: 14px;
        padding: 8px 16px;
        border-radius: 8px;
        transition: all 0.3s;
        display: block;
    }

    .menu a:hover,
    .menu a.active {
        color: #f5c518;
        background: rgba(245, 197, 24, 0.08);
    }

    /* ГЛАВНЫЙ ЭКРАН */
    .hero {
        min-height: 100vh;
        display: flex;
        align-items: center;
        position: relative;
        overflow: hidden;
        background: radial-gradient(ellipse at 30% 50%, rgba(245, 197, 24, 0.08) 0%, transparent 60%),
                    radial-gradient(ellipse at 80% 80%, rgba(245, 197, 24, 0.05) 0%, transparent 50%);
    }

    .hero::before {
        content: '';
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-image: 
            linear-gradient(rgba(245, 197, 24, 0.03) 1px, transparent 1px),
            linear-gradient(90deg, rgba(245, 197, 24, 0.03) 1px, transparent 1px);
        background-size: 60px 60px;
        pointer-events: none;
    }

    .container {
        width: 90%;
        max-width: 1200px;
        margin: auto;
        position: relative;
        z-index: 2;
    }

    .hero-content {
        padding: 120px 0 80px;
    }

    .hero-badge {
        display: inline-block;
        padding: 6px 16px;
        border: 1px solid #f5c518;
        border-radius: 30px;
        color: #f5c518;
        font-size: 12px;
        letter-spacing: 3px;
        text-transform: uppercase;
        margin-bottom: 30px;
    }

    .hero h1 {
        font-size: clamp(40px, 7vw, 90px);
        line-height: 1.05;
        letter-spacing: -3px;
        margin-bottom: 25px;
        font-weight: 800;
    }

    .hero h1 .accent {
        color: #f5c518;
    }

    .hero-description {
        max-width: 600px;
        color: #999;
        font-size: 18px;
        line-height: 1.7;
        margin-bottom: 40px;
    }

    .hero-buttons {
        display: flex;
        gap: 15px;
        flex-wrap: wrap;
    }

    .btn {
        display: inline-flex;
        align-items: center;
        gap: 8px;
        padding: 14px 28px;
        border-radius: 10px;
        font-size: 15px;
        font-weight: 600;
        transition: all 0.3s;
        cursor: pointer;
        border: none;
        font-family: inherit;
    }

    .btn-primary {
        background: #f5c518;
        color: #000;
    }

    .btn-primary:hover {
        background: #fff;
        transform: translateY(-2px);
    }

    .btn-outline {
        background: transparent;
        color: #fff;
        border: 1px solid #333;
    }

    .btn-outline:hover {
        border-color: #f5c518;
        color: #f5c518;
    }

    /* СТАТИСТИКА */
    .stats {
        display: grid;
        grid-template-columns: repeat(4, 1fr);
        gap: 20px;
        margin-top: 70px;
    }

    .stat {
        padding: 25px;
        background: rgba(255, 255, 255, 0.02);
        border: 1px solid #1a1a1a;
        border-radius: 15px;
        transition: all 0.3s;
    }

    .stat:hover {
        border-color: #f5c518;
        transform: translateY(-5px);
    }

    .stat-value {
        font-size: 36px;
        font-weight: 800;
        color: #f5c518;
        margin-bottom: 5px;
    }

    .stat-label {
        color: #777;
        font-size: 13px;
        text-transform: uppercase;
        letter-spacing: 1px;
    }

    /* СЕКЦИИ */
    section {
        padding: 100px 0;
        border-bottom: 1px solid #111;
    }

    .section-number {
        color: #f5c518;
        font-size: 12px;
        letter-spacing: 4px;
        margin-bottom: 12px;
        font-weight: 600;
    }

    .section-title {
        font-size: clamp(32px, 4vw, 48px);
        margin-bottom: 20px;
        letter-spacing: -1px;
    }

    .section-subtitle {
        color: #888;
        font-size: 17px;
        max-width: 600px;
        line-height: 1.7;
        margin-bottom: 50px;
    }

    /* ПАНЕЛИ */
    .panels {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
        gap: 20px;
    }

    .panel {
        background: #0a0a0a;
        border: 1px solid #1a1a1a;
        border-radius: 18px;
        overflow: hidden;
        transition: all 0.35s;
    }

    .panel:hover {
        border-color: #f5c518;
        transform: translateY(-6px);
        box-shadow: 0 20px 50px rgba(245, 197, 24, 0.08);
    }

    .panel-header {
        padding: 22px 25px;
        display: flex;
        justify-content: space-between;
        align-items: center;
        cursor: pointer;
        user-select: none;
        border-bottom: 1px solid transparent;
        transition: border-color 0.3s;
    }

    .panel.open .panel-header {
        border-bottom-color: #1a1a1a;
    }

    .panel-title {
        display: flex;
        align-items: center;
        gap: 14px;
        font-size: 17px;
        font-weight: 600;
    }

    .panel-icon {
        width: 38px;
        height: 38px;
        border-radius: 10px;
        background: rgba(245, 197, 24, 0.1);
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 18px;
        transition: all 0.3s;
    }

    .panel:hover .panel-icon,
    .panel.open .panel-icon {
        background: #f5c518;
        color: #000;
    }

    .panel-arrow {
        color: #555;
        font-size: 18px;
        transition: all 0.3s;
    }

    .panel.open .panel-arrow {
        transform: rotate(180deg);
        color: #f5c518;
    }

    .panel-body {
        max-height: 0;
        overflow: hidden;
        transition: max-height 0.4s ease, padding 0.3s ease;
        padding: 0 25px;
    }

    .panel.open .panel-body {
        max-height: 800px;
        padding: 22px 25px 28px;
    }

    .panel-body p {
        color: #999;
        line-height: 1.75;
        margin-bottom: 15px;
        font-size: 15px;
    }

    .panel-body p:last-child {
        margin-bottom: 0;
    }

    .panel-body ul {
        color: #999;
        line-height: 1.9;
        padding-left: 20px;
        margin-bottom: 15px;
        font-size: 15px;
    }

    .panel-body li::marker {
        color: #f5c518;
    }

    .panel-body strong {
        color: #ddd;
    }

    .panel-tags {
        display: flex;
        flex-wrap: wrap;
        gap: 8px;
        margin-top: 20px;
    }

    .tag {
        padding: 5px 12px;
        border: 1px solid #222;
        border-radius: 6px;
        font-size: 12px;
        color: #999;
        transition: all 0.3s;
    }

    .tag:hover {
        border-color: #f5c518;
        color: #f5c518;
    }

    /* ТЕХНОЛОГИИ */
    .tech-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
        gap: 15px;
        margin-top: 30px;
    }

    .tech-item {
        padding: 20px 15px;
        background: #0a0a0a;
        border: 1px solid #1a1a1a;
        border-radius: 12px;
        text-align: center;
        transition: all 0.3s;
        cursor: default;
    }

    .tech-item:hover {
        border-color: #f5c518;
        transform: translateY(-4px);
        background: rgba(245, 197, 24, 0.03);
    }

    .tech-name {
        font-size: 14px;
        font-weight: 600;
        margin-bottom: 4px;
    }

    .tech-role {
        font-size: 11px;
        color: #666;
        text-transform: uppercase;
        letter-spacing: 1px;
    }

    /* БЛОКИ КОДА */
    .code-block {
        background: #0d0d0d;
        border: 1px solid #1a1a1a;
        border-radius: 12px;
        padding: 20px;
        margin: 15px 0;
        overflow-x: auto;
        font-family: 'Courier New', monospace;
        font-size: 13px;
        line-height: 1.7;
        color: #ccc;
    }

    .code-block .kw { color: #f5c518; }
    .code-block .str { color: #7ec699; }
    .code-block .cm { color: #555; font-style: italic; }

    /* ДИАГРАММА / СХЕМА */
    .flow {
        display: flex;
        align-items: center;
        flex-wrap: wrap;
        gap: 10px;
        margin: 25px 0;
        padding: 25px;
        background: #0a0a0a;
        border: 1px solid #1a1a1a;
        border-radius: 15px;
    }

    .flow-step {
        padding: 12px 18px;
        background: rgba(245, 197, 24, 0.08);
        border: 1px solid rgba(245, 197, 24, 0.3);
        border-radius: 10px;
        font-size: 13px;
        color: #f5c518;
        font-weight: 600;
    }

    .flow-arrow {
        color: #444;
        font-size: 18px;
    }

    /* ТАБЛИЦА */
    .table-wrap {
        overflow-x: auto;
        margin-top: 20px;
        border-radius: 12px;
        border: 1px solid #1a1a1a;
    }

    table {
        width: 100%;
        border-collapse: collapse;
        font-size: 14px;
    }

    th {
        background: #0d0d0d;
        color: #f5c518;
        padding: 14px 18px;
        text-align: left;
        font-weight: 600;
        font-size: 12px;
        text-transform: uppercase;
        letter-spacing: 1px;
        border-bottom: 1px solid #1a1a1a;
    }

    td {
        padding: 13px 18px;
        color: #999;
        border-bottom: 1px solid #111;
    }

    tr:last-child td {
        border-bottom: none;
    }

    tr:hover td {
        background: rgba(245, 197, 24, 0.02);
        color: #ccc;
    }

    /* КАЛЬКУЛЯТОР */
    .calc {
        background: #0a0a0a;
        border: 1px solid #1a1a1a;
        border-radius: 18px;
        padding: 30px;
        max-width: 550px;
        margin-top: 20px;
    }

    .calc-row {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 18px;
    }

    .calc-row label {
        color: #aaa;
        font-size: 14px;
    }

    .calc-row input,
    .calc-row select {
        width: 180px;
        padding: 10px 14px;
        background: #000;
        border: 1px solid #222;
        border-radius: 8px;
        color: #fff;
        font-size: 14px;
        font-family: inherit;
        outline: none;
        transition: border-color 0.3s;
    }

    .calc-row input:focus,
    .calc-row select:focus {
        border-color: #f5c518;
    }

    .calc-total {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding-top: 20px;
        margin-top: 10px;
        border-top: 1px solid #1a1a1a;
    }

    .calc-total span:first-child {
        color: #888;
        font-size: 15px;
    }

    .calc-total span:last-child {
        color: #f5c518;
        font-size: 28px;
        font-weight: 800;
    }

    /* СКРИПТЫ */
    .scripts {
        display: flex;
        gap: 10px;
        flex-wrap: wrap;
        margin-top: 20px;
    }

    .script-btn {
        padding: 10px 18px;
        background: #0a0a0a;
        border: 1px solid #1a1a1a;
        border-radius: 8px;
        color: #999;
        font-size: 13px;
        cursor: pointer;
        transition: all 0.3s;
        font-family: inherit;
    }

    .script-btn:hover {
        border-color: #f5c518;
        color: #f5c518;
    }

    .script-btn.active {
        background: #f5c518;
        color: #000;
        border-color: #f5c518;
    }

    .script-output {
        margin-top: 15px;
        padding: 18px;
        background: #0d0d0d;
        border: 1px solid #1a1a1a;
        border-radius: 10px;
        font-family: 'Courier New', monospace;
        font-size: 13px;
        color: #7ec699;
        min-height: 50px;
        white-space: pre-wrap;
    }

    /* ЗАКЛЮЧЕНИЕ */
    .conclusion {
        background: linear-gradient(135deg, rgba(245, 197, 24, 0.05) 0%, transparent 100%);
        border: 1px solid rgba(245, 197, 24, 0.15);
        border-radius: 20px;
        padding: 45px;
        text-align: center;
    }

    .conclusion h3 {
        font-size: 28px;
        margin-bottom: 20px;
    }

    .conclusion p {
        color: #999;
        line-height: 1.8;
        max-width: 700px;
        margin: 0 auto 25px;
        font-size: 16px;
    }

    /* FOOTER */
    footer {
        padding: 40px 0;
        text-align: center;
        color: #444;
        font-size: 13px;
        border-top: 1px solid #111;
    }

    footer a {
        color: #f5c518;
    }

    /* АДАПТИВ */
    @media (max-width: 900px) {
        .stats {
            grid-template-columns: repeat(2, 1fr);
        }

        .nav-container {
            flex-direction: column;
            padding: 12px 0;
            gap: 10px;
        }

        .menu {
            flex-wrap: wrap;
            justify-content: center;
        }

        .menu a {
            font-size: 12px;
            padding: 6px 12px;
        }
    }

    @media (max-width: 600px) {
        .stats {
            grid-template-columns: 1fr;
        }

        section {
            padding: 70px 0;
        }

        .panel-header {
            padding: 18px 20px;
        }

        .panel-body {
            padding-left: 20px;
            padding-right: 20px;
        }

        .panel.open .panel-body {
            padding: 18px 20px 22px;
        }

        .calc-row {
            flex-direction: column;
            align-items: flex-start;
            gap: 8px;
        }

        .calc-row input,
        .calc-row select {
            width: 100%;
        }
    }
</style>
</head>
<body>

<!-- НАВИГАЦИЯ -->
<nav>
    <div class="nav-container">
        <div class="logo">
            <div class="logo-icon">Т</div>
            <span>TAXI<span style="color:#f5c518">.</span>DEV</span>
        </div>
        <ul class="menu">
            <li><a href="#intro" class="active">Введение</a></li>
            <li><a href="#analysis">Анализ</a></li>
            <li><a href="#design">Проектирование</a></li>
            <li><a href="#tech">Технологии</a></li>
            <li><a href="#implementation">Реализация</a></li>
            <li><a href="#calc">Калькулятор</a></li>
            <li><a href="#conclusion">Заключение</a></li>
        </ul>
    </div>
</nav>

<!-- ГЛАВНЫЙ ЭКРАН -->
<section class="hero" id="hero">
    <div class="container">
        <div class="hero-content">
            <div class="hero-badge">Курсовая работа · 2026</div>
            <h1>
                Разработка<br>
                <span class="accent">такси-сервиса</span><br>
                на веб-платформе
            </h1>
            <p class="hero-description">
                Проектирование и реализация информационной системы
                для заказа такси с личным кабинетом пользователя,
                панелью водителя и административной частью.
            </p>
            <div class="hero-buttons">
                <a href="#intro" class="btn btn-primary">Начать изучение →</a>
                <a href="#implementation" class="btn btn-outline">Смотреть код</a>
            </div>

            <div class="stats">
                <div class="stat">
                    <div class="stat-value">6</div>
                    <div class="stat-label">Разделов</div>
                </div>
                <div class="stat">
                    <div class="stat-value">4</div>
                    <div class="stat-label">Роли</div>
                </div>
                <div class="stat">
                    <div class="stat-value">12+</div>
                    <div class="stat-label">Функций</div>
                </div>
                <div class="stat">
                    <div class="stat-value">3</div>
                    <div class="stat-label">Языка</div>
                </div>
            </div>
        </div>
    </div>
</section>

<!-- ВВЕДЕНИЕ -->
<section id="intro">
    <div class="container">
        <div class="section-number">01 — INTRODUCTION</div>
        <h2 class="section-title">Введение</h2>
        <p class="section-subtitle">
            Актуальность темы, цель и задачи курсовой работы.
        </p>

        <div class="panels">
            <div class="panel open">
                <div class="panel-header" onclick="togglePanel(this)">
                    <div class="panel-title">
                        <div class="panel-icon">📋</div>
                        Актуальность темы
                    </div>
                    <div class="panel-arrow">▼</div>
                </div>
                <div class="panel-body">
                    <p>
                        Рынок такси в России демонстрирует устойчивый рост.
                        Ежедневно миллионы людей пользуются услугами
                        онлайн-заказа такси. Автоматизация этого процесса
                        повышает качество обслуживания и снижает издержки
                        перевозчиков.
                    </p>
                    <p>
                        Создание собственного веб-сервиса позволяет
                        изучить полный цикл разработки: от проектирования
                        базы данных до реализации интерфейса пользователя.
                    </p>
                </div>
            </div>

            <div class="panel">
                <div class="panel-header" onclick="togglePanel(this)">
                    <div class="panel-title">
                        <div class="panel-icon">🎯</div>
                        Цель работы
                    </div>
                    <div class="panel-arrow">▼</div>
                </div>
                <div class="panel-body">
                    <p>
                        <strong>Цель:</strong> разработать веб-приложение
                        для заказа такси с разделением ролей пользователей
                        и удобным интерфейсом.
                    </p>
                </div>
            </div>

            <div class="panel">
                <div class="panel-header" onclick="togglePanel(this)">
                    <div class="panel-title">
                        <div class="panel-icon">📌</div>
                        Задачи
                    </div>
                    <div class="panel-arrow">▼</div>
                </div>
                <div class="panel-body">
                    <ul>
                        <li>Проанализировать существующие такси-сервисы;</li>
                        <li>Спроектировать архитектуру приложения;</li>
                        <li>Разработать базу данных;</li>
                        <li>Реализовать пользовательский интерфейс;</li>
                        <li>Написать серверную логику;</li>
                        <li>Провести тестирование.</li>
                    </ul>
                </div>
            </div>

            <div class="panel">
                <div class="panel-header" onclick="togglePanel(this)">
                    <div class="panel-title">
                        <div class="panel-icon">👥</div>
                        Роли пользователей
                    </div>
                    <div class="panel-arrow">▼</div>
                </div>
                <div class="panel-body">
                    <p><strong>Клиент</strong> — заказывает поездку, отслеживает статус, оплачивает.</p>
                    <p><strong>Водитель</strong> — принимает заказы, отмечает статус поездки.</p>
                    <p><strong>Диспетчер</strong> — контролирует активные заказы.</p>
                    <p><strong>Администратор</strong> — управляет пользователями и тарифами.</p>
                </div>
            </div>
        </div>
    </div>
</section>

<!-- АНАЛИЗ -->
<section id="analysis">
    <div class="container">
        <div class="section-number">02 — ANALYSIS</div>
        <h2 class="section-title">Анализ предметной области</h2>
        <p class="section-subtitle">
            Сравнение существующих решений и выявление требований к системе.
        </p>

        <div class="table-wrap">
            <table>
                <thead>
                    <tr>
                        <th>Сервис</th>
                        <th>Заказ онлайн</th>
                        <th>Оплата картой</th>
                        <th>Отслеживание</th>
                        <th>Рейтинг</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>Яндекс.Такси</td>
                        <td>✓</td>
                        <td>✓</td>
                        <td>✓</td>
                        <td>4.8</td>
                    </tr>
                    <tr>
                        <td>Uber</td>
                        <td>✓</td>
                        <td>✓</td>
                        <td>✓</td>
                        <td>4.7</td>
                    </tr>
                    <tr>
                        <td>Ситимобил</td>
                        <td>✓</td>
                        <td>✓</td>
                        <td>✓</td>
                        <td>4.5</td>
                    </tr>
                    <tr>
                        <td><strong>Наш сервис</strong></td>
                        <td>✓</td>
                        <td>✓</td>
                        <td>✓</td>
                        <td>—</td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</section>

<!-- ПРОЕКТИРОВАНИЕ -->
<section id="design">
    <div class="container">
        <div class="section-number">03 — DESIGN</div>
        <h2 class="section-title">Проектирование системы</h2>
        <p class="section-subtitle">
            Архитектура приложения и схема взаимодействия компонентов.
        </p>

        <div class="panels">
            <div class="panel open">
                <div class="panel-header" onclick="togglePanel(this)">
                    <div class="panel-title">
                        <div class="panel-icon">🏗</div>
                        Архитектура приложения
                    </div>
                    <div class="panel-arrow">▼</div>
                </div>
                <div class="panel-body">
                    <p>Приложение построено по клиент-серверной архитектуре:</p>
                    <div class="flow">
                        <div class="flow-step">Клиент</div>
                        <div class="flow-arrow">→</div>
                        <div class="flow-step">HTTP/REST API</div>
                        <div class="flow-arrow">→</div>
                        <div class="flow-step">Сервер</div>
                        <div class="flow-arrow">→</div>
                        <div class="flow-step">База данных</div>
                    </div>
                    <p>
                        Frontend отвечает за отображение и взаимодействие
                        с пользователем. Backend обрабатывает запросы,
                        работает с БД и возвращает данные в формате JSON.
                    </p>
                </div>
            </div>

            <div class="panel">
                <div class="panel-header" onclick="togglePanel(this)">
                    <div class="panel-title">
                        <div class="panel-icon">🗄</div>
                        Схема базы данных
                    </div>
                    <div class="panel-arrow">▼</div>
                </div>
                <div class="panel-body">
                    <p>Основные таблицы базы данных:</p>
                    <ul>
                        <li><strong>users</strong> — пользователи (id, имя, телефон, роль)</li>
                        <li><strong>drivers</strong> — водители (id, авто, рейтинг)</li>
                        <li><strong>orders</strong> — заказы (id, клиент, водитель, адрес, статус)</li>
                        <li><strong>tariffs</strong> — тарифы (id, название, цена за км)</li>
                        <li><strong>payments</strong> — платежи (id, заказ, сумма, статус)</li>
                    </ul>
                </div>
            </div>

            <div class="panel">
                <div class="panel-header" onclick="togglePanel(this)">
                    <div class="panel-title">
                        <div class="panel-icon">🔄</div>
                        Жизненный цикл заказа
                    </div>
                    <div class="panel-arrow">▼</div>
                </div>
                <div class="panel-body">
                    <div class="flow">
                        <div class="flow-step">Создан</div>
                        <div class="flow-arrow">→</div>
                        <div class="flow-step">Поиск</div>
                        <div class="flow-arrow">→</div>
                        <div class="flow-step">Принят</div>
                        <div class="flow-arrow">→</div>
                        <div class="flow-step">В пути</div>
                        <div class="flow-arrow">→</div>
                        <div class="flow-step">Завершён</div>
                    </div>
                </div>
            </div>

            <div class="panel">
                <div class="panel-header" onclick="togglePanel(this)">
                    <div class="panel-title">
                        <div class="panel-icon">🔐</div>
                        Авторизация
                    </div>
                    <div class="panel-arrow">▼</div>
                </div>
                <div class="panel-body">
                    <p>
                        Используется JWT-аутентификация. При входе
                        пользователь получает токен, который хранится
                        в localStorage и передаётся в заголовке
                        <strong>Authorization</strong> при каждом запросе.
                    </p>
                </div>
            </div>
        </div>
    </div>
</section>

<!-- ТЕХНОЛОГИИ -->
<section id="tech">
    <div class="container">
        <div class="section-number">04 — TECHNOLOGIES</div>
        <h2 class="section-title">Используемые технологии</h2>
        <p class="section-subtitle">
            Стек технологий, выбранный для реализации проекта.
        </p>

        <div class="tech-grid">
            <div class="tech-item">
                <div class="tech-name">HTML5</div>
                <div class="tech-role">Разметка</div>
            </div>
            <div class="tech-item">
                <div class="tech-name">CSS3</div>
                <div class="tech-role">Стилизация</div>
            </div>
            <div class="tech-item">
                <div class="tech-name">JavaScript</div>
                <div class="tech-role">Логика клиента</div>
            </div>
            <div class="tech-item">
                <div class="tech-name">Python</div>
                <div class="tech-role">Backend</div>
            </div>
            <div class="tech-item">
                <div class="tech-name">Flask</div>
                <div class="tech-role">Web-фреймворк</div>
            </div>
            <div class="tech-item">
                <div class="tech-name">SQLite</div>
                <div class="tech-role">База данных</div>
            </div>
            <div class="tech-item">
                <div class="tech-name">Git</div>
                <div class="tech-role">Контроль версий</div>
            </div>
            <div class="tech-item">
                <div class="tech-name">REST API</div>
                <div class="tech-role">Взаимодействие</div>
            </div>
        </div>
    </div>
</section>

<!-- РЕАЛИЗАЦИЯ -->
<section id="implementation">
    <div class="container">
        <div class="section-number">05 — IMPLEMENTATION</div>
        <h2 class="section-title">Реализация</h2>
        <p class="section-subtitle">
            Ключевые фрагменты кода и интерактивные примеры.
        </p>

        <div class="panels">
            <div class="panel open">
                <div class="panel-header" onclick="togglePanel(this)">
                    <div class="panel-title">
                        <div class="panel-icon">🐍</div>
                        Модель базы данных
                    </div>
                    <div class="panel-arrow">▼</div>
                </div>
                <div class="panel-body">
                    <div class="code-block">
<span class="kw">class</span> <span class="str">Order</span>(db.Model):
    id = db.Column(db.Integer, primary_key=<span class="kw">True</span>)
    client_id = db.Column(db.Integer, db.ForeignKey(<span class="str">'user.id'</span>))
    driver_id = db.Column(db.Integer, db.ForeignKey(<span class="str">'driver.id'</span>))
    from_addr = db.Column(db.String(<span class="str">200</span>))
    to_addr = db.Column(db.String(<span class="str">200</span>))
    status = db.Column(db.String(<span class="str">20</span>), default=<span class="str">'created'</span>)
    price = db.Column(db.Float)
    created_at = db.Column(db.DateTime, default=datetime.utcnow)
                    </div>
                </div>
            </div>

            <div class="panel">
                <div class="panel-header" onclick="togglePanel(this)">
                    <div class="panel-title">
                        <div class="panel-icon">🌐</div>
                        API-маршрут заказа
                    </div>
                    <div class="panel-arrow">▼</div>
                </div>
                <div class="panel-body">
                    <div class="code-block">
<span class="cm"># Создание заказа</span>
<span class="kw">@app</span>.route
