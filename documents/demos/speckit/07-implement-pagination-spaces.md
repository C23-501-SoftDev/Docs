# Spec Kit: Implement — что именно реализуем в коде

## Цель внедрения
Сделать одинаковую “пользовательскую” семантику пагинации для обоих эндпоинтов.

## Конкретные правки
- `SpaceController`
  - `GET /api/spaces` -> `ResponseEntity<PageResponse<SpaceResponse>>`
  - `GET /api/admin/spaces` -> `ResponseEntity<PageResponse<SpaceResponse>>`
  - сборка `PageResponse.of(content, page, size, totalElements)`

- `SpaceService`
  - подсчет `totalElements`:
    - ADMIN: `spaceRepository.count()`
    - не-ADMIN: `количество доступных spaceIds`
  - slicing:
    - сортировка по `createdAt DESC`
    - выбор подмассива `page/size`

## Ожидаемый результат
Swagger: контракты показывают `PageResponse` и корректные метаданные пагинации.

