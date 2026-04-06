# Spec Kit: Plan — пофазный план внедрения

## Plan steps
1. Изменить API-контракты:
   - `SpaceController` возвращает `ResponseEntity<PageResponse<SpaceResponse>>` для обоих эндпоинтов
2. Добавить в application слой подсчет `totalElements`:
   - ADMIN: `SpaceRepository.count()`
   - не-ADMIN: `count = число доступных spaceIds`
3. Реализовать slicing:
   - ADMIN: страница из `SpaceRepository.findAll(page,size)`
   - не-ADMIN: сортировка `createdAt DESC` + slicing `page/size`
4. Сборка `PageResponse.of(...)` в контроллере (или сервисе — согласовать дизайн, но в демонстрации достаточно одного места)
5. Ручная проверка через Swagger UI.

## Deliverables
- Обновленные контроллеры/сервисы
- Обновленные OpenAPI схемы (generic `PageResponse<T>`)

