# 🚀 Гайд по публикации расширений «Щепки» в Chrome Web Store

> Этот документ — постоянный шаблон. При публикации каждого нового расширения Manus добавляет в конец раздел с готовыми текстами для конкретного расширения.

---

## Шаг 1. Загрузка пакета

1. Перейди в [Chrome Developer Dashboard](https://chrome.google.com/webstore/devconsole).
2. Нажми **+ Добавить продукт** (New Item).
3. Загрузи ZIP-архив расширения.
4. Дождись загрузки — откроется форма заполнения.

---

## Шаг 2. Вкладка «Сведения о магазине» (Store Listing)

### Поля, которые заполняются автоматически из manifest.json:
- **Название** — берётся из `"name"` в manifest
- **Краткое описание** — берётся из `"description"` в manifest

### Поля, которые нужно заполнить вручную:

**Описание*** (до 16 000 символов) — вставь готовый текст из раздела конкретного расширения ниже.

**Категория*** — выбирай **«Производительность» (Productivity)** для всех щепок. НЕ «Здоровье», НЕ «Инструменты разработчика».

**Язык*** — выбирай **«Английский (Соединённые Штаты)»**.

---

## Шаг 3. Графические объекты — ТОЧНЫЕ ТРЕБОВАНИЯ

> ⚠️ Все изображения должны быть **JPEG или 24-bit PNG без альфа-канала**. PNG с прозрачностью не принимается!

### 🎨 Стандарт иконок Schepki (обязательно для всех расширений)

Иконки должны выглядеть как иконки мобильных приложений — **сплошной непрозрачный фон**, как у Grammarly, 1Password, Notion. Никакой прозрачности, никаких «плавающих» символов.

**Требования к дизайну:**
- Сплошной цветной фон (никакой прозрачности, никакого альфа-канала)
- Скруглённые углы в стиле iOS-иконок (radius ~22% от размера)
- Один чистый белый символ по центру — минималистичный, плоский, без градиентов
- Стиль: flat design, как у топовых расширений Chrome
- Каждое расширение — свой цвет фона для узнаваемости

**Цвета фона по расширениям:**

| Расширение | Цвет фона | HEX |
|---|---|---|
| Breathing Timer | Тёмный бирюзовый | `#0d7377` |
| Tab Limiter | Синий индиго | `#3d5a99` |
| Pomodoro Timer | Тёмно-красный | `#c0392b` (рекомендуется) |
| Новые расширения | Выбирать уникальный тёмный цвет | — |

**Исходный файл:** генерировать в 2048×2048px, нарезать через Python PIL на нужные размеры.

**Промпт-шаблон для генерации иконки (подставить название и цвет):**
```
Professional Chrome extension app icon for '[NAME]'. Solid flat design, no transparency.
Solid [COLOR] background filling the entire square. Rounded corners like iOS app icons.
Center: single clean white minimalist [SYMBOL DESCRIPTION]. Pure white, no gradients.
Flat, modern, similar to Grammarly/1Password/Notion icons. 512x512.
```

| Поле | Размер | Формат | Кол-во | Примечание |
|---|---|---|---|---|
| **Значок магазина** | 128 × 128 px | PNG | 1 | `icon128.png` из папки icons/ |
| **Скриншоты** | 1280 × 800 px или 640 × 400 px | JPEG или PNG 24-bit | 1–5 | Загружай все 5 для максимального охвата |
| **Маленькое рекламное изображение** | **ровно 440 × 280 px** | JPEG или PNG 24-bit | 1 | `banner_440x280.jpg` |
| **Очень большое рекламное изображение** | **ровно 1400 × 560 px** | JPEG или PNG 24-bit | 1 | `banner_1400x560.jpg` |
| **Глобальный проморолик** | URL YouTube | — | 0–1 | Необязательно, можно пропустить |

**Порядок загрузки скриншотов:**
1. `screenshot_1.jpg` — главный экран (UI попапа)
2. `screenshot_2.jpg` — ключевая фича в действии
3. `screenshot_3.jpg` — список всех фич
4. `screenshot_4.jpg` — Rate Us / дополнительная фича
5. `screenshot_5.jpg` — Before vs After / эмоциональный

---

## Шаг 4. Дополнительные поля (Additional Fields)

- **Официальный URL:** Нет
- **URL главной страницы:** `https://nikol-dev-tools.github.io/schepki-config/privacy.html`
- **URL службы поддержки:** `https://nikol-dev-tools.github.io/schepki-config/privacy.html`
- **Только для взрослых:** Выключено ❌

---

## Шаг 5. Вкладка «Конфиденциальность» (Privacy)

### Единое назначение (Single Purpose)
Опиши одной фразой что делает расширение. Готовый текст — в разделе конкретного расширения ниже.

### Обоснование разрешений (Permissions Justification)
Для каждого разрешения в manifest.json нужно написать обоснование. Готовые тексты — в разделе конкретного расширения ниже.

### Удалённый код (Remote Code)
- Выбери **«Да, я использую разрешение "удалённый код"»**
- **Обоснование:** `The extension fetches a remote JSON configuration file from raw.githubusercontent.com to allow dynamic updates of settings (such as donation link URL) without requiring a Chrome Web Store update. No code is executed remotely — only a static JSON data file is loaded.`

### Использование данных (Data Usage)
- **Сбор персональных данных:** НЕТ — оставляй все чекбоксы пустыми.
- **Подтверждаю следующее:** Отметь **все три** чекбокса внизу ✅✅✅
- **Политика конфиденциальности:** `https://nikol-dev-tools.github.io/schepki-config/privacy.html`

---

## Шаг 6. Вкладка «Распространение» (Distribution)

- **Регионы:** Все регионы (All regions)
- **Видимость:** Общедоступно (Public)

---

## Шаг 7. Публикация

1. Нажми **Сохранить как черновик** (Save draft) — убедись что ошибок нет.
2. Нажми **Отправить на проверку** (Submit for review).
3. Жди письма на `nikol.dev.tools@gmail.com` — обычно 1–3 дня.
4. Как придёт письмо с одобрением — сообщи Manus Store ID (из URL или письма), чтобы обновить `config.json`.

---

## ⚠️ Важные замечания

- После публикации Chrome может показывать предупреждение «Будьте осторожны» — это норма для новых расширений. Проходит само после ~100 установок и нескольких недель активности.
- Не обновляй живые расширения без веской причины — каждое обновление проходит повторную модерацию (1–3 дня).
- Если добавляешь новые разрешения в manifest при обновлении — Chrome попросит пользователей подтвердить, часть отключится.

---

## 🔄 Обновление уже опубликованного расширения

Обновление делится на два типа — важно понимать разницу:

| Что меняется | Нужна модерация? | Сколько ждать? | Что делать |
|---|---|---|---|
| Только **Store listing** (иконка, скрины, описание) | Да, но быстро | Несколько часов | Изменить в Dashboard → Store listing → Опубликовать |
| **ZIP-пакет** (код, иконки внутри) | Да, полная | 1–3 дня | Загрузить новый ZIP → Отправить на проверку |

**Правило обновления ZIP:** всегда делать все исправления за один раз (иконка + аналитика + новые фичи), чтобы не гонять на проверку несколько раз.

**Что не меняется при обновлении ZIP:** скриншоты, описание, категория, обоснования разрешений — всё это сохраняется. Перезаполнять не нужно.

---

---

# 📋 Данные для конкретных расширений

---

## Tab Limiter — Stay Focused

### Описание (вставить в поле «Описание»):
```
Tab Limiter — Stay Focused | Set a maximum number of open tabs and let the extension enforce it automatically.

When you hit your limit, any new tab is instantly closed — keeping your browser clean and your mind focused. Perfect for ADHD, deep work, and anyone who opens too many tabs.

✅ Set any limit from 1 to 100 tabs
✅ Live badge shows current open tab count at a glance
✅ Works silently in the background — no interruptions
✅ Simple toggle to enable/disable anytime
✅ Clean, minimal interface
✅ Multi-language support (English, German, French, Spanish, Portuguese)

Free forever. No tracking, no bloatware. Just focus.
```

### Единое назначение (вставить в поле «Single Purpose»):
```
This extension limits the maximum number of open tabs to help users stay focused and reduce browser clutter.
```

### Обоснование разрешений (вставить для каждого разрешения):

| Разрешение | Текст обоснования |
|---|---|
| `tabs` | Required to count open tabs and close new ones when the limit is exceeded. |
| `storage` | Required to save user preferences (tab limit, enabled state) locally on the device. |
| `alarms` | Required for background tasks and analytics session management. |
| `host_permissions` (raw.githubusercontent.com) | Required to fetch remote configuration for dynamic updates without requiring extension updates. |

### Графические файлы для загрузки:
- Значок: `tab-limiter/icons/icon128.png`
- Скриншоты: `tab-limiter/store/screenshot_1.jpg` … `screenshot_5.jpg`
- Баннер 440×280: `tab-limiter/store/banner_440x280.jpg`
- Баннер 1400×560: `tab-limiter/store/banner_1400x560.jpg`

---

## Pomodoro Timer

*(Данные будут добавлены после одобрения)*

---

## Breathing Timer — Calm & Focus

*(Данные будут добавлены при следующем обновлении)*
