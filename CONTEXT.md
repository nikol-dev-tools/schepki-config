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
cd /home/ubuntu && git clone https://nikol-dev-tools:ТОКЕН@github.com/nikol-dev-tools/schepki-config.git 2>/dev/null || (cd schepki-config && git pull)
cd /home/ubuntu/schepki-config
git remote set-url origin "https://nikol-dev-tools:ТОКЕН@github.com/nikol-dev-tools/schepki-config.git"
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
| **Гайд по публикации** | `PUBLISHING_GUIDE.md` в этом репо — пошаговая инструкция для Chrome Web Store |

### Как работает Remote Config:
- Все расширения при запуске тянут `config.json` с GitHub (кэш 6 часов).
- Если GitHub недоступен — используются fallback-значения внутри `remote-config.js`.
- Ссылка на донат `buymeacoffee.com/nikoltools` уже прописана и **протестирована в боевом режиме**.
- GEO-оверрайды: для Индии (IN) и Бразилии (BR) — crypto_btc (пока заглушка).

---

## 4. Статус расширений (на 22 марта 2026)

**Легенда статусов:** 🟢 Live | 🟡 In Review | 🔵 Ready to Upload | 🔴 Rejected | ⚪ Planned

**Легенда фич:** ✅ Есть | ❌ Нет | 🔄 Планируется

### Таблица продуктов

| # | Расширение | Статус | Store ID |
|---|---|---|---|
| 1 | **Pomodoro Timer** | 🟡 In Review | Ожидается |
| 2 | **Breathing Timer — Calm & Focus** | 🟢 Live | `oplkicaedpgnccocfflaakmkefgeepbd` |
| 3 | **Tab Limiter — Stay Focused** | 🔵 Ready to Upload | После публикации |
| 4 | **Quick Notes** | ⚪ Planned | — |

> **Coin Flip** — тестовая версия, нигде не публиковалась, в работе не используется. Упоминать не нужно.

### Таблица фич по продуктам

| Фича | Pomodoro Timer | Breathing Timer | Tab Limiter | Quick Notes |
|---|---|---|---|---|
| **Manifest V3** | ✅ | ✅ | ✅ | ⚪ |
| **Remote Config (GitHub)** | ✅ | ✅ | ✅ | ⚪ |
| **GA4 аналитика** | ✅ | ✅ | ✅ | ⚪ |
| **Событие «первый запуск»** | ❌ | ❌ | ✅ | ⚪ |
| **Use count (счётчик запусков)** | ❌ | ❌ | ✅ | ⚪ |
| **UTM-параметры в доната-ссылке** | ❌ | ❌ | ✅ | ⚪ |
| **Донат-баннер (Buy Me a Coffee)** | ✅ | ✅ | ✅ | ⚪ |
| **Задержка баннера (3 запуска)** | ❌ | ❌ | ✅ | ⚪ |
| **Rate Us (запрос оценки)** | ❌ | ❌ | ✅ (после 10 исп.) | ⚪ |
| **i18n (мультиязычность)** | ❌ | ❌ | ✅ EN/DE/FR/ES/PT | ⚪ |
| **GEO-оверрайды (IN, BR)** | ✅ | ✅ | ✅ | ⚪ |
| **Live badge на иконке** | ❌ | ❌ | ✅ (счётчик вкладок) | ⚪ |
| **Toggle вкл/выкл** | ❌ | ❌ | ✅ | ⚪ |
| **Privacy Policy ссылка** | ✅ | ✅ | ✅ | ⚪ |
| **Промо 1280x800** | ✅ | ✅ | ✅ | ⚪ |
| **Промо 440x280** | ✅ | ✅ | ✅ | ⚪ |
| **Иконки 16/32/48/128px** | ✅ | ✅ | ✅ | ⚪ |

> **Приоритет при следующем обновлении Pomodoro и Breathing Timer:** добавить первый запуск, UTM, use count, задержку баннера, Rate Us, i18n — сделать одним обновлением сразу для обоих.

---

## 5. Boilerplate — как использовать для новых расширений

1. Клонировать: `gh repo clone nikol-dev-tools/schepki-boilerplate new-extension-name`
2. В `popup.js` заменить `REPLACE_WITH_EXTENSION_ID` на ключ (например, `quick_notes`).
3. Добавить новый ключ в `config.json` в репо `schepki-config`.
4. Написать логику в секции `STEP 3: YOUR EXTENSION LOGIC HERE` в `popup.js`.
5. **НЕ трогать** `remote-config.js` и `analytics.js` — они работают идеально.

### Стандарт архитектуры v2.0 (Tab Limiter и все последующие):
- ✅ Событие «первый запуск» в GA4
- ✅ UTM-параметры в ссылке на донат (`?utm_source=EXTENSION_ID&utm_medium=extension`)
- ✅ Задержка донат-баннера (показывать с 3-го запуска)
- ✅ Rate Us после 10 использований
- ✅ i18n через `navigator.language` (EN + 4 языка минимум)
- ✅ Версия расширения в каждом GA4-событии
- ✅ Use count для поведенческой аналитики

---

## 6. Текущие приоритеты

### Приоритет 1 — Загрузить Tab Limiter в Chrome Web Store
- ZIP-архив `tab-limiter-v1.0.0.zip` готов к загрузке.
- Гайд по заполнению всех полей: `PUBLISHING_GUIDE.md` в этом репо.
- После публикации: заменить `REPLACE_WITH_TAB_LIMITER_ID_AFTER_PUBLISH` в `config.json`.

### Приоритет 2 — Когда одобрят Pomodoro и Tab Limiter
- Вписать их реальные `store_url` в `config.json`.
- Сделать одно обновление для Breathing Timer и Pomodoro: UTM + Rate Us + первый запуск + i18n.

### Приоритет 3 — Следующая щепка
- Кандидат: **Subscription Reminder** (напоминание об отмене триала).
- Рынок: США / Канада. Аудитория: все кто пользуется SaaS-сервисами.

### Стратегия:
- Сначала строим пачку из 5+ расширений, потом полируем все разом.
- Обновления живых расширений не трогаем пока нет весомой причины — риск повторной модерации.
- Предупреждение «Будьте осторожны» при установке — это норма для новых расширений, проходит само после ~100 установок и нескольких недель активности.

---

## 7. Правила работы для Manus

1. **Всегда используй архитектуру v2.0** при создании новых расширений (см. раздел 5).
2. **Не трогай** логику Remote Config и GA4 в бойлерплейте — она работает.
3. **Обновляй статусы:** Если пользователь говорит, что расширение одобрили — обнови таблицу фич (🟡 → 🟢) и вставь `store_url` в `config.json`.
4. **Обновляй таблицу фич** при каждом создании нового расширения или обновлении существующего.
5. **Стиль общения:** Пользователь — CEO без технического опыта. Объясняй всё просто, пошагово.
6. **При публикации** всегда готовь промо-материалы: иконки 128×128, скриншоты 1280×800, промо-баннер 440×280 + SEO-описание для US рынка на английском. Все данные для заполнения стора — в `PUBLISHING_GUIDE.md`.
7. **В конце каждого диалога** — обновлять этот файл `CONTEXT.md` и пушить на GitHub.

---

## 8. История изменений

### 22 марта 2026 (вечер)
- Добавлен `PUBLISHING_GUIDE.md` — постоянный гайд по публикации расширений в Chrome Web Store.
- Добавлена детальная таблица фич по всем продуктам (раздел 4).
- **Tab Limiter — Stay Focused** полностью разработан, готов к загрузке.
  - Архитектура v2.0: GA4 (первый запуск, use count, tab blocked), Remote Config (UTM, GEO), Rate Us (после 10 использований), i18n (EN/DE/FR/ES/PT), toggle вкл/выкл, live badge на иконке.
  - ZIP: `tab-limiter-v1.0.0.zip` (35KB, 13 файлов).
  - Промо: `promo_1280x800.png`, `promo_440x280.png`, иконки 16/32/48/128px.
  - После публикации: заменить `REPLACE_WITH_TAB_LIMITER_ID_AFTER_PUBLISH` в `config.json`.

### 22 марта 2026 (утро)
- **Breathing Timer — Calm & Focus** одобрен Chrome Web Store 🎉 → статус 🟢 Live.
- Store ID: `oplkicaedpgnccocfflaakmkefgeepbd`. `config.json` обновлён с реальным store_url.
- Обсуждены архитектурные улучшения для следующих расширений.
- Принята стратегия: сначала набрать 5+ расширений, потом полировать все разом.

### 21 марта 2026
- Создан GitHub аккаунт `nikol-dev-tools`.
- Созданы репо `schepki-config` и `schepki-boilerplate`.
- Remote Config и GA4 настроены и протестированы в боевом режиме.
- Buy Me a Coffee + Stripe подключены.
- Pomodoro Timer и Breathing Timer отправлены на модерацию.
- Настроен PAT токен для пуша из Manus.
