# Design Guide (UI/UX стили и палитра)

## Цель
Данный документ описывает базовые стили интерфейса, цветовую палитру и принципы визуального оформления системы документации.

---

## Цветовая палитра

### Основные цвета
| Назначение        | Цвет        | HEX       |
|------------------|------------|----------|
| Primary          | Indigo     | #6366F1  |
| Primary Hover    | Indigo     | #4F46E5  |
| Primary Light    | Светлый    | #EEF2FF  |
| Secondary        | Серый      | #6B7280  |
| Background       | Светлый    | #F8FAFC  |
| Surface          | Белый      | #FFFFFF  |
| Border           | Светло-серый | #E2E8F0 |
| Text Primary     | Тёмный     | #0F172A  |
| Text Secondary   | Серый      | #475569  |

---

### Состояния
| Состояние  | Цвет       | HEX       |
|-----------|-----------|----------|
| Success   | Зеленый   | #22C55E  |
| Error     | Красный   | #EF4444  |
| Warning   | Оранжевый | #F59E0B  |

---

## Типографика

### Шрифт
- Основной: `Inter`, `Arial`, sans-serif

### Размеры
| Элемент        | Размер |
|---------------|--------|
| Заголовок H1  | 24px (в document-view) |
| Заголовок H2  | 24px   |
| Заголовок H3  | 20px   |
| Основной текст| 16px   |
| Малый текст   | 14px   |

### Вес
- Regular (400)
- Medium (500)
- Bold (700)

---

## Отступы и сетка

### Базовая единица
- 8px (используется для всех отступов)

### Примеры
- Малый отступ: 8px
- Средний: 16px
- Большой: 24px
- Очень большой: 32px

---

## Кнопки

### Primary Button
background: #6366F1;
color: white;
border-radius: 6px;
padding: 8px 16px;


### Secondary Button
background: #E2E8F0;
color: #0F172A;

### Hover
opacity: 0.9;

---

## Карточки и контейнеры

background: #FFFFFF;
border: 1px solid #E2E8F0;
border-radius: 16px;
padding: 16px;
box-shadow: 0 1px 2px rgba(0,0,0,0.05);

## Таблицы
- Ширина 100%
- Заголовок (thead): background #F8FAFC, font-weight 600, border-bottom 2px solid #E2E8F0
- Строки (tbody tr): border-bottom 1px solid #E2E8F0
- Отступы (padding): 12px 16px
- Текст при наведении (hover): background #F3F4F6

## Фильтры
- Основа: Input (см. раздел Формы) или выпадающий список (Select)
- Label: font-weight 500, font-size 14px
- Gap: 8px между элементами фильтрации
- Кнопка сброса: Secondary style, но меньше размер
## Пагинация
- Контейнер: flex, gap 8px, align-items center
- Кнопки (страницы):
  - Normal: border 1px solid #E2E8F0; background #FFFFFF
  - Active: background #6366F1; color #FFFFFF; border none
  - Disabled: opacity 0.5, cursor not-allowed

## Навигация

- Левая панель:
  - фиксированная ширина
  - вертикальный список
- Активный элемент:
background: #E0E7FF;
color: #1D4ED8;

---

## Формы

### Input
border: 1px solid #E2E8F0;
border-radius: 6px;
padding: 8px;

### Focus
border-color: #6366F1;
outline: none;

---

## Базовые CSS-переменные
```css
:root {
    --primary-color: #6366f1;
    --primary-hover: #4f46e5;
    --primary-light: #eef2ff;
    --secondary-color: #6b7280;
    --danger-color: #ef4444;
    --success-color: #22c55e;
    --bg-color: #f8fafc;
    --text-color: #0f172a;
    --text-secondary: #475569;
    --border-color: #e2e8f0;
    --radius-sm: 6px;
    --radius-md: 10px;
    --radius-lg: 16px;
    --shadow-sm: 0 1px 2px rgba(0,0,0,0.05);
    --shadow-md: 0 4px 6px -1px rgba(0,0,0,0.1);
    --shadow-lg: 0 10px 15px -3px rgba(0,0,0,0.1);
    --transition: all 0.2s ease;
}
```

## Базовые CSS стили
body {
font-family: Inter, Arial, sans-serif;
background-color: #F8FAFC;
color: #0F172A;
margin: 0;
}

h1, h2, h3 {
font-weight: 600;
}

button {
cursor: pointer;
border: none;
}

.container {
max-width: 1200px;
margin: 0 auto;
padding: 16px;
}

---

## Accessibility

- Контраст текста не ниже WCAG AA
- Поддержка клавиатурной навигации
- Видимый focus state
- Размер кликабельных элементов ≥ 40px

---

## Принципы дизайна

- Минимализм
- Консистентность
- Предсказуемость
- Обратная связь
- Удобство чтения

---

## Будущие улучшения

- Темная тема
- Design system (компоненты)
- UI-kit
- Figma макеты

