# Spec Kit: Constitution — `pagination-spaces-page-response`

## Goal
Единая и предсказуемая пагинация для списка пространств:
- `GET /api/spaces` (не-ADMIN)
- `GET /api/admin/spaces` (ADMIN)

Требование: обе операции возвращают `PageResponse<SpaceResponse>`, а для не-ADMIN применяют `page/size`.

## Non-goals
- Документы/версии/аттачменты
- Изменения авторизации/ролей
- Рефакторинг persistence “в одно SQL” для не-ADMIN (оптимизация позже)

## Success Criteria (коротко)
- ADMIN: `totalElements` = общее число spaces, контент ограничен `size`
- Не-ADMIN: `totalElements` = число доступных spaces пользователю, контент соответствует `page/size`
- сортировка контента стабильно по `createdAt DESC`

