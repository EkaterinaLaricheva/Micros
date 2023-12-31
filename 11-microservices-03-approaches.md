# Домашнее задание к занятию «Микросервисы: подходы»

Вы работаете в крупной компании, которая строит систему на основе микросервисной архитектуры.
Вам как DevOps-специалисту необходимо выдвинуть предложение по организации инфраструктуры для разработки и эксплуатации.


## Задача 1: Обеспечить разработку

Предложите решение для обеспечения процесса разработки: хранение исходного кода, непрерывная интеграция и непрерывная поставка. 
Решение может состоять из одного или нескольких программных продуктов и должно описывать способы и принципы их взаимодействия.

Решение должно соответствовать следующим требованиям:
- облачная система;
- система контроля версий Git;
- репозиторий на каждый сервис;
- запуск сборки по событию из системы контроля версий;
- запуск сборки по кнопке с указанием параметров;
- возможность привязать настройки к каждой сборке;
- возможность создания шаблонов для различных конфигураций сборок;
- возможность безопасного хранения секретных данных (пароли, ключи доступа);
- несколько конфигураций для сборки из одного репозитория;
- кастомные шаги при сборке;
- собственные докер-образы для сборки проектов;
- возможность развернуть агентов сборки на собственных серверах;
- возможность параллельного запуска нескольких сборок;
- возможность параллельного запуска тестов.

Обоснуйте свой выбор.

Для обеспечения процесса разработки по требованиям выше я выбрала GitLab CI/CD. Это решение позволяет реализовать непрерывную интеграцию и непрерывную доставку посредством автоматизации процессов с помощью набора инструментов, поддерживаемых в единой облачной платформе GitLab. Возможности GitLab CI/CD:

- GitLab CI/CD - облачная система, которая поддерживает систему контроля версий Git;
- У каждого сервиса может быть собственный репозиторий в настройках проекта;
- Запуск сборки может быть выполнен автоматически по событию из системы контроля версий, либо при помощи кнопок на указанных страницах сборок;
- Настройки могут быть созданы для каждой сборки и сохраняться в виде шаблона для последующего использования;
- GitLab предоставляет возможность создавать шаблоны для различных конфигураций сборок;
- Безопасный хранение секретных данных в Gitlab защититься при помощи переменных окружения проекта или также можно использовать базу данных хранилищь секретов;
- Несколько конфигураций для сборки из одного репозитория в виде скрипта;
- Кастомные шаги при сборке через файл описания задачи (.gitlab-ci.yml);
- Собственные докер-образы для сборки проектов могут быть использованы в процессе настройки;
- Возможность развернуть агенты сборки на собственных серверах для большей производительности и масштабируемости;
- Возможность параллельного запуска нескольких сборок;
- Возможность параллельного запуска тестов.

GitLab CI/CD - это инструмент, который можно использовать для автоматизации интеграции и доставки своих приложений в облачном окружении. Он имеет большое количество настраиваемых параметров и гибких инструментов, позволяющих получить подходящее решения для любого проекта. 

## Задача 2: Логи

Предложите решение для обеспечения сбора и анализа логов сервисов в микросервисной архитектуре.
Решение может состоять из одного или нескольких программных продуктов и должно описывать способы и принципы их взаимодействия.

Решение должно соответствовать следующим требованиям:
- сбор логов в центральное хранилище со всех хостов, обслуживающих систему;
- минимальные требования к приложениям, сбор логов из stdout;
- гарантированная доставка логов до центрального хранилища;
- обеспечение поиска и фильтрации по записям логов;
- обеспечение пользовательского интерфейса с возможностью предоставления доступа разработчикам для поиска по записям логов;
- возможность дать ссылку на сохранённый поиск по записям логов.

Обоснуйте свой выбор.

Для обеспечения сбора и анализа логов сервисов в микросервисной архитектуре я бы порекомендовал использовать Elastic Stack. Elastic Stack - это набор из нескольких программных продуктов, включающих в себя Elasticsearch, Logstash, и Kibana. 
Но сейчас ест сложности с приобритением данных продуктов. Поэтому можно воспользоваться Clickhouse (соберет логи вместо Elasticsearch), Vector (доставит логи вместо Logstash) и Grafana (визуализирует вместо Kibana)


Clickhouse - это поисковый и аналитический движок, который используется для хранения логов. Он обеспечивает высокую доступность, масштабируемость и производительность. Clickhouse может индексировать и хранить данные в реальном времени, а также обеспечивает поиск, фильтрацию и агрегацию данных.

Vector - это система сбора и обработки логов. Он может принимать данные из разных источников, обрабатывать их и отправлять в Clickhouse для хранения. Vector позволяет структурировать данные и преобразовывать их в нужный формат.

Grafana - это веб-интерфейс для визуализации и анализа данных, хранящихся в Clickhouse.

Использование этих инструментов позволяет обеспечить сбор логов из разных источников и их отправку в центральное хранилище, обеспечивает минимальные требования к приложениям, так как логи собираются из stdout, а также гарантированную доставку логов до центрального хранилища.
К сожалению, я не очень знакома с работой данных инструментов, но это рабочие инструменты, которые в наше время есть возможность использовать.
Если необходимо дать более полное описание, могу это сделать на примере Elastic Stack.

## Задача 3: Мониторинг

Предложите решение для обеспечения сбора и анализа состояния хостов и сервисов в микросервисной архитектуре.
Решение может состоять из одного или нескольких программных продуктов и должно описывать способы и принципы их взаимодействия.

Решение должно соответствовать следующим требованиям:
- сбор метрик со всех хостов, обслуживающих систему;
- сбор метрик состояния ресурсов хостов: CPU, RAM, HDD, Network;
- сбор метрик потребляемых ресурсов для каждого сервиса: CPU, RAM, HDD, Network;
- сбор метрик, специфичных для каждого сервиса;
- пользовательский интерфейс с возможностью делать запросы и агрегировать информацию;
- пользовательский интерфейс с возможностью настраивать различные панели для отслеживания состояния системы.

Обоснуйте свой выбор.

Можно использовать Prometheus в сочетании с Grafana для визуализации данных.

Prometheus - это система мониторинга и оповещения с открытым исходным кодом, которая собирает метрики со всех хостов, обслуживающих систему, в режиме реального времени. Он также может собирать метрики состояния ресурсов хостов (CPU, RAM, HDD, Network), метрики потребляемых ресурсов для каждого сервиса (CPU, RAM, HDD, Network) и специфичные для каждого сервиса метрики.

Prometheus имеет свой собственный язык запросов, который позволяет агрегировать и анализировать метрики. Он также может отправлять оповещения, если определенные метрики превышают заданные пороговые значения.

Grafana - это инструмент для визуализации данных, который может использоваться для создания пользовательского интерфейса с возможностью делать запросы и агрегировать информацию. 

Для настройки сбора метрик можно использовать экспортеры Prometheus, которые собирают метрики из различных источников и предоставляют их в формате, который может быть прочитан Prometheus. 
Таким образом, решение может состоять из следующих компонентов:
- Prometheus для сбора и анализа метрик;
- Экспортеры для сбора метрик из различных источников;
- Grafana для визуализации и настройки пользовательского интерфейса.

Для обеспечения высокой доступности и масштабируемости можно использовать кластеризацию Prometheus и Grafana.

## Задача 4: Логи * (необязательная)

Продолжить работу по задаче API Gateway: сервисы, используемые в задаче, пишут логи в stdout. 

Добавить в систему сервисы для сбора логов Vector + ElasticSearch + Kibana со всех сервисов, обеспечивающих работу API.

### Результат выполнения: 

docker compose файл, запустив который можно перейти по адресу http://localhost:8081, по которому доступна Kibana.
Логин в Kibana должен быть admin, пароль qwerty123456.


## Задача 5: Мониторинг * (необязательная)

Продолжить работу по задаче API Gateway: сервисы, используемые в задаче, предоставляют набор метрик в формате prometheus:

- сервис security по адресу /metrics,
- сервис uploader по адресу /metrics,
- сервис storage (minio) по адресу /minio/v2/metrics/cluster.

Добавить в систему сервисы для сбора метрик (Prometheus и Grafana) со всех сервисов, обеспечивающих работу API.
Построить в Graphana dashboard, показывающий распределение запросов по сервисам.

### Результат выполнения: 

docker compose файл, запустив который можно перейти по адресу http://localhost:8081, по которому доступна Grafana с настроенным Dashboard.
Логин в Grafana должен быть admin, пароль qwerty123456.

---

### Как оформить ДЗ?

Выполненное домашнее задание пришлите ссылкой на .md-файл в вашем репозитории.

---
