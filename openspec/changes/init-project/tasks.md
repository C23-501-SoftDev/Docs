## 1. Инициализация проекта и инфраструктуры

- [ ] 1.1 Создать структуру Maven проекта и `pom.xml` с базовыми зависимостями (Spring Boot Starter Web, Data JPA, Security, Validation, PostgreSQL, Liquibase, Springdoc OpenAPI).
- [ ] 1.2 Настроить базовую структуру пакетов по Clean Architecture: `com.baza.domain`, `com.baza.application`, `com.baza.infrastructure`, `com.baza.web`.
- [ ] 1.3 Создать конфигурационные файлы `application.yml`, `application-dev.yml`, `application-test.yml`, `application-prod.yml`.
- [ ] 1.4 Настроить логирование через `logback-spring.xml`.

## 2. База данных и миграции

- [ ] 2.1 Настроить подключение к PostgreSQL в `application-dev.yml`.
- [ ] 2.2 Инициализировать Liquibase и создать первый changelog для создания таблиц `users`, `roles`, `user_roles`.
- [ ] 2.3 Создать SQL/YAML миграцию для вставки начальных данных (роли ADMIN, EDITOR, READER и дефолтный администратор).

## 3. Безопасность и Web

- [ ] 3.1 Реализовать `SecurityConfig` с настройкой `SecurityFilterChain` (Form Login, защита всех эндпоинтов).
- [ ] 3.2 Создать базовый `IndexController` и `index.html` (Thymeleaf) для корневого URL.
- [ ] 3.3 Настроить `UserDetailsService` для аутентификации через БД.

## 4. Документация и проверка

- [ ] 4.1 Проверить доступность Swagger UI по адресу `/swagger-ui.html`.
- [ ] 4.2 Убедиться в успешном прохождении `mvn clean install`.
