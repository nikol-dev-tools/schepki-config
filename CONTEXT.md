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
| **GA4 API Secret** | ✅ Реальный: `TaFzQ3cgRP25jG3BSYtASA` (псевдоним: schepki_prod, создан 22.03.2026). Вписан во все analytics.js |
| **Buy Me a Coffee** | [buymeacoffee.com/nikoltools](https://buymeacoffee.com/nikoltools) — Stripe подключён на Mykola Kolesnykov, Кипр |
| **Chrome Developer Dashboard** | Зарегистрирован на основной email, взнос $5 оплачен |

---

## 3. Инфраструктура (Уже настроено и работает)

| Компонент | Ссылка / Детали |
|---|---|
| **GitHub Config Repo** | [github.com/nikol-dev-tools/schepki-config](https://github.com/nikol-dev-tools/schepki-config) |
| **GitHub Boilerplate Repo** | [github.com/nikol-dev-tools/schepki-boilerplate](https://github.com/nikol-dev-tools/schepki-boilerplate) — **v2.0** (GA4, i18n, Rate Us, UTM, donate delay) |
| **GitHub Tab Limiter Repo** | [github.com/nikol-dev-tools/tab-limiter](https://github.com/nikol-dev-tools/tab-limiter) |
| **GitHub Breathing Timer Repo** | [github.com/nikol-dev-tools/breathing-timer](https://github.com/nikol-dev-tools/breathing-timer) (ветка: master) |
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
| 3 | **Tab Limiter — Stay Focused** | 🟡 In Review | `clpenohkhonpjaclhcedbldknallghmn` |
| 4 | **Quick Notes** | ⚪ Planned | — |

> **Coin Flip** — тестовая версия, нигде не публиковалась, в работе не используется. Упоминать не нужно.

### Таблица фич по продуктам (что делает каждая фича и как управлять)

| Фича | Pomodoro Timer | Breathing Timer | Tab Limiter | Quick Notes |

**Расшифровка фич:**
- **Remote Config** — расширение при запуске тянет `config.json` с GitHub (кэш 6ч). Позволяет менять ссылку на донат, включать/выключать баннер, менять порог Rate Us — **без обновления расширения в сторе**. Меняется в `schepki-config/config.json`.
- **Событие «первый запуск»** — при первой установке отправляет событие `first_open` в GA4. Позволяет видеть реальное число новых пользователей (не просто открытий попапа).
- **Use count** — считает сколько раз пользователь открыл попап. Используется для Rate Us и задержки баннера.
- **UTM-параметры** — к ссылке buymeacoffee добавляется `?utm_source=tab_limiter&utm_medium=extension`. Позволяет видеть в аналитике откуда именно пришёл донатер.
- **Задержка баннера** — донат-баннер не показывается первые 3 открытия попапа. Снижает раздражение новых пользователей, повышает retention.
- **Rate Us** — после N открытий попапа показывает мягкое предложение оставить отзыв в сторе. Порог задаётся в `config.json` → `rate_us_after_opens` (сейчас: 10). Ссылка — `store_url` в config.json.
- **i18n** — автоматически определяет язык браузера (`navigator.language`) и показывает текст на нужном языке. Добавить язык = добавить объект в `popup.js` → `translations`.
- **Live badge** — на иконке расширения в тулбаре всегда видно текущее число открытых вкладок. Обновляется в реальном времени.
- **Toggle вкл/выкл** — кнопка временно отключает лимит без удаления расширения. Состояние сохраняется в `chrome.storage.local`.
- **Уведомления (push)** — всплывающие системные уведомления через `chrome.notifications`. Требует разрешение `notifications` в manifest. Планируется в следующих расширениях.
- **Напоминания (alarms)** — `chrome.alarms` для фоновых задач. В Tab Limiter — для аналитики. В будущем — для напоминаний типа «пора сделать перерыв».

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
| **Уведомления (push)** | ❌ | ❌ | ❌ | ⚪ |
| **Напоминания (alarms)** | ❌ | ❌ | ✅* | ⚪ |
| **i18n (мультиязычность)** | ❌ | ❌ | ✅ EN/DE/FR/ES/PT | ⚪ |
| **GEO-оверрайды (IN, BR)** | ✅ | ✅ | ✅ | ⚪ |
| **Live badge на иконке** | ❌ | ❌ | ✅ (счётчик вкладок) | ⚪ |
| **Toggle вкл/выкл** | ❌ | ❌ | ✅ | ⚪ |
| **Privacy Policy ссылка** | ✅ | ✅ | ✅ | ⚪ |
| **Промо 1280x800** | ✅ | ✅ | ✅ | ⚪ |
| **Промо 440x280** | ✅ | ✅ | ✅ | ⚪ |
| **Иконки 16/32/48/128px** | ✅ | ✅ | ✅ | ⚪ |

> *В Tab Limiter alarms используется для аналитики, не для пользовательских напоминаний.

> **Приоритет при следующем обновлении Pomodoro и Breathing Timer:** добавить первый запуск, UTM, use count, задержку баннера, Rate Us, i18n — сделать одним обновлением сразу для обоих.

---

## 5. Boilerplate — как использовать для новых расширений

1. Клонировать: `gh repo clone nikol-dev-tools/schepki-boilerplate new-extension-name`
2. В `popup.js` заменить `REPLACE_WITH_EXTENSION_ID` на ключ (например, `quick_notes`).
3. Добавить новый ключ в `config.json` в репо `schepki-config`.
4. Написать логику в секции `STEP 3: YOUR EXTENSION LOGIC HERE` в `popup.js`.
5. **НЕ трогать** `remote-config.js` и `analytics.js` — они работают идеально.

### Стандарт архитектуры v2.0 (Бойлерплейт обновлён, Tab Limiter и все последующие):
- ✅ Событие «первый запуск» в GA4
- ✅ UTM-параметры в ссылке на донат (`?utm_source=EXTENSION_ID&utm_medium=extension`)
- ✅ Задержка донат-баннера (показывать с 3-го запуска)
- ✅ Rate Us после 10 использований
- ✅ i18n через `navigator.language` (EN + 4 языка минимум)
- ✅ Версия расширения в каждом GA4-событии
- ✅ Use count для поведенческой аналитики

---

## 6. Текущие приоритеты

### ⚠️ TODO — отложенные задачи (MUST DO при следующем обновлении)

1. **Breathing Timer + Tab Limiter** — обновить ZIP одним пакетом:
   - Добавить `extension_id` и `extension_version` в каждый вызов `trackEvent()` в `popup.js` (GA4 не видит данные без этого)
   - Перенести все фичи Tab Limiter v2 в Breathing Timer (и Pomodoro): UTM, Rate Us, first_open, use count, i18n, задержка баннера
   - Добавить новые иконки v3 в ZIP Breathing Timer
   - **Делать одним пакетом** — не гонять на проверку несколько раз

2. **Tab Limiter** — дождаться одобрения, затем сразу обновить ZIP (см. п. 1)

3. **Pomodoro Timer** — дождаться одобрения, вписать store_url в config.json

### Приоритет 1 — Tab Limiter загружен, ждём одобрения ✅
- Tab Limiter отправлен на модерацию 22 мар 2026.
- Store ID: `clpenohkhonpjaclhcedbldknallghmn`.
- `config.json` уже обновлён с реальным store_url.

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

## 9. Как получить реальный GA4 API Secret (один раз для всех расширений)

Аналитика сейчас не работает — во всех расширениях стоят заглушки. Чтобы включить сбор данных:

1. Открой [analytics.google.com](https://analytics.google.com)
2. Выбери свой аккаунт → **Admin** (шестерёнка внизу слева)
3. В разделе **Property** → **Data Streams**
4. Кликни на свой поток (Extension)
5. Прокрути вниз → **Measurement Protocol API secrets** → **Create**
6. Дай любое название (например `schepki_prod`) → скопируй полученный секрет
7. Отправь секрет Manus — он обновит `analytics.js` во всех расширениях сразу

**Где смотреть аналитику:**
- [analytics.google.com](https://analytics.google.com) → свой аккаунт
- Раздел **Reports** → **Realtime** — видеть активных пользователей за последние 30 мин
- Раздел **Reports** → **Engagement** → **Events** — все события (popup_open, first_open, donate_click, tab_blocked)
- Раздел **Reports** → **Acquisition** — откуда приходят пользователи

---

## 8. История изменений

### 22 марта 2026 (день)
- **Иконки v3** для Breathing Timer: тёмный фон `#0a0e1a`, неоновый лотос (cyan/teal) — единый стиль с баннерами. Загружены на GitHub.
- **GA4 Custom Dimensions** настроены в GA4: `extension_id` и `extension_version` (скоп — Event). Теперь в отчётах можно фильтровать по каждому расширению отдельно.
- **DASHBOARD.md** создан — единый навигационный док со всеми ссылками проекта.
- **PUBLISHING_GUIDE.md** обновлён: стандарт иконок Schepki (цвета, стиль, промпт-шаблон), раздел про обновление ZIP vs Store listing.
- **Breathing Timer** отправлен на повторную модерацию с новой иконкой (Store listing).

### 22 марта 2026 (ночь)
- **GA4 API Secret** получен и вписан во все расширения: `TaFzQ3cgRP25jG3BSYtASA` (псевдоним: schepki_prod). Аналитика активна во всех расширениях.
- **Boilerplate v2.0** создан и загружен на GitHub: [schepki-boilerplate](https://github.com/nikol-dev-tools/schepki-boilerplate). Фичи: GA4 с реальным секретом, i18n (EN/DE/FR/ES/PT), Rate Us, UTM, задержка баннера, Remote Config.

### 22 марта 2026 (вечер)
- Добавлен `PUBLISHING_GUIDE.md` — постоянный гайд по публикации расширений в Chrome Web Store.
- Добавлена детальная таблица фич по всем продуктам (раздел 4).
- **Tab Limiter — Stay Focused** полностью разработан, готов к загрузке.
  - Архитектура v2.0: GA4 (первый запуск, use count, tab blocked), Remote Config (UTM, GEO), Rate Us (после 10 использований), i18n (EN/DE/FR/ES/PT), toggle вкл/выкл, live badge на иконке.
  - ZIP: `tab-limiter-v1.0.0.zip` (35KB, 13 файлов).
  - Промо: `promo_1280x800.png`, `promo_440x280.png`, иконки 16/32/48/128px.
  - Store ID: `clpenohkhonpjaclhcedbldknallghmn`. `config.json` обновлён.
  - Код загружен на GitHub: [nikol-dev-tools/tab-limiter](https://github.com/nikol-dev-tools/tab-limiter).

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
