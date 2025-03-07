---
tags:
  - HTTP
  - HTTP_headers
  - HTTPS
  - URL_запрос
---

---
#HTTP
# HTTP

**HTTP** (HyperText Transfer Protocol — протокол передачи гипертекста) — это основной протокол для передачи данных, особенно веб-страниц, изображений, видео и других ресурсов в World Wide Web. 

HTTP определяет способ взаимодействия между веб-клиентами (обычно веб-браузерами) и веб-серверами. Он является частью более обширного протокола TCP/IP, который лежит в основе всей сетевой коммуникации в Интернете.

#### Как он работает

**1. Запрос от клиента:** Когда пользователь вводит URL веб-сайта в браузере или кликает на ссылку, браузер отправляет запрос HTTP на сервер, где расположен запрашиваемый ресурс.

**2. Обработка запроса сервером:** Веб-сервер принимает запрос, обрабатывает его и возвращает ответ, который может включать запрошенный контент (например, HTML-страницу) или сообщение об ошибке, если ресурс не найден или доступ к нему запрещён.

**3. Ответ сервера:** Ответ содержит статус выполнения запроса (код состояния) и, при успешном запросе, запрошенные данные.

#### HTTP запрос

![](Pasted%20image%2020241205113051.png)

1. Стартовая строка содержит метод, путь до ресурса, версию протокола.
2. Заголовки.
3. Blank line – пустая строка (ее обязательно ставят между заголовками и боди запроса).
4. Тело сообщения.
#### Особенности:

- **Без состояний:** Является протоколом без сохранения состояния (stateless), что означает, что каждый запрос обрабатывается независимо, без сохранения информации о предыдущих взаимодействиях. Это упрощает архитектуру, но для сохранения состояния между запросами используются куки и сессии.
	
- **Простота и расширяемость:** Предлагает простую структуру запросов и ответов, которая легко расширяема через заголовки для передачи дополнительной информации.
	
- **Методы запросов:** Определяет различные [методы запросов](HTTP%20методы), такие как GET для получения данных, POST для отправки данных на сервер, DELETE для удаления ресурсов и другие, позволяя реализовывать различные операции над ресурсами.
	
- **Безопасность:** Поскольку он по умолчанию не шифрует данные, передаваемые между клиентом и сервером, для обеспечения безопасности часто используется HTTPS (HTTP Secure), который добавляет шифрование с помощью SSL/TLS.

HTTP продолжает развиваться, и его последняя версия, HTTP/2 (опубликована в 2015 году), предлагает улучшения в эффективности передачи данных и производительности по сравнению с предыдущими версиями.

---
#HTTP_headers
# Заголовки HTTP запроса

Все заголовки разделяются на ***четыре основных группы***:

1. **General Headers** (Основные заголовки) 
	- могут включаться в любое сообщение клиента и сервера.
2. **Request Headers** (Заголовки запроса) 
	- используются только в запросах клиента.
3. **Responce Headers** (Заголовки ответа) 
	- используются только для ответов от сервера.
4. **Entity Headers** (Заголовки сущности) 
	- сопровождают каждую сущность сообщения.

## Легче всего запоминаются:

#### 1. Accept 
-  используется, чтобы определить тип информации, который должен содержаться в ответе сервера
- *@:* Accept: text/plain; q=0.5, text/html, text/x-dvi; q=0.8, text/x-c
#### 2. Authorization 
- используется для отправки данных авторизации на сервер. 
- *@:* Authorization: Basic QWxhZGRpbjpvcGVuIHNlc2FtZQ==
#### 3. Host 
- используется для указания доменного имени и порта запрашиваемого ресурса
- *@:* Host: zametkinapolyah.ru
#### 4. Proxy-Authorization 
- содержит в себе информацию для авторизации на прокси-сервере
- *@:* Proxy-Authorization: Basic QWxhZGRpbjpvcGVuIHNlc2FtZQ==
#### 5. Referer 
- содержит в себе URI ресурса, с которого клиент перешел на данный ресурс
- *@:* Referer: //zametkinapolyah.ru
#### 6. User-Agent
- содержит в себе полную информацию о клиенте пользователя, например, о браузере
- *@:* User-Agent: CERN-LineMode/2.15 libwww/2.17b3
#### 7. Content-Encoding 
- указывает на дополнительный способ кодирования тела HTTP объекта с целью сжатия
- *@:* Content-Encoding: gzip
#### 8. Content-Language
- указывает серверу на каком языке нужна информация, находящаяся в теле объекта
- *@:* Content-Language: mi, en
#### 9. Content-Type 
- используется для указания типа данных в теле сообщения
- *@:* Content-Type: text/html;charset=utf-8

[Все виды заголовков и их описание](https://zametkinapolyah.ru/servera-i-protokoly/tema-10-spravochnik-polej-http-zagolovkov-spisok-polej-http-zagolovka-zagolovki-http-soobshhenij-zaprosov-i-otvetov.html)

---
#URL_запрос
# HTTP(S) запрос по REST

## Состав запроса URL

#### 1. Выбор протокола
- Фрагмент *'http://'* или *'https://'*
- Определяет какой должен использоваться протокол для браузера при обращении на сайт
#### 2. Выбор домена сайта (второго уровня)
- Фрагмент *'example.com'* или *'www.example.com'* - одно и то же
- Определяет выбор сервера, к которому следует подключение
#### 3. Прописываем ***/*** для запроса конкретного документа
- Получается *'example.com/document'* - обращение к конкретному ресурсу сервера
#### 4. Прописываем дополнительные параметры к документу через ***?*** и ***=***
- называется *параметрами запроса*
- знак *?* - разделитель, далее следует пара ключ-значение через *=*
- *@:* http://example.com/login.php?id=228
#### 5. Знак ***&*** используется для объединения нескольких параметров
- *@:* http://example.com/login.php?id=228&sect=8
#### 6. Знак ***#*** используется для выбора части документа
- *@:* https://example.com/document?page=4#anekdoti

[Сурс](https://confluence.senlainc.com/pages/viewpage.action?pageId=30376261#:~:text=C%D1%82%D1%80%D1%83%D0%BA%D1%82%D1%83%D1%80%D0%B0%20%D0%BF%D1%80%D0%BE%D1%82%D0%BE%D0%BA%D0%BE%D0%BB%D0%B0%20HTTP,%D0%B4%D0%BB%D1%8F%20%D0%BE%D1%82%D0%BF%D1%80%D0%B0%D0%B2%D0%BA%D0%B8%20%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81%D0%B0%3F)

---
#HTTPS
# HTTPS

**HTTPS** (HyperText Transfer Protocol Secure) — это расширенная безопасная версия протокола HTTP, предназначенная для безопасной передачи данных между клиентом (обычно веб-браузером) и сервером. Основное отличие HTTPS от HTTP заключается в том, что HTTPS использует шифрование для защиты передаваемой информации, предотвращая её перехват и изменение посторонними лицами.
## Ключевые аспекты:

- **Шифрование:** Данные, передаваемые между клиентом и сервером, шифруются с использованием SSL (Secure Sockets Layer) или TLS (Transport Layer Security) протоколов. Это означает, что даже если данные будут перехвачены, они окажутся бессмысленным набором символов без ключа шифрования.
- **Аутентификация:** HTTPS помогает убедиться, что пользователь действительно соединяется с тем сервером, за который он себя выдает. Это достигается благодаря использованию SSL/TLS сертификатов, которые выдаются и подписываются доверенными центрами сертификации (CA).
- **Целостность данных:** Протокол гарантирует, что передаваемые данные не будут изменены или повреждены в процессе передачи, обеспечивая их целостность.
## Применение:

- **Веб-сайты, требующие аутентификации:** Любой сайт, который требует от пользователей ввода логина и пароля, должен использовать его для защиты учетных данных.
- **Электронная коммерция:** Сайты, на которых происходят финансовые транзакции и обработка платёжной информации, используют его для защиты финансовой информации клиентов.
- **Конфиденциальная информация:** Сайты, обрабатывающие личные данные, медицинскую информацию, и другие чувствительные данные, используют его для обеспечения конфиденциальности информации.

***Основное отличие*** между HTTP и HTTPS заключается в том, что HTTPS обеспечивает зашифрованное и безопасное соединение, предотвращая возможность чтения или изменения передаваемых данных третьими лицами. Это делает HTTPS предпочтительным выбором для обеспечения безопасности и конфиденциальности в Интернете.

[HTTPS](https://easyoffer.ru/question/7890)
[Разница HTTP и HTTPS](https://easyoffer.ru/question/7890)

---