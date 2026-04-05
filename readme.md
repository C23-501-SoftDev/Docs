# База Знаний

Проект по систематизации и управлению требованиями, процессами и бэклогом.

## Разработка и просмотр

### Динамическая проверка бэклога

#### Установка Node.js (версия 18+) + live-server:

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

Для интерактивного просмотра бэклога используйте `index.html` в директории [`documents/`](documents/).

## Установка и настройка окружения


### Git

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

#### Рекомендуется скачать GitHub Desktop (исключительно для удобства)

##### 1. Скачивание и установка GitHub Desktop

1. Перейдите на официальный сайт: [https://desktop.github.com](https://desktop.github.com)
2. Нажмите кнопку **Download for Windows (или macOS)**.
3. Запустите скачанный установочный файл.
4. Следуйте инструкциям мастера установки (оставьте настройки по умолчанию).
5. После установки запустите GitHub Desktop.
6. Войдите в свой аккаунт GitHub (нажмите *Sign in* и авторизуйтесь в браузере).

##### 2. Клонирование репозитория `Docs`

1. В GitHub Desktop нажмите `File` → `Clone repository`.
2. Перейдите на вкладку **URL**.
3. В поле *Repository URL* введите: https://github.com/C23-501-SoftDev/Docs.git
4. В поле *Local path* выберите папку, куда сохранить репозиторий.
5. Нажмите **Clone**.
**Аналогично с репозиторием Project по ссылке:** https://github.com/C23-501-SoftDev/Project.git

##### 3. Проверка

После клонирования оба репозитория появятся в левой боковой панели GitHub Desktop. Вы можете открыть их в проводнике через контекстное меню (правой кнопкой мыши по репозиторию → `Show in Explorer` / `Reveal in Finder`).