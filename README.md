## Сервис курсов валют

Это приложение Spring Boot, которое получает курсы валют от Центрального банка Российской Федерации (ЦБ РФ) и сохраняет их в базе данных PostgreSQL.

## Функционал

- **Получение последних курсов валют:**  Приложение периодически запрашивает API ЦБ РФ для получения актуальных курсов валют.
- **Сохранение истории курсов:** Все полученные курсы валют сохраняются в базе данных для дальнейшего анализа и использования.
- **API для получения курсов:** Предоставляет REST API для получения курсов валют по коду валюты и дате.
- **Повторные попытки при ошибках:** В случае ошибки при получении данных от API ЦБ РФ, приложение выполняет несколько повторных попыток с заданной задержкой.
- **Метрики:** Собирает метрики, связанные с работой приложения, такие как время выполнения задач, количество успешных и неудачных запросов к API ЦБ РФ, и время выполнения методов сервиса.
- **Контейнеризация:** Приложение может быть запущено в Docker-контейнере для удобства развертывания и изоляции.

## Доступные API endpoints

- **`/rates/{charCode}`**:
    - Возвращает последний актуальный курс валюты по ее символьному коду (charCode).
    - **Пример:** `/rates/USD`

- **`/rates/{charCode}?rateDate=yyyy-MM-dd`**:
    - Возвращает курс валюты на заданную дату (rateDate). Если на заданную дату нет данных, возвращает курс на последнюю доступную дату, предшествующую заданной.
    - **Пример:** `/rates/USD?rateDate=2024-08-10`

## Технологии

- Java 17
- Spring Boot
- Spring Data JPA
- PostgreSQL
- Docker
- Docker Compose
- Prometheus
- Grafana
- Spring AOP (для сбора метрик)

## Запуск приложения

1. **Сборка и запуск с помощью Docker Compose:**
    ```bash
    docker-compose up -d
    ```

2. **Локальный запуск:**
    - Убедитесь, что PostgreSQL запущен и настроен.
    - Обновите настройки подключения к базе данных в `application.yml`.
    - Соберите и запустите приложение:
    ```bash
    mvn clean install
    mvn spring-boot:run
    ```

## Мониторинг

- Метрики приложения доступны по адресу: `http://localhost:8080/actuator/prometheus`.
- Рекомендуется использовать Prometheus и Grafana для сбора и визуализации метрик.

## Дополнительная информация

- Код проекта содержит unit-тесты и integration-тесты.
- Документация по API ЦБ РФ: [https://www.cbr.ru/development/](https://www.cbr.ru/development/)

## Разработчики

- Меркулов Андрей

## Лицензия

- Бесплатно