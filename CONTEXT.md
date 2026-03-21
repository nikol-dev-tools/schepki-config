# 🪵 Мастер-контекст проекта «Щепки» (Micro-SaaS Empire)

> **ВНИМАНИЕ ДЛЯ ИИ:** Прочитай этот файл целиком. Затем **сразу восстанови доступ к GitHub** по инструкции в разделе 0 — и приступай к работе без лишних вопросов о том, что уже сделано.

---

## 0. Восстановление доступа к GitHub (первое действие в новом диалоге)

После прочтения этого файла выполни в shell:

```bash
git config --global user.email "kolesnikov.nikol@gmail.com"
git config --global user.name "nikol-dev-tools"
```

Попроси пользователя прислать GitHub PAT токен (он начинается с `ghp_`, хранится в файле `SCHEPKI_TOKEN.doc`).

После получения токена выполни:
```bash
git remote set-url origin "https://nikol-dev-tools:ТОКЕН_ОТ_ПОЛЬЗОВАТЕЛЯ@github.com/nikol-dev-tools/schepki-config.git"
```

---

## 1. Суть проекта

Пользователь (CEO, без технического опыта) создаёт портфель из 30+ простых, атомарных браузерных расширений («щепок») для рынка США / Канады / Европы.

- **Монетизация:** Донаты (Buy Me a Coffee) + в будущем подписки / реклама.
- **Инфраструктура:** Единая система управления (Remote Config) для всех расширений.
- **Аналитика:** Единый счётчик GA4 для отслеживания всех установок и активности.
- **Технологии:** Только Vanilla JS, HTML, CSS (Manifest V3). Никаких фреймворков (React/Vue).
- **Роль Manus:** CTO — весь код, архитектура, автоматизация. Объяснять всё простым языком.

---

## 2. Ключевые доступы и аккаунты

| Сервис | Данные |
|---|---|
| **Основной Email** | `kolesnikov.nikol@gmail.com` |
| **Рабочий Email (сторы)** | `nikol.dev.tools@gmail.com` |
| **GitHub аккаунт** | `nikol-dev-tools` |
| **GitHub PAT (запись)** | Хранится у пользователя в файле `SCHEPKI_TOKEN.doc` — попроси прислать в начале диалога |
| **Google Analytics 4** | Measurement ID: `G-3ZKRBK0TBV` |
| **GA4 API Secret** | В `analytics.js` стоит заглушка `schepki_secret_v1` — заменить на реальный из GA4 Dashboard |
| **Buy Me a Coffee** | [buymeacoffee.com/nikoltools](https://buymeacoffee.com/nikoltools) — Stripe подключён на Mykola Kolesnykov, Кипр |
| **Chrome Developer Dashboard** | Зарегистрирован на основной email, взнос $5 оплачен |

---

## 3. Инфраструктура (Уже настроено и работает)

| Компонент | Ссылка / Детали |
|---|---|
| **GitHub Config Repo** | [github.com/nikol-dev-tools/schepki-config](https://github.com/nikol-dev-tools/schepki-config) |
| **GitHub Boilerplate Repo** | [github.com/nikol-dev-tools/schepki-boilerplate](https://github.com/nikol-dev-tools/schepki-boilerplate) |
| **Remote Config URL** | `https://raw.githubusercontent.com/nikol-dev-tools/schepki-config/main/config.json` |
| **Privacy Policy** | [nikol-dev-tools.github.io/schepki-config/privacy.html](https://nikol-dev-tools.github.io/schepki-config/privacy.html) |

### Как работает Remote Config:
- Все расширения при запуске тянут `config.json` с GitHub (кэш 6 часов).
- Если GitHub недоступен — используются fallback-значения внутри `remote-config.js`.
- Ссылка на донат `buymeacoffee.com/nikoltools` уже прописана и **протестирована в боевом режиме**.
- GEO-оверрайды: для Индии (IN) и Бразилии (BR) — crypto_btc (пока заглушка).

---

## 4. Статус расширений (на 21 марта 2026)

| # | Расширение | Описание | Статус | Store URL | Примечания |
|---|---|---|---|---|---|
| 1 | **Pomodoro Timer** | Таймер фокуса по технике Помодоро | 🟡 In Review | Ожидается после аппрува | GA4 ✅ Remote Config ✅ |
| 2 | **Breathing Timer** | Таймер дыхательных упражнений (4-7-8) | 🟡 In Review | Ожидается после аппрува | GA4 ✅ Remote Config ✅ |
| 3 | **Coin Flip** | Подбрасывание монетки — быстрое решение | 🟡 In Review | Ожидается после аппрува | GA4 ✅ Remote Config ✅ |
| 4 | **Tab Limiter** | Ограничение количества вкладок | ⚪ Planned | — | — |
| 5 | **Quick Notes** | Быстрые заметки на новой вкладке | ⚪ Planned | — | — |

**Легенда:** 🟢 Live | 🟡 In Review | 🔵 In Development | ⚪ Planned | 🔴 Rejected

> Когда расширение одобряют — обновить `store_url` в `config.json` и поменять статус (🟡 → 🟢).

---

## 5. Boilerplate — как использовать для новых расширений

1. Клонировать: `gh repo clone nikol-dev-tools/schepki-boilerplate new-extension-name`
2. В `popup.js` заменить `REPLACE_WITH_EXTENSION_ID` на ключ (например, `tab_limiter`).
3. Добавить новый ключ в `config.json` в репо `schepki-config`.
4. Написать логику в секции `STEP 3: YOUR EXTENSION LOGIC HERE` в `popup.js`.
5. **НЕ трогать** `remote-config.js` и `analytics.js` — они работают идеально.

---

## 6. Планы на следующий диалог (приоритеты)

### Приоритет 1 — Новое расширение (4-я щепка для Chrome)
- Придумать и создать ещё одно атомарное расширение для рынка **США / Канады**.
- Три расширения одновременно на проверке — это нормально, Chrome Web Store не ограничивает.
- Фокус: простая идея, высокий поисковый спрос, минимальный код.

### Приоритет 2 — Кроссбраузерность
- Опубликовать существующие расширения в **Firefox Add-ons** и **Opera Add-ons**.
- Код на Manifest V3 / WebExtensions API уже совместим с Firefox и Opera — минимальные правки.
- **Edge — пропустить пока** (неудобный процесс публикации, были трудности на практике).

---

## 7. Правила работы для Manus

1. **Всегда используй `schepki-boilerplate`** при создании новых расширений.
2. **Не трогай** логику Remote Config и GA4 в бойлерплейте — она работает.
3. **Обновляй статусы:** Если пользователь говорит, что расширение одобрили — обнови `README.md` (🟡 → 🟢) и вставь `store_url` в `config.json`.
4. **Стиль общения:** Пользователь — CEO без технического опыта. Объясняй всё просто, пошагово.
5. **При публикации** всегда готовь промо-материалы: иконки 128×128, скриншоты 1280×800, промо-баннер 440×280 + SEO-описание для US рынка на английском.
6. **В конце каждого диалога** — обновлять этот файл `CONTEXT.md` и пушить на GitHub.

---

## 8. Последнее обновление

**Дата:** 21 марта 2026

**Что сделано сегодня:**
- Создан GitHub аккаунт `nikol-dev-tools`.
- Создан репо `schepki-config` с Remote Config, Privacy Policy и дашбордом.
- Создан репо `schepki-boilerplate` с полным шаблоном (GA4 + Remote Config + донат-баннер).
- Remote Config протестирован в боевом режиме — ссылка на Buy Me a Coffee подтягивается корректно.
- Buy Me a Coffee настроен, Stripe подключён, донаты работают.
- Pomodoro Timer, Breathing Timer и Coin Flip отправлены на модерацию в Chrome Web Store.
- Создан `CONTEXT.md` для сохранения контекста между диалогами.
- Настроен PAT токен с правами `repo` для пуша из Manus.
- Обсуждены планы на следующий день: новая щепка + выход на Firefox и Opera.
