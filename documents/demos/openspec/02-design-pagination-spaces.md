# OpenSpec Design: Пагинация `spaces` через `PageResponse`

## Контракт API (что меняется)
Оба эндпоинта должны возвращать единый контейнер:

- `GET /api/spaces` -> `PageResponse<SpaceResponse>`
- `GET /api/admin/spaces` -> `PageResponse<SpaceResponse>`

Параметры:
- `page` (0-based)
- `size`

## Логика поведения

### ADMIN
1. Получить `totalElements = SpaceRepository.count()`
2. Получить страницу через `SpaceRepository.findAll(page, size)` (уже существует)
3. Вернуть `PageResponse.of(content, page, size, totalElements)`

### Не-ADMIN
1. Получить список доступных пространств пользователя из `SpacePermissionRepository`
2. Получить объекты `Space` для этих ID
3. Отсортировать по `createdAt DESC`
4. Применить slicing `page/size` к отсортированному списку
5. Вернуть `PageResponse.of(content, page, size, totalElements)`

## Детали сортировки
- Текущая реализация репозитория сортирует по `createdAt DESC`; дизайн фиксирует это как источник истины.

## Ограничения/риски
- Для не-ADMIN демонстрационная реализация может потребовать загрузки множества `Space` в память перед slicing.
- На уровне демонстрации это приемлемо; дальнейшая оптимизация может быть сделана позже.

## Маппинг “требование -> код”
С высокой вероятностью изменения затронут:
- `SpaceController` (return type и сборка PageResponse)
- `SpaceService` (подсчет total + slicing/сортировка для не-ADMIN)
- (опционально) `SpaceRepository` (если понадобится count-метод/способ получения total)

