# Marrow: a raw pet-food kitchen site with Formgong forms

Сайт кухні сирого корму для собак і котів з формами Формгонг

A bright one-page site for a small kitchen that makes fresh-frozen raw meals and treats for dogs and cats and takes orders by message, with no checkout. Everything is in one `index.html` plus an `img/` folder. The demo kitchen, Marrow Kitchen in Portland, its recipes, prices, address and reviews are fictional.

- **Page wipe.** An orange panel slides off to the left as the page opens.
- **Header.** Menu links on the left, the bowl-and-bone mark in the middle, search, contact and order buttons on the right, an "Order now" pill and a round menu button. The menu opens a full-screen orange panel. Once you scroll, the header turns white and the mark folds away into the word MARROW.
- **Hero.** A rounded blue card with a giant MARROW wordmark and a cut-out photo of a dog in front of it, plus two white strokes that draw themselves. A dog/cat switch swaps the picture, the "Raw meals for dogs" pill, the recipes below and the meal finder. On desktop the card stays pinned for the first 400 px of scroll, then shrinks and fades a little while the next section rises.
- **Meal finder (form 1).** Age, weight, activity and neutered in one white bar. "See my plan" works out the daily amount and the pack size, and the visitor can email the plan to themselves.
- **Wave dividers.** Between sections the colour above bends into the next one as you scroll.
- **Recipes.** Six dog recipes and three cat recipes in cards that rise in one after another. The arrow on a card opens the order form with that recipe already chosen.
- **Why raw.** A thick orange band behind a big bowl that grows as it scrolls in, ingredients that drift as you scroll, four short benefit cards and a link to the questions.
- **Treats.** A carousel of six treats with a next button and drag. On desktop an orange "drag" circle follows the mouse over it.
- **Reviews.** A ribbon of running text, sample review cards with arrows, and "Leave a review" (form 3). Reviews you approve in Formgong replace the samples.
- **Questions.** Six answers in an accordion and an "Ask us" button (form 4).
- **Recipe banner and footer.** A full-width photo with "Build a recipe", then contacts, links, hours and round social buttons.

The order form (form 2) opens from "Order now", the bag icon, every recipe arrow and every "Add to order". With `prefers-reduced-motion: reduce` there is no wipe and no scroll motion and everything is visible. Without JavaScript all the content is still on the page.

## English

**Set up the forms**

1. Create a form in the Formgong dashboard and copy its access key.
2. In `index.html`, replace every `fk_your_access_key` with that key. There are four forms; they can share one key or use their own.
3. Each form also sends `access_key`, a hidden `subject` and the empty spam trap `botcheck`. It shows thanks only when Formgong answers `success: true`. Anything else shows the error and keeps what was typed. "Send another" brings the form back.

| Form | Fields (\* required) | Subject |
|---|---|---|
| `f-plan`, meal finder | `pet` (hidden: dog or cat), `age_months`\*, `weight_kg`\*, `activity` (low, medium, high), `neutered` (yes, no), `daily_grams` (hidden, filled in by the calculation), `email`\* | Meal plan request |
| `f-order`, order window | `item`\*, `pack`\* (250 g, 500 g, 750 g, 1000 g; treats send "One pouch"), `quantity`\* (1–20), `delivery`\* (Local delivery, Pick up at the kitchen), `name`\*, `email`\*, `phone`, `postcode` (required for local delivery), `note` | Order request |
| `f-review`, review window | `rating`\* (1–5), `name`\*, `review`\*, `email` (not shown on the site) | New review |
| `f-write`, write-to-us window | `topic` (Question, Custom recipe, Wholesale), `name`\*, `email`\*, `message`\* | Message |

**Reviews**

1. In the Formgong dashboard, open Reviews (https://formgong.com/dashboard/reviews) and turn reviews on for the form whose key is in `f-review`. A submission with a `rating` from 1 to 5 becomes a pending review that you approve or hide there.
2. Once at least one review is approved, the page loads them from `https://formgong.com/reviews/<your key>.json`. They replace the six sample cards, and the label above the heading shows the real average and count.
3. Until then the sample reviews stay. They are examples written for this template, so replace or delete them before you launch.

**Edit**

- Colours are at the top of the styles. `--hero` is the hero card; the hero photos are cut out, so any colour works. `--accent` is the orange of the pills and circles (text on it is `--ink`), `--accent-dark` is for prices, `--cream` and `--mist` are the soft section and card colours.
- `--on-hero` is the colour of the header links and icons over the hero. It is navy because white on the light blue card is too faint to read (about 2.3:1). Switch it to `#fff` only if your `--hero` is dark enough for 4.5:1.
- Fonts are Unbounded for the wordmark and headings and Figtree for everything else, loaded from Google Fonts.
- Recipe cards are `<li class="card">` items in the dog grid and the cat grid. The `data-order-item` of a card's arrow must match an option in the order form's `item` list. Treats work the same way in the carousel.
- The meal finder rule is in `dailyGrams()` in the script: dogs under 6 months 5 % of body weight a day, 6–12 months 4 %, adults 2, 2.5 or 3 % by activity; cats 3, 3.5 or 4 %, kittens 6 %; 10 % less when neutered; rounded to 10 g. It suggests the smallest of the 250, 500, 750 and 1000 g packs that covers one day.
- Address, phone, email and hours are in the menu panel and the footer.

**Images**

The page expects these files in `img/`: `hero-dog.webp` and `hero-cat.webp` (transparent stills, 3:2), `recipe-chicken`, `recipe-beef`, `recipe-lamb`, `recipe-turkey`, `recipe-duck`, `recipe-salmon`, `cat-chicken`, `cat-rabbit`, `cat-fish`, `treat-1` to `treat-6`, `bowl`, `peas`, `carrot`, `blueberries`, `pumpkin` (all transparent `.webp`) and `cta-dog.webp` (a photo). Until a file is there, its box shows a soft colour shape, so the layout never jumps.

The images were generated for this template with ChatGPT image generation (OpenAI). The animals, people and places are fictional. You may use them in your own site.

**Sample content.** Recipes, prices, the address and the reviews are examples. The meal finder gives a starting point, not vet advice; the note under the result says so.

## Українська

Яскравий односторінковий сайт для невеликої кухні, яка готує свіжозаморожений сирий корм і ласощі для собак і котів та приймає замовлення повідомленням, без кошика й оплати на сайті. Усе в одному `index.html` і папці `img/`. Кухня Marrow Kitchen у Портленді, рецепти, ціни, адреса й відгуки вигадані.

На сторінці:

- помаранчева шторка, що з'їжджає вліво під час відкриття;
- шапка з меню, знаком «миска з кісткою» посередині й кнопкою «Order now»; під час прокрутки знак згортається в слово MARROW, а меню відкривається на весь екран;
- перший екран: блакитна картка з величезним словом MARROW і вирізаним фото собаки перед ним; перемикач «собака / кіт» змінює фото, рецепти й калькулятор; на комп'ютері картка тримається перші 400 px прокрутки, а потім зменшується;
- калькулятор порції (форма 1): вік, вага, активність, стерилізація; він рахує грами на день і розмір пакета, а план можна надіслати собі на пошту;
- хвилясті переходи між секціями, що згинаються під час прокрутки;
- рецепти: шість для собак і три для котів; стрілка на картці відкриває замовлення з уже вибраним рецептом;
- «Чому сирий корм»: помаранчева смуга, миска, що збільшується, інгредієнти, що пливуть, і чотири картки з перевагами;
- карусель ласощів, яку можна тягнути; на комп'ютері за мишею ходить коло «drag»;
- відгуки зі стрічкою тексту, що біжить, і кнопкою «Leave a review» (форма 3); схвалені у Formgong відгуки замінюють приклади;
- питання й відповіді та кнопка «Ask us» (форма 4);
- банер «Build a recipe» з фото і футер з контактами й годинами роботи.

Вікно замовлення (форма 2) відкривають «Order now», іконка сумки, кожна стрілка рецепта й кожна кнопка «Add to order». Якщо в системі ввімкнено зменшення руху, анімацій немає, і все видно одразу.

**Налаштування форм.** Створіть форму в кабінеті Formgong і замініть кожне `fk_your_access_key` у `index.html` на свій ключ. Кожна форма надсилає `access_key`, прихований `subject` і порожнє поле-пастку `botcheck`. Подяка з'являється лише тоді, коли Formgong відповідає `success: true`.

- `f-plan` (калькулятор): `pet`, `age_months`\*, `weight_kg`\*, `activity`, `neutered`, `daily_grams`, `email`\*; тема «Meal plan request».
- `f-order` (замовлення): `item`\*, `pack`\*, `quantity`\* (1–20), `delivery`\*, `name`\*, `email`\*, `phone`, `postcode` (обов'язковий для доставки), `note`; тема «Order request».
- `f-review` (відгук): `rating`\* (1–5), `name`\*, `review`\*, `email` (на сайті не показується); тема «New review».
- `f-write` (повідомлення): `topic`, `name`\*, `email`\*, `message`\*; тема «Message».

**Відгуки.** У кабінеті Formgong відкрийте Reviews (https://formgong.com/dashboard/reviews) і ввімкніть відгуки для форми, ключ якої стоїть у `f-review`. Щойно ви схвалите перший відгук, сторінка завантажить їх замість шести прикладів разом зі справжньою середньою оцінкою. Приклади написані для шаблону, тож замініть або видаліть їх перед запуском.

**Що змінювати.** Кольори на початку стилів: `--hero` (картка першого екрана; фото на ній вирізані, тож колір може бути будь-який), `--accent`, `--accent-dark`, `--cream`, `--mist`. `--on-hero` за замовчуванням темно-синій, бо білий текст на світло-блакитному фоні читається погано; білий ставте лише на достатньо темний `--hero`. Правило калькулятора у функції `dailyGrams()`: цуценята до 6 місяців 5 % ваги на день, 6–12 місяців 4 %, дорослі 2, 2,5 або 3 % залежно від активності; коти 3, 3,5 або 4 %, кошенята 6 %; після стерилізації на 10 % менше. Це орієнтир, а не порада ветеринара.

**Зображення.** Фото згенеровано для цього шаблону в ChatGPT (OpenAI). Тварини, люди й місця вигадані. Поки файлу немає, на його місці м'яка кольорова форма, тож сторінка не стрибає. Рецепти, ціни, адреса й відгуки є прикладами.

MIT license.
