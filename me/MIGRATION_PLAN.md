# 📋 План миграции Таплинка Мишки Макса

> Что нужно изменить в `index.html`, чтобы из текущей версии получить новую.
> Изменения сгруппированы по логическим блокам — от простых к сложным.

---

## 1. `<head>` — мелкие правки

### 1.1 Обновить `meta description`
```html
<!-- Было -->
<meta name="description" content="Смотри новые серии, скачивай песенки и развивающие материалы для детей! Мультики, сценарии и материалы для занятий.">

<!-- Стало -->
<meta name="description" content="Мультики, песенки и развивающие материалы для детей 1–5 лет! Мишка Макс — добрый друг для малышей.">
```

---

## 2. CSS — добавить новые переменные

В блок `:root { ... }` добавить две переменные для зелёного цвета (используется в кнопке primary-cta):

```css
--green: #2ECC71;
--green-dark: #27AE60;
```

Также удалить неиспользуемую переменную `--cloud-white: #F8F9FA;`.

---

## 3. CSS — добавить стили для разделителей секций

Добавить новый блок стилей после `.links { ... }`:

```css
.section-label {
    display: flex;
    align-items: center;
    gap: 10px;
    margin: 10px 0 4px;
    animation: slideIn 0.6s ease-out backwards;
}

.section-label-text {
    font-family: 'Fredoka', sans-serif;
    font-size: 13px;
    font-weight: 600;
    color: rgba(255,255,255,0.9);
    text-transform: uppercase;
    letter-spacing: 1.5px;
    white-space: nowrap;
    text-shadow: 1px 1px 3px rgba(0,0,0,0.2);
}

.section-label-line {
    flex: 1;
    height: 1px;
    background: rgba(255,255,255,0.4);
    border-radius: 1px;
}
```

---

## 4. CSS — добавить стиль `.live-dot` (пульсирующий индикатор на CTA)

```css
.live-dot {
    position: absolute;
    top: 12px;
    right: 16px;
    width: 10px;
    height: 10px;
    background: #fff;
    border-radius: 50%;
    z-index: 2;
    animation: live-pulse 1.8s ease-in-out infinite;
}

@keyframes live-pulse {
    0%, 100% { transform: scale(1); opacity: 1; box-shadow: 0 0 0 0 rgba(255,255,255,0.7); }
    50% { transform: scale(1.2); opacity: 0.9; box-shadow: 0 0 0 6px rgba(255,255,255,0); }
}
```

---

## 5. CSS — добавить стиль `.link-button.primary-cta` (зелёная кнопка для мам)

Добавить новый вариант кнопки — зелёный, первичный CTA:

```css
.link-button.primary-cta {
    background: linear-gradient(135deg, #3DD68C 0%, #27AE60 100%);
    border: 4px solid var(--white);
    box-shadow: 0 8px 32px rgba(39,174,96,0.45), 0 4px 12px rgba(0,0,0,0.15), inset 0 2px 4px rgba(255,255,255,0.4);
}

.link-button.primary-cta::before {
    background: linear-gradient(135deg, #2ECC71 0%, #1E8449 100%);
}

.link-button.primary-cta .link-title,
.link-button.primary-cta .link-desc { color: var(--white); text-shadow: 1px 1px 3px rgba(0,0,0,0.25); }

.link-button.primary-cta .link-icon {
    background: rgba(255,255,255,0.25);
    box-shadow: 0 4px 12px rgba(0,0,0,0.1), inset 0 2px 4px rgba(255,255,255,0.3);
}

.link-button.primary-cta:hover {
    transform: translateY(-10px) scale(1.03) rotate(-1deg);
    box-shadow: 0 20px 56px rgba(39,174,96,0.6), 0 6px 20px rgba(0,0,0,0.2);
    border-color: #A9F5C8;
}

.link-button.primary-cta:hover .link-title,
.link-button.primary-cta:hover .link-desc { color: var(--white); }
```

---

## 6. CSS — добавить стиль `.link-button.partnership` (тёмная кнопка для бизнеса)

```css
.link-button.partnership {
    background: linear-gradient(135deg, #2C3E50 0%, #1A252F 100%);
    border: 3px solid rgba(255,255,255,0.2);
    box-shadow: 0 6px 24px rgba(0,0,0,0.3), 0 2px 8px rgba(0,0,0,0.2);
}

.link-button.partnership::before { background: linear-gradient(135deg, #3D5168 0%, #2C3E50 100%); }

.link-button.partnership .link-title { color: var(--yellow); text-shadow: 1px 1px 3px rgba(0,0,0,0.4); }
.link-button.partnership .link-desc { color: rgba(255,255,255,0.75); }

.link-button.partnership .link-icon {
    background: linear-gradient(135deg, var(--yellow) 0%, var(--orange) 100%);
    box-shadow: 0 6px 16px rgba(255,210,63,0.3);
}

.link-button.partnership .link-icon svg { fill: #2C3E50; }

.link-button.partnership:hover {
    border-color: var(--yellow);
    box-shadow: 0 16px 48px rgba(0,0,0,0.4), 0 4px 16px rgba(255,210,63,0.2);
}

.link-button.partnership:hover .link-title { color: var(--yellow); }
.link-button.partnership:hover .link-desc { color: rgba(255,255,255,0.9); }
```

---

## 7. CSS — добавить стиль `.reach-badge` (бейдж с охватами)

```css
.reach-badge {
    position: absolute;
    top: 10px;
    right: 14px;
    background: linear-gradient(135deg, var(--yellow), var(--orange));
    color: #2C3E50;
    font-family: 'Fredoka', sans-serif;
    font-size: 11px;
    font-weight: 700;
    padding: 3px 9px;
    border-radius: 10px;
    z-index: 2;
    box-shadow: 0 3px 10px rgba(255,210,63,0.4);
    letter-spacing: 0.3px;
}
```

---

## 8. CSS — добавить стиль `.social-hint`

```css
.social-hint {
    font-size: 12px;
    color: rgba(255,255,255,0.8);
    text-align: center;
    font-weight: 700;
    margin-top: 10px;
    text-shadow: 1px 1px 2px rgba(0,0,0,0.15);
}
```

---

## 9. CSS — обновить стили `.social-icons` и `.social-icon-btn`

Изменить `.social-icons`: убрать `margin: 20px 0 36px`, заменить на `margin-top: 12px`.

Изменить `.social-icon-btn`: уменьшить размер с `64px` до `58px`, фон сделать полупрозрачным `rgba(255,255,255,0.85)` вместо `var(--white)`.

---

## 10. CSS — обновить `@media (hover: none)`

Добавить правила для новых классов кнопок:

```css
@media (hover: none) {
    /* ... существующие правила ... */
    .link-button.primary-cta:hover { transform: none; }
    .link-button.partnership:hover { transform: none; }
}
```

---

## 11. HTML — шапка `<header>`

### 11.1 Удалить блок `.social-icons` из шапки целиком

Удалить весь блок `<div class="social-icons">...</div>` из `<header>`.

### 11.2 Изменить текст `.subtitle`

```html
<!-- Было -->
<p class="subtitle">Добрые мультики 🎬, песенки 🎵 и развивающие материалы 📚</p>

<!-- Стало -->
<p class="subtitle">Мультики, песенки и развивашки для детей 1–5 лет 🐻</p>
```

---

## 12. HTML — блок `.links` — полная реструктуризация

Это основное изменение. Текущий порядок кнопок полностью меняется.

### Было (порядок):
1. Кладовая педагога (featured)
2. Сказки Мишки Макса (stories)
3. Telegram-канал
4. Мессенджер MAX
5. Дзен
6. Сотрудничество

### Стало (порядок с разделителями):

```
── 👩‍👧 Для мам и малышей ──
1. [primary-cta] Мультики и песенки — бесплатно → Telegram-канал
2. [stories]     Аудиосказки для малышей → Telegram сказки

── 👩‍🏫 Для воспитателей ──
3. [featured]    Кладовая педагога → t.me/mishka_max/245

── 📺 Смотреть везде ──
4. [обычная]     VK (Вконтакте)
5. [обычная]     Мессенджер MAX (с бейджем NEW)
6. [обычная]     Дзен

── 📲 Мы в соцсетях ──
   [иконки]  Instagram · TikTok · YouTube
   [текст]   221К · 95К · подпишись...

── 🤝 Для бизнеса ──
7. [partnership] Сотрудничество и реклама (с бейджем 326К+)
```

### Шаблон разделителя (вставлять перед каждой группой):

```html
<div class="section-label">
    <div class="section-label-line"></div>
    <span class="section-label-text">👩‍👧 Для мам и малышей</span>
    <div class="section-label-line"></div>
</div>
```

### Шаблон первой кнопки (primary-cta, Telegram):

```html
<a href="https://t.me/+7-oGjM-AgbcxNWQ6" class="link-button primary-cta" onclick="ym(105821243,'reachGoal','click_telegram_cta')">
    <div class="live-dot"></div>
    <div class="link-icon">
        <!-- SVG Telegram -->
    </div>
    <div class="link-content">
        <div class="link-title">🎵 Мультики и песенки — бесплатно</div>
        <div class="link-desc">Telegram-канал · 14 000+ подписчиков</div>
    </div>
</a>
```

### Изменения в существующих кнопках:

| Кнопка | Что изменить |
|--------|-------------|
| **Кладовая педагога** | Убрать `featured` из первой позиции, переместить в блок педагогов. Добавить цену в `.link-desc`: `· подписка 260₽/мес` |
| **Сказки** | Переместить в блок мам (2-я кнопка). Текст без изменений |
| **Telegram-канал** | Превратить в `primary-cta` (зелёная). Изменить текст и добавить `live-dot`. Поставить первой |
| **VK** | Переместить в блок «Смотреть везде». Добавить SVG VK, обновить описание |
| **MAX** | Переместить в блок «Смотреть везде» |
| **Дзен** | Переместить в блок «Смотреть везде». Описание: `Статьи и видео для родителей` |
| **Сотрудничество** | Класс кнопки: заменить на `partnership`. Добавить `<div class="reach-badge">326К+ подписчиков</div>`. Изменить SVG иконку на иконку людей. Текст: `Сотрудничество и реклама` / `Интеграции, партнёрства, медиакит` |

---

## 13. HTML — добавить блок соцсетей-иконок в конец `.links`

Перед разделителем «Для бизнеса» вставить:

```html
<div class="social-icons">
    <a href="https://instagram.com/mishka_max_" class="social-icon-btn" onclick="ym(105821243,'reachGoal','click_instagram')" title="Instagram">
        <!-- SVG Instagram -->
    </a>
    <a href="https://tiktok.com/@mishka_max_" class="social-icon-btn" onclick="ym(105821243,'reachGoal','click_tiktok')" title="TikTok">
        <!-- SVG TikTok -->
    </a>
    <a href="https://youtube.com/@mishka_max?si=7SXOoxTl8nIRQ7YK" class="social-icon-btn" onclick="ym(105821243,'reachGoal','click_youtube_icon')" title="YouTube">
        <!-- SVG YouTube -->
    </a>
</div>
<p class="social-hint">221К · 95К · подпишись, чтобы не пропустить новые серии 🐾</p>
```

> SVG-коды для иконок — те же, что уже есть в оригинальном файле в блоке `.social-icons` шапки. Просто перенести оттуда.

---

## 14. HTML — футер

Изменить текст:

```html
<!-- Было -->
<p class="footer-text">Подписывайся на все каналы! 🐻💛</p>

<!-- Стало -->
<p class="footer-text">Мишка Макс любит тебя! 🐻💛</p>
```

---

## Итоговый чеклист

- [ ] Обновить `meta description`
- [ ] Добавить CSS-переменные `--green`, `--green-dark`
- [ ] Добавить CSS `.section-label`, `.section-label-text`, `.section-label-line`
- [ ] Добавить CSS `.live-dot` и `@keyframes live-pulse`
- [ ] Добавить CSS `.link-button.primary-cta` и его состояния
- [ ] Добавить CSS `.link-button.partnership` и его состояния
- [ ] Добавить CSS `.reach-badge`
- [ ] Добавить CSS `.social-hint`
- [ ] Обновить CSS `.social-icons` (отступы) и `.social-icon-btn` (размер)
- [ ] Обновить `@media (hover: none)` — добавить новые классы
- [ ] Удалить блок `.social-icons` из `<header>`
- [ ] Обновить текст `.subtitle` в шапке
- [ ] Полностью переписать содержимое блока `.links`:
  - [ ] Добавить разделители секций
  - [ ] Создать новую зелёную кнопку (Telegram CTA) первой
  - [ ] Переместить «Сказки» в блок мам
  - [ ] Переместить «Кладовую педагога» в блок воспитателей, добавить цену
  - [ ] Добавить VK-кнопку в блок «Смотреть везде»
  - [ ] Переместить MAX и Дзен туда же
  - [ ] Добавить иконки соцсетей + `.social-hint` перед блоком для бизнеса
  - [ ] Переделать кнопку «Сотрудничество» в `partnership` с бейджем охватов
- [ ] Обновить текст футера
