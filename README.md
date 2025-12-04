# ParserJob — многопоточный парсер вакансий

## Описание проекта
**ParserJob** — это многопоточное Spring Boot приложение, которое:
- имитирует парсинг вакансий с сайтов (hh.ru, SuperJob, Habr Career);
- сохраняет данные в встроенную базу **H2**;
- выполняет задачи по расписанию с помощью `@Scheduled`;
- использует `ExecutorService` и потокобезопасные структуры данных (`BlockingQueue`);
- пишет логи о работе в файл `vacancies.log` через демон-поток (`FileLoggerService`).

Примечание: Проект полностью автономен — никакие дополнительные настройки, API или базы не нужны.

## Как запустить проект
1. **Открыть проект в IDE**  
   IntelliJ IDEA → Открыть → выбрать папку `ParserJob`.

2. **Запустить приложение**  
   В файле: src/main/java/com/example/ParserJob/ParserJobApplication.java

3. **Нажать Run 'ParserJobApplication'**  
   После запуска в консоли появится сообщение: Started ParserJobApplication in ... seconds

4. **Проверить работоспособность API**

### Получение вакансий с фильтрацией и сортировкой
Открыть браузер или Postman и перейти по ссылке: http://localhost:8080/api/answer

Или с фильтрацией:
http://localhost:8080/api/answer?city=Москва&sort=postedDate&page=0&size=5

Пример ответа:
```json
[
  {
    "title": "Java Developer",
    "company": "TechSoft",
    "salary": "от 100 000 до 150 000 ₽",
    "city": "Москва",
    "postedDate": "2025-10-25",
    "sourceUrl": "https://hh.ru/vacancy/12345"
  }
]
