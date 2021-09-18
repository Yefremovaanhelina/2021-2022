---
# Front matter
lang: ru-RU
title: "Лабораторная работа №1"
subtitle: "Установка и конфигурация операционной системы на виртуальную машину"
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

Приобретение практических навыков установки операционной системы на виртуальную машину, настройки минимально необходимых для дальнейшей работы сервисов.

# Задание

1. Установка VirtualBox 
2. Установка на виртуальную машину VirtualBox операционной системы Linux, дистрибутив Centos
3. Создание, запуск и конфигурация виртуальной машины Base
4. Создание виртуальной машины Host2 на основе созданной виртуальной машины Base

# Выполнение лабораторной работы

1. Я создала на своем ноутбуке новый каталог на диске С с моим именем пользователя arefremova и загрузила в него образ виртуальной машины CentOS-6.6-i386-bin-DVD1.iso (рис -@fig:001).

![Новый каталог arefremova и образ в нем](image/1.png){ #fig:001 width=70% }

Запустила виртуальную машину, введя VirtualBox в командной строке (рис -@fig:002).

![Менеджер VirtualBox](image/2.png){ #fig:002 width=70% }

Проверила в свойствах VirtualBox месторасположение каталога для виртуальных машин. Для этого в VirtualBox выбрала "Файл", затем "Свойства", зашла во вкладку "Общие". В поле "Папка для машин" должен стоять путь к недавносозданному каталогу с моим именем. И все верно - путь стоит к нужной мне папке (рис -@fig:003).

![Окно «Свойства» VirtualBox](image/3.png){ #fig:003 width=70% }

Создала новую виртуальную машину. Для этого в VirtualBox выбрала "Машина" - "Создать". Указала имя виртуальной машины — Base, тип операционной системы — Linux, RedHat (рис -@fig:004).

![Окно «Имя машины и тип ОС»](image/4.png){ #fig:004 width=70% }

Указала размер основной памяти виртуальной машины — 1024 МБ (рис -@fig:005).

![Окно «Размер основной памяти»](image/5.png){ #fig:005 width=70% }

Задала конфигурацию жёсткого диска — загрузочный (рис -@fig:006), VDI (BirtualBox Disk Image) (рис -@fig:007), динамический виртуальный диск (рис -@fig:008).

![Окно «Виртуальный жесткий диск»](image/6.png){ #fig:006 width=70% }

![Окно «Мастер создания нового виртуального диска»](image/7.png){ #fig:007 width=70% }

![Окно «Дополнительные атрибуты виртуального диска»](image/8.png){ #fig:008 width=70% }

Задам размер диска — 40 ГБ, его расположение — в данном случае в папке Base в моем созданном каталоге (рис -@fig:009).

![Окно «Расположение и размер виртуального диска»](image/9.png){ #fig:009 width=70% }

2. Выделяю в окне менеджера VirtualBox виртуальную машину Base, и открываю окно "Свойства". Проверю, что папка для снимков виртуальной машины Base имеет путь к /Base/Snapshots в моем созданном каталоге. Для этого выбираю в VirtualBox "Свойства" виртуальной машины Base, "Общие", вкладка "Дополнительно". Все в порядке, путь верный (рис -@fig:010).

![Окно «Свойства» виртуальной машины Base](image/10.png){ #fig:010 width=70% }

Выберу в VirtualBox "Свойства" - "Носители виртуальной машины" (рис -@fig:011).

![Окно «Носители» виртуальной машины Base: выбор образа оптического диска](image/11.png){ #fig:011 width=70% }

Добавлю новый привод оптических дисков и выберу образ CentOS-6.6-i386-bin-DVD1.iso (рис -@fig:012).

![Окно «Носители» виртуальной машины Base](image/12.png){ #fig:012 width=70% }

3. Запускаю виртуальную машину Base, выберу установку системы на жёсткий диск (рис -@fig:013).

![Запуск установки системы](image/13.png){ #fig:013 width=70% }

Устанавливаю русский язык для интерфейса (рис -@fig:014) и раскладки клавиатуры (рис -@fig:015).

![Виртуальная машина Base. Установка русского языка](image/14.png){ #fig:014 width=70% }

![Виртуальная машина Base. Установка русского языка для раскладки клавиатуры](image/15.png){ #fig:015 width=70% }

Указываю "Стандартные накопители" для установки ОС (рис -@fig:016).

![Виртуальная машина Base](image/16.png){ #fig:016 width=70% }

В окне конфигурации жёсткого диска выбираю "Да, удалить данные" (рис -@fig:017).

![Конфигурация жёсткого диска](image/17.png){ #fig:017 width=70% }

В качестве имени машины указываю «arefremova.localdomain» (рис -@fig:018).

![Задать сетевое имя виртуальной машины](image/18.png){ #fig:018 width=70% }

Указываю часовой пояс «Москва» (рис -@fig:019).

![Указать часовой пояс «Москва»](image/19.png){ #fig:019 width=70% }

Устанавливаю пароль для root (рис -@fig:020).

![Установка пароля для root](image/20.png){ #fig:020 width=70% }

При конфигурировании размера жёсткого диска указываю «Всё пространство» (рис -@fig:021).

![Конфигурирование размера жёсткого диска](image/21.png){ #fig:021 width=70% }

Выбираю вариант стандартной установки CentOS (рис -@fig:022).

![Варианты стандартной установки CentOS](image/22.png){ #fig:022 width=70% }

Завершаю установку операционной системы (рис -@fig:023) и перезагружаю её.

![Виртуальная машина Base. Завершение установки](image/23.png){ #fig:023 width=70% }

В VirtualBox оптический диск должен отключиться автоматически, что он, к счастью, и сделал. Запустила виртуальную машину Base и настроила её (рис -@fig:024, рис -@fig:025, рис -@fig:026, рис -@fig:027).

![Запуск системы](image/24.png){ #fig:024 width=70% }

![Информация о лицензии](image/25.png){ #fig:025 width=70% }

![Настройка виртуальной машины: учётная запись](image/26.png){ #fig:026 width=70% }

![Настройка виртуальной машины: дата и время](image/27.png){ #fig:027 width=70% }

Подключилась к виртуальной машине с помощью созданной учётной записи и ввела пароль (рис -@fig:028).

![Подключение к виртуальной машине](image/28.png){ #fig:028 width=70% }

На виртуальной машине Base запустила терминал, перешла под учетную запись root с помощью команды su (рис -@fig:029).

![Переход под учетную запись root](image/29.png){ #fig:029 width=70% }

С помощью команды yum update обновила системные файлы (рис -@fig:030).

![Обновление системных файлов](image/30.png){ #fig:030 width=70% }

Установила необходимые программы, например, mc с помощью команд yum update; yum install mc (рис -@fig:031).

![Установка необходимых программ](image/31.png){ #fig:031 width=70% }

4. После установки необходимых программ завершаю работу виртуальной машины. Её конфигурация сохранится на жёстком диске. Для того чтобы другие виртуальные машины могли использовать машину Base и её конфигурацию как базовую, произвела следующие действия. В VirtualBox в меню выбрала "Файл" - "Менеджер виртуальных носителей" - "Жёсткие диски" и, выделив «Base.dvi», указала "Освободить" (рис -@fig:032, рис -@fig:033).

![Менеджер виртуальных носителей: освободить жёсткий диск](image/32.png){ #fig:032 width=70% }

![Менеджер виртуальных носителей: множественное подключение](image/33.png){ #fig:033 width=70% }

Теперь на основе виртуальной машины Base создам машину Host2, выбрав в VirtualBox "Машина" - "Создать" и в «Мастере создания новой виртуальной машины» укажу в качестве имени машины Host2, в качестве типа операционной системы — Linux, версия «RedHat» (рис -@fig:034).

![Настройка виртуальной машины Host2](image/34.png){ #fig:034 width=70% }

При конфигурации виртуального жёсткого диска выберу «Использовать существующий жёсткий диск» Base.vdi (рис -@fig:035).

![Конфигурация виртуального жёсткого диска Host2](image/35.png){ #fig:035 width=70% }

Вот наша готовая машина Host2 на основе виртуальной машины Base (рис -@fig:036).

![Готовая машина Host2 на основе виртуальной машины Base](image/36.png){ #fig:036 width=70% }

# Выводы

В процессе выполнения лабораторной работы 1 я приобрела навыки установки операционной системы на виртуальную машину, настройки минимально необходимых для дальнейшей работы сервисов.
