# diploma

вставить картинку с браузером внутри веб сервиса, добавить больше результатов тестирования.
Виды ошибок, какие цели тестирования, применяются такие то методы для выявления таких то ошибок.
Из речи убирать лишние определения, разобраться с девопсом, не использовать жаргон, использовать на английском если нет на русском

## Доклад

### Слайд 1

Добрый день, я студент группы P3555, тема моей выпускной квалификационной работы: автоматизации управления жизненным циклом веб-сервиса.

### Слайд 2

В практических целях был получен веб-сервис для развёртывания.
И на основании выданного технического задания, определяется цель исследования: развернуть и автоматизировать управление жизненным циклом веб-сервиса на базе Node.js

Для реализации цели исследования ставятся следующие задачи:

1. Провести обзор необходимых средств для автоматизации управления жизненным циклом веб-сервиса,
2. Рассмотреть полученный для развёртывания веб-сервис и проанализировать требования,
3. Провести проектирование механизмов автоматизации управления жизненного цикла веб-сервиса,
4. Составить план тестирования механизмов развёртывания веб-сервиса,
5. Провести практические работы по развёртыванию и автоматизации управления жизненного цикла веб-сервиса,
6. Провести тестирование механизмов развёртывания и обосновать полученные результаты.

### Слайд 3

Разрабатываемая в рамках данной работы система автоматизации управления жизненным циклом веб-сервиса, согласно техническому заданию, должна отвечать следующим требованиям:

1. Использовать современные DevOps методологии,
2. Взаимодействовать с конечным пользователем по методологии SaaS,
3. Так же должна быть возможность добавления в систему не описанных заранее сервисов по методологии IaC,
4. Система должна использовать методологии CI/CD для взаимодействия с инфраструктурой и организации контроля качества,
5. Помимо этого система должна иметь конфигурации прав доступа или приватизации исходного кода,
6. Система должна иметь хранилища пакетов и образов,
7. А так же стоимость установки и обслуживания системы должна составлять не более 2 500 рублей за установку и 2 500 рублей в месяц за обслуживание на момент написания данной работы.

### Слайд 4

В результате обзора необходимых средств для автоматизации управления жизненным циклом веб-сервиса были рассмотрены преимущества системы контроля версий Git по сравнению с CVS и Subversion и наибольшее внимание было уделено сравнению Git хостингов GitHub, BitBucket, GitLab и Space.

Результаты сравнения представлены на слайде с учётом бесплатного тарифа использования.

### Слайд 5

На основании проведённого сравнения был выбран git хостинг GitLab.
К основным преимуществам хостинга относятся:

1. Гибкие настройки прав доступа и приватизации исходного кода без ограничений,
2. Расширенные возможности и функции CI/CD, включающие API для работы с инструментами автоматизированного тестирования,
3. Хранилище npm пакетов и docker контейнеров 10 Gb,
4. Неограниченное количество пользователей в группах, репозиториях и проектах,
5. Крупное сообщество пользователей, а так же доступная и понятная документация.

### Слайд 6

Полученный для развёртывания веб-сервис является программой базе архитектуры <<Клиент-Сервер>>, пользователь получает доступ к услугам посредством веб-браузера, запрашивающего HTML страницу у SSR сервиса web-client, содержание которой зависит от сервиса api. 

В этих двух сервисах используется общая библиотека исходного кода common.
В качестве хранилища данных используется СУБД PostgreSQL версии 14.1. 
Диаграмма развёртывания представлена на слайде.

### Слайд 7

Согласно требованиям были сформулированы актёры в работе системы:

1. Администратор - пользователь системы имеющий доступ на чтение и редактирование конфигураций прав доступа и развёртывания веб-сервиса,
2. Разработчик - пользователь системы имеющий доступ к репозиториям с исходным кодом, хранилищам пакетов и контейнеров, а так же управлению релизами веб-сервиса,
3. Сотрудник отдела качества (или тестировщик на слайде) - пользователь системы имеющий доступ к просмотру аналитических данных и проведению автоматизированных тестовых сценариев внутри заранее подготовленных окружений.

Данные актёры и случаи использования приведены на диаграмме на слайде.

### Слайд 8

Работа проектируемых механизмов автоматизации управления жизненным циклом веб-сервиса сосредоточена вокруг коммита пользователем в репозиторий и автоматическим запуском одной или нескольких задач внутри определённой линии.

Каждая задача является набором последовательно исполняемых инструкций ожидаемо завершённых с не нулевым значением кода завершения.

В случае ошибки выполнение всей линии завершается и повторяется только по запросу пользователя.

При этом линии задач строятся динамически в зависимости от репозитория и значения хеша коммита.

Результатами работы линий являются артефакты, которые содержат результаты работы задачи.

Данное поведение представлено на диаграмме последовательностей на слайде.

### Слайд 9

В ходе проектирования была составлена диаграмма компонентов репозиториев:

1. Репозиторий с конфигурациями развёртывания (deployment на слайде) - уникален, предоставляет интерфейс в виде задач update и publish компонентам Source repository,
2. Репозиторий с исходным кодом компонента веб-сервиса (Source repository на слайде) - не уникален, требует реализации интерфейсов задач update и publish для развёртывания.
Api или web-client в контексте данной работы.
3. Репозиторий с исходным кодом библиотек компонентов веб-сервиса (node-packages на слайде) - уникален.
Common в контексте данной работы.

### Слайд 10

Основной целью тестирования является снижение количества ошибок в работе веб-сервиса и как следствие повышение соответствия к заявленным требованиям.
Данная цель будет достигаться при помощи автоматизации, а конкретнее - работы двух линий задач, разделённых по виду тестирования и представленных на слайде в виде таблицы.

### Слайд 11

На данном слайде представлен пример работы задачи модульного тестирования в репозитории web-client и загрузки артефактов в GitLab.

### Слайд 12

Так же представлена конфигурация планирования интеграционного тестирования в репозитории deployment в GitLab.

### Слайд 13

Как было сказано ранее, deployment предоставляет интерфейс компонентам Source repository, реализуется данный контракт при помощи обязательного требования Dockerfile в корне репозитория с исходным кодом.

На слайде представлена диаграмма компонентов стадии build в разных репозиториях с исходным кодом.

### Слайд 14

Перед подготовкой плана тестирования была определена цель - снижение количества ошибок в работе линий и задач. 
Отсюда следует набор основных ошибок для нахождения при поведении тестирования: синтаксические в описании файлов конфигураций и логические в работе линий и задач.

Основную часть синтаксических и логических ошибок можно найти и исправить на этапе описания файлов конфигураций в эмуляторе GitLab Runner, который представлен на слайде.

Использование данного эмулятора не поможет при поиске более сложных логических ошибок, поскольку задачи не будут исполняться, тем не менее его применение значительно ускоряет рабочий процесс разработки и описания файлов конфигураций.

### Слайд 15

Для нахождения логических ошибок, требующих запуска задач было применено ручное тестирование белого ящика.

Тестовые сценарии в плане основаны на случаях использования системы.

### Слайд 16

В ходе практических работ в Gitlab была создана группа и репозитории.

На данном слайде приведены репозитории исходного кода - api и web-client;
так же репозиторий с конфигурациями развёртывания - deployment; и репозиторий c кодом библиотек - node-packages.

### Черновик

### Слайд 15

картинка репозитории веб сервиса, текст создана группа, созданы репозитории, типы репозиториев

### Слайд 16 

Картинка с браузером и линиями, текст был зарегистрирован раннер, подготовлен кластер Docker Swarm, были описаны конфигурации gitlab-ci

### Слайд 17

Рассказать про результаты тестирования, на слайде таблица с результатами


