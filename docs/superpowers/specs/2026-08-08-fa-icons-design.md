# Замена эмоджи на Font Awesome (DELF A1)

Дата: 2026-08-08
Статус: approved (одобрено пользователем в чате)

## Цель

Заменить все эмоджи в HTML-файлах курса «МУДРО» (DELF A1) на иконки Font Awesome 6 Free — единый, аккуратный вид иконок.

## Файлы

1. `index.html`
2. `autoevaluation.html`
3. `oral.html`
4. `ecrits.html`
5. `production-ecrite.html`
6. `production-orale.html`
7. `blancs.html`

## Подключение

В `<head>` каждого файла добавить:

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@fortawesome/fontawesome-free@6.5.2/css/all.min.css">
```

Тот же CDN (jsdelivr), что уже используется для шрифта Nunito.

## Карта замен

| Эмоджи | Класс | | Эмоджи | Класс |
|---|---|---|---|---|
| 🦉 | `fa-owl` | | ✅ | `fa-circle-check` |
| 🏠 | `fa-house` | | ❌ | `fa-circle-xmark` |
| 🎧 | `fa-headphones` | | ⭐ | `fa-star` |
| 📖 | `fa-book-open` | | 💡 | `fa-lightbulb` |
| ✍️ | `fa-pen-nib` | | 🎙 | `fa-microphone` |
| 🗣️ | `fa-comments` | | ⏹ | `fa-stop` |
| 🚧 | `fa-construction` | | 🔴 | `fa-circle` |
| 🪞 | `fa-face-smile` | | ⏱ | `fa-stopwatch` |
| 💬 | `fa-comments` | | 🃏 | `fa-layer-group` |
| 😊, 🙂 | `fa-face-smile` | | 🛒 | `fa-cart-shopping` |
| 😃 | `fa-face-smile-beam` | | 🧑🌾 | `fa-user-tie` |
| 😉 | `fa-face-smile-wink` | | 🙈 | `fa-eye-slash` |
| 😕, 😐 | `fa-face-meh` | | 🇷🇺 | `fa-language` |
| 🔄 | `fa-rotate` | | ✋ | `fa-hand` |
| 📍 | `fa-location-dot` | | 👇 | `fa-arrow-down` |
| 👥 | `fa-users` | | ☝️ | `fa-arrow-up` |
| 🎾 | `fa-table-tennis-paddle-ball` | | 👋 | `fa-hand-sparkles` |
| 🌦 | `fa-cloud-sun` | | 🐢 | `fa-forward` |
| 🔗 | `fa-link` | | ▶ | `fa-circle-play` |
| 🍎 | `fa-apple-whole` | | 🍅 | `fa-pepper-hot` |
| 🥕 | `fa-carrot` | | 🥔 | `fa-bowl-food` |
| 🥬 | `fa-seedling` | | 🍌 | `fa-basket-shopping` |

Примечания:
- Продуктовые эмоджи рынка (pe/po блоки) — берём ближайшую свободную иконку (томат/перец, картошка/тарелка с едой и т.п.).
- Иконки вставляются как `<i class="fa-solid fa-xxx" aria-hidden="true"></i>`.
- В местах, где элемент создаётся через `textContent` (кнопки «🎙 Записать» и т.п.), переводим на `innerHTML` с иконкой, чтобы тег `<i>` отрендерился.
- Эмоджи внутри BLOCKS-данных (product.emo, идеи карточек, фразы-опоры, SMILES) тоже заменяются.
- Смайлы автооценки (SMILES) → `fa-face-smile` / `fa-face-smile-beam` / `fa-face-meh` / `fa-face-frown-wink` по смыслу; стиль `.ae-btn i` — размер шрифта наследуется от `.ae-btn`.

## Проверка

- `node --check` извлечённых `<script>` из каждого файла.
- jsdom-смоук: рендер всех страниц без ошибок; в autoevaluation — заполнение анкеты, сообщения, toggle отмечают результаты в localStorage.

## Объём

~ 7 файлов, ~120 вхождений эмоджи (93 из них в autoevaluation.html).
