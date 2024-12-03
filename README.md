# Scroll Father

- [🇬🇧 English documentation](https://github.com/Poliklot/scroll-father/blob/master/docs/en/README.md)

Scroll Father — это лёгкая и многофункциональная библиотека на JavaScript/TypeScript, предоставляющая набор полезных
функций для работы со скроллом в веб-приложениях. Она позволяет разработчикам легко интегрировать необходимую
функциональность, импортируя только нужные функции, что способствует оптимизации загрузки и повышению
производительности.

## Особенности

- **Модульность:** Импортируйте только те функции, которые вам необходимы.
- **Богатый функционал:** Функции для определения направления скролла, плавной прокрутки, отслеживания элементов на
  странице и многое другое.
- **Высокая производительность:** Оптимизированный код с минимальным влиянием на размер бандла.
- **Поддержка TypeScript:** Полные типы для удобной разработки и автодополнения.
- **Лёгкость использования:** Простые и понятные API для быстрой интеграции.

## Установка

Установите через npm:

```bash
npm i scroll-father
```

Или добавьте через CDN:

```html
<script src="https://cdn.jsdelivr.net/npm/scroll-father/dist/ScrollFather.min.js"></script>
```

# Быстрый старт

### Импорт необходимых функций

Вы можете импортировать только те функции, которые вам нужны:

```javascript
// Импорт отдельных функций
import { trackScrollState, smoothScrollToElement } from 'scroll-father';
```

Или импортировать всё сразу (не стоит так делать):

```javascript
// Импорт всей библиотеки
import * as ScrollFather from 'scroll-father';
```

## Использование функций

### 1. Определение состояния скролла

Автоматически добавляет атрибут (например, `data-scrolled`) к указанному элементу при прокрутке страницы.

```javascript
import { trackScrollState } from 'scroll-father';

trackScrollState({
	attribute: 'data-scrolled', // Имя атрибута (по умолчанию 'data-scrolled')
	element: document.body, // Элемент для установки атрибута (по умолчанию document.body)
	onScrollStart: () => console.log('Скролл начался!'),
	onScrollReset: () => console.log('Скролл сброшен!'),
});
```

### 2. Определение направления скролла

Определяет направление скролла и устанавливает атрибут (`data-scroll-direction="up"` или `"down"`) на элементе `<body>`.

```javascript
import { initScrollDirectionTracking } from 'scroll-father';

initScrollDirectionTracking();
```

### 3. Реализация бесконечной прокрутки

Загружает дополнительный контент, когда пользователь достигает конца страницы.

```javascript
import { initInfiniteScroll } from 'scroll-father';

initInfiniteScroll(
	async () => {
		// Ваш код для загрузки дополнительного контента
		await fetchMoreData();
	},
	{
		threshold: 300, // Пороговое значение в пикселях до конца страницы (по умолчанию 300)
	},
);
```

### 4. Дебаунс события прокрутки

Добавляет обработчик прокрутки с дебаунсом, гарантируя, что переданный колбэк будет вызываться не чаще, чем с указанной
задержкой.

```javascript
import { debounceScroll } from 'scroll-father';

debounceScroll(() => {
	// Ваш код, который будет вызываться при прокрутке с дебаунсом
}, 200); // Задержка в миллисекундах перед вызовом функции (по умолчанию 200)
```

### 5. Отслеживание видимости элемента

Инициализирует отслеживание элемента с помощью `IntersectionObserver`. Вызывает функции при появлении или исчезновении
элемента из области просмотра.

```javascript
import { initIntersectionSection } from 'scroll-father';

const $section = document.querySelector('#my-section');

initIntersectionSection(
	$section,
	() => {
		// Функция вызывается, когда элемент входит в область видимости
		console.log('Элемент появился в области видимости');
	},
	() => {
		// Функция вызывается, когда элемент выходит из области видимости
		console.log('Элемент вышел из области видимости');
	},
	{
		rootMargin: '-50% 0px', // Отступы для области видимости (по умолчанию '-50% 0px')
		threshold: 0, // Пороговое значение видимости (по умолчанию 0)
	},
);
```

### 6. Плавная прокрутка для якорных ссылок

Добавляет плавную прокрутку ко всем ссылкам-якорям на странице.

```javascript
import { smootherAllAnchorLinks } from 'scroll-father';

smootherAllAnchorLinks();
```

## Описание функций

- **debounceScroll(callback, delay?)** Добавляет обработчик прокрутки с дебаунсом. Колбэк `callback` будет вызываться не
  чаще, чем раз в `delay` миллисекунд.

- **initInfiniteScroll(loadMoreCallback, options?)** Реализует бесконечную прокрутку, вызывая `loadMoreCallback`, когда
  пользователь достигает конца страницы. Параметр `options.threshold` определяет, за сколько пикселей до конца страницы
  следует вызвать колбэк.

- **initIntersectionSection($section, onStart, onEnd, options?)** Отслеживает элемент `$section` с помощью
  `IntersectionObserver`. Вызывает `onStart`, когда элемент появляется в области видимости, и `onEnd`, когда исчезает.

- **initScrollDirectionTracking()** Отслеживает направление скролла и устанавливает атрибут `data-scroll-direction` на
  `<body>` со значениями `"up"` или `"down"`.

- **trackScrollState(options?)** Отслеживает состояние скролла страницы и устанавливает атрибут (по умолчанию
  `data-scrolled`) на указанном элементе при прокрутке.

- **smootherAllAnchorLinks()** Добавляет плавную прокрутку ко всем ссылкам-якорям на странице, обеспечивая более плавный
  переход к целевым элементам.

## Сотрудничество

Мы приветствуем вклад! Не стесняйтесь отправлять проблемы или пул-реквесты через наш
[репозиторий на GitHub](https://github.com/Poliklot/scroll-father).

## Лицензия

Проект лицензирован под лицензией MIT — см. файл
[LICENSE](https://github.com/Poliklot/scroll-father/blob/master/LICENSE) для подробностей.
