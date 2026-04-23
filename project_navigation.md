# Навигация по документации проекта «База знаний»

Этот документ поможет быстро найти нужную документацию по задаче или цели. Структура ориентирована на задачи (что вы хотите сделать), а не просто на список файлов.

---

## 1. Начало работы

### 1.1. Что это за система? Какие функции?
| Документ | Путь | Назначение |
|----------|------|------------|
| Требования к системе | `Docs/base-requirements.md` | Полное описание: процессы, функциональные/нефункциональные/технические требования, stack |
| Логическая схема | `Docs/logic_scheme.md` | Архитектура компонентов, потоки данных, Mermaid-диаграмма |
| Ядро vs Фичи (MVP) | `Docs/documents/core_and_features.md` | Что входит в MVP, что — во вторую очередь |
| Глоссарий | `Docs/documents/010.glossary.md` | Определения терминов (БЗ, Space, Wiki-разметка, CRUD, Soft-delete и т.д.) |

### 1.2. Как начать работать с документацией?
| Документ | Путь | Назначение |
|----------|------|------------|
| README проекта | `Docs/readme.md` | Установка Git, Node.js, live-server, клонирование репозиториев |
| Навигация (этот файл) | `Docs/project_navigation.md` | Карта всех документов |

---

## 2. Анализ требований

### 2.1. Кто работает с системой? Каковы их роли и права?
| Документ | Путь | Назначение |
|----------|------|------------|
| Участники (Actors) | `Docs/documents/030.actors.md` | Читатель, Редактор, Администратор, System Actor — цели и описание |
| Матрица ролей (RBAC) | `Docs/documents/070.role-matrix.md` | Таблица прав по ролям, три уровня доступа (глобальный, пространство, документ) |

### 2.2. Какие сценарии использования?
| Документ | Путь | Назначение |
|----------|------|------------|
| Use Cases | `Docs/documents/060.use-cases.md` | Диаграмма вариантов использования, описания UC-1 (создание), UC-2 (откат), UC-3 (пространства) |

### 2.3. С какими данными работаем?
| Документ | Путь | Назначение |
|----------|------|------------|
| Сущности и жизненный цикл | `Docs/documents/050.entities.md` | 8 сущностей (User, Space, Document, Version, Attachment и др.), статусы документа, Mermaid-диаграмма |
| Моделирование данных (ER) | `Docs/documents/120.data-model.md` | Полная ER-диаграмма, 8 таблиц с типами/ограничениями/индексами, связи ON DELETE |

### 2.4. Как организован UI/UX?
| Документ | Путь | Назначение |
|----------|------|------------|
| UI/UX требования | `Docs/documents/110.ui-ux.md` | Экраны, принципы UX, accessibility, состояния интерфейса, UX-трансформации |
| Design Guide (стили) | `Docs/documents/design-guid.md` | Цветовая палитра, типографика, отступы, кнопки, формы, таблицы, CSS |

### 2.5. Проверка полноты требований
| Документ | Путь | Назначение |
|----------|------|------------|
| Матрица трассировки (RTM) | `Docs/documents/140.requirements-check.md` | Связь BR-ID → артефакты → элементы бэклога, статус покрытия |
| Трассировка базовых требований | `Docs/base-requirements.trace.md` |Трассировка base-requirements.md на backlog.json |
| Трассировка логической схемы | `Docs/logic_scheme.trace.md` |Трассировка logic_scheme.md на backlog.json |

---

## 3. Бэклог и планирование

### 3.1. Где весь бэклог?
| Ресурс | Путь | Назначение |
|--------|------|------------|
| Бэклог (JSON) | `Docs/documents/backlog.json` | Полный иерархический бэклог: Epics → Features → User Stories с метаданными и трассировкой |
| Визуализатор бэклога | `Docs/documents/index.html` | Открыть в браузере для интерактивного просмотра backlog.json |
| Подробные описания | `Docs/documents/backlog-descriptions/` | Папки повторяют структуру backlog.json, содержат `description.md` с детализацией по каждому элементу |

### 3.2. Структура папки backlog-descriptions/
Эпик-папки:
- `E1 Управление контентом (Content Management)/`
- `E2 Жизненный цикл и Версионность (Lifecycle & Versioning)/`
- `E3 Навигация и Поиск (Navigation & Search)/`
- `E4 Администрирование и Безопасность (Admin & Security)/`
- `E5 Экспорт и Отчетность (Export)/`

Каждая папка содержит вложенные Feature-папки → UserStory-папки → `description.md`.

### 3.3. Правила и стандарты работы с бэклогом
| Документ | Путь | Назначение |
|----------|------|------------|
| Структура backlog.json | `Docs/ai-analysis-core/backlog-structure.md` | JSON-схема, поля Epic/Feature/UserStory, metadata.requirements_check |
| Структура описаний | `Docs/ai-analysis-core/backlog-descriptions-structure.md` | Правила именования папок, содержание description.md, автоматизация синхронизации |
| Верификация бэклога | `Docs/ai-analysis-core/backlog-verification.md` | Как проводить трассировку, правила заполнения requirements_check, примеры JSON |
| Методология трассировки | `Docs/ai-analysis-core/backlog-trace.md` | Прямая и обратная трассировка, алгоритм, критерии успешности |
| CRUD-шаблон | `Docs/ai-analysis-core/crud-template.md` | Шаблон описания CRUD: модель данных, UI/UX, API, бизнес-логика, RBAC, история |

> **Примечание:** Файл `Docs/documents/backlog.md` не актуален — используйте `backlog.json` и `backlog-descriptions/`.

---

## 4. Процессы и сценарии

### 4.1. Как AI-аналитик должен работать с документацией?
| Документ | Путь | Назначение |
|----------|------|------------|
| Процесс анализа | `Docs/ai-analysis-core/analysis_process.md` | Пошаговый процесс: глоссарий → actors → entities → use-cases → role-matrix → data-model → RTM |
| Прототипы | `Docs/documents/prototypes/` | Папка с прототипами (включая `admin-panel/`) |
| Фреймворки (Spec-Driven) | `Docs/documents/framework.md` | Сравнение Kiro, Spec Kit, OpenSpec, OpenCode — выбор подхода для AI-агентов |

### 4.2. User Stories и Acceptance Criteria
User Stories описаны в `backlog.json` и детализированы в `backlog-descriptions/`. Файл `Docs/documents/080.user-stories.md` не актуален.

### 4.3. Epics и Features
Группировка в `Docs/documents/090.features-epics.md` описывает 5 Epic-ов и их Features. Актуальная структура — в `backlog.json`.

---

## 5. Технические детали

### 5.1. Стек технологий
Из `base-requirements.md`:
- **Бэкенд:** Java 17+, Spring Boot, Spring Security, Spring Data JPA, Maven, JGit
- **Фронтенд:** Thymeleaf (SSR), JavaScript/TypeScript, Tiptap Editor (WYSIWYG)
- **БД:** PostgreSQL 18
- **Хранилище:** Git (для .md файлов), Blob (для вложений)
- **Уведомления:** SMTP (асинхронная рассылка)

### 5.2. Какие ещё файлы есть?
| Документ | Путь | Назначение |
|----------|------|------------|
| Review (UI) | `Docs/documents/review.md` | Замечания и предложения по UI/UX документам |

---

## 6. Быстрый поиск по типам задач

| Если вам нужно... | Откройте |
|-------------------|----------|
| Понять, что делает система | `base-requirements.md`, `core_and_features.md` |
| Узнать архитектуру | `logic_scheme.md`, `base-requirements.md` (Раздел «Технические требования») |
| Узнать роли и права | `documents/030.actors.md`, `documents/070.role-matrix.md` |
| Узнать структуру БД | `documents/120.data-model.md`, `documents/050.entities.md` |
| Найти конкретную задачу | `documents/backlog.json` или `documents/index.html` |
| Прочитать детали задачи | `documents/backlog-descriptions/.../description.md` |
| Убедиться, что требование покрыто | `documents/140.requirements-check.md`, `base-requirements.trace.md`, `logic_scheme.trace.md` |
| Шаблоны описания CRUD | `ai-analysis-core/crud-template.md` |
| Правила работы с бэклогом | `ai-analysis-core/backlog-structure.md`, `ai-analysis-core/backlog-descriptions-structure.md` |
| Как аналитику работать с репо | `ai-analysis-core/analysis_process.md`, `ai-analysis-core/backlog-trace.md`, `ai-analysis-core/backlog-verification.md` |
| Дизайн-систему и стили | `documents/design-guid.md`, `documents/110.ui-ux.md` |
| Настроить среду | `readme.md` |
