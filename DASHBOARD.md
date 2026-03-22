# 🗺️ Schepki Dashboard — Все ссылки и кабинеты

> Сохрани эту страницу в закладки: **[github.com/nikol-dev-tools/schepki-config/blob/main/DASHBOARD.md](https://github.com/nikol-dev-tools/schepki-config/blob/main/DASHBOARD.md)**
>
> Здесь собраны все ссылки, кабинеты и инструменты проекта. Обновляется по мере роста.

---

## 🚀 Быстрый старт — открываю новый диалог с Manus

Скажи: **«Открой CONTEXT.md из schepki-config и продолжаем»** — Manus прочитает файл и будет в курсе всего.

---

## 📦 Продукты в Chrome Web Store

| Расширение | Статус | Ссылка на страницу в сторе | Store ID |
|---|---|---|---|
| Breathing Timer | 🟢 Live | [Открыть](https://chromewebstore.google.com/detail/oplkicaedpgnccocfflaakmkefgeepbd) | `oplkicaedpgnccocfflaakmkefgeepbd` |
| Tab Limiter | 🟡 In Review | — (ещё не опубликован) | `clpenohkhonpjaclhcedbldknallghmn` |
| Pomodoro Timer | 🟡 In Review | — (ещё не опубликован) | ожидается |

---

## 🛠️ Кабинеты и инструменты

### Chrome Web Store Developer Dashboard
**[chromewebstore.google.com/u/0/developer/dashboard](https://chromewebstore.google.com/u/0/developer/dashboard)**

Что здесь делать:
- Загружать новые расширения (кнопка «New item»)
- Следить за статусом модерации (In Review / Published / Rejected)
- Смотреть статистику установок по каждому расширению
- Отвечать на отзывы пользователей
- Публиковать обновления (загрузить новый ZIP → Submit for review)

---

### Google Analytics 4
**[analytics.google.com](https://analytics.google.com)**
> Аккаунт: **Micro SaaS Empire** → Ресурс: **Schepki Extensions** (G-3ZKRBK0TBV)

Что здесь смотреть:

| Раздел | Путь | Что показывает |
|---|---|---|
| Активные сейчас | Reports → Realtime | Кто открыл расширение прямо сейчас |
| Все события | Reports → Engagement → Events | popup_open, first_launch, donation_click, tab_blocked |
| По расширению | Любой отчёт → Add filter → extension_id | Статистика отдельно по каждому плагину |
| Новые установки | Events → first_launch | Сколько новых пользователей за период |
| Доходность | Events → donation_click | Сколько кликов на донат |

Ключевые события которые мы отслеживаем:
- `first_launch` — первое открытие после установки
- `popup_open` — каждое открытие попапа
- `donation_click` — клик на кнопку доната
- `tab_blocked` — заблокированная вкладка (только Tab Limiter)

---

### Buy Me a Coffee
**[buymeacoffee.com/nikoltools](https://buymeacoffee.com/nikoltools)**

Что здесь делать:
- Смотреть поступившие донаты
- Видеть кто поддержал и сообщения от них
- Настраивать суммы и описание страницы
- Выводить деньги (Stripe → банковская карта)

---

### GitHub — все репозитории
**[github.com/nikol-dev-tools](https://github.com/nikol-dev-tools)**

| Репозиторий | Назначение | Ссылка |
|---|---|---|
| `schepki-config` | База знаний, Remote Config, документация | [Открыть](https://github.com/nikol-dev-tools/schepki-config) |
| `schepki-boilerplate` | Шаблон v2 для новых расширений | [Открыть](https://github.com/nikol-dev-tools/schepki-boilerplate) |
| `breathing-timer` | Код Breathing Timer v1.0.0 | [Открыть](https://github.com/nikol-dev-tools/breathing-timer) |
| `tab-limiter` | Код Tab Limiter v1.0.0 | [Открыть](https://github.com/nikol-dev-tools/tab-limiter) |

---

### Remote Config (config.json)
**[raw.githubusercontent.com/nikol-dev-tools/schepki-config/main/config.json](https://raw.githubusercontent.com/nikol-dev-tools/schepki-config/main/config.json)**

Что это: файл настроек который все расширения читают с GitHub каждые 6 часов. Позволяет менять поведение расширений без обновления в сторе.

Что можно менять без обновления расширения:
- `donate_url` — ссылка на донат (можно менять под акции)
- `show_donate_banner` — включить/выключить баннер доната
- `rate_us_after_opens` — через сколько открытий показывать Rate Us
- `store_url` — ссылка на страницу в сторе (для Rate Us)
- `is_active` — включить/выключить расширение полностью

---

### Privacy Policy
**[nikol-dev-tools.github.io/schepki-config/privacy.html](https://nikol-dev-tools.github.io/schepki-config/privacy.html)**

Ссылка на политику конфиденциальности — используется во всех расширениях и при публикации в Chrome Web Store.

---

## 📊 SEO и ASO — принятие решений

### Где смотреть позиции и трафик расширений

| Инструмент | Ссылка | Что показывает |
|---|---|---|
| Chrome Web Store Stats | [Developer Dashboard](https://chromewebstore.google.com/u/0/developer/dashboard) | Установки, удаления, активные пользователи |
| GA4 Acquisition | [analytics.google.com](https://analytics.google.com) → Reports → Acquisition | Откуда приходят (поиск в сторе, прямая ссылка, реферал) |
| Chrome Web Store Search | [chromewebstore.google.com/search/](https://chromewebstore.google.com/search/) | Проверить позиции по ключевым словам вручную |

### Ключевые слова по расширениям

| Расширение | Основные ключевые слова |
|---|---|
| Breathing Timer | `breathing exercise`, `box breathing`, `4-7-8 breathing`, `anxiety relief`, `calm breathing` |
| Tab Limiter | `tab limiter`, `limit tabs`, `tab manager`, `focus tabs`, `reduce tabs` |
| Pomodoro Timer | `pomodoro timer`, `focus timer`, `25 minute timer`, `productivity timer` |

---

## 📋 Документация проекта

| Документ | Назначение | Ссылка |
|---|---|---|
| CONTEXT.md | Полный контекст проекта для Manus | [Открыть](https://github.com/nikol-dev-tools/schepki-config/blob/main/CONTEXT.md) |
| PUBLISHING_GUIDE.md | Пошаговый гайд публикации в Chrome Web Store | [Открыть](https://github.com/nikol-dev-tools/schepki-config/blob/main/PUBLISHING_GUIDE.md) |
| DASHBOARD.md | Этот файл — все ссылки и кабинеты | [Открыть](https://github.com/nikol-dev-tools/schepki-config/blob/main/DASHBOARD.md) |
| config.json | Remote Config для всех расширений | [Открыть](https://github.com/nikol-dev-tools/schepki-config/blob/main/config.json) |

---

## 🔑 Важные данные (не публиковать)

> Эти данные хранятся здесь только для удобства работы с Manus. GitHub репозиторий приватный.

| Параметр | Значение |
|---|---|
| Google Analytics Measurement ID | `G-3ZKRBK0TBV` |
| GA4 API Secret | `TaFzQ3cgRP25jG3BSYtASA` (псевдоним: schepki_prod) |
| GA4 Stream ID | `14162072589` |
| Buy Me a Coffee URL | [buymeacoffee.com/nikoltools](https://buymeacoffee.com/nikoltools) |
| Рабочий email | `nikol.dev.tools@gmail.com` |
| GitHub PAT | Хранится в файле `SCHEPKI_TOKEN.doc` на локальном компьютере |

---

## 🗓️ Чеклист — что проверять еженедельно

- [ ] Chrome Web Store Dashboard — новые установки, отзывы, статус модерации
- [ ] GA4 → Events → `first_launch` — сколько новых пользователей за неделю
- [ ] GA4 → Events → `donation_click` — конверсия в донаты
- [ ] Buy Me a Coffee — новые поддержки
- [ ] Статус расширений на модерации (Tab Limiter, Pomodoro)

---

*Последнее обновление: 22 марта 2026*
