<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>IP & Security Checker Pro | Расширенная проверка безопасности</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        :root {
            --primary: #2c3e50;
            --secondary: #3498db;
            --accent: #e74c3c;
            --success: #2ecc71;
            --warning: #f39c12;
            --light: #ecf0f1;
            --dark: #2c3e50;
            --gray: #95a5a6;
            --purple: #9b59b6;
            --teal: #1abc9c;
        }

        body {
            background-color: #f5f7fa;
            color: #333;
            line-height: 1.6;
            min-height: 100vh;
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Header */
        header {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            padding: 2rem 0;
            text-align: center;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
            position: relative;
            overflow: hidden;
        }

        .header-pattern {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: 
                radial-gradient(circle at 10% 20%, rgba(255,255,255,0.1) 0%, transparent 20%),
                radial-gradient(circle at 90% 80%, rgba(255,255,255,0.1) 0%, transparent 20%);
            pointer-events: none;
        }

        .logo {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 15px;
            margin-bottom: 10px;
            position: relative;
            z-index: 1;
        }

        .logo i {
            font-size: 2.5rem;
        }

        .logo h1 {
            font-size: 2.5rem;
            font-weight: 700;
        }

        .tagline {
            font-size: 1.1rem;
            opacity: 0.9;
            margin-bottom: 1.5rem;
            position: relative;
            z-index: 1;
        }

        /* Tabs */
        .tabs {
            display: flex;
            justify-content: center;
            gap: 10px;
            margin: 30px 0;
            flex-wrap: wrap;
        }

        .tab-btn {
            background: rgba(255, 255, 255, 0.1);
            border: none;
            color: white;
            padding: 10px 20px;
            border-radius: 30px;
            cursor: pointer;
            font-size: 0.9rem;
            font-weight: 600;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .tab-btn:hover {
            background: rgba(255, 255, 255, 0.2);
            transform: translateY(-2px);
        }

        .tab-btn.active {
            background: white;
            color: var(--primary);
        }

        /* Main content */
        .tab-content {
            display: none;
            animation: fadeIn 0.5s ease;
        }

        .tab-content.active {
            display: block;
        }

        .main-content {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 30px;
            margin: 40px 0;
        }

        @media (max-width: 768px) {
            .main-content {
                grid-template-columns: 1fr;
            }
        }

        .card {
            background: white;
            border-radius: 12px;
            padding: 25px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            height: 100%;
            display: flex;
            flex-direction: column;
        }

        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.1);
        }

        .card-header {
            display: flex;
            align-items: center;
            gap: 15px;
            margin-bottom: 20px;
            padding-bottom: 15px;
            border-bottom: 2px solid #f0f0f0;
        }

        .card-header i {
            font-size: 2rem;
            color: var(--secondary);
        }

        .card-header h2 {
            font-size: 1.5rem;
            color: var(--primary);
            flex-grow: 1;
        }

        .card-badge {
            background: var(--accent);
            color: white;
            padding: 4px 12px;
            border-radius: 20px;
            font-size: 0.8rem;
            font-weight: 600;
        }

        .btn {
            display: inline-block;
            background: var(--secondary);
            color: white;
            border: none;
            padding: 12px 25px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 1rem;
            font-weight: 600;
            transition: all 0.3s ease;
            text-align: center;
            width: 100%;
            margin-top: auto;
            text-decoration: none;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }

        .btn:hover {
            background: var(--primary);
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(52, 152, 219, 0.3);
        }

        .btn-danger {
            background: var(--accent);
        }

        .btn-danger:hover {
            background: #c0392b;
            box-shadow: 0 5px 15px rgba(231, 76, 60, 0.3);
        }

        .btn-success {
            background: var(--success);
        }

        .btn-success:hover {
            background: #27ae60;
            box-shadow: 0 5px 15px rgba(46, 204, 113, 0.3);
        }

        .btn-warning {
            background: var(--warning);
        }

        .btn-warning:hover {
            background: #d68910;
            box-shadow: 0 5px 15px rgba(243, 156, 18, 0.3);
        }

        .btn-purple {
            background: var(--purple);
        }

        .btn-purple:hover {
            background: #8e44ad;
            box-shadow: 0 5px 15px rgba(155, 89, 182, 0.3);
        }

        .btn-teal {
            background: var(--teal);
        }

        .btn-teal:hover {
            background: #16a085;
            box-shadow: 0 5px 15px rgba(26, 188, 156, 0.3);
        }

        /* Input groups */
        .input-group {
            margin-bottom: 20px;
        }

        .input-label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: var(--dark);
        }

        .input-field {
            width: 100%;
            padding: 12px 15px;
            border: 2px solid #e0e0e0;
            border-radius: 8px;
            font-size: 1rem;
            transition: border-color 0.3s ease;
        }

        .input-field:focus {
            outline: none;
            border-color: var(--secondary);
        }

        /* Ports section */
        .ports-container {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(120px, 1fr));
            gap: 10px;
            margin: 20px 0;
            max-height: 300px;
            overflow-y: auto;
            padding: 10px;
        }

        .port-item {
            background: #f8f9fa;
            padding: 10px;
            border-radius: 8px;
            text-align: center;
            transition: all 0.3s ease;
            cursor: pointer;
        }

        .port-item.open {
            background: rgba(231, 76, 60, 0.1);
            border-left: 4px solid var(--accent);
        }

        .port-item.closed {
            background: rgba(46, 204, 113, 0.1);
            border-left: 4px solid var(--success);
        }

        .port-item.filtered {
            background: rgba(243, 156, 18, 0.1);
            border-left: 4px solid var(--warning);
        }

        .port-number {
            font-weight: 700;
            font-size: 1.1rem;
        }

        .port-status {
            font-size: 0.8rem;
            margin-top: 5px;
            font-weight: 600;
        }

        /* Results section */
        .results {
            margin-top: 30px;
            background: white;
            border-radius: 12px;
            padding: 25px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
        }

        .results-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
            padding-bottom: 15px;
            border-bottom: 2px solid #f0f0f0;
        }

        .results-header h2 {
            color: var(--primary);
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .results-actions {
            display: flex;
            gap: 10px;
        }

        .action-btn {
            background: #f8f9fa;
            border: none;
            padding: 8px 15px;
            border-radius: 6px;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 5px;
            transition: all 0.3s ease;
        }

        .action-btn:hover {
            background: var(--secondary);
            color: white;
        }

        .result-item {
            display: flex;
            justify-content: space-between;
            padding: 12px 0;
            border-bottom: 1px dashed #eee;
        }

        .result-item:last-child {
            border-bottom: none;
        }

        .result-label {
            font-weight: 600;
            color: var(--dark);
            flex: 1;
        }

        .result-value {
            color: var(--primary);
            text-align: right;
            flex: 2;
            word-break: break-word;
        }

        .status-safe {
            color: var(--success);
            font-weight: 600;
        }

        .status-warning {
            color: var(--warning);
            font-weight: 600;
        }

        .status-danger {
            color: var(--accent);
            font-weight: 600;
        }

        .status-info {
            color: var(--secondary);
            font-weight: 600;
        }

        /* File upload */
        .file-upload {
            border: 2px dashed var(--gray);
            border-radius: 8px;
            padding: 30px;
            text-align: center;
            margin-bottom: 20px;
            transition: border 0.3s ease;
            flex-grow: 1;
        }

        .file-upload:hover {
            border-color: var(--secondary);
        }

        .file-upload i {
            font-size: 3rem;
            color: var(--gray);
            margin-bottom: 15px;
        }

        /* Progress bar */
        .progress-container {
            background: #eee;
            border-radius: 10px;
            height: 10px;
            margin: 20px 0;
            overflow: hidden;
            display: none;
        }

        .progress-bar {
            background: linear-gradient(90deg, var(--secondary), var(--teal));
            height: 100%;
            width: 0%;
            transition: width 0.5s ease;
        }

        /* History section */
        .history-container {
            margin-top: 30px;
        }

        .history-item {
            background: white;
            border-radius: 8px;
            padding: 15px;
            margin-bottom: 10px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.05);
            border-left: 4px solid var(--secondary);
        }

        /* Footer */
        footer {
            background: var(--primary);
            color: white;
            text-align: center;
            padding: 40px 0 20px;
            margin-top: 50px;
        }

        .footer-content {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 30px;
            margin-bottom: 30px;
        }

        .footer-section h3 {
            margin-bottom: 15px;
            font-size: 1.2rem;
        }

        .footer-links {
            list-style: none;
        }

        .footer-links li {
            margin-bottom: 10px;
        }

        .footer-links a {
            color: white;
            text-decoration: none;
            transition: color 0.3s ease;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .footer-links a:hover {
            color: var(--secondary);
        }

        .copyright {
            padding-top: 20px;
            border-top: 1px solid rgba(255,255,255,0.1);
            font-size: 0.9rem;
            opacity: 0.8;
        }

        /* Animations */
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); }
        }

        .pulse {
            animation: pulse 2s infinite;
        }

        /* Responsive adjustments */
        @media (max-width: 600px) {
            .logo h1 {
                font-size: 2rem;
            }
            
            .card {
                padding: 20px;
            }
            
            .footer-content {
                grid-template-columns: 1fr;
            }
            
            .results-header {
                flex-direction: column;
                gap: 15px;
                align-items: flex-start;
            }
            
            .results-actions {
                width: 100%;
                justify-content: space-between;
            }
        }
    </style>
</head>
<body>
    <header>
        <div class="header-pattern"></div>
        <div class="container">
            <div class="logo">
                <i class="fas fa-shield-alt"></i>
                <h1>IP & Security Checker Pro</h1>
                <span class="card-badge">PRO</span>
            </div>
            <p class="tagline">Полный набор инструментов для проверки безопасности в интернете</p>
            
            <div class="tabs">
                <button class="tab-btn active" data-tab="basic">
                    <i class="fas fa-home"></i> Основное
                </button>
                <button class="tab-btn" data-tab="advanced">
                    <i class="fas fa-chart-line"></i> Расширенное
                </button>
                <button class="tab-btn" data-tab="tools">
                    <i class="fas fa-tools"></i> Инструменты
                </button>
                <button class="tab-btn" data-tab="history">
                    <i class="fas fa-history"></i> История
                </button>
            </div>
        </div>
    </header>

    <div class="container">
        <!-- Основные функции -->
        <div id="basic" class="tab-content active">
            <div class="main-content">
                <!-- IP Check Card -->
                <div class="card">
                    <div class="card-header">
                        <i class="fas fa-globe"></i>
                        <h2>Проверка IP-адреса</h2>
                    </div>
                    <p>Полная информация о вашем IP-адресе: местоположение, провайдер, тип соединения и координаты.</p>
                    <div class="input-group">
                        <label class="input-label">Введите IP или домен для проверки:</label>
                        <input type="text" id="ipInput" class="input-field" placeholder="Ваш IP или example.com">
                    </div>
                    <button id="checkIpBtn" class="btn">Проверить IP</button>
                </div>

                <!-- Anonymity Check Card -->
                <div class="card">
                    <div class="card-header">
                        <i class="fas fa-user-secret"></i>
                        <h2>Проверка анонимности</h2>
                    </div>
                    <p>Определите уровень вашей анонимности в сети. Обнаружение VPN, прокси и TOR.</p>
                    <button id="checkAnonymityBtn" class="btn btn-warning">Проверить анонимность</button>
                </div>

                <!-- File Check Card -->
                <div class="card">
                    <div class="card-header">
                        <i class="fas fa-file-shield"></i>
                        <h2>Проверка файла на вирусы</h2>
                    </div>
                    <p>Загрузите файл для проверки на вирусы с использованием 68 антивирусных движков.</p>
                    <div class="file-upload">
                        <i class="fas fa-cloud-upload-alt"></i>
                        <p>Перетащите файл сюда или нажмите для выбора</p>
                        <input type="file" id="fileInput" style="display: none;">
                        <button id="selectFileBtn" class="btn" style="width: auto; margin-top: 10px;">Выбрать файл</button>
                    </div>
                    <div class="progress-container" id="progressContainer">
                        <div class="progress-bar" id="progressBar"></div>
                    </div>
                    <button id="checkFileBtn" class="btn btn-danger" disabled>Проверить файл</button>
                </div>

                <!-- System Security Card -->
                <div class="card">
                    <div class="card-header">
                        <i class="fas fa-laptop-medical"></i>
                        <h2>Проверка безопасности системы</h2>
                    </div>
                    <p>Комплексная проверка настроек безопасности браузера и операционной системы.</p>
                    <button id="checkSecurityBtn" class="btn btn-success">Проверить безопасность</button>
                </div>
            </div>
        </div>

        <!-- Расширенные функции -->
        <div id="advanced" class="tab-content">
            <div class="main-content">
                <!-- WHOIS информация -->
                <div class="card">
                    <div class="card-header">
                        <i class="fas fa-search"></i>
                        <h2>WHOIS информация</h2>
                    </div>
                    <p>Получите полную WHOIS информацию о домене или IP-адресе: регистратор, дата создания, контакты владельца.</p>
                    <div class="input-group">
                        <label class="input-label">Введите домен или IP для WHOIS:</label>
                        <input type="text" id="whoisInput" class="input-field" placeholder="example.com или 8.8.8.8">
                    </div>
                    <button id="checkWhoisBtn" class="btn btn-purple">Проверить WHOIS</button>
                </div>

                <!-- Проверка портов -->
                <div class="card">
                    <div class="card-header">
                        <i class="fas fa-plug"></i>
                        <h2>Сканер портов</h2>
                    </div>
                    <p>Проверьте открытые порты на указанном хосте. Определите уязвимости в сетевой безопасности.</p>
                    <div class="input-group">
                        <label class="input-label">Целевой хост:</label>
                        <input type="text" id="portHostInput" class="input-field" placeholder="example.com или IP">
                    </div>
                    <div class="input-group">
                        <label class="input-label">Диапазон портов:</label>
                        <select id="portRangeSelect" class="input-field">
                            <option value="common">Общие порты (1-1024)</option>
                            <option value="web">Веб-серверы (80,443,8080)</option>
                            <option value="all">Все порты (1-65535)</option>
                            <option value="custom">Выбрать вручную</option>
                        </select>
                    </div>
                    <button id="scanPortsBtn" class="btn btn-teal">Сканировать порты</button>
                </div>

                <!-- Информация о владельце -->
                <div class="card">
                    <div class="card-header">
                        <i class="fas fa-user-tie"></i>
                        <h2>Информация о владельце</h2>
                    </div>
                    <p>Получите информацию о владельце домена или IP-адреса: организация, контакты, местоположение.</p>
                    <div class="input-group">
                        <label class="input-label">Домен или IP для проверки:</label>
                        <input type="text" id="ownerInput" class="input-field" placeholder="example.com">
                    </div>
                    <button id="checkOwnerBtn" class="btn btn-purple">Найти владельца</button>
                </div>

                <!-- DNS информация -->
                <div class="card">
                    <div class="card-header">
                        <i class="fas fa-sitemap"></i>
                        <h2>DNS информация</h2>
                    </div>
                    <p>Получите полную DNS информацию о домене: A, MX, TXT, NS записи и многое другое.</p>
                    <div class="input-group">
                        <label class="input-label">Домен для DNS проверки:</label>
                        <input type="text" id="dnsInput" class="input-field" placeholder="example.com">
                    </div>
                    <button id="checkDnsBtn" class="btn btn-teal">Проверить DNS</button>
                </div>
            </div>
        </div>

        <!-- Инструменты -->
        <div id="tools" class="tab-content">
            <div class="main-content">
                <!-- Конвертер IP -->
                <div class="card">
                    <div class="card-header">
                        <i class="fas fa-exchange-alt"></i>
                        <h2>Конвертер IP</h2>
                    </div>
                    <p>Конвертируйте IP-адреса между различными форматами: десятичный, шестнадцатеричный, бинарный.</p>
                    <div class="input-group">
                        <label class="input-label">Введите IP-адрес:</label>
                        <input type="text" id="convertIpInput" class="input-field" placeholder="192.168.1.1">
                    </div>
                    <button id="convertIpBtn" class="btn">Конвертировать</button>
                </div>

                <!-- Геолокация -->
                <div class="card">
                    <div class="card-header">
                        <i class="fas fa-map-marked-alt"></i>
                        <h2>Геолокация IP</h2>
                    </div>
                    <p>Точное определение географического местоположения по IP-адресу с отображением на карте.</p>
                    <div class="input-group">
                        <label class="input-label">IP для геолокации:</label>
                        <input type="text" id="geolocationInput" class="input-field" placeholder="8.8.8.8">
                    </div>
                    <button id="geolocationBtn" class="btn btn-success">Найти на карте</button>
                </div>

                <!-- Проверка SSL -->
                <div class="card">
                    <div class="card-header">
                        <i class="fas fa-lock"></i>
                        <h2>Проверка SSL сертификата</h2>
                    </div>
                    <p>Проверьте SSL/TLS сертификат любого сайта: срок действия, издатель, алгоритм шифрования.</p>
                    <div class="input-group">
                        <label class="input-label">URL сайта для проверки SSL:</label>
                        <input type="text" id="sslInput" class="input-field" placeholder="https://example.com">
                    </div>
                    <button id="checkSslBtn" class="btn btn-warning">Проверить SSL</button>
                </div>

                <!-- Ping инструмент -->
                <div class="card">
                    <div class="card-header">
                        <i class="fas fa-network-wired"></i>
                        <h2>Ping инструмент</h2>
                    </div>
                    <p>Проверьте доступность хоста и задержку соединения с помощью ping-запросов.</p>
                    <div class="input-group">
                        <label class="input-label">Хост для ping:</label>
                        <input type="text" id="pingInput" class="input-field" placeholder="example.com">
                    </div>
                    <button id="pingBtn" class="btn">Выполнить Ping</button>
                </div>
            </div>
        </div>

        <!-- История -->
        <div id="history" class="tab-content">
            <div class="results">
                <div class="results-header">
                    <h2><i class="fas fa-history"></i> История проверок</h2>
                    <div class="results-actions">
                        <button id="clearHistoryBtn" class="action-btn">
                            <i class="fas fa-trash"></i> Очистить
                        </button>
                        <button id="exportHistoryBtn" class="action-btn">
                            <i class="fas fa-download"></i> Экспорт
                        </button>
                    </div>
                </div>
                <div id="historyContent">
                    <!-- История будет загружена здесь -->
                </div>
            </div>
        </div>

        <!-- Results Section -->
        <div class="results" id="resultsSection" style="display: none;">
            <div class="results-header">
                <h2 id="resultsTitle">Результаты проверки</h2>
                <div class="results-actions">
                    <button id="copyResultsBtn" class="action-btn">
                        <i class="far fa-copy"></i> Копировать
                    </button>
                    <button id="saveResultsBtn" class="action-btn">
                        <i class="far fa-save"></i> Сохранить
                    </button>
                    <button id="shareResultsBtn" class="action-btn">
                        <i class="fas fa-share-alt"></i> Поделиться
                    </button>
                </div>
            </div>
            <div id="resultsContent">
                <!-- Результаты будут отображаться здесь -->
            </div>
        </div>
    </div>

    <footer>
        <div class="container">
            <div class="footer-content">
                <div class="footer-section">
                    <h3>Инструменты</h3>
                    <ul class="footer-links">
                        <li><a href="#"><i class="fas fa-globe"></i> Проверка IP</a></li>
                        <li><a href="#"><i class="fas fa-user-secret"></i> Проверка анонимности</a></li>
                        <li><a href="#"><i class="fas fa-file-shield"></i> Проверка файлов</a></li>
                        <li><a href="#"><i class="fas fa-search"></i> WHOIS поиск</a></li>
                    </ul>
                </div>
                <div class="footer-section">
                    <h3>Ресурсы</h3>
                    <ul class="footer-links">
                        <li><a href="#"><i class="fas fa-book"></i> Документация</a></li>
                        <li><a href="#"><i class="fas fa-question-circle"></i> Помощь</a></li>
                        <li><a href="#"><i class="fas fa-blog"></i> Блог</a></li>
                        <li><a href="#"><i class="fas fa-tools"></i> API для разработчиков</a></li>
                    </ul>
                </div>
                <div class="footer-section">
                    <h3>Контакты</h3>
                    <ul class="footer-links">
                        <li><a href="#"><i class="fas fa-envelope"></i> Поддержка</a></li>
                        <li><a href="#"><i class="fas fa-comments"></i> Обратная связь</a></li>
                        <li><a href="#"><i class="fab fa-github"></i> GitHub</a></li>
                        <li><a href="#"><i class="fab fa-twitter"></i> Twitter</a></li>
                    </ul>
                </div>
            </div>
            <div class="copyright">
                <p>IP & Security Checker Pro &copy; 2023 | Все проверки выполняются с соблюдением конфиденциальности</p>
                <p>Внимание: Этот инструмент предназначен только для легального использования в целях безопасности</p>
            </div>
        </div>
    </footer>

    <script>
        // Элементы DOM
        const tabs = document.querySelectorAll('.tab-btn');
        const tabContents = document.querySelectorAll('.tab-content');
        const checkIpBtn = document.getElementById('checkIpBtn');
        const checkAnonymityBtn = document.getElementById('checkAnonymityBtn');
        const checkFileBtn = document.getElementById('checkFileBtn');
        const selectFileBtn = document.getElementById('selectFileBtn');
        const fileInput = document.getElementById('fileInput');
        const checkSecurityBtn = document.getElementById('checkSecurityBtn');
        const checkWhoisBtn = document.getElementById('checkWhoisBtn');
        const checkOwnerBtn = document.getElementById('checkOwnerBtn');
        const checkDnsBtn = document.getElementById('checkDnsBtn');
        const scanPortsBtn = document.getElementById('scanPortsBtn');
        const geolocationBtn = document.getElementById('geolocationBtn');
        const checkSslBtn = document.getElementById('checkSslBtn');
        const pingBtn = document.getElementById('pingBtn');
        const convertIpBtn = document.getElementById('convertIpBtn');
        const resultsSection = document.getElementById('resultsSection');
        const resultsContent = document.getElementById('resultsContent');
        const resultsTitle = document.getElementById('resultsTitle');
        const progressContainer = document.getElementById('progressContainer');
        const progressBar = document.getElementById('progressBar');
        const copyResultsBtn = document.getElementById('copyResultsBtn');
        const saveResultsBtn = document.getElementById('saveResultsBtn');
        const shareResultsBtn = document.getElementById('shareResultsBtn');
        const clearHistoryBtn = document.getElementById('clearHistoryBtn');
        const exportHistoryBtn = document.getElementById('exportHistoryBtn');
        const historyContent = document.getElementById('historyContent');

        let selectedFile = null;
        let scanHistory = JSON.parse(localStorage.getItem('scanHistory')) || [];

        // Инициализация истории
        loadHistory();

        // Обработчики вкладок
        tabs.forEach(tab => {
            tab.addEventListener('click', () => {
                const tabId = tab.getAttribute('data-tab');
                
                tabs.forEach(t => t.classList.remove('active'));
                tab.classList.add('active');
                
                tabContents.forEach(content => content.classList.remove('active'));
                document.getElementById(tabId).classList.add('active');
            });
        });

        // Общие функции
        function showLoading(title, message) {
            resultsTitle.textContent = title;
            resultsContent.innerHTML = `
                <div style="text-align: center; padding: 40px;">
                    <i class="fas fa-spinner fa-spin pulse" style="font-size: 2.5rem; color: var(--secondary); margin-bottom: 20px;"></i>
                    <p style="font-size: 1.1rem; color: var(--dark);">${message}</p>
                </div>
            `;
            resultsSection.style.display = 'block';
            window.scrollTo({ top: resultsSection.offsetTop - 20, behavior: 'smooth' });
        }

        function displayResults(title, items, type = 'info') {
            resultsTitle.textContent = title;
            let html = '';
            
            items.forEach(item => {
                const statusClass = item.status ? `status-${item.status}` : '';
                html += `
                    <div class="result-item">
                        <div class="result-label">${item.label}</div>
                        <div class="result-value ${statusClass}">${item.value}</div>
                    </div>
                `;
            });
            
            resultsContent.innerHTML = html;
            resultsSection.style.display = 'block';
            window.scrollTo({ top: resultsSection.offsetTop - 20, behavior: 'smooth' });
            
            // Сохраняем в историю
            saveToHistory(title, items, type);
        }

        function saveToHistory(title, items, type) {
            const historyItem = {
                id: Date.now(),
                title: title,
                items: items,
                type: type,
                timestamp: new Date().toLocaleString('ru-RU'),
                date: new Date().toISOString()
            };
            
            scanHistory.unshift(historyItem);
            if (scanHistory.length > 50) {
                scanHistory = scanHistory.slice(0, 50);
            }
            
            localStorage.setItem('scanHistory', JSON.stringify(scanHistory));
            loadHistory();
        }

        function loadHistory() {
            if (scanHistory.length === 0) {
                historyContent.innerHTML = `
                    <div style="text-align: center; padding: 40px; color: var(--gray);">
                        <i class="fas fa-history" style="font-size: 3rem; margin-bottom: 20px;"></i>
                        <p>История проверок пуста</p>
                        <p>Выполните первую проверку, и она появится здесь</p>
                    </div>
                `;
                return;
            }
            
            let html = '';
            scanHistory.forEach(item => {
                const icon = getIconByType(item.type);
                html += `
                    <div class="history-item" onclick="loadHistoryItem(${item.id})" style="cursor: pointer;">
                        <div style="display: flex; justify-content: space-between; margin-bottom: 10px;">
                            <strong><i class="${icon}"></i> ${item.title}</strong>
                            <span style="font-size: 0.8rem; color: var(--gray);">${item.timestamp}</span>
                        </div>
                        <div style="font-size: 0.9rem; color: var(--dark);">
                            ${item.items.slice(0, 2).map(i => `<div>${i.label}: ${i.value}</div>`).join('')}
                            ${item.items.length > 2 ? '<div>...</div>' : ''}
                        </div>
                    </div>
                `;
            });
            
            historyContent.innerHTML = html;
        }

        function getIcon
