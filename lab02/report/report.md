---
# Front matter
lang: ru-RU
title: "Лабораторная работа №2"
subtitle: "Дискреционное разграничение прав в Linux. Основные атрибуты"
author: "Ефремова Ангелина Романовна"

# Formatting
toc-title: "Содержание"
toc: true # Table of contents
toc_depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4paper
documentclass: scrreprt
polyglossia-lang: russian
polyglossia-otherlangs: english
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase
indent: true
pdf-engine: lualatex
header-includes:
  - \linepenalty=10 # the penalty added to the badness of each line within a paragraph (no associated penalty node) Increasing the value makes tex try to have fewer lines in the paragraph.
  - \interlinepenalty=0 # value of the penalty (node) added after each line of a paragraph.
  - \hyphenpenalty=50 # the penalty for line breaking at an automatically inserted hyphen
  - \exhyphenpenalty=50 # the penalty for line breaking at an explicit hyphen
  - \binoppenalty=700 # the penalty for breaking a line at a binary operator
  - \relpenalty=500 # the penalty for breaking a line at a relation
  - \clubpenalty=150 # extra penalty for breaking after first line of a paragraph
  - \widowpenalty=150 # extra penalty for breaking before last line of a paragraph
  - \displaywidowpenalty=50 # extra penalty for breaking before last line before a display math
  - \brokenpenalty=100 # extra penalty for page breaking after a hyphenated line
  - \predisplaypenalty=10000 # penalty for breaking before a display
  - \postdisplaypenalty=0 # penalty for breaking after a display
  - \floatingpenalty = 20000 # penalty for splitting an insertion (can only be split footnote in standard LaTeX)
  - \raggedbottom # or \flushbottom
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Получение практических навыков работы в консоли с атрибутами файлов, закрепление теоретических основ дискреционного разграничения доступа в современных системах с открытым кодом на базе ОС Linux.

# Задание

1. Создание учётной записи пользователя guest
2. Выполнение базовых операций с директориями и файлами
3. Заполнение таблицы "Установленные права и разрешённые действия" опытным путем
4. Заполнение таблицы "Минимальные права для совершения операций" на основании заполненной таблицы 

# Выполнение лабораторной работы

1. В установленной при выполнении предыдущей лабораторной работы операционной системе создала учётную запись пользователя guest (используя учётную запись администратора): useradd guest (рис -@fig:001).

![Создание учётной запись пользователя guest](image/1.png){ #fig:001 width=70% }

Задала пароль для пользователя guest (используя учётную запись администратора): passwd guest (рис -@fig:002).

![Задание пароля для пользователя guest](image/2.png){ #fig:002 width=70% }

Вошла в систему от имени пользователя guest (рис -@fig:003).

![Вход в систему от имени пользователя guest](image/3.png){ #fig:003 width=70% }

2. Определила директорию, в которой я нахожусь, командой pwd. Сравнила её с приглашением командной строки. Она является моей домашней директорией (рис -@fig:004).

![Опредение директории](image/4.png){ #fig:004 width=70% }

Уточнила имя пользователя командой whoami (рис -@fig:005).

![Уточнение имени пользователя командой whoami](image/5.png){ #fig:005 width=70% }

Уточнила имя пользователя, его группу, а также группы, куда входит пользователь, командой id (рис -@fig:006). 

![Команда id](image/6.png){ #fig:006 width=70% }

Выведенные значения uid, gid и др. запомнила. Сравнила вывод id с выводом команды groups, они совпадают (рис -@fig:007).

![Сравнение вывода id с выводом команды groups](image/7.png){ #fig:007 width=70% }

Просмотрела файл /etc/passwd командой cat /etc/passwd. Нашла в нём свою учётную запись. Определила uid пользователя. Определила gid пользователя. Сравнила найденные значения с полученными в предыдущих пунктах. Все сходится (рис -@fig:008).

![Команда cat /etc/passwd](image/8.png){ #fig:008 width=70% }

Определила существующие в системе директории командой ls -l /home/. Мне удалось получить список поддиректорий директории /home. Права на директориях установлены такие: drwx------, одинаковы для обоих поддиректорий (рис -@fig:009).

![Определение существующих в системе директорий](image/9.png){ #fig:009 width=70% }

Проверила, какие расширенные атрибуты установлены на поддиректориях, находящихся в директории /home, командой: lsattr /home. Мне удалось увидеть расширенные атрибуты директории. Однако не удалось увидеть расширенные атрибуты директорий других пользователей (рис -@fig:010).

![Проверка расширенных атрибутов](image/10.png){ #fig:010 width=70% }

Создала в домашней директории поддиректорию dir1 командой mkdir dir1 (рис -@fig:011).

![Создание в домашней директории поддиректории dir1 ](image/11.png){ #fig:011 width=70% }

Определила командами ls -l (рис -@fig:012) и lsattr (рис -@fig:013), какие права доступа и расширенные атрибуты были выставлены на директорию dir1.

![Права доступа на директорию dir1](image/12.png){ #fig:012 width=70% }

![Расширенные атрибуты на директорию dir1](image/13.png){ #fig:013 width=70% }

Сняла с директории dir1 все атрибуты командой chmod 000 dir1 и проверила с её помощью правильность выполнения команды ls -l (рис -@fig:014).

![Изменение прав на директории dir1и команда ls -l](image/14.png){ #fig:014 width=70% }

Попыталась создать в директории dir1 файл file1 командой echo "test" > /home/guest/dir1/file1. Я получила отказ в выполнении операции по созданию файла потому что у папки недосточно прав. Проверила командой ls -l /home/guest/dir1, действительно - файл file1 не находится внутри директории dir1 (рис -@fig:015).

![Попытка создать в директории dir1 файл file1](image/15.png){ #fig:015 width=70% }

3. Заполнила таблицу «Установленные права и разрешённые действия», выполняя действия от имени владельца директории (файлов), определив опытным путём, какие операции разрешены, а какие нет.
Если операция разрешена, занесила в таблицу знак «+», если не разрешена, знак «-».

Я не буду объяснять все операции, так как все они аналогичны и были разобраны выше, меняются только права папок и файлов. Кратко о моих действиях : (рис -@fig:016), (рис -@fig:017), (рис -@fig:018), (рис -@fig:019), (рис -@fig:020), (рис -@fig:021), (рис -@fig:022), (рис -@fig:023), (рис -@fig:024).


![Заполнение таблицы «Установленные права и разрешённые действия»](image/16.png){ #fig:016 width=70% }

![Заполнение таблицы «Установленные права и разрешённые действия»](image/17.png){ #fig:017 width=70% }

![Заполнение таблицы «Установленные права и разрешённые действия»](image/18.png){ #fig:018 width=70% }

![Заполнение таблицы «Установленные права и разрешённые действия»](image/19.png){ #fig:019 width=70% }

![Заполнение таблицы «Установленные права и разрешённые действия»](image/20.png){ #fig:020 width=70% }

![Заполнение таблицы «Установленные права и разрешённые действия»](image/21.png){ #fig:021 width=70% }

![Заполнение таблицы «Установленные права и разрешённые действия»](image/22.png){ #fig:022 width=70% }

![Заполнение таблицы «Установленные права и разрешённые действия»](image/23.png){ #fig:023 width=70% }

![Заполнение таблицы «Установленные права и разрешённые действия»](image/24.png){ #fig:024 width=70% }

И сама таблица (таб. 3.1):


|Права д-ии|Права ф-ла|Созд. ф-ла|Удал. ф-ла|Зап. в ф-л|Чт. ф-ла|Смена д-ии|Просм. ф-в|Переим. ф-ла|См. атр.|
|----------|----------|----------|----------|----------|--------|----------|----------|------------|--------|
|(000)     |(000)     |-         |-         |-         |-       |-         |-         |-           |-       |
|(100)     |(000)     |-         |-         |-         |-       |+         |-         |-           |+       |
|(200)     |(000)     |-         |-         |-         |-       |-         |-         |-           |-       |
|(300)     |(000)     |+         |+         |-         |-       |+         |-         |+           |+       |
|(400)     |(000)     |-         |-         |-         |-       |-         |+         |-           |-       |
|(500)     |(000)     |-         |-         |-         |-       |+         |+         |-           |+       |
|(600)     |(000)     |-         |-         |-         |-       |-         |+         |-           |-       |
|(700)     |(000)     |+         |+         |-         |-       |+         |+         |+           |+       |
|(100)     |(100)     |-         |-         |-         |-       |+         |-         |-           |+       |
|(300)     |(100)     |+         |+         |-         |-       |+         |-         |+           |+       |
|(500)     |(100)     |-         |-         |-         |-       |+         |+         |-           |+       |
|(700)     |(100)     |+         |+         |-         |-       |+         |+         |+           |+       |
|(100)     |(200)     |-         |-         |+         |-       |+         |-         |-           |+       |
|(300)     |(200)     |+         |+         |+         |-       |+         |-         |+           |+       |
|(500)     |(200)     |-         |-         |+         |-       |+         |+         |-           |+       |
|(700)     |(200)     |+         |+         |+         |-       |+         |+         |+           |+       |
|(100)     |(300)     |-         |-         |+         |-       |+         |-         |-           |+       |
|(300)     |(300)     |+         |+         |+         |-       |+         |-         |+           |+       |
|(500)     |(300)     |-         |-         |+         |-       |+         |+         |-           |+       |
|(700)     |(300)     |+         |+         |+         |-       |+         |+         |+           |+       |
|(100)     |(400)     |-         |-         |-         |+       |+         |-         |-           |+       |
|(300)     |(400)     |+         |+         |-         |+       |+         |-         |+           |+       |
|(500)     |(400)     |-         |-         |-         |+       |+         |+         |-           |+       |
|(700)     |(400)     |+         |+         |-         |+       |+         |+         |+           |+       |
|(100)     |(500)     |-         |-         |-         |+       |+         |-         |-           |+       |
|(300)     |(500)     |+         |+         |-         |+       |+         |-         |+           |+       |
|(500)     |(500)     |-         |-         |-         |+       |+         |+         |-           |+       |
|(700)     |(500)     |+         |+         |-         |+       |+         |+         |+           |+       |
|(100)     |(600)     |-         |-         |+         |+       |+         |-         |-           |+       |
|(300)     |(600)     |+         |+         |+         |+       |+         |-         |+           |+       |
|(500)     |(600)     |-         |-         |+         |+       |+         |+         |-           |+       |
|(700)     |(600)     |+         |+         |+         |+       |+         |+         |+           |+       |
|(100)     |(700)     |-         |-         |+         |+       |+         |-         |-           |+       |
|(300)     |(700)     |+         |+         |+         |+       |+         |-         |+           |+       |
|(500)     |(700)     |-         |-         |+         |+       |+         |+         |-           |+       |
|(700)     |(700)     |+         |+         |+         |+       |+         |+         |+           |+       |

Таблица 3.1: Установленные права и разрешённые действия


4. На основании заполненной таблицы определила те или иные минимально необходимые права для выполнения операций внутри директории
dir1, заполнила таблицу "Минимальные права для совершения операций" (таб. 4.1).


|Операция              |Мин. права на директорию|Мин. права на файл|
|----------------------|------------------------|------------------|
|Создание файла        |d-wx------ (300)        |0                 |
|Удаление файла        |d-wx------ (300)        |0                 |
|Чтение файла          |d--x------ (100)        |-r-------- (400)  |
|Запись в файл         |d--x------ (100)        |--w------- (200)  |
|Переименование файла  |d-wx------ (300)        |0                 |
|Создание поддиректории|d-wx------ (300)        |0                 |
|Удаление поддиректории|d-wx------ (300)        |0                 |

Таблица 4.1: Минимальные права для совершения операций
                

# Выводы

В процессе выполнения лабораторной работы 2 я приобрела практические навыки работы в консоли с атрибутами файлов, закрепление теоретических основ дискреционного разграничения доступа в современных системах с открытым кодом на базе ОС Linux.