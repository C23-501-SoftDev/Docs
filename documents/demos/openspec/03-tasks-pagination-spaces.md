# OpenSpec Tasks: внедрение пагинации `spaces`

## Таск 1 — Контракт ответов
Изменить тип ответа контроллера:
- `GET /api/spaces` заменить `ResponseEntity<List<SpaceResponse>>` на `ResponseEntity<PageResponse<SpaceResponse>>`
- `GET /api/admin/spaces` заменить `ResponseEntity<List<SpaceResponse>>` на `ResponseEntity<PageResponse<SpaceResponse>>`

Ожидаемо: контракты Swagger/OpenAPI обновятся.

## Таск 2 — totalElements для ADMIN
Добавить в application layer:
- метод `SpaceService.countAllSpaces()`

И использовать его в сборке `PageResponse`.

## Таск 3 — totalElements и slicing для не-ADMIN
Добавить в `SpaceService`:
- метод `countSpacesForUser(userId, isAdmin)` (для isAdmin == true можно проксировать в total)
- для не-ADMIN:
  - получить доступные spaceIds
  - отсортировать соответствующие `Space` по `createdAt DESC`
  - сделать slicing `page/size`

## Таск 4 — сборка PageResponse
В `SpaceController` собрать:
- `PageResponse.of(content, page, size, totalElements)`

## Таск 5 — Минимальная проверка вручную
Прогнать сценарии через Swagger:
- ADMIN: `GET /api/admin/spaces?page=0&size=1` => `totalElements` и `content.size<=1`
- не-ADMIN: `GET /api/spaces?page=0&size=1` => `content.size<=1` и metadata совпадает с числом доступных пространств

