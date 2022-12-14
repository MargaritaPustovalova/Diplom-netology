# Курсовой проект по модулю «Автоматизация тестирования» для профессии «Инженер по тестированию»

## Описание проекта

В рамках данного проекта необходимо автоматизировать тестирование комплексного сервиса покупки тура, взаимодействующего с СУБД и API Банка.

![service](https://user-images.githubusercontent.com/96742286/175264606-6260b628-88c3-4f86-9f43-8d2a0675e7ce.PNG)


Покупка тура возможна с помощью банковской карты и в кредит. Данные по картам обрабатываются отдельными сервисами (Payment Gate, Credit Gate). Разработчики сделали один сервис, симулирующий и Payment Gate, и Credit Gate.

Сервис обрабатывает только специальные номера карт, которые предоставлены для тестирования:

- APPROVED карта - 1111 2222 3333 4444

- DECLINED карта - 5555 6666 7777 8888.

Приложение должно в собственной СУБД сохранять информацию о том, каким способом был совершён платёж, и успешно ли он был совершён (при этом данные карт сохранять не допускается).

## Документация

* [План автоматизации](https://github.com/MargaritaPustovalova/Diplom-netology/blob/master/Reports/Plan.md)
* [Отчёт по итогам тестирования](https://github.com/MargaritaPustovalova/Diplom-netology/blob/master/Reports/Report.md)
* [Отчёт по итогам автоматизации](https://github.com/MargaritaPustovalova/Diplom-netology/blob/master/Reports/Summary.md)

## Запуск приложения

### Предусловия

1. Требуется изучить пречень используемых инструментов, описаных в [плане автоматизации тестирования](https://github.com/MargaritaPustovalova/Diplom-netology/blob/master/Reports/Plan.md). Обеспечить их дальнейшее использование в проекте;
2. Клонировать [репозиторий](https://github.com/MargaritaPustovalova/Diplom-netology) командой
> git clone
3. Запустить Docker Desktop;
4. Открыть проект в IntelliJ IDEA.

### Запуск

1. Запустить базу данных MySQL. Параметры для запуска хранятся в файле [docker-compose.yml](https://github.com/MargaritaPustovalova/Diplom-netology/blob/master/docker-compose.yml). Для запуска необходимо ввести в терминале команду:
> docker-compose up
2. Для запуска приложения ввести в терминале команду
> MySQL база: java "-Dspring.profiles.active=mysql" -jar artifacts/aqa-shop.jar -port=8080
> Postgres база: java "-Dspring.profiles.active=postgres" -jar artifacts/aqa-shop.jar -port=8080
3. Приложение должно запуститься и работать по адресу [http://localhost:8080/](http://localhost:8080/).

### Запуск тестов

1. В терминале IntelliJ IDEA ввести команду;
> Поменять проперти на соответсвующую базу (MySQL, POSTGRES)
> ./gradlew clean test
2. Подождать пока пройдут все тесты и посмотреть результат.

### Формирование отчета AllureReport по результатам тестирования

1. Для генерации отчета и автоматического открытия его в браузере следует ввести в терминале IntelliJ IDEA команду:
> ./gradlew allureServe
2. Подождать генерации отчета и посмотреть его в открывшемся браузере.
