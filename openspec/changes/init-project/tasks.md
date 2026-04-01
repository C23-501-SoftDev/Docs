## 1. Инициализация проекта и инфраструктуры

- [x] 1.1 Создать структуру Maven проекта и `pom.xml` с базовыми зависимостями (Spring Boot Starter Web, Data JPA, Security, Validation, PostgreSQL, Liquibase, Springdoc OpenAPI).
- [x] 1.2 Настроить базовую структуру пакетов по Clean Architecture: `com.baza.domain`, `com.baza.application`, `com.baza.infrastructure`, `com.baza.web`.
- [x] 1.3 Создать конфигурационные файлы `application.yml`, `application-dev.yml`, `application-test.yml`, `application-prod.yml`.
- [x] 1.4 Настроить логирование через `logback-spring.xml`.

## 2. База данных и миграции

- [x] 2.1 Настроить подключение к PostgreSQL в `application-dev.yml`.
- [x] 2.2 Инициализировать Liquibase и создать первый changelog для создания таблиц `users`, `roles`, `user_roles`.
- [x] 2.3 Создать SQL/YAML миграцию для вставки начальных данных (роли ADMIN, EDITOR, READER и дефолтный администратор).

## 3. Безопасность и Web

- [x] 3.1 Реализовать `SecurityConfig` с настройкой `SecurityFilterChain` (Form Login, защита всех эндпоинтов).
- [x] 3.2 Создать базовый `IndexController` и `index.html` (Thymeleaf) для корневого URL.
- [x] 3.3 Настроить `UserDetailsService` для аутентификации через БД.

## 4. Документация и проверка

- [x] 4.1 Проверить доступность Swagger UI по адресу `/swagger-ui.html`.
- [x] 4.2 Убедиться в успешном прохождении `mvn clean install`.
