# Scroll Father

- [🇬🇧 English documentation](README.md)

Scroll Father — это лёгкая библиотека на JavaScript/TypeScript для обработки событий скролла, определения направления скролла и интеграции с `IntersectionObserver`. Она помогает управлять динамическими классами и атрибутами на основе положения скролла и других событий, связанных со скроллом.

## Особенности

- **Определение состояния скролла:** Автоматически добавляет или удаляет атрибуты на основе положения скролла.
- **Определение направления скролла:** Добавляет `data-scroll-direction="up"` или `"down"` к элементу `<body>`.
- **Интеграция с IntersectionObserver:** Легко вызывайте коллбэки, когда элементы появляются или исчезают из области видимости.
- **Высокая настраиваемость:** Настройте атрибуты, элементы, отступы и многое другое.

## Установка

Установите через npm:

```bash
npm install scroll-father
```

Или добавьте через CDN:

```html
<script src="https://cdn.jsdelivr.net/npm/scroll-father/dist/index.js"></script>
```

## Использование

### 1. Определение состояния скролла
Автоматически добавляет атрибут (например, `data-scrolled`) к указанному элементу при прокрутке страницы.

```typescript
import ScrollFather from 'scroll-father';

const scrollFather = new ScrollFather({
  attribute: 'data-scrolled', // Default attribute
  element: document.body      // Default element is the <body>
});
```

### 2. Определение направления скролла
Определяет направление скролла и устанавливает атрибут (`data-scroll-direction="up"` или `"down"`) на элементе `<body>`.

```typescript
scrollFather.initScrollDirectionTracking();
```

### 3. IntersectionObserver для секций
Инициализируйте секцию для отслеживания, когда она появляется или исчезает из области видимости.

```typescript
scrollFather.initIntersectionSection(
  document.querySelector('.section') as HTMLElement,
  () => console.log('Section is in view'),
  () => console.log('Section is out of view')
);
```

## Опции конфигурации

- `ScrolledOptions`: Конфигурация для определения состояния скролла.
    - `attribute`: Имя атрибута, который будет установлен на элементе при скролле (по умолчанию `data-scrolled`).
    - `element`: Элемент, к которому будет применяться атрибут (по умолчанию `document.body`).
- `IntersectionOptions`: Опции для IntersectionObserver.
    - `rootMargin`: Отступ вокруг корня для пересечения (по умолчанию `-50% 0px`).
    - `threshold`: Порог для определения, когда секция считается в области видимости (по умолчанию `0`).

## Сотрудничество
Мы приветствуем вклад! Не стесняйтесь отправлять проблемы или пул-реквесты через наш [репозиторий на GitHub](https://github.com/Poliklot/scroll-father).

## Лицензия
Проект лицензирован под лицензией MIT — см. файл [LICENSE](https://github.com/Poliklot/scroll-father/blob/master/LICENSE) для подробностей.
