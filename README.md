## Сервис курсов валют

Это приложение Spring Boot, которое получает курсы валют от Центрального банка Российской Федерации (ЦБ РФ) и сохраняет их в базе данных PostgreSQL.

## Функционал

- Получает последние курсы валют из API ЦБ РФ.
- Сохраняет историю курсов валют в базе данных.
- Использует составной первичный ключ для отслеживания курсов валют по дате.
- Запускается по расписанию каждый час.
- Контейнеризировано с помощью Docker.

## Необходимые условия

- Java 17 или более поздняя версия
- Maven
- Docker
- Docker Compose
- База данных PostgreSQL

## Настройка

- **Подключение к базе данных:**
  - Настройте параметры подключения к базе данных в файле `application.yml`, включая URL-адрес, имя пользователя и пароль.
- **URL-адрес API ЦБ РФ:**
  - URL-адрес API ЦБ РФ настроен в файле `application.yml`.
- **Расписание:**
  - Задача получения данных о курсах валют запланирована на запуск каждый час с использованием аннотации Spring `@Scheduled`.

## Запуск приложения

**С помощью Docker Compose:**

1.  **Сборка образа Docker:**
    ```bash
    docker-compose build
    ```

2.  **Запуск контейнеров Docker:**
    ```bash
    docker-compose up -d
    ```

Это запустит приложение и контейнеры базы данных PostgreSQL.

**Локальный запуск (без Docker):**

1.  **Запуск базы данных PostgreSQL:**
    - Убедитесь, что PostgreSQL установлен и запущен.
    - Создайте базу данных с именем `your_database_name` если необходимо.

2.  **Настройка подключения к базе данных:**
    - Обновите файл `application.yml` с данными подключения к базе данных PostgreSQL.

3.  **Сборка и запуск приложения:**
    ```bash
    ./mvnw clean install
    ./mvnw spring-boot:run
    ```

## Тестирование

- **Модульные тесты:**
  - Предусмотрены модульные тесты для уровней сервиса и репозитория.
  - Тесты используют базу данных H2 в памяти.
- **Интеграционные тесты:**
  - Также предусмотрены интеграционные тесты для проверки взаимодействия между сервисом и базой данных.
  - Интеграционные тесты используют базу данных PostgreSQL, запущенную в контейнере Docker (с помощью Testcontainers).
