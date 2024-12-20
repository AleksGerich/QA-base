---
tags:
  - bash
  - мета_символы
  - конвейер
  - apt
---

---

#bash
# Bash

**Bash** (Bourne Again SHell) — это один из наиболее популярных и мощных командных интерпретаторов для операционных систем на базе Unix (Linux, macOS). Bash является частью проекта GNU и по сути представляет собой улучшенную версию раннего интерпретатора команд Bourne Shell (sh), добавляя к нему множество новых возможностей.

## Основные возможности Bash:

- **Интерпретатор командной строки**
	
- **Скриптинг**: Bash можно использовать для написания скриптов (последовательности команд)
	
- **Перенаправление ввода/вывода** (`|`)
	
- **Множество встроенных команд** (@: `ls`, `cd`, `grep`, `find`, и т. д.)
	
- **Переменные и функции**: Bash поддерживает работу с переменными, как встроенными (например, `PATH`, `HOME`), так и пользовательскими. Также можно создавать функции для повторного использования кода в скриптах
    
- **Циклы и условия**: Bash позволяет управлять выполнением команд с помощью условий (`if`, `else`, `elif`) и циклов (`for`, `while`, `until`), что дает возможность автоматизировать сложные сценарии

## Примеры использования Bash:

1. **Автоматизация задач**
2. **Системное администрирование**: Системные администраторы используют Bash для управления серверами и системными настройками, включая управление пользователями, процессами, файлами и сетью
3. **Обработка текстов**: Комбинации команд вроде `grep`, `awk`, `sed` позволяют обрабатывать текстовые файлы, искать строки, изменять содержимое файлов и многое другое

[Bash-одностроковые команды](https://onceupon.github.io/Bash-Oneliner/)

---
#мета_символы #meta_characters #bash #регулярные_выражения
# Мета символы

**Мета-символы** — это специальные символы, используемые в различных языках программирования, инструментах для работы с текстом (например, регулярные выражения), оболочках (таких как Bash) и других системах обработки данных. Мета-символы могут влиять на способ интерпретации текста или команд и используются для управления выводом, поиска, замены или других операций.

## Регулярные выражения
Используют мета-символы для описания шаблонов поиска в строках
1. **`.` (точка)**: соответствует любому одному символу
    - @: `a.b` найдет такие строки, как `aab`, `acb`, `a1b`
2. **`^` (каретка)**: обозначает начало строки
    - @: `^abc` найдет строки, которые начинаются с `abc`
3. **`$` (знак доллара)**: обозначает конец строки
    - @: `xyz$` найдет строки, которые заканчиваются на `xyz`
4. **`*` (звездочка)**: соответствует нулю или более предыдущих символов
    - @: `ab*` найдет такие строки, как `a`, `ab`, `abb`
5. **`+` (плюс)**: соответствует одному или более предыдущих символов
    - @: `ab+` найдет `ab`, `abb`, но не просто `a`
6. **`[]` (квадратные скобки)**: определяет набор символов для поиска
    - @: `[abc]` найдет `a`, `b`, или `c`
7. **`\` (обратный слэш)**: используется для экранирования мета-символов
    - @: если вам нужно найти точку в строке, вы пишете `\.` вместо `.`

## Bash:
Используются для перенаправления, подстановок и управления выполнением команд
1. **`*` (звездочка)**: подстановка, соответствует любому числу символов
    - @: `ls *.txt` найдет все файлы с расширением `.txt`
2. **`?`**: подстановка, соответствует одному символу
    - @: `ls file?` найдет файлы, названия которых состоят из пяти символов и начинаются на `file`
3. **`|` (пайп)**: перенаправляет вывод одной команды в качестве ввода для другой команды
    - @: `ls | grep "txt"` выводит только те файлы, которые содержат "txt" в названии
4. **`>` и `>>`**: используются для перенаправления вывода в файл. `>` перезаписывает файл, а `>>` добавляет данные в конец файла
    - @: `echo "Hello" > file.txt` перезапишет файл `file.txt` строкой "Hello"
5. **`&`**: используется для выполнения команды в фоновом режиме
    - @: `./script.sh &` запустит скрипт в фоне

---

#pipeline #пайплайны #bash #конвейер
# Pipeline (конвейер)

В контексте работы с данными, **data pipeline** — это процесс передачи данных из одного источника в другой (например, из базы данных в хранилище или аналитическую систему), включающий этапы извлечения, трансформации и загрузки (ETL — Extract, Transform, Load)

Типичные шаги:
- Извлечение данных из различных источников.
- Трансформация данных (нормализация, фильтрация, агрегация).
- Загрузка данных в конечную систему (например, в хранилище данных или аналитический инструмент).

**В контексте оболочки Bash** — это комбинация команд, которые выполняются последовательно, где вывод одной команды передается в качестве ввода для следующей. Это достигается с помощью символа `|` (pipe).

- @: cat file.txt | grep "pattern" | sort | uniq

---
#apt #DPKG
# apt и DPKG

В Linux ПО = software packages

**В любое время можно установить и удалить пакеты**

Как правило, устанавливаемым пакетам нужны зависимости - дополнительные пакеты, которые устанавливаются перед или после установки нужных пакетов

Но в Linux зачастую есть **систама управления пакетами**, устанавливающая необходимые зависимости сама, а также может обновлять и удалять пакеты - ***apt*** (advanced package tool)

• Все пакеты храдятся в удаленных хранилищах, откуда ведется скачивание - репозитории
• путь репозитория по умолчанию: /etc/apt/sources.list (использовать cat для открытия)
• лист содержит URL-адреса, ведущих на сайты скачивания

#### Команды для взаимодействия с apt:

- **apt-cache search** - поиск нужного пакета
	
- **apt-cache show** - показ информации о пакете
	
- **apt-get install** - установка пакета
	
- **-y** - опция для авто-ответов да
	
- **apt-get remove** - удаление пакета (но оставляет файлы конфигурации)
	
- **apt-get purge** - удаление и пакета и файлов конфигурации
	
- **apt-get update** - обновление системы
	
- **apt-get upgrade** - обновление установленных пакетов
	
- **apt-get dist-upgrade** - обновление пакетов с зависимостями


Иногда система жертвы может не быть подключена к интернету. В таком случает не получится установить необходимые пакеты привычным образом. В этом  случае используется **DPKG** (depackage)

Помогает, когда невозможно найти определенное ПО в репозиториях.

Пакет берется с сайта-источника с расширением .deb и устанавливается

Зависимости придется искать и устанавливать самому

#### Работа с DPKG:

- **dpkg -l** - проверка версии установленных приложений
	
- **dpkg -i \[имя пакета].deb** - установка пакета
	
- **dpkg -r \[имя пакета].deb** - удаление пакета



