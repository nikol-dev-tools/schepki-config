# 🚀 Гайд по публикации расширений «Щепки» в Chrome Web Store

Этот документ содержит пошаговую инструкцию по заполнению всех полей в Chrome Developer Dashboard для публикации новых расширений.

---

## 1. Загрузка пакета
1. Перейдите в [Chrome Developer Dashboard](https://chrome.google.com/webstore/devconsole).
2. Нажмите **+ Добавить продукт** (Add new item).
3. Загрузите ZIP-архив расширения (например, `tab-limiter-v1.0.0.zip`).

---

## 2. Вкладка «Сведения о магазине» (Store Listing)

### Основная информация
*   **Название:** Берется из `manifest.json` автоматически.
*   **Краткое описание:** Берется из `manifest.json` автоматически.
*   **Подробное описание:** Скопируйте текст, подготовленный Manus (см. ниже для Tab Limiter).
*   **Категория:** Выберите наиболее подходящую (обычно «Инструменты разработчика» или «Продуктивность»).
*   **Язык:** Выберите основной язык (обычно Английский).

### Графические объекты
*   **Значок магазина (128x128):** Загрузите `icon128.png`.
*   **Скриншоты (1280x800):** Загрузите `promo_1280x800.png` (минимум 1, максимум 5).
*   **Рекламный баннер (440x280):** Загрузите `promo_440x280.png`.

---

## 3. Вкладка «Конфиденциальность» (Privacy)

### Единое назначение (Single Purpose)
*   **Описание назначения:** Опишите одной фразой, что делает расширение.
    *   *Пример для Tab Limiter:* "This extension limits the maximum number of open tabs to help users stay focused and reduce browser clutter."

### Разрешения (Permissions)
Обоснуйте каждое разрешение, запрошенное в `manifest.json`:
*   **tabs:** "Required to count open tabs and close new ones when the limit is exceeded."
*   **storage:** "Required to save user preferences (tab limit, enabled state) locally."
*   **alarms:** "Required for background tasks and analytics session management."
*   **Host permissions (raw.githubusercontent.com):** "Required to fetch remote configuration (Remote Config) for dynamic updates without requiring extension updates."

### Использование данных (Data Usage)
*   **Сбор данных:** Отметьте, что расширение **НЕ** собирает личные данные.
*   **Политика конфиденциальности:** Вставьте ссылку: `https://nikol-dev-tools.github.io/schepki-config/privacy.html`

---

## 4. Вкладка «Распространение» (Distribution)
*   **Регионы:** Выберите «Все регионы» (All regions).
*   **Видимость:** Выберите «Общедоступно» (Public).

---

## 5. Отправка на модерацию
1. Нажмите **Сохранить как черновик** (Save draft).
2. Нажмите **Отправить на проверку** (Submit for review).

---

## 📝 Данные для Tab Limiter (Копировать отсюда)

**Подробное описание (Detailed Description):**
```text
Tab Limiter — Stay Focused | Set a maximum number of open tabs and let the extension enforce it automatically. 

When you hit your limit, any new tab is instantly closed — keeping your browser clean and your mind focused. Perfect for ADHD, deep work, and anyone who opens too many tabs. 

Features:
- Set any limit from 1 to 100 tabs
- Live badge shows current open tab count
- Works silently in the background
- Simple toggle to enable/disable anytime
- Clean, minimal interface
- Multi-language support (EN, DE, FR, ES, PT)

Free forever. No tracking, no bloatware. Just focus.
```

**Единое назначение (Single Purpose):**
```text
This extension limits the maximum number of open tabs to help users stay focused and reduce browser clutter.
```

**Обоснование разрешений (Permissions Justification):**
*   **tabs:** `Required to count open tabs and close new ones when the limit is exceeded.`
*   **storage:** `Required to save user preferences (tab limit, enabled state) locally.`
*   **alarms:** `Required for background tasks and analytics session management.`
*   **Host permissions:** `Required to fetch remote configuration for dynamic updates.`
