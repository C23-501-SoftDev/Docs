# Spec Kit: Specify — что именно должны сделать артефакты

## In scope
1. Контракт ответов
   - `GET /api/spaces` -> `PageResponse<SpaceResponse>`
   - `GET /api/admin/spaces` -> `PageResponse<SpaceResponse>`
2. Пагинация контента:
   - ADMIN: JPA paging (по `createdAt DESC`)
   - Не-ADMIN: сортировка по `createdAt DESC` + slicing `page/size`
3. Подсчет `totalElements` для обеих ролей

## Expected inputs
- `page` (0-based) и `size` из query params
- `currentUser` и флаг `isAdmin`

## Output schema (контракт)
- `PageResponse` должен заполнять:
  - `content`
  - `page`, `size`
  - `totalElements`
  - `totalPages`, `last` (через `PageResponse.of(...)`)

