---
tags:
  - методы_взаимодействия_сервисов
  - RPC
  - gRPC
---

---
#методы_взаимодействия_сервисов
# Основные методы взаимодействия сервисов в общем

#### 1. REST (Representational State Transfer)
	
- Архитектурный стиль, основанный на [принципах](REST%20и%20SOAP#Принципы%20REST), описанных в диссертации Роя Филдинга.
    
- Использует стандартные методы HTTP (GET, POST, PUT, DELETE) для взаимодействия с ресурсами.
    
- Обмен данных часто происходит в формате [JSON](Форматы%20данных#Формат%20данных%20JSON) или [XML](Форматы%20данных#Формат%20данных%20XML).
    
#### 2. RPC (Remote Procedure Call):
    
- Механизм, позволяющий вызывать функции или процедуры на удаленном сервере, как если бы они были локальными.
    
- Примеры: gRPC, SOAP, JSON-RPC.
    
#### 3. Message Brokers:
    
- Асинхронный метод обмена сообщениями между различными компонентами системы.
    
- Примеры: [RabbitMQ](Base/Микросервисы%20и%20брокеры#RabbitMQ), [Apache Kafka](/Base/Микросервисы%20и%20брокеры#Apache%20Kafka), Apache ActiveMQ.

---
#RPC 
# Протокол RPC

**Remote Procedure Call (RPC)** – это протокол взаимодействия между клиентом и сервером, который позволяет клиенту вызывать процедуры (функции, методы) на удаленном сервере, как если бы они были локальными

Позволяет программам работать в распределенной среде, скрывая сложности передачи данных и выполнения удаленных операций

- передача сообщений между программами
-  программист специально не кодирует детали для удаленного взаимодействия
- вызов процедуры также управляет транспортным протоколом низкого уровня 
	- *@:* протокол пользовательских дейтаграмм, протокол управления передачей / Интернет-протокол
- уязвим к сбоям (задействованы система связи, другая машина и другой процесс)
- легкая обучаемость
- большое сообщество

#### Основные компоненты RPC

- **Клиент**: Программа или компонент, инициирующий вызов удаленной процедуры.
    
- **Сервер**: Программа или компонент, предоставляющий методы, которые могут быть вызваны удаленно.
    
- **Прокси**: Клиент использует прокси-объект для вызова удаленных процедур на сервере, как если бы они были локальными.
    
- **Сериализация**: процесс преобразования данных и параметров процедур в формат, который может быть передан через сеть (например, в формат JSON, бинарный формат и т.д.)
    
- **Транспорт**: механизм передачи сериализованных данных между клиентом и сервером, например, http.
    
- **IDL** (Interface Definition Language): Язык определения интерфейса, который определяет структуру и сигнатуры удаленных процедур.

Протокол RPC позволяет разработчикам вызывать функции или методы на удаленных серверах таким образом, что код клиента выглядит так, как будто вызовы происходят локально. Процессы сериализации и десериализации обеспечивают преобразование данных между форматами, понятными клиенту и серверу.

Преимущества RPC включают простоту использования, удобство абстракции и возможность вызова удаленных процедур, не заботясь о деталях взаимодействия по сети.
#### Используемые форматы данных
- JSON, 
- XML, 
- Protobuf, 
- Thrift, 
- FlatBuffers
#### Где используется
- Командный и ориентированный на действия API; 
- внутренняя высокопроизводительная коммуникация в массивных системах микросервисов  
- Благодаря своей сильной связанности RPC хорошо годится для внутренних микросервисов, но это не вариант для сильного внешнего API или API-сервиса.

#### Инструменты для реализации

- **gRPC** - это фреймворк, разработанный компанией Google, который предоставляет мощный и эффективный механизм для реализации RPC в различных языках программирования. Он использует Protocol Buffers для определения структуры данных и HTTP/2 для передачи данных. Хотя Protobuf не единственный способ представления данных, но самый распиаренный. Появляются такие инструменты, например, как FlatBuffers, которые пытаются ускорить сериализацию данных. В gRPC также поддерживаются различные языки, что делает его очень гибким.
    
- **JSON-RPC** - это простой протокол для обмена данными в формате JSON между сервером и клиентом
    
- **Twirp** - это фреймворк для создания простых и эффективных API с использованием протокола RPC. Он также основан на Protocol Buffers.

По таким причинам обычно берут самый популярный, удовлетворяющий производительностью, хорошо документированный, мультиязычный и функциональный инструмент. В европейских регионах это gRPC.

[Материал с CoderLessons (с VPN)](https://coderlessons.com/tutorials/akademicheskii/osnovy-operatsionnykh-sistem/13-udalennyi-vyzov-protsedur-rpc)
[Статья на Хабр](https://habr.com/ru/articles/787164/)

---
#gRPC 
# Протокол gRPC

**gRPC** - это Google фреймворк, т.е. достаточно комплексное решение. На данный момент он отправляет данные по протоколу http 2. Обычно поверх него не добавляются шифрование в виде протокола TLS, однако при необходимости его можно добавить.

Передача данных идет в бинарном формате. Данных получается меньше, они более оптимизированы, чем тот же json (весь json объект будет приведен в символы ASCII для передачи, что влечёт за собой передача неоптимальных и ненужных байтов).

- **protobuf** - самый популярный протокол преобразования данных
*@:*
syntax = "proto3";
message User {  
	string name = 1;
}

## Возможности gRPC

#### 1. Протокол-независимая сериализация
	
- По умолчанию используется Protocol Buffers (ProtoBuf) для сериализации данных.
    
- Возможна поддержка других форматов сериализации, таких как JSON.
#### 2. Поддержка множества языков:
    
- gRPC поддерживает множество языков программирования, включая C++, Java, Python, Go, Ruby, C#, Node.js, и многие другие.
#### 3. Одновременные запросы (Multiplexing):
    
- Позволяет отправлять несколько запросов и получать несколько ответов одновременно на одном соединении.
#### 4. Streaming:
	
- Поддерживает как однонаправленный, так и двунаправленный поток данных.
    
- Клиенты и серверы могут отправлять последовательности сообщений.
#### 5. Автоматическая генерация кода:
    
- Генерация клиентского и серверного кода на основе описания API в proto файле (Protocol Buffers).
#### 6. Сжатие данных:
    
- Возможность сжимать данные для уменьшения объема трафика.
#### 7. Поддержка SSL/TLS:
    
- Возможность обеспечивать безопасную передачу данных с использованием SSL/TLS.
#### 8. Библиотека метаданных:
    
- Возможность отправлять и получать метаданные в заголовках запросов.
#### 9. Отмена запросов:
	
- Клиенты могут отменять отправленные запросы, что особенно полезно в асинхронных сценариях.
#### 10. gRPC-заголовки:
    
- Поддержка кастомизированных заголовков для передачи дополнительной информации.
#### 11. Дополнительные аутентификационные механизмы:
    
- Поддержка аутентификации с использованием токенов и других механизмов.
#### 12. gRPC Web:
	
- Возможность использовать gRPC в веб-браузерах с использованием gRPC Web.
#### 13. Средства мониторинга и трассировки:
    
- Интеграция с инструментами мониторинга, такими как Prometheus, и трассировки, такими как Jaeger.
#### 14. Встроенная поддержка статусов:
    
- Поддержка стандартных и пользовательских кодов статуса.

## Пример запроса

***Тело запроса***

message User {  
	string name = "321";
}

***Запрос:***
1. **POST /path/to/resource/CreateUser HTTP/2**
	- Указывает метод запроса и версию HTTP (HTTP/2.0).
	
2. **Host: [example.com](http://example.com/)** 
	- Заголовок Host указывает на адрес сервера
	
3. **Content-Type: application/grpc** 
    - Указывает, что контент запроса представляет собой gRPC
	
4. **User-Agent: grpc-go/1.42.0**  
    - Информация о пользователе, указывающая на использование gRPC на сервере go 1.42.0 версии
	
5. **Content-Length: 5**
    - Указывает на длину бинарного тела запроса в байтах
	
6. **0a033231**
	- Тело запроса, представленное в виде 16-ричной системы для более удобной читаемости. Оно содержит бинарное представление protobuf-сообщения
		- *0a:* Тег и тип поля. В данном случае, 0a указывает на поле с тегом 1 (поле name) и типом данных "байтовая строка" (string)
		- *03*: Длина следующей строки в байтах. Здесь 03 означает, что следующая строка имеет длину 3 байта
		- *3231*: Это ASCII-кодированное представление строки "321" в шестнадцатеричной системе счисления

Дополнительно заголовки шифруются по принципам http 2 с помощью алгоритма HPACK

[Статья на Хабр](https://habr.com/ru/articles/787164/)

---
#коды_состояний #gRPC 
# Коды состояний gRPC

Согласно официальной документации gRPC, эти коды стандартизированы и применяются для всех языков

### Основные коды ответа gRPC

1. **OK (0)**  
    Указывает на успешное выполнение операции. Это стандартный код при успешном завершении вызова.
    
2. **CANCELLED (1)**  
    Указывает, что операция была отменена либо клиентом, либо сервером. Причины могут быть разными, включая истечение времени ожидания или пользовательскую отмену.
    
3. **UNKNOWN (2)**  
    Ошибка неизвестного характера. Может быть вызвана непредвиденной ошибкой, не отображенной в других статусах.
    
4. **INVALID_ARGUMENT (3)**  
    Клиент передал недопустимый аргумент. Обычно это ошибка валидации входных данных.
    
5. **DEADLINE_EXCEEDED (4)**  
    Превышен лимит времени выполнения операции. Сервер мог не успеть обработать запрос до истечения дедлайна.
    
6. **NOT_FOUND (5)**  
    Указывает, что запрашиваемый ресурс или данные не найдены.
    
7. **ALREADY_EXISTS (6)**  
    Ресурс или объект, который пытается создать клиент, уже существует.
    
8. **PERMISSION_DENIED (7)**  
    У клиента недостаточно прав для выполнения операции. Это может быть связано с ошибками аутентификации или авторизации.
    
9. **RESOURCE_EXHAUSTED (8)**  
    Достигнут лимит использования ресурса, например, исчерпанная квота или нехватка оперативной памяти.
    
10. **FAILED_PRECONDITION (9)**  
    Операция не может быть выполнена в текущем состоянии системы, например, несоответствие предпосылок выполнения.
    
11. **ABORTED (10)**  
    Операция прервана, возможно, из-за конфликта, например, при конкурентной модификации данных.
    
12. **OUT_OF_RANGE (11)**  
    Операция выходит за пределы допустимого диапазона, например, индексация вне границ массива.
    
13. **UNIMPLEMENTED (12)**  
    Запрашиваемый метод не поддерживается сервером.
    
14. **INTERNAL (13)**  
    Внутренняя ошибка сервера. Это может быть вызвано неисправностью сервера или его компонентов.
    
15. **UNAVAILABLE (14)**  
    Сервер недоступен, например, из-за сбоев в сети или отключения сервера.
    
16. **DATA_LOSS (15)**  
    Указывает на необратимую потерю данных. Это считается одним из самых серьезных ошибок.
    
17. **UNAUTHENTICATED (16)**  
    Клиент не прошел аутентификацию. Обычно это связано с отсутствием или недействительными учетными данными.

---
