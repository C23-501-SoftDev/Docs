# Spec Kit: Tasks — чеклист изменений

1. `SpaceController`
   - заменить return type на `PageResponse<SpaceResponse>`
   - собрать `PageResponse.of(...)` используя `totalElements`

2. `SpaceService`
   - добавить методы подсчёта:
     - `countAllSpaces()` (для ADMIN)
     - `countSpacesForUser(userId, isAdmin)` (для не-ADMIN)
   - добавить slicing для не-ADMIN

3. Проверка
   - убедиться, что Swagger отображает `PageResponse` метаданные
   - прогнать сценарии:
     - ADMIN page=0/1 size=10
     - не-ADMIN page=0/size=5

