# Шеринг

## Что это

Генерация шейринг-картинок на канвасе с помощь [Fabric.js](http://fabricjs.com/). 
[Скачать](http://cdnjs.cloudflare.com/ajax/libs/fabric.js/4.3.0/fabric.min.js) / [NPM](https://www.npmjs.com/package/fabric).

Генерация и скачивание занимает примерно 200 мс.

При каждом запросе по ссылке генерируется и скачивается PNG-картинка (метод `download(canvas)`)

## Файлы

Написано скриптом, встроенным в HTML-файл main.html. В ассетах лого и иконка.

В examples  немного примеров.

При генерации получаем файл musiq sharing **n** in **playlist**.png, где n — количество очков, playlist — название плейлиста. Имя файла обрезается до 32х символов.

## Присутствующие элементы и иерархия:

- **Заголовок** (heading) — большой зелёный текст
- Анонимная группа
    - **Обложка** плейлиста (cover) — загружается по ссылке
    - Текстовая группа (textGroup) — справа от обложки
        - **Текст** (text) — белый сопровождающий текст
        - **Плейлист** (playlist) — название плейлиста
- **Лого** (logo) — внизу справа
- Нижняя группа (bottomGroup) — можно поставить вместо иконки
    - **Иконка** (icon) — эквалайзер
    - **Текст** (bottomText) — любой текст

## URL-параметры

Для отладки есть околоGET URL-параметры

### score

Число от 1 до 10. 

Количество набранных очков в игре.

Влияют на заголовок и текст.

Пример: [`http://127.0.0.1:5500/main.html?score=2`](http://127.0.0.1:5500/main.html?score=2)

### cover

URL-ссылка на изображение.

Ссылка на обложку плейлиста.

Пример: [`http://127.0.0.1:5500/main.html?cover=https://charts-images.scdn.co/assets/locale_en/regional/daily/region_global_large.jpg`](http://127.0.0.1:5500/main.html?cover=https://charts-images.scdn.co/assets/locale_en/regional/daily/region_global_large.jpg)

### playlist

Строка.

Меняет зелёный текст с названием плейлиста.

Пример: [`http://127.0.0.1:5500/main.html?playlist=Шкатулка с колыбельными`](http://127.0.0.1:5500/main.html?playlist=%D0%A8%D0%BA%D0%B0%D1%82%D1%83%D0%BB%D0%BA%D0%B0%20%D1%81%20%D0%BA%D0%BE%D0%BB%D1%8B%D0%B1%D0%B5%D0%BB%D1%8C%D0%BD%D1%8B%D0%BC%D0%B8)

### bottom

Строка.

Меняет текст внизу справа.

Слева от текста иконка проекта.

Пример: [`http://127.0.0.1:5500/main.html?bottom=dergunov × qurle`](http://127.0.0.1:5500/main.html?bottom=derginov%20%C3%97%20qurle)

Несколько пааметров: [`http://127.0.0.1:5500/main.html?score=10&cover=https://i.scdn.co/image/ab67706f00000003e1ce4acd2b501398c6d745eb&playlist=mint Presents... Best Dance Songs of 2020&bottom=awesome.devs`](http://127.0.0.1:5500/main.html?score=10&cover=https://i.scdn.co/image/ab67706f00000003e1ce4acd2b501398c6d745eb&playlist=mint%20Presents...%20Best%20Dance%20Songs%20of%202020&bottom=awesome.devs)

## Дебаг и костыли

Строчка `setTimeout(function () { link.click() }, IS_DEBUG ? 500 : 0)`

При IS_DEBUG = true скрипт даёт время канвасу прогрузиться. При не-дебаге имитируется нажатие кнопки скачивания сразу же. Если оставить без тайм-аута, то работать не будет.

## Другие константы

`Colors (enum)` — палитра

`Sizes (enum)` — размеры канваса и повторяющиеся значения

`headings[]` — большие зелёные заголовки

`texts[]` — маленькие белые незаголовки