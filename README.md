# Установка Moodle с помощью Docker

## Что такое Moodle?

Moodle — это система управления обучением с открытым исходным кодом, предназначенная для создания и администрирования онлайн-курсов. Moodle поддерживает разнообразные инструменты для организации контента, проведения оценок и общения, благодаря чему широко используется в учебных заведениях и компаниях по всему миру.

В этом руководстве мы рассмотрим процесс установки Moodle с использованием Docker и файла docker-compose.yml, что упростит развертывание и настройку системы.

### Предварительные требования
Убедитесь, что у вас установлены:

* Docker
* Docker Compose

Шаги по установке Moodle с Docker

1. клонируйте репозиторий:
```
git clone https://github.com/iSmartyPRO/docker-moodle.git moodle
```

2. Настройте переменные окружения
    Для работы с docker-compose.yml необходимо создать файл .env в той же директории, где находится ваш файл docker-compose.yml. В этом файле укажите следующие параметры:

    ```env
    DOCKER_CONTAINER_NAME=moodle-container
    MOODLE_PORT_HTTP=80
    MOODLE_PORT_HTTPS=443
    MOODLE_URL=http://localhost
    MOODLE_DATABASE_HOST=ваш_адрес_базы_данных
    MOODLE_DATABASE_NAME=имя_базы_данных
    MOODLE_DATABASE_USER=пользователь_базы_данных
    MOODLE_DATABASE_PASSWORD=пароль_базы_данных
    MOODLE_USERNAME=admin
    MOODLE_PASSWORD=admin_password
    MOODLE_LANG=ru
    TZ=Europe/Moscow
    ALLOW_EMPTY_PASSWORD=no
    ```
    Замените значения на свои данные.

3. Запустите контейнеры

    Теперь можно развернуть Moodle с помощью команды:

    ```bash
    docker-compose up -d
    ```
    Docker Compose загрузит необходимое изображение, создаст контейнер и развернет Moodle на указанном порту.

4. Доступ к Moodle
    После успешного запуска контейнеров вы сможете получить доступ к Moodle, открыв веб-браузер и введя URL, который вы указали в переменной MOODLE_URL (например, http://localhost).

5. Завершение работы и остановка контейнеров
Чтобы остановить и удалить контейнеры, используйте следующую команду:

    ```bash
    docker-compose down
    ```

Эта инструкция поможет быстро развернуть Moodle в Docker, используя Bitnami образ, который включает все необходимые зависимости для работы платформы.