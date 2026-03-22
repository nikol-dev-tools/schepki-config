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

### Как работает Remote Config:
- Все расширения при запуске тянут `config.json` с GitHub (кэш 6 часов).
- Если GitHub недоступен — используются fallback-значения внутри `remote-config.js`.
- Ссылка на донат `buymeacoffee.com/nikoltools` уже прописана и **протестирована в боевом режиме**.
- GEO-оверрайды: для Индии (IN) и Бразилии (BR) — crypto_btc (пока заглушка).

---

## 4. Статус расширений (на 22 марта 2026)

| # | Расширение | Точное название в сторе | Статус | Store ID / URL | Примечания |
|---|---|---|---|---|---|
| 1 | **Pomodoro Timer** | Pomodoro Timer | 🟡 In Review | Ожидается после аппрува | GA4 ✅ Remote Config ✅ |
| 2 | **Breathing Timer** | Breathing Timer — Calm & Focus | 🟢 Live | ID: `oplkicaedpgnccocfflaakmkefgeepbd` | GA4 ✅ Remote Config ✅ |
| 3 | **Tab Limiter** | Tab Limiter — Stay Focused | 🔵 Ready to Upload | ZIP готов | GA4 ✅ Remote Config ✅ UTM ✅ Rate Us ✅ i18n ✅ |
| 4 | **Quick Notes** | — | ⚪ Planned | — | — |

> **Coin Flip** — тестовая версия, нигде не публиковалась, в работе не используется. Упоминать не нужно.

**Легенда:** 🟢 Live | 🟡 In Review | 🔵 In Development | ⚪ Planned | 🔴 Rejected

> Когда расширение одобряют — обновить `store_url` в `config.json` и поменять статус (🟡 → 🟢).

---

## 5. Boilerplate — как использовать для новых расширений

1. Клонировать: `gh repo clone nikol-dev-tools/schepki-boilerplate new-extension-name`
2. В `popup.js` заменить `REPLACE_WITH_EXTENSION_ID` на ключ (например, `tab_limiter`).
3. Добавить новый ключ в `config.json` в репо `schepki-config`.
4. Написать логику в секции `STEP 3: YOUR EXTENSION LOGIC HERE` в `popup.js`.
5. **НЕ трогать** `remote-config.js` и `analytics.js` — они работают идеально.

### Что добавить в следующих расширениях (архитектурные улучшения):
- **Событие «первый запуск»** — передавать в GA4 при первом открытии (знать install vs active users).
- **UTM-параметры в ссылках** — добавить `?utm_source=EXTENSION_ID` к ссылке на донат.
- **Rate Us флаг** — после N использований мягко просить оценку в сторе (через Remote Config).
- **Версия в аналитике** — передавать `version` из `manifest.json` в каждое GA4-событие.
- **Флаг показа баннера** — не показывать донат-баннер первые 3 дня (улучшает retention).
- Все эти улучшения управляются через `config.json` — обновление расширений не нужно.

---

## 6. Текущие приоритеты

### Приоритет 1 — Обновить config.json
- Вписать реальный `store_url` для Breathing Timer (ID: `oplkicaedpgnccocfflaakmkefgeepbd`).
- Когда одобрят Pomodoro — вписать его ID тоже.

### Приоритет 2 — Новое расширение (следующая щепка для Chrome)
- Придумать и создать атомарное расширение для рынка **США / Канады**.
- Фокус: простая идея, высокий поисковый спрос, минимальный код.
- Использовать boilerplate + добавить архитектурные улучшения из раздела 5.

### Приоритет 3 — Кроссбраузерность
- Опубликовать существующие расширения в **Firefox Add-ons** и **Opera Add-ons**.
- Код уже совместим — минимальные правки.
- **Edge — пропустить пока** (неудобный процесс публикации).

### Стратегия:
- Сначала строим пачку из 5+ расширений, потом полируем все разом (Rate Us, UTM и т.д.).
- Обновления живых расширений не трогаем пока нет весомой причины — риск повторной модерации.

---

## 7. Правила работы для Manus

1. **Всегда используй `schepki-boilerplate`** при создании новых расширений.
2. **Не трогай** логику Remote Config и GA4 в бойлерплейте — она работает.
3. **Обновляй статусы:** Если пользователь говорит, что расширение одобрили — обнови `README.md` (🟡 → 🟢) и вставь `store_url` в `config.json`.
4. **Стиль общения:** Пользователь — CEO без технического опыта. Объясняй всё просто, пошагово.
5. **При публикации** всегда готовь промо-материалы: иконки 128×128, скриншоты 1280×800, промо-баннер 440×280 + SEO-описание для US рынка на английском.
6. **В конце каждого диалога** — обновлять этот файл `CONTEXT.md` и пушить на GitHub.

---

## 8. История изменений

### 22 марта 2026
- **Breathing Timer — Calm & Focus** одобрен Chrome Web Store 🎉 → статус 🟢 Live.
- Store ID: `oplkicaedpgnccocfflaakmkefgeepbd`. `config.json` обновлён с реальным store_url.
- Обсуждены архитектурные улучшения для следующих расширений (первый запуск, UTM, Rate Us, версия, i18n).
- Принята стратегия: сначала набрать 5+ расширений, потом полировать все разом.
- **Tab Limiter — Stay Focused** полностью разработан, готов к загрузке в Chrome Web Store.
  - Архитектура v2.0: GA4 (первый запуск, use count, tab blocked), Remote Config (UTM, GEO), Rate Us (после 10 использований), i18n (EN/DE/FR/ES/PT), toggle вкл/выкл, live badge на иконке.
  - ZIP: `tab-limiter-v1.0.0.zip` (35KB, 13 файлов).
  - Промо: `promo_1280x800.png`, `promo_440x280.png`, иконки 16/32/48/128px.
  - После публикации: заменить `REPLACE_WITH_TAB_LIMITER_ID_AFTER_PUBLISH` в `config.json`.

### 21 марта 2026
- Создан GitHub аккаунт `nikol-dev-tools`.
- Созданы репо `schepki-config` и `schepki-boilerplate`.
- Remote Config и GA4 настроены и протестированы в боевом режиме.
- Buy Me a Coffee + Stripe подключены.
- Pomodoro Timer и Breathing Timer отправлены на модерацию.
- Настроен PAT токен для пуша из Manus.
