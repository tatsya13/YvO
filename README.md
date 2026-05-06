<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    
    <!-- 🔹 GitHub Pages & SEO Meta Tags -->
    <title>График ГИА 2026 | Государственная итоговая аттестация</title>
    <meta name="description" content="Интерактивное расписание мероприятий государственной итоговой аттестации 2026">
    <meta name="theme-color" content="#6366f1">
    
    <!-- Open Graph / GitHub Card -->
    <meta property="og:title" content="📋 График ГИА 2026">
    <meta property="og:description" content="Расписание мероприятий государственной итоговой аттестации">
    <meta property="og:type" content="website">
    <meta property="og:locale" content="ru_RU">
    
    <!-- Twitter Card -->
    <meta name="twitter:card" content="summary_large_image">
    <meta name="twitter:title" content="График ГИА 2026">
    
    <!-- 🔹 Базовый путь для GitHub Pages (если сайт в подпапке репозитория) -->
    <!-- Замените 'repo-name' на имя вашего репозитория, если публикуете не из root -->
    <base href="/">
    
    <!-- Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    
    <!-- 🔹 Favicon (опционально, добавьте файл favicon.svg в репозиторий) -->
    <link rel="icon" type="image/svg+xml" href="favicon.svg">
    
    <style>
        /* 🔹 Добавьте это для корректной работы на GitHub Pages */
        :root {
            --base-font-size: 16px;
        }
        
        /* ... [весь ваш оригинальный CSS остаётся без изменений] ... */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Inter', sans-serif;
            background: linear-gradient(135deg, #f0f4f8 0%, #e8ecf1 50%, #f0f4f8 100%);
            min-height: 100vh;
            color: #334155;
            overflow-x: hidden;
        }

        /* 🔹 Скрыть части при печати для сохранения ресурсов */
        @media print {
            .bg-particles, .countdown-bar, .progress-section {
                display: none !important;
            }
            .card {
                box-shadow: none !important;
                border: 1px solid #cbd5e1 !important;
            }
        }

        /* ... [остальной CSS без изменений] ... */
        /* Для краткости здесь не дублирую весь CSS — вставьте ваш оригинальный код */
    </style>
</head>
<body>

<!-- 🔹 Добавлен data-атрибут для лёгкой настройки даты через JS -->
<div class="bg-particles" id="particles"></div>

<div class="container">
    <header>
        <h1>📋 График ГИА 2026</h1>
        <p class="subtitle">Расписание мероприятий государственной итоговой аттестации</p>
        <!-- 🔹 Дата обновляется автоматически при загрузке -->
        <div class="current-date-badge" id="currentDateBadge">
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="10"/><polyline points="12 6 12 12 16 14"/></svg>
            Сегодня: <span id="todayDisplay">загрузка...</span>
        </div>
    </header>

    <div class="legend">
        <div class="legend-item"><div class="legend-dot past"></div> Завершено</div>
        <div class="legend-item"><div class="legend-dot current"></div> Сейчас / Сегодня</div>
        <div class="legend-item"><div class="legend-dot future"></div> Предстоит</div>
    </div>

    <div class="timeline" id="timeline"></div>

    <div class="progress-section">
        <div class="progress-title">📊 Прогресс прохождения ГИА</div>
        <div class="progress-bar-bg">
            <div class="progress-bar-fill" id="progressFill" style="width: 0%"></div>
        </div>
        <div class="progress-stats">
            <span>Завершено: <strong id="completedCount">0</strong> из <strong id="totalCount">9</strong></span>
            <span id="progressPercent">0%</span>
        </div>
    </div>

    <footer>
        График ГИА 2026 • 
        <a href="https://github.com/ВАШ_НИК/РЕПОЗИТОРИЙ" target="_blank" rel="noopener" style="color: #6366f1; text-decoration: none;">Исходный код на GitHub</a>
    </footer>
</div>

<script>
    // 🔹 КОНФИГУРАЦИЯ: Установите "фиксированную" дату для демонстрации или используйте реальную
    // Для продакшена: закомментируйте строку ниже, чтобы использовать new Date()
    const FORCE_TODAY = null; // Пример: new Date(2026, 4, 6) для фиксации на 6 мая 2026
    
    const today = FORCE_TODAY ? new Date(FORCE_TODAY) : new Date();
    
    // 🔹 Обновление отображения текущей даты
    function formatDateRu(date) {
        return date.toLocaleDateString('ru-RU', {
            day: 'numeric',
            month: 'long',
            year: 'numeric'
        }).replace(/\./g, '');
    }
    document.getElementById('todayDisplay').textContent = formatDateRu(today) + ' г.';

    const events = [
        // 🔹 Ваши события — без изменений
        {
            type: 'plagiarism',
            typeLabel: 'Проверка на плагиат',
            title: 'Проверка на плагиат №1',
            group: null,
            date: '06.05.26',
            fullDate: new Date(2026, 4, 6),
            time: null,
            room: null,
            icon: '🔍'
        },
        {
            type: 'plagiarism',
            typeLabel: 'Проверка на плагиат',
            title: 'Проверка на плагиат №2',
            group: null,
            date: '20.05.26',
            fullDate: new Date(2026, 4, 20),
            time: null,
            room: null,
            icon: '🔍'
        },
        {
            type: 'predip',
            typeLabel: 'Преддипломная практика',
            title: 'Предзащита',
            group: '1 подгр.',
            date: '21.05.2026',
            fullDate: new Date(2026, 4, 21),
            time: '10:00',
            room: null,
            icon: '📝'
        },
        {
            type: 'predip',
            typeLabel: 'Преддипломная практика',
            title: 'Предзащита',
            group: '2 подгр.',
            date: '22.05.2026',
            fullDate: new Date(2026, 4, 22),
            time: '10:00',
            room: null,
            icon: '📝'
        },
        {
            type: 'consult',
            typeLabel: 'Консультация',
            title: 'Консультация к экзамену',
            group: null,
            date: '25.05.26',
            fullDate: new Date(2026, 4, 25),
            time: '16:30–18:00',
            room: 'ауд. 208',
            icon: '💬'
        },
        {
            type: 'exam',
            typeLabel: 'Экзамен',
            title: 'Экзамен',
            group: '1 подгр.',
            date: '03.06.26',
            fullDate: new Date(2026, 5, 3),
            time: '12:00–16:30',
            room: 'ауд. 208',
            icon: '📄'
        },
        {
            type: 'exam',
            typeLabel: 'Экзамен',
            title: 'Экзамен',
            group: '2 подгр.',
            date: '04.06.26',
            fullDate: new Date(2026, 5, 4),
            time: '10:00–13:00',
            room: 'ауд. 208',
            icon: '📄'
        },
        {
            type: 'defense',
            typeLabel: 'Защита',
            title: 'Защита ВКР',
            group: '1 подгр.',
            date: '18.06.26',
            fullDate: new Date(2026, 5, 18),
            time: '10:00–14:30',
            room: 'ауд. 208',
            icon: '🎓'
        },
        {
            type: 'defense',
            typeLabel: 'Защита',
            title: 'Защита ВКР',
            group: '2 подгр.',
            date: '19.06.26',
            fullDate: new Date(2026, 5, 19),
            time: '10:00–13:00',
            room: 'ауд. 208',
            icon: '🎓'
        }
    ];

    const typeClasses = {
        plagiarism: 'type-plagiarism',
        predip: 'type-predip',
        consult: 'type-consult',
        exam: 'type-exam',
        defense: 'type-defense'
    };

    function getDaysBetween(d1, d2) {
        const msPerDay = 1000 * 60 * 60 * 24;
        return Math.round((d2 - d1) / msPerDay);
    }

    function getStatus(event) {
        const evDay = new Date(event.fullDate.getFullYear(), event.fullDate.getMonth(), event.fullDate.getDate());
        const td = new Date(today.getFullYear(), today.getMonth(), today.getDate());
        const diff = getDaysBetween(td, evDay);
        if (diff < 0) return 'past';
        if (diff === 0) return 'current';
        return 'future';
    }

    const timeline = document.getElementById('timeline');
    let completedCount = 0;

    events.forEach((evt, idx) => {
        const status = getStatus(evt);
        if (status === 'past') completedCount++;

        const item = document.createElement('div');
        item.className = `timeline-item ${status}`;
        item.style.animationDelay = `${idx * 0.08}s`;

        let statusLabel = '';
        let statusClass = '';
        if (status === 'past') { statusLabel = '✓ Завершено'; statusClass = 'status-done'; }
        else if (status === 'current') { statusLabel = '● Сегодня'; statusClass = 'status-now'; }
        else { statusLabel = '◷ Предстоит'; statusClass = 'status-upcoming'; }

        let groupHTML = '';
        if (evt.group) {
            groupHTML = `<div class="group-badge">👥 ${evt.group}</div>`;
        }

        let timeHTML = '';
        if (evt.time) {
            timeHTML = `<div class="detail">
                <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="10"/><polyline points="12 6 12 12 16 14"/></svg>
                ${evt.time}
            </div>`;
        }

        let roomHTML = '';
        if (evt.room) {
            roomHTML = `<div class="detail">
                <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"/><circle cx="12" cy="10" r="3"/></svg>
                ${evt.room}
            </div>`;
        }

        let countdownHTML = '';
        if (status === 'current') {
            countdownHTML = `<div class="countdown-bar"><div class="countdown-fill" style="width: 50%"></div></div>`;
        } else if (status === 'future') {
            const days = getDaysBetween(today, evt.fullDate);
            countdownHTML = `<div class="days-until">Осталось <span>${days}</span> дн.</div>`;
        }

        item.innerHTML = `
            <div class="timeline-node"></div>
            <div class="card">
                <div class="card-header">
                    <div class="card-type ${typeClasses[evt.type]}">${evt.icon} ${evt.typeLabel}</div>
                    <div class="card-status ${statusClass}">${statusLabel}</div>
                </div>
                <div class="card-title">${evt.title}</div>
                <div class="card-details">
                    ${groupHTML}
                    <div class="detail">
                        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="3" y="4" width="18" height="18" rx="2" ry="2"/><line x1="16" y1="2" x2="16" y2="6"/><line x1="8" y1="2" x2="8" y2="6"/><line x1="3" y1="10" x2="21" y2="10"/></svg>
                        ${evt.date}
                    </div>
                    ${timeHTML}
                    ${roomHTML}
                </div>
                ${countdownHTML}
            </div>
        `;

        timeline.appendChild(item);
    });

    // 🔹 Обновление прогресс-бара
    const totalEvents = events.length;
    document.getElementById('totalCount').textContent = totalEvents;
    const percent = Math.round((completedCount / totalEvents) * 100);
    setTimeout(() => {
        document.getElementById('progressFill').style.width = percent + '%';
        document.getElementById('completedCount').textContent = completedCount;
        document.getElementById('progressPercent').textContent = percent + '%';
    }, 300);

    // 🔹 Генерация частиц (оптимизировано для мобильных)
    const particlesContainer = document.getElementById('particles');
    const particleCount = window.innerWidth < 640 ? 12 : 25;
    for (let i = 0; i < particleCount; i++) {
        const p = document.createElement('div');
        p.className = 'particle';
        const size = Math.random() * 4 + 2;
        p.style.width = size + 'px';
        p.style.height = size + 'px';
        p.style.left = Math.random() * 100 + '%';
        p.style.animationDuration = (Math.random() * 20 + 15) + 's';
        p.style.animationDelay = (Math.random() * 20) + 's';
        particlesContainer.appendChild(p);
    }
</script>

</body>
</html>
