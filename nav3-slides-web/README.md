# Navigation 3 — основы и миграция · слайды

Веб-версия доклада для мобильных инженеров Dodo Engineering.
Тема: Jetpack **Navigation 3** — основы и итеративная миграция с Navigation 2.

Слайды — это изображения исходной презентации (пиксель-в-пиксель), поверх которых
лежит **прозрачный текстовый слой**: текст можно выделять и копировать прямо со слайда
(удобно для имён классов, API и сниппетов кода). Движок — [reveal.js](https://revealjs.com/),
подключён локально (без CDN).

## Управление

| Действие | Клавиша |
| --- | --- |
| Вперёд / назад | `→` `←` (или `Space`) |
| Полный экран | `F` |
| Обзор всех слайдов | `S` или `Esc` |
| Показать, где лежит выделяемый текст | `T` |
| Перейти к слайду №N | напишите номер и `Enter` |

Адрес открывается сразу на нужном слайде: `…/#/12` — слайд 12.

## Публикация на GitHub Pages

### Вариант А — автодеплой через GitHub Actions (рекомендую)

1. Создайте **публичный** репозиторий на GitHub (например `nav3-slides`).
2. Залейте в него содержимое этой папки:
   ```bash
   cd nav3-slides            # эта папка
   git init
   git add .
   git commit -m "Navigation 3 slides"
   git branch -M main
   git remote add origin https://github.com/<ваш-логин>/nav3-slides.git
   git push -u origin main
   ```
3. На GitHub: **Settings → Pages → Build and deployment → Source → GitHub Actions**.
4. Готово. Workflow `.github/workflows/deploy.yml` соберёт и опубликует сайт при каждом
   push в `main`. Адрес появится во вкладке **Actions** и в **Settings → Pages**:
   `https://<ваш-логин>.github.io/nav3-slides/`

### Вариант Б — без Actions (deploy from branch)

Если не хотите Actions: **Settings → Pages → Source → Deploy from a branch →
`main` / `/ (root)`**. Файлы лежат в корне репозитория, поэтому сайт заработает сразу.
(Файл `.nojekyll` уже добавлен, чтобы GitHub не обрабатывал сайт через Jekyll.)

## Локальный предпросмотр

`index.html` нельзя открывать как `file://` — нужен http-сервер:

```bash
python3 -m http.server 8000
# затем откройте http://localhost:8000
```

## Структура

```
index.html            видео-плеер слайдов (reveal.js) + встроенный текстовый слой
slides/               slide-01.webp … slide-32.webp — 32 слайда (WebP, 2667×1500)
vendor/reveal/        reveal.js 5.2.1 (локально)
.github/workflows/    деплой на GitHub Pages
.nojekyll
```

## Как пересобрать слайды из .pptx

Если исходник изменился, перегенерируйте картинки:

```bash
libreoffice --headless --convert-to pdf "Navigation 3.pptx"
pdftoppm -png -r 200 "Navigation 3.pdf" /tmp/s
# затем сконвертируйте /tmp/s-NN.png → slides/slide-NN.webp (quality 90)
```
