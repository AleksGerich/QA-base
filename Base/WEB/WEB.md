---
tags:
  - порты
  - REST
  - состояния_ответов
  - интерфейсы
  - распределенные_системы
  - json
  - xml
---

---
#порты
# Порты

1. Порт **20** и **21** (FTP) — File Transfer Protocol
FTP — протокол для передачи файлов между компьютерами в сети.
    - Порт 21 используется для управления соединением.
    - Порт 20 используется для передачи данных.

2. Порт **22** (SSH) — Secure Shell
Используется для безопасного удалённого доступа и управления сервером через зашифрованное соединение.

3. Порт **80** (HTTP) — Hypertext Transfer Protocol
Протокол для передачи данных по сети в незащищённом виде. Используется для загрузки веб-страниц в браузере.

4. Порт **443** (HTTPS) — Hypertext Transfer Protocol Secure
Защищённая версия HTTP. Использует SSL/TLS для шифрования передачи данных, что обеспечивает безопасность при работе с веб-сайтами.

5. Порт **53** (DNS) — Domain Name System
Протокол для преобразования доменных имён в IP-адреса и наоборот.

6. Порт **67** и **68** (DHCP) — Dynamic Host Configuration Protocol
    - Порт **67** используется сервером для назначения IP-адресов клиентам.
    - Порт **68** используется клиентами для получения IP-адресов от сервера.

---
7. Порт **25** (SMTP) — Simple Mail Transfer Protocol
Протокол для отправки электронной почты между почтовыми серверами.

8. Порт **110** (POP3) — Post Office Protocol 3
Протокол для получения электронной почты с почтового сервера. Позволяет загружать письма локально.

9. Порт **995** (POP3S) — POP3 Secure
Защищённая версия протокола POP3 с использованием SSL/TLS.

10. Порт **143** (IMAP) — Internet Message Access Protocol
Протокол для управления и синхронизации электронной почты. В отличие от POP3, оставляет письма на сервере и синхронизирует изменения на всех устройствах.

11. Порт **993** (IMAPS) — IMAP Secure
Защищённая версия протокола IMAP с использованием SSL/TLS.

---

12. Порт **123** (NTP) — Network Time Protocol
Используется для синхронизации времени между устройствами в сети.

13. Порт **3389** (RDP) — Remote Desktop Protocol
Протокол, используемый для удалённого управления рабочим столом через графический интерфейс.

14. Порт **135** (RPC) — Remote Procedure Call
Используется для удалённого вызова процедур между разными системами.

15. Порт **137**-**139** (NetBIOS) — Network Basic Input Output System
Используется в локальных сетях для передачи данных между компьютерами.

16. Порт **161** (SNMP) — Simple Network Management Protocol
Протокол для управления и мониторинга сетевых устройств (например, роутеров и серверов).

---
#REST
# REST

**REST** (Representational state transfer) – это стиль архитектуры программного обеспечения для распределенных систем, таких как World Wide Web, который, как правило, используется для построения веб-служб. Системы, поддерживающие REST, называются *RESTful*-системами (системы, следующие принципам REST).

### Концепция
1. Архитектура в стиле REST состоит из клиентов и серверов. 
2. Клиенты инициируют запросы к серверам; 
3. Серверы обрабатывают запросы и возвращают подходящие ответы. 
4. Запросы и ответы создаются на базе передачи представлений ресурсов.

### Цели REST
- Масштабируемость взаимодействия компонентов
- Общность интерфейсов
- Независимое внедрение компонентов
- Промежуточные компоненты, снижающие задержку, усиливающие безопасность и инкапсулирующие устаревшие системы

### Методы REST

- **GET** - используется для получения (или чтения) представления ресурса.
	
- **PUT** - обычно используется для предоставления возможности обновления ресурса. Тело запроса при отправке PUT-запроса к существующему ресурсу URI должно содержать обновленные данные оригинального ресурса (полностью, или только обновляемую часть).
	
- **POST** - используется для создания новых ресурсов. На практике он используется для создания вложенных ресурсов. POST запрос отправляется к родительскому ресурсу и, таким образом, сервис берет на себя ответственность на установление связи создаваемого ресурса с родительским ресурсом, назначение новому ресурсу ID и т.п.
	
- **DELETE** - используется для удаления ресурса, идентифицированного конкретным URI (ID).

## Принципы REST

1. **Технология «клиент-сервер»**. Клиенты отделены от сервера единым интерфейсом. Это разделение ответственности означает, что клиенты не отвечают за хранилище данных - так что переносимость кода клиента улучшается. Серверы не отвечают за пользовательский интерфейс или пользовательское состояние - серверы могут быть проще и более масштабируемыми.
	
2.  **Отсутствие состояния**. Каждый запрос от клиента к серверу должен содержать всю необходимую информацию для его обработки. Сервер не хранит никаких данных о состоянии клиента между запросами, что упрощает масштабирование и поддержку.
	
3. **Кэшируемость**. клиенты могут кэшировать ответы. Поэтому ответы должны, явно или неявно, определять себя кэшируемыми или нет, чтобы предотвратить использование клиентом старые или неподходящие данные при ответе на следующие запросы.
	
4. **Многоуровневая система**. Клиент не может однозначно определить, подключается ли он непосредственно к серверу или к посреднику по пути подключения.
	
5. **Код по требованию (опционально)**. Серверы могут временно расширить или настроить функциональность клиента, передавая ему исполняемую логику.
	
6. **Единый интерфейс**. REST требует стандартного, согласованного интерфейса Единый интерфейс между клиентами и серверами, упрощает и разделяет архитектуру, позволяя каждой части развиваться самостоятельно.
	
	- *Идентификация ресурсов*: Каждый ресурс имеет уникальный URL.
	- *Манипуляция ресурсом через представление*: Сервер предоставляет клиенту необходимую информацию о взаимодействии с ресурсом.
	- *Самоописывающие сообщения*: Запросы содержат всю необходимую информацию для понимания.
	- *Гипермедиа как движущая сила приложения (HATEOAS)*: Ответы могут содержать ссылки, которые показывают клиенту возможные дальнейшие действия.
	
7. **Начало от нуля (Starting with the Null Style)**. Клиент знает только одну точку входа на сервер. Дальнейшие возможности по взаимодействию обеспечиваются сервером.

---
#### Преимущества

- **Надёжность** (за счёт отсутствия необходимости сохранять информацию о состоянии клиента, которая может быть утеряна);
	
- **Производительность** (за счёт использования кэша);
	
- **Масштабируемость**;
	
- **Прозрачность системы взаимодействия** (особенно необходимая для приложений обслуживания сети);
	
- **Простота интерфейсов**;
	
- **Портативность компонентов**;
	
- **Лёгкость внесения изменений**;

#### Форматы данных:
- JSON
- HTML
- XML
- TXT

## Около-примеры

API-интерфейсы управления. API, ориентированные на управление объектами в системе и предназначенные для многих потребителей, распространены шире всего. REST помогает таким API, обеспечивая сильную обнаруживаемость и хорошую документацию, и тем самым вписывается в эту объектную модель.

Простые приложения, управляемые ресурсами. REST  —  это валидный подход для подключения приложений, управляемых ресурсами, которые не нуждаются в гибкости запросов

[Инфа по REST из базы знаний](https://confluence.senlainc.com/display/KB/REST)

---
#soap
# SOAP

**SOAP** (Simple Object Access Protocol до версии 1.2) - протокол обмена структурированными сообщениями в распределённой вычислительной среде. 

Первоначально SOAP предназначался в основном для реализации удалённого вызова процедур (RPC). Сейчас протокол используется для обмена произвольными сообщениями в формате XML, а не только для вызова процедур. 

*Нюансы:*
- более "тяжеловесный" в плане обработки данных в сравнении с REST
- SOAP работает только с XML форматом 
- REST прощее и быстрее SOAP

Официальная спецификация последней версии 1.2 протокола никак не расшифровывает название SOAP. SOAP является расширением протокола XML-RPC.

SOAP может использоваться с любым протоколом прикладного уровня: SMTP, FTP, HTTP, HTTPS и др. Однако его взаимодействие с каждым из этих протоколов имеет свои особенности, которые должны быть определены отдельно. 

Чаще всего SOAP используется поверх HTTP.

Протокол начинает свою работу с файла WSDL (характерная черта - добавление ?WSDL вконце url)

WSDL описывает все операции, которые умеет выполнять сервис в виде XML (документация всего сервиса)

В приложении SOAP UI, при открытии проекта, в нем появляются две версии SOAP: обычная и версия 1.2 

**Отступление про пространство имен:**
- по сути, аналог полиморфизма. Для объектов xml файла с одинаковым именем вводится собственный идентификатор
- так же служит для разграничения таблиц, для обращения к определенной
- имя пространства принято писать через url
*@:*
<h:TEMP xmlns:h="http://www.example.com/temp">
  <h:tr>
    ...
  </h:tr>
</h:TEMP>

---
## Использование метаданных в SOAP

SOAP — это протокол для обмена структурированными сообщениями в веб-сервисах, и метаданные играют ключевую роль для передачи информации, необходимой для правильной обработки сообщения, таких как аутентификация, сессии, трассировка и другое.

Метаданные (в общем) - данные о данных. Описывают структуру, содержание, контекст или другие важные характеристики информации. 

**В контексте SOAP метаданные** - информация, передающаяся вместе с сообщением для маршрутизации и интерпретации. Содержится зачастую в заголовке (\<header>) и частично в теле (<body\>)

Хотя XML-теги описывают структуру SOAP-сообщения, **не все они являются метаданными**, поскольку большинство из них служат для форматирования и передачи фактического содержания сообщения.

### Заголовки (header)

**Header** - секция в SOAP-сообщении, где хранятся метаданные. Не является обязательной.

Содержит информацию о маршрутизации, аутентификации и других настройках, необходимых для интерпретации и маршрутизации сообщения.

*@:*
- идентификаторы сессии
- токены аутентификации
- параметры безопасности
- другие контекстные данные, которые не относятся к основному содержанию (body) сообщения

### Атрибуты

SOAP-сообщения используют XML-формат, и атрибуты XML в теле и заголовках сообщения также могут содержать метаданные. 

**Определяют**:
- параметры вызова
- типы данных
- дополнительные параметры (@: валидация типов)

### WSDL

Описание метаданных о самом веб-сервисе хранится в формате **WSDL** (Web Services Description Language). Хотя WSDL не передается вместе с SOAP-сообщением, оно описывает доступные методы, ожидаемые параметры и типы ответов, что можно считать метаданными о сервисе.
#### WSDL описывает:
- информация о структурах сообщений
- типах данных 
- форматы операций

[Ответы по вопросам Web-сервисов](https://jsehelper.blogspot.com/2016/04/web-services.html)

## Послесловие

В настоящее время архитектура SOAP чаще всего применяется для интеграции внутри предприятий или с их доверенными партнерами.

Надежность передачи данных. Жесткая структура SOAP, а также возможности в плане безопасности и авторизации, делают его наиболее подходящим вариантом для обеспечения соответствия формальному программному контракту между API и клиентом при соблюдении юридического контракта между поставщиком API и потребителем API. Вот почему финансовые организации и другие корпоративные пользователи выбирают SOAP.

---
#xml #wsdl #xsd
# XML, WSDL, XSD

**XML**, в переводе с англ eXtensible Markup Language — расширяемый язык разметки. Используется для хранения и передачи данных. Так что увидеть его можно не только в API, но и в коде. Этот формат рекомендован Консорциумом Всемирной паутины (W3C), поэтому он часто используется для передачи данных по API.

**XSD** — это язык описания структуры XML документа. Его также называют XML Schema. При использовании XML Schema XML парсер может проверить не только правильность синтаксиса XML документа, но также его структуру, модель содержания и типы данных. (Схема в документе WSDL). на основе XSD строится схема в SOAP UI 

**WSDL** расшифровывается как язык описания веб-сервисов. Это стандартный формат для описания веб-службы. WSDL был разработан совместно Microsoft и IBM.

XML: расширяемый язык разметки.
XSD: определение схемы XML.
WSDL: язык определения веб-сервисов.

---
#различия_SOAP_REST
# Сравнение REST и SOAP

## Различия
#### Принципиальное:
- REST - архитектурный подход для создания ПО
- SOAP - протокол передачи данных в формате XML

#### Различия между REST и SOAP Веб-сервисами

- REST поддерживает различные форматы: text, JSON, XML; SOAP - только XML,
	
- REST работает только по HTTP(S), а SOAP может работать с различными протоколами
	
- SOAP на основе чтения не может быть помещена в кэш, а REST в этом случае может быть закэширован
	
- SOAP поддерживает SSL и WS-security, в то время как REST - только SSL,
	
- SOAP поддерживает ACID (Atomicity, Consistency, Isolation, Durability). REST поддерживает транзакции, но не один из ACID не совместим с двух фазовым коммитом.

## Сравнение

#### Плюсы SOAP
- **Независимость от языка и платформы.** Встроенная функциональность для создания веб-сервисов позволяет SOAP обрабатывать сообщения и делать ответы независимыми от языка и платформы
	
- **Связанность с различными транспортными протоколами.** SOAP гибок с точки зрения протоколов передачи и приспосабливается к более чем одному сценарию (когда REST - только HTTP)
	
- **Встроенная обработка ошибок.** Спецификация SOAP API позволяет возвращать XML-сообщение Retry с кодом ошибки и ее объяснением
	
- **Ряд расширений безопасности.** Благодаря интеграции с протоколами WS-Security качество транзакций SOAP соответствует корпоративным стандартам. SOAP гарантирует конфиденциальность и целостность внутри транзакций, обеспечивая при этом шифрование на уровне сообщений

#### Минусы SOAP
- **Только XML.** SOAP-сообщения содержат много метаданных и поддерживают только подробные XML-структуры для запросов и ответов
	
- **Тяжеловесность**. Из-за большого размера XML-файлов SOAP-сервисы требуют большой пропускной способности
	
- **Узкоспециализированные знания.** Создание серверов SOAP API требует глубокого понимания всех задействованных протоколов и их строгих правил
	
- **Утомительное обновление сообщений.** Требуются дополнительные усилия для добавления или удаления свойств сообщения  —  жесткая схема SOAP замедляет принятие

SOAP  —  это хлопотно, но его обширный функционал в плане безопасности по-прежнему незаменим для биллинговых операций, систем бронирования и платежей.


#### Плюсы REST
- **Разделение клиента и сервера**. По возможности разделяя клиент и сервер, REST обеспечивает лучшую абстракцию по сравнению с RPC. Система с уровнями абстракции способна инкапсулировать свои детали, чтобы лучше идентифицировать и поддерживать свои свойства. Поэтому REST API достаточно гибок, чтобы развиваться с течением времени и при этом оставаться стабильной системой
	
- **Открытость**. Все описывается связью между клиентом и сервером, так что для понимания, как взаимодействовать с REST API, не требуется никакая внешняя документация
	
- **Дружественность к кэшу**. REST  —  единственный стиль, который позволяет кэшировать данные на уровне HTTP благодаря повторному использованию множества HTTP-инструментов. В то же время, реализация кэширования в любом другом API потребует настройки дополнительного модуля кэширования
	
- **Поддержка нескольких форматов.** Возможность поддержки нескольких форматов хранения и обмена данными  —  одна из причин, по которым REST в настоящее время преобладает в сфере создания общедоступных API

#### Минусы REST
- **Нет единой структуры REST**. Нет точного правильного способа создания REST API. Как моделировать ресурсы и какие ресурсы моделировать, будет зависеть от каждого сценария. Это делает REST простым в теории, но трудным на практике
	
- **Большие полезные нагрузки**. REST возвращает много богатых метаданных, так что клиент может понять все необходимое о состоянии приложения только из его ответов. И эта болтливость не имеет большого значения для большой сетевой трубы с большой пропускной способностью. Но это не всегда так. Это стало ключевым движущим фактором для Facebook, придумавшего описание стиля GraphQL в 2012 году
	
- **Проблемы чрезмерных или недостаточных данных**. Ответы REST зачастую содержат либо слишком много данных, либо их недостаточное количество, и создают необходимость в дополнительном запросе

REST обладает самой высокой абстракцией и лучшим моделированием API. Но он, как правило, тяжелее в плане нагрузки на сеть и многословнее  —  недостаток, если вы работаете на мобильных устройствах.

[Сурс (с VPN)](https://nuancesprog.ru/p/11310/)

---
#RPC 
# Протокол RPC

Удаленный вызов процедур (RPC) – это метод межпроцессного взаимодействия. Используется для клиент-серверных приложений. 

Механизмы RPC используются, когда компьютерная программа вызывает выполнение процедуры или подпрограммы в другом адресном пространстве, которое закодировано как обычный вызов процедуры, при этом программист специально не кодирует детали для удаленного взаимодействия. Этот вызов процедуры также управляет транспортным протоколом низкого уровня, таким как протокол пользовательских дейтаграмм, протокол управления передачей / Интернет-протокол и т.д. 

Он используется для передачи данных сообщения между программами. 

Самый большой недостаток метода RPC заключается в том, что он очень уязвим к сбоям, поскольку в нем задействованы система связи, другая машина и другой процесс.

[Материал с CoderLessons (с VPN)](https://coderlessons.com/tutorials/akademicheskii/osnovy-operatsionnykh-sistem/13-udalennyi-vyzov-protsedur-rpc)

RPC — подходящий выбор для отправки команд в удаленную систему. Например, Slack API очень командно-ориентирован: зайти на канал, покинуть канал, отправить сообщение. Разработчики Slack API как раз и смоделировали его в стиле RPC, сделав его маленьким, компактным и простым в использовании.

---
# Сравнение протоколов

![[Pasted image 20241112165450.png]]

|                              |                                                                                                                                                                                                                                                                                       |                                                                                                                                                                                                                                                                    |                                                                                                                                                                                                                                                 |                                                                                                                                                                                              |
| ---------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **API Architectural Styles** |                                                                                                                                                                                                                                                                                       |                                                                                                                                                                                                                                                                    |                                                                                                                                                                                                                                                 |                                                                                                                                                                                              |
|                              | **RPC**                                                                                                                                                                                                                                                                               | **SOAP**                                                                                                                                                                                                                                                           | **REST**                                                                                                                                                                                                                                        | **GraphQL**                                                                                                                                                                                  |
| **Формат**                   | JSON, XML, Protobuf, Thrift, FlatBuffers                                                                                                                                                                                                                                              | XML                                                                                                                                                                                                                                                                | XML, JSON, HTML, plain text                                                                                                                                                                                                                     | JSON                                                                                                                                                                                         |
| **Обучаемость**              | Легко                                                                                                                                                                                                                                                                                 | Сложно                                                                                                                                                                                                                                                             | Легко                                                                                                                                                                                                                                           | Средне                                                                                                                                                                                       |
| **Сообщество**               | Большое                                                                                                                                                                                                                                                                               | Маленькое                                                                                                                                                                                                                                                          | Большое                                                                                                                                                                                                                                         | Растущее                                                                                                                                                                                     |
| **Где применяется**          | командный и ориентированный на действия API; внутренняя высокопроизводительная коммуникация в массивных системах микросервисов  <br>Благодаря своей сильной связанности RPC хорошо годится для внутренних микросервисов, но это не вариант для сильного внешнего API или API-сервиса. | платежные системы, CRM-решения для управления идентификацией, финансовые и телекоммуникационные сервисы,  <br>SOAP — это хлопотно, но его обширный функционал в плане безопасности по-прежнему незаменим для биллинговых операций, систем бронирования и платежей. | простые приложения с открытым API  <br>  <br>REST обладает самой высокой абстракцией и лучшим моделированием API. Но он, как правило, тяжелее в плане нагрузки на сеть и многословнее — недостаток, если вы работаете на мобильных устройствах. | Мобильные API, сложные системы, микро-сервисы  <br>  <br>GraphQL — большой шаг вперед с точки зрения извлечения данных, но не у всех достаточно времени и возможностей, чтобы его осваивать. |


---
#методы_HTTP
# Методы HTTP

HTTP определяет множество **методов запроса**, которые указывают, какое желаемое действие выполнится для данного ресурса.

Каждый реализует свою семантику, но каждая группа команд разделяет общие свойства: так, методы могут быть [безопасными](https://developer.mozilla.org/ru/docs/Glossary/Safe), [идемпотентными](https://developer.mozilla.org/ru/docs/Glossary/Idempotent) или [кешируемыми](https://developer.mozilla.org/ru/docs/Glossary/Cacheable).

1. **GET** - Метод `GET` запрашивает представление ресурса. Запросы с использованием этого метода могут только извлекать данные. Доступ к информации при использовании метода GET осуществляется через URI. 
	
2. **HEAD** - `HEAD` запрашивает ресурс так же, как и метод GET, но без тела ответа. Обычно используется для получение метаинформации об объекте. 
	- *@:* для тестирования HTTP соединений и достижимости узлов и ресурсов, так как нет необходимости гонять по сети содержимое, тестирование HTTP методом HEAD производится гораздо быстрее
	
3. **POST** - используется для отправки сущностей к определённому ресурсу. Часто вызывает изменение состояния или какие-то побочные эффекты на сервере. (позволяет отправлять данные на сервер)
	
4. **PUT** - заменяет все текущие представления ресурса данными запроса. Загружает по указанному URI объект в запросе. Если по URI уже есть какие-либо данные, то запрос их изменяет (считается модификацией)
	
5. **DELETE** - `DELETE` удаляет указанный в URI ресурс.
	
6. **CONNECT** - `CONNECT` устанавливает "туннель" к серверу, определённому по ресурсу. Используется для преобразования HTTP соединения в прозрачный NCP/IP туннель (для шифрования соединения)
	
7. **OPTIONS** - используется для описания параметров соединения с ресурсом. Дает возможность запросить параметры для конкретного ресурса, указанного в URI. Особенность метода в том, что он не производит никаких действий с самим ресурсом (даже не загружает указанную страницу) 
	
8. **TRACE** - выполняет вызов возвращаемого тестового сообщения с ресурса. Используется для получения информации о том, что происходит с сообщением на промежуточных узлах.
	
9. **PATCH** - используется для частичного изменения ресурса. Аналогично PUT, но применяется только к фрагменту ресурса.

#### Имеют тело ответа:
POST, PUT, PATCH

#### Не имеют тела методы:
OPTIONS, GET, HEAD, TRACE, CONNECT

#### Может иметь тело ответа:
DELETE 
- Метод DELETE будет выполнять ту задачу, которую задумал разработчик

---
## Безопасность и идемпотентность

**Безопасный запрос** - это запрос, который не меняет состояние приложения

**Идемпотентный запрос** - это запрос, эффект которого от многократного выполнения равен эффекту от однократного выполнения
- если повторный идентичный запрос, сделанный один или несколько раз подряд, имеет один и тот же эффект, *не изменяющий состояние сервера*
- идемпотентный метод не должен иметь *никаких побочных эффектов* (side-effects), кроме сбора статистики или подобных операций
- Корректно реализованные методы GET, HEAD, PUT и DELETE **идемпотентны**, но не метод POST
- **все безопасные методы являются идемпотентными**

![[Pasted image 20241108173420.png]]

Для идемпотентности нужно рассматривать только изменение фактического внутреннего состояния сервера, а возвращаемые запросами коды статуса могут отличаться
*@:* первый вызов DELETE вернёт код 200, в то время как последующие вызовы вернут код 404

Из идемпотентности DELETE неявно следует, что разработчки не должны использовать метод DELETE при реализации RESTful API с функциональностью **удалить последнюю запись**.

Идемпотентность метода **не гарантируется сервером**, и некоторые приложения могут нарушать ограничение идемпотентности

*@:*
![[Pasted image 20241108173905.png]]

---
#состояния_ответов #ответы
# Коды состояния ответов HTTP

**2xx (success):**
- 200 OK
- 201 Created (в основном на PUT или POST)
- 204 No Content (успешно обработан сервером, но сервер не возвращает тело ответа) (DELETE, PUT, PATCH мб POST)
**3xxx (redirect):**
- 301 Moved Permanently (запрашиваемый ресурс перемещен на новый URL)
- 304 Not Modified (запрашиваемый ресурс не был изменен с последнего доступа клиента к нему. Следовательно, используется кешированная версия ресурса и клиент использует свою копию) (тела ответа нет)
**4xx (Client Error)**
- 400 Bad Request
- 401 Unauthorized
- 402 Payment Required
- 403 Forbidden
- 409 Conflict (конфликт возникает в тех случаях, когда одно и то же действие пытаются выполнить несколько пользователей или когда состояние ресурса не позволяет завершить операцию)
- 404 Not Found 
**5xx (Server Error)**
- 500 Server Error

![[Pasted image 20241108174717.png]]

---
#интерфейсы
# Интерфейсы

**Интерфейс (interface)** - Совокупность возможностей, способов и методов взаимодействия двух информационных систем, устройств или программ

**Интерфейс программирования приложений (API)** - Набор методов, которые можно использовать для доступа к функциональности другой программы.

**Интерфейс командной строки (CLI)** - Инструкции компьютеру даются путём ввода с клавиатуры текстовых строк (команд).

**Графический интерфейс пользователя (GUI)** - Программные функции представляются графическими элементами экрана.

**Заглушки (stab) и драйверы (driver)** - Используются для эмуляции недостающих компонентов:
-  Внешние компоненты/системы (регистрация из соц. сетей без подключения к ним);
- Подсистемы/неготовые модули (регистрация без БД);
Может понадобиться специально написать их для тестируемой системы (SUT)

[API спецификаця из базы знаний](https://confluence.senlainc.com/display/KB/API+specs)
[Тестирование API](https://testengineer.ru/testirovanie-api/)

---
#api
# API

## Что такое

**API** (Application Programming Interface — программный интерфейс приложения, или интерфейс программирования приложений) — специальный протокол для взаимодействия компьютерных программ, который позволяет использовать функции одного приложения внутри другого                

API отвечает на вопрос “Как ко мне, к моей системе можно обратиться?”, и включает в себя:
- саму операцию, которую мы можем выполнить
- данные, которые поступают на вход
- данные, которые оказываются на выходе (контент данных или сообщение об ошибке)

API — это набор функций. Это может быть одна функция, а может быть много

## Примеры

На сайте «Главред» есть сервис для улучшения текстов. Чтобы воспользоваться сервисом и проанализировать свой текст, пользователям нужно было заходить на сайт. А потом разработчики «Главреда» добавили API. Теперь разработчики других платформ могут встроить сервис «Главреда» к себе, чтобы пользователи могли проводить анализ текста, не покидая приложение и не переходя на другой сайт.

Или другой пример — быстрая регистрация с помощью аккаунта в соцсетях. Приложение может использовать API социальной сети, чтобы предоставить пользователю упрощённый доступ.

Проще говоря, использовать возможности API — это как нанять внештатного сотрудника на удалённую работу. Одно приложение поручает другому выполнить необходимую работу, а его продукт предоставляет как свой.

## Как вызвать API

Напрямую:
- Система вызывает функции внутри себя
- Система вызывает метод другой систем
- Человек вызывает метод
- Автотесты дергают методы

Косвенно:
- Пользователь работает с GUI


---
#распределенные_системы
# Распределенные системы

**Распределённые системы** — это системы, состоящие из множества независимых компьютеров или узлов, которые работают вместе как единое целое для достижения общей цели. В таких системах ресурсы и задачи распределены между несколькими компьютерами, чтобы повысить производительность, устойчивость и надёжность.

### Основные характеристики распределённых систем:
	
1. **Множественность узлов**: Система состоит из нескольких вычислительных устройств (серверов, рабочих станций, мобильных устройств и т.д.), которые взаимодействуют между собой по сети.
    
2. **Прозрачность**: Пользователь взаимодействует с распределённой системой как с единым целым, не зная и не заботясь о том, что под капотом работают несколько узлов. Это касается управления данными, отказоустойчивости и даже масштабирования.
    
3. **Отказоустойчивость**: Один из ключевых аспектов распределённых систем. Сбой одного узла не должен приводить к отказу всей системы, так как другие узлы могут взять на себя его задачи.
    
4. **Масштабируемость**: Распределённые системы легко масштабируются за счёт добавления новых узлов. Это позволяет системе расти в зависимости от объёма обрабатываемых данных и нагрузки.
    
5. **Синхронизация**: Важно, чтобы все узлы работали согласованно. Это может быть сложной задачей в распределённых системах из-за проблем с задержкой и доступностью сетевых ресурсов.

### Примеры распределённых систем:
	
1. **Кластерные системы**: Несколько серверов объединяются в единый кластер, чтобы совместно решать задачи или хранить данные. Пример — кластеры баз данных (например, Cassandra или MongoDB).
    
2. **Облачные вычисления**: В облачных системах (например, AWS, Microsoft Azure) данные и вычислительные ресурсы распределяются между множеством серверов в разных местах по всему миру.
    
3. **Микросервисная архитектура**: Система состоит из множества микросервисов, которые выполняют отдельные функции. Каждый микросервис может работать на отдельном узле и взаимодействовать с другими через API.
    
4. **P2P-сети**: Peer-to-peer сети, такие как BitTorrent или блокчейн, состоят из множества равноправных узлов, которые обмениваются данными между собой без единого управляющего центра.
    

### Преимущества распределённых систем:
	
- **Устойчивость к сбоям**: Даже если один или несколько узлов выйдут из строя, система продолжит функционировать.
- **Масштабируемость**: Легко добавить новые узлы для увеличения производительности.
- **Повышение производительности**: Задачи могут параллельно распределяться между узлами, что увеличивает общую вычислительную мощность.

### Недостатки:
	
- **Сложность разработки**: Создание распределённых систем требует решения множества проблем, таких как синхронизация данных, управление отказами и сетевыми сбоями.
- **Проблемы с безопасностью**: В распределённых системах каждый узел может быть уязвим, что требует продуманного управления доступом и защитой данных.

---
#json
# Формат данных JSON (в разработке)

https://confluence.senlainc.com/display/KB/JSON

---
#xml
# Формат данных XML (в разработке)

https://confluence.senlainc.com/pages/viewpage.action?pageId=2752705

---
#gRPC #протокол #микросервисы #api
# Протокол gRPC



---
