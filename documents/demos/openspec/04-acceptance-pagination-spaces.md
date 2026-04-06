# OpenSpec Acceptance Criteria: пагинация `spaces`

## 1) ADMIN: корректные metadata и content
**Given** в системе есть `N` пространств.  
**When** выполнить `GET /api/admin/spaces?page=1&size=10`.  
**Then**
- `totalElements == N`
- `totalPages == ceil(N/10)`
- `content.size() <= 10`
- элементы в `content` отсортированы по `createdAt DESC`

## 2) Не-ADMIN: slicing по `page/size`
**Given** пользователь имеет доступ к `M` пространствам.  
**When** выполнить `GET /api/spaces?page=0&size=5`.  
**Then**
- `totalElements == M`
- `content.size() <= 5`
- `content` соответствует первыми 5 элементам списка, отсортированного по `createdAt DESC`

## 3) Вне диапазона `page`
**Given** `page` больше `totalPages - 1`.  
**When** выполнить вызов соответствующего эндпоинта.  
**Then**
- `content` пустой
- `totalElements` остаётся корректным

