# Design Guide (UI/UX стили и палитра)

## Цель
Данный документ описывает базовые стили интерфейса, цветовую палитру и принципы визуального оформления системы документации.

---

## Цветовая палитра

### Основные цвета
| Назначение        | Цвет        | HEX       |
|------------------|------------|----------|
| Primary          | Синий      | #2563EB  |
| Secondary        | Серый      | #6B7280  |
| Background       | Светлый    | #F9FAFB  |
| Surface          | Белый      | #FFFFFF  |
| Border           | Светло-серый | #E5E7EB |

---

### Состояния
| Состояние  | Цвет       | HEX       |
|-----------|-----------|----------|
| Success   | Зеленый   | #16A34A  |
| Error     | Красный   | #DC2626  |
| Warning   | Оранжевый | #F59E0B  |
| Info      | Голубой   | #0EA5E9  |

---

## Типографика

### Шрифт
- Основной: `Inter`, `Arial`, sans-serif

### Размеры
| Элемент        | Размер |
|---------------|--------|
| Заголовок H1  | 32px   |
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
background: #2563EB;
color: white;
border-radius: 8px;
padding: 8px 16px;


### Secondary Button
background: #E5E7EB;
color: #111827;

### Hover
opacity: 0.9;

---

## Карточки и контейнеры

background: #FFFFFF;
border: 1px solid #E5E7EB;
border-radius: 12px;
padding: 16px;
box-shadow: 0 1px 3px rgba(0,0,0,0.1);

## Таблицы
- Ширина 100%
- Заголовок (thead): background #F9FAFB, font-weight 600, border-bottom 2px solid #E5E7EB
- Строки (tbody tr): border-bottom 1px solid #E5E7EB
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
  - Normal: border 1px solid #E5E7EB; background #FFFFFF
  - Active: background #2563EB; color #FFFFFF; border none
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
border: 1px solid #E5E7EB;
border-radius: 6px;
padding: 8px;

### Focus
border-color: #2563EB;
outline: none;

---

## Базовые CSS стили
body {
font-family: Inter, Arial, sans-serif;
background-color: #F9FAFB;
color: #111827;
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

