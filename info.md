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

---

# Актуальный статус деплоя — 26 апреля 2026

Сайт уже загружен на GitHub Pages.

## Финальный адрес сайта

```text
https://kinosnimaemm.github.io/
```

## Финальный GitHub repository

Репозиторий был переименован:

```text
старое имя: kino.web.github.io
новое имя: kinosnimaemm.github.io
```

Текущий repository:

```text
https://github.com/kinosnimaemm/kinosnimaemm.github.io
```

Git remote в локальной папке проекта:

```text
https://github.com/kinosnimaemm/kinosnimaemm.github.io.git
```

## Что было сделано

1. Установлен GitHub CLI:

```text
gh 2.91.0
```

2. Выполнена авторизация под GitHub-аккаунтом:

```text
kinosnimaemm
```

3. Репозиторий переименован в:

```text
kinosnimaemm.github.io
```

4. Сайт загружен в ветку:

```text
main
```

5. GitHub Pages настроен на:

```text
Source: Deploy from a branch
Branch: main
Folder: / root
```

6. GitHub Pages status после проверки:

```text
built
```

7. Проверка сайта дала:

```text
HTTP 200
content: ok
```

## Последний известный commit сайта

```text
18d89c8 Create kinosnimaemm portfolio landing page
```

## Как обновлять сайт дальше

После любых изменений в файлах сайта выполнить:

```bash
cd '/Users/eqtech/Desktop/ПОРТФОЛИО/web_kino'
git status
git add .
git commit -m "Update portfolio site"
git push
```

После `git push` GitHub Pages обычно обновляется за 1–3 минуты.

Проверить сайт:

```text
https://kinosnimaemm.github.io/
```

Если сайт в браузере не обновился сразу, сделать hard refresh:

```text
Cmd + Shift + R
```

## Как проверить GitHub Pages через Terminal

```bash
gh api repos/kinosnimaemm/kinosnimaemm.github.io/pages --jq '{html_url:.html_url,status:.status,source:.source}'
```

Ожидаемый результат:

```text
html_url: https://kinosnimaemm.github.io/
status: built
source.branch: main
source.path: /
```

## Как проверить сайт через Terminal

```bash
curl -L -I https://kinosnimaemm.github.io/
```

Ожидаемо:

```text
HTTP/2 200
```

## Важное про доступы

GitHub CLI сейчас авторизован на этом Mac под аккаунтом:

```text
kinosnimaemm
```

Проверить:

```bash
gh auth status
```

Выйти из аккаунта:

```bash
gh auth logout
```

Повторно войти:

```bash
gh auth login --web --git-protocol https --scopes repo
```

Пароли и токены по-прежнему **не хранить в этом файле**.
