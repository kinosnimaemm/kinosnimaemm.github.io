# kinosnimaemm portfolio — инструкция и доступы

Проект: сайт-портфолио продакшна **kinosnimaemm** / Andrii Hevich.

Папка проекта:

```text
/Users/eqtech/Desktop/ПОРТФОЛИО/web_kino
```

GitHub repository:

```text
https://github.com/kinosnimaemm/kinosnimaemm.github.io
```

Важно: **не хранить пароли, GitHub token, email-пароли, доступы к Instagram/Telegram/WhatsApp в этом файле**, если проект будет загружаться на GitHub. Этот файл может оказаться публичным.

Для паролей использовать:

- iCloud Keychain;
- 1Password;
- Bitwarden;
- заметку вне репозитория;
- GitHub Secrets, если когда-нибудь появится автоматический deploy.

---

## Что внутри проекта

```text
index.html        — основная страница сайта
styles.css        — дизайн, цвета, анимации, адаптивность
script.js         — переключение языков, hover-play видео, scroll-анимации
README.md         — короткая инструкция
info.md           — этот файл
assets/video/     — web-версии видео для сайта
assets/posters/   — постеры/превью для видео
```

---

## Как работает сайт

Сайт статический. Это значит, что для него не нужен backend, база данных или серверное приложение.

GitHub Pages просто отдает файлы:

```text
index.html
styles.css
script.js
assets/...
```

Главные функции:

1. **Hero-видео**
   - открывается сразу на первом экране;
   - использует `assets/video/hero-full-frame.mp4`.

2. **Переключение языков**
   - RU / EN / DE;
   - тексты лежат в `script.js` внутри объекта `translations`.

3. **Видео в портфолио**
   - при наведении мышки видео начинает играть;
   - когда мышка уходит, видео останавливается на текущем кадре;
   - на телефоне видео запускается тапом.

4. **Горизонтальные видео**
   - используются как cinematic scroll-сцены между блоками;
   - включаются, когда появляются в зоне видимости;
   - ставятся на паузу, когда пользователь листает дальше.

5. **Контакты**
   - email и Telegram уже добавлены;
   - Instagram / WhatsApp можно подключить позже.

---

## Как проверить сайт локально

Открыть Terminal и выполнить:

```bash
cd '/Users/eqtech/Desktop/ПОРТФОЛИО/web_kino'
python3 -m http.server 8080
```

Потом открыть в браузере:

```text
http://localhost:8080
```

Если изменения не видны, сделать hard refresh:

```text
Cmd + Shift + R
```

---

## Варианты GitHub Pages URL

Текущий репозиторий:

```text
kinosnimaemm.github.io
```

Если использовать этот репозиторий как project site, сайт будет примерно здесь:

```text
https://kinosnimaemm.github.io/
```

Если нужен красивый основной адрес вида:

```text
https://kinosnimaemm.github.io/
```

то репозиторий должен называться строго:

```text
kinosnimaemm.github.io
```

То есть без `kino.web.`.

---

## Первый upload на GitHub

Перед upload нужно быть в папке проекта:

```bash
cd '/Users/eqtech/Desktop/ПОРТФОЛИО/web_kino'
```

Проверить файлы:

```bash
ls -la
```

Если git еще не создан:

```bash
git init
```

Добавить remote repository:

```bash
git remote add origin https://github.com/kinosnimaemm/kinosnimaemm.github.io.git
```

Если remote уже существует, проверить:

```bash
git remote -v
```

Добавить файлы:

```bash
git add .
```

Создать commit:

```bash
git commit -m "Create portfolio landing page"
```

Переименовать ветку в `main`:

```bash
git branch -M main
```

Отправить на GitHub:

```bash
git push -u origin main
```

Если GitHub попросит логин/пароль:

- login: GitHub username, например `kinosnimaemm`;
- password: использовать не обычный пароль, а **GitHub Personal Access Token**.

Пароль/token в этот файл не вставлять.

---

## Как включить GitHub Pages

После push:

1. Открыть репозиторий:

```text
https://github.com/kinosnimaemm/kinosnimaemm.github.io
```

2. Перейти:

```text
Settings → Pages
```

3. В разделе **Build and deployment** выбрать:

```text
Source: Deploy from a branch
Branch: main
Folder: / root
```

4. Нажать **Save**.

5. Подождать 1–3 минуты.

6. GitHub покажет ссылку на сайт.

---

## Как обновлять сайт после правок

После любых изменений:

```bash
cd '/Users/eqtech/Desktop/ПОРТФОЛИО/web_kino'
git status
git add .
git commit -m "Update portfolio site"
git push
```

Через 1–3 минуты GitHub Pages обновит сайт.

---

## Где менять контакты

Контакты находятся в `index.html`, блок `contact`.

Найти примерно такие строки:

```html
<a href="mailto:kinosnimaemm@gmail.com">kinosnimaemm@gmail.com</a>
<a href="https://t.me/youmee_to">Telegram</a>
<a href="#" aria-disabled="true">Instagram soon</a>
<a href="#" aria-disabled="true">WhatsApp soon</a>
```

Когда будут ссылки, заменить `#` на реальные ссылки.

---

## Где менять тексты

Большинство текстов для RU / EN / DE лежит в:

```text
script.js
```

Ищи объект:

```js
const translations = {
  ru: { ... },
  en: { ... },
  de: { ... }
}
```

---

## Где менять дизайн

Дизайн находится в:

```text
styles.css
```

Основные цвета в начале файла:

```css
:root {
  --bg: ...;
  --text: ...;
  --accent: ...;
  --accent-2: ...;
}
```

---

## Где менять видео

Видео для сайта лежат здесь:

```text
assets/video/
```

Постеры здесь:

```text
assets/posters/
```

Важно: не загружать на GitHub огромные оригиналы 300MB+. Для сайта лучше использовать web-версии до 10–20MB на файл.

---

## Что нельзя делать

Не добавлять в репозиторий:

- пароли;
- GitHub tokens;
- email-пароли;
- доступы Instagram/Telegram/WhatsApp;
- приватные документы;
- исходные тяжелые видео, если они больше 100MB.

GitHub не принимает файлы больше 100MB обычным push.

---

## Доступы — безопасный шаблон

GitHub username:

```text
kinosnimaemm
```

GitHub repository:

```text
https://github.com/kinosnimaemm/kinosnimaemm.github.io
```

GitHub Pages URL после включения:

```text
https://kinosnimaemm.github.io/
```

Email для сайта:

```text
kinosnimaemm@gmail.com
```

Telegram для сайта:

```text
https://t.me/youmee_to
```

Instagram:

```text
добавить позже
```

WhatsApp:

```text
добавить позже
```

Пароли:

```text
НЕ ХРАНИТЬ В ЭТОМ ФАЙЛЕ
```
