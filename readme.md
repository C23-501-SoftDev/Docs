# База Знаний

Проект по систематизации и управлению требованиями, процессами и бэклогом.

## Разработка и просмотр

### Динамическая проверка бэклога

Для интерактивного просмотра бэклога используйте `index.html` в директории [`documents/`](documents/).

**Запуск:**

```bash
# Переход в директорию проекта (если требуется)
cd documents
# Запуск локального сервера
live-server
```

## Установка и настройка окружения

### 1. Кому что нужно устанавливать (памятка для команды)

| Роль | Необходимые программы |
|------|----------------------|
| **Все** | Git, браузер (Chrome/Firefox/Edge), live-server (Node.js) |
| **Backend-разработчик** | Java 25 JDK, Maven 3.9.14, PostgreSQL 18 |
| **Frontend-разработчик** | Node.js |
| **Тестировщик (QA)** | Браузер, Postman(или альтернатива, например, Insomnia), pgAdmin) |
| **Аналитик** | Только общий набор |
| **Техлид** | Всё вышеперечисленное |

### 2. Node.js, npm и live-server

#### Установка Node.js (версия 18+):

- Скачайте установщик с [nodejs.org](https://nodejs.org) (рекомендуется LTS-версия)

#### Проверка:

```bash
node -v
npm -v
```

#### Установка live-server для просмотра документации
```bash
npm install -g live-server
```

#### Как использовать live-server:
1. Откройте терминал (командную строку)
2. Перейдите в папку с документацией проекта
3. Запустите live-server:
```cmd
live-server
```
4. Браузер автоматически откроется на адресе http://127.0.0.1:8080
5. Вы увидите интерактивный бэклог, где можно просматривать Epic, Feature и User Story с их связями
**Остановка live-server:** нажмите Ctrl+C в терминале

### 3. Java 25 (JDK)

Для работы бэкенда необходима Java версии 25 или новее.

**Скачивание с официального сайта:**

1. Перейдите по ссылке:  
   [https://www.oracle.com/java/technologies/javase/jdk25-archive-downloads.html](https://www.oracle.com/java/technologies/javase/jdk25-archive-downloads.html)

2. Выберите установщик для вашей операционной системы:

   | ОС | Тип файла |
   |----|-----------|
   | Windows | `.exe` или `.msi` (x64 Installer) |
   | macOS | `.dmg` (Arm 64 или x64 в зависимости от процессора) |
   | Linux | `.tar.gz` (x64) |

3. Запустите скачанный файл и следуйте инструкциям установщика

**Проверка установки:**

Откройте командную строку (терминал) и выполните:

```bash
java -version
```

Вы должны увидеть что-то вроде:
java version "25" 2025-09-16
Java(TM) SE Runtime Environment (build 25+...)

### 4. Maven (система сборки)

**Если используете IntelliJ IDEA и запускать проект планируете из неё, то этот пункт можно пропустить, эта IDE уже имеет встроенный maven**

Maven используется для управления зависимостями и сборки бэкенда.  
Устанавливается последняя стабильная версия (на текущий момент — **3.9.14**).

#### Windows

1. Скачайте архив `apache-maven-3.9.14-bin.zip` с официального сайта:  
   [https://maven.apache.org/download.cgi](https://maven.apache.org/download.cgi)

2. Распакуйте архив в папку, например: `C:\maven`

3. Добавьте `C:\maven\bin` в переменную окружения `PATH`:
   - Нажмите `Win + R`, введите `sysdm.cpl`
   - Перейдите на вкладку `Advanced` → `Environment Variables`
   - В разделе `System variables` найдите `Path`, нажмите `Edit`
   - Добавьте новую строку: `C:\maven\bin`
   - Нажмите `OK` во всех окнах

#### macOS
```bash
brew install maven
```

#### Linux (Ubuntu/Debian)
```bash
sudo apt update
sudo apt install maven
```

#### Проверка после установки (для всех ОС):
```cmd
mvn -version
```

### 5. Git

Git необходим для клонирования репозитория и работы с версиями документов.

#### Установка:

- **Windows**: скачать с [git-scm.com](https://git-scm.com)
- **macOS**: `brew install git`
- **Linux**: `sudo apt install git`

#### Настройка (обязательно для коммитов):

```bash
git config --global user.name "Ваше Имя"
git config --global user.email "ваш.email@example.com"
```

#### Проверка
```cmd
git --version
```

#### Клонирование репозиториев:
```cmd
git clone https://github.com/C23-501-SoftDev/Docs.git
git clone https://github.com/C23-501-SoftDev/Project.git
```

### 6. PostgreSQL

У большинства уже установлен через pgAdmin в рамках других дисциплин.  
Если нет — установите PostgreSQL 18 с официального сайта: https://www.postgresql.org/download/

#### Создание базы данных (через pgAdmin)

1. Откройте pgAdmin
2. Подключитесь к серверу
3. В окне Query Tools (Инструмент запросов) для базы postgres введите следующий SQL-запрос

```sql
CREATE DATABASE knowledge_base
   WITH 
   OWNER = postgres
   ENCODING = 'UTF8'
   CONNECTION LIMIT = -1;
```
А потом ещё один в окне Query Tools созданной БД
```sql
-- =====================================================
-- 1. Таблица пользователей
-- =====================================================
CREATE TABLE users (
    id              BIGSERIAL PRIMARY KEY,
    login           VARCHAR(100) NOT NULL UNIQUE,
    password_hash   VARCHAR(255) NOT NULL,
    email           VARCHAR(255) NOT NULL UNIQUE,
    role            VARCHAR(20) NOT NULL CHECK (role IN ('Admin', 'Editor', 'Reader')),
    created_at      TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at      TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

COMMENT ON TABLE users IS 'Зарегистрированные пользователи системы';
COMMENT ON COLUMN users.role IS 'Глобальная роль: Admin, Editor, Reader';

-- =====================================================
-- 2. Таблица пространств
-- =====================================================
CREATE TABLE spaces (
    id              BIGSERIAL PRIMARY KEY,
    name            VARCHAR(200) NOT NULL UNIQUE,
    description     TEXT,
    owner_id        BIGINT NOT NULL REFERENCES users(id) ON DELETE RESTRICT,
    created_at      TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at      TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

COMMENT ON TABLE spaces IS 'Логические группировки документов с едиными правами доступа';
COMMENT ON COLUMN spaces.owner_id IS 'Ответственный редактор (пользователь с ролью Editor или Admin)';

-- =====================================================
-- 3. Таблица прав доступа к пространствам
-- =====================================================
CREATE TABLE space_permissions (
    id              BIGSERIAL PRIMARY KEY,
    space_id        BIGINT NOT NULL REFERENCES spaces(id) ON DELETE CASCADE,
    user_id         BIGINT NOT NULL REFERENCES users(id) ON DELETE CASCADE,
    permission_type VARCHAR(20) NOT NULL CHECK (permission_type IN ('READ', 'WRITE', 'OWNER')),
    granted_at      TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    
    UNIQUE(space_id, user_id, permission_type)
);

COMMENT ON TABLE space_permissions IS 'Права доступа пользователей к конкретным пространствам';
COMMENT ON COLUMN space_permissions.permission_type IS 'READ - чтение, WRITE - создание/редактирование, OWNER - полный контроль';

-- =====================================================
-- 4. Таблица шаблонов документов
-- =====================================================
CREATE TABLE templates (
    id              BIGSERIAL PRIMARY KEY,
    name            VARCHAR(200) NOT NULL UNIQUE,
    description     TEXT,
    content         TEXT NOT NULL,
    role            VARCHAR(20) NOT NULL CHECK (role IN ('Admin', 'Editor', 'Reader', 'Developer', 'Analyst')),
    is_system       BOOLEAN NOT NULL DEFAULT TRUE,
    created_at      TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at      TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

COMMENT ON TABLE templates IS 'Предустановленные шаблоны документов для разных ролей';
COMMENT ON COLUMN templates.role IS 'Роль, для которой доступен шаблон';
COMMENT ON COLUMN templates.is_system IS 'Системные шаблоны нельзя изменять (MVP)';

-- =====================================================
-- 5. Таблица документов
-- =====================================================
CREATE TABLE documents (
    id              BIGSERIAL PRIMARY KEY,
    title           VARCHAR(500) NOT NULL,
    content         TEXT,
    status          VARCHAR(20) NOT NULL DEFAULT 'Draft' CHECK (status IN ('Draft', 'Published', 'Deleted')),
    is_deleted      BOOLEAN NOT NULL DEFAULT FALSE,
    author_id       BIGINT NOT NULL REFERENCES users(id) ON DELETE RESTRICT,
    space_id        BIGINT NOT NULL REFERENCES spaces(id) ON DELETE RESTRICT,
    template_id     BIGINT NULL REFERENCES templates(id) ON DELETE SET NULL,
    parent_document_id BIGINT NULL REFERENCES documents(id) ON DELETE CASCADE,
    deleted_at      TIMESTAMP,
    created_at      TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at      TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

COMMENT ON TABLE documents IS 'Основные единицы хранения информации (документы)';
COMMENT ON COLUMN documents.status IS 'Draft - черновик, Published - опубликован, Deleted - в корзине';
COMMENT ON COLUMN documents.is_deleted IS 'Флаг мягкого удаления';
COMMENT ON COLUMN documents.deleted_at IS 'Дата мягкого удаления (заполняется автоматически)';
COMMENT ON COLUMN documents.template_id IS 'Какой шаблон использовался при создании';
COMMENT ON COLUMN documents.parent_document_id IS 'Для иерархической структуры документов';

-- Индексы для документов
CREATE INDEX idx_documents_space_status ON documents(space_id, status) WHERE is_deleted = FALSE;
CREATE INDEX idx_documents_not_deleted ON documents(is_deleted) WHERE is_deleted = FALSE;
CREATE INDEX idx_documents_author ON documents(author_id);
CREATE INDEX idx_documents_created_at ON documents(created_at);
CREATE INDEX idx_documents_updated_at ON documents(updated_at);

-- =====================================================
-- 6. Таблица версий документов
-- =====================================================
CREATE TABLE versions (
    id              BIGSERIAL PRIMARY KEY,
    document_id     BIGINT NOT NULL REFERENCES documents(id) ON DELETE RESTRICT,
    git_hash        VARCHAR(40) NOT NULL,
    author_id       BIGINT NOT NULL REFERENCES users(id) ON DELETE RESTRICT,
    comment         VARCHAR(500),
    restored_from_version_id BIGINT NULL REFERENCES versions(id) ON DELETE SET NULL,
    is_deleted      BOOLEAN NOT NULL DEFAULT FALSE,
    created_at      TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

COMMENT ON TABLE versions IS 'История изменений документов (метаданные Git-коммитов)';
COMMENT ON COLUMN versions.git_hash IS 'SHA-1 хэш коммита в Git-репозитории';
COMMENT ON COLUMN versions.restored_from_version_id IS 'Если версия создана через откат, указываем ID версии, из которой восстановили';

CREATE INDEX idx_versions_document ON versions(document_id);
CREATE INDEX idx_versions_git_hash ON versions(git_hash);
CREATE INDEX idx_versions_author ON versions(author_id);

-- =====================================================
-- 7. Таблица вложений
-- =====================================================
CREATE TABLE attachments (
    id              BIGSERIAL PRIMARY KEY,
    document_id     BIGINT NOT NULL REFERENCES documents(id) ON DELETE RESTRICT,
    version_id      BIGINT NULL REFERENCES versions(id) ON DELETE CASCADE,
    filename        VARCHAR(255) NOT NULL,
    content_type    VARCHAR(100),
    size_bytes      BIGINT NOT NULL,
    storage_path    VARCHAR(500) NOT NULL,
    is_deleted      BOOLEAN NOT NULL DEFAULT FALSE,
    uploaded_at     TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    uploaded_by     BIGINT REFERENCES users(id) ON DELETE SET NULL
);

COMMENT ON TABLE attachments IS 'Метаданные файлов, прикреплённых к документам';
COMMENT ON COLUMN attachments.storage_path IS 'Путь к файлу в blob-хранилище';
COMMENT ON COLUMN attachments.version_id IS 'К какой версии документа относится вложение (NULL = актуальное)';

CREATE INDEX idx_attachments_document ON attachments(document_id);
CREATE INDEX idx_attachments_version ON attachments(version_id);
CREATE INDEX idx_attachments_uploaded_by ON attachments(uploaded_by);

-- =====================================================
-- 8. Таблица прав доступа на уровне документа
-- =====================================================
CREATE TABLE document_permissions (
    id              BIGSERIAL PRIMARY KEY,
    document_id     BIGINT NOT NULL REFERENCES documents(id) ON DELETE CASCADE,
    user_id         BIGINT NOT NULL REFERENCES users(id) ON DELETE CASCADE,
    permission_type VARCHAR(20) NOT NULL CHECK (permission_type IN ('READ', 'WRITE', 'OWNER')),
    granted_by      BIGINT NOT NULL REFERENCES users(id) ON DELETE SET NULL,
    granted_at      TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    
    UNIQUE(document_id, user_id, permission_type)
);

COMMENT ON TABLE document_permissions IS 'Дополнительные права на конкретный документ (поверх прав пространства)';
COMMENT ON COLUMN document_permissions.permission_type IS 'READ, WRITE, OWNER';

CREATE INDEX idx_doc_permissions_document ON document_permissions(document_id);
CREATE INDEX idx_doc_permissions_user ON document_permissions(user_id);

-- =====================================================
-- Триггеры и функции
-- =====================================================

-- Функция для автоматического обновления updated_at
CREATE OR REPLACE FUNCTION update_updated_at_column()
RETURNS TRIGGER AS $$
BEGIN
    NEW.updated_at = CURRENT_TIMESTAMP;
    RETURN NEW;
END;
$$ LANGUAGE plpgsql;

-- Триггеры для updated_at
CREATE TRIGGER trigger_users_updated_at BEFORE UPDATE ON users FOR EACH ROW EXECUTE FUNCTION update_updated_at_column();
CREATE TRIGGER trigger_spaces_updated_at BEFORE UPDATE ON spaces FOR EACH ROW EXECUTE FUNCTION update_updated_at_column();
CREATE TRIGGER trigger_documents_updated_at BEFORE UPDATE ON documents FOR EACH ROW EXECUTE FUNCTION update_updated_at_column();
CREATE TRIGGER trigger_templates_updated_at BEFORE UPDATE ON templates FOR EACH ROW EXECUTE FUNCTION update_updated_at_column();

-- Функция для автоматического заполнения deleted_at и статуса при soft-delete
CREATE OR REPLACE FUNCTION set_deleted_at()
RETURNS TRIGGER AS $$
BEGIN
    IF NEW.is_deleted = TRUE AND OLD.is_deleted = FALSE THEN
        NEW.deleted_at = CURRENT_TIMESTAMP;
        NEW.status = 'Deleted';
    ELSIF NEW.is_deleted = FALSE AND OLD.is_deleted = TRUE THEN
        NEW.deleted_at = NULL;
        NEW.status = 'Published';
    END IF;
    RETURN NEW;
END;
$$ LANGUAGE plpgsql;

CREATE TRIGGER trigger_documents_set_deleted_at
    BEFORE UPDATE ON documents
    FOR EACH ROW
    EXECUTE FUNCTION set_deleted_at();

-- Функция для каскадного мягкого удаления зависимостей
CREATE OR REPLACE FUNCTION soft_delete_dependencies()
RETURNS TRIGGER AS $$
BEGIN
    IF NEW.is_deleted = TRUE AND OLD.is_deleted = FALSE THEN
        UPDATE versions SET is_deleted = TRUE 
        WHERE document_id = NEW.id AND is_deleted = FALSE;
        
        UPDATE attachments SET is_deleted = TRUE 
        WHERE document_id = NEW.id AND is_deleted = FALSE;
    END IF;
    RETURN NEW;
END;
$$ LANGUAGE plpgsql;

CREATE TRIGGER trigger_documents_soft_delete_deps
    AFTER UPDATE ON documents
    FOR EACH ROW
    EXECUTE FUNCTION soft_delete_dependencies();

-- Функция для физического удаления документа
CREATE OR REPLACE FUNCTION hard_delete_document(p_document_id BIGINT)
RETURNS VOID AS $$
BEGIN
    DELETE FROM versions WHERE document_id = p_document_id;
    DELETE FROM attachments WHERE document_id = p_document_id;
    DELETE FROM document_permissions WHERE document_id = p_document_id;
    DELETE FROM documents WHERE id = p_document_id;
END;
$$ LANGUAGE plpgsql SECURITY DEFINER;

COMMENT ON FUNCTION hard_delete_document IS 'Полное физическое удаление документа (только для администратора)';
```