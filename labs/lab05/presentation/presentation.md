---
## Front matter
lang: ru-RU
title: Лабораторная работа № 5
author:
  - Юрченко Артём Алексеевич
group:
  - НФИбд-02-20, 1032201660
date: 2023, Москва

## i18n babel
babel-lang: russian
babel-otherlangs: english

## Fonts
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase,Scale=0.9

## Formatting pdf
toc: false
toc-title: Содержание
slide_level: 2
aspectratio: 169
section-titles: true
theme: metropolis
header-includes:
 - \metroset{progressbar=frametitle,sectionpage=progressbar,numbering=fraction}
 - '\makeatletter'
 - '\beamer@ignorenonframefalse'
 - '\makeatother'
---

## Цели

Изучение механизмов изменения идентификаторов, применения
SetUID- и Sticky-битов. Получение практических навыков работы в консоли с дополнительными атрибутами. Рассмотрение работы механизма
смены идентификатора процессов пользователей, а также влияние бита
Sticky на запись и удаление файлов.

## Задачи

1. Исследовать SetUID- и SetGID-биты.

2. Исследовать Sticky-бит.


## Ход работы

От имени пользователя guest создадим программу simpleid.c, скомпилируем ее и убедимся, что файл создан.

![Создание файла simleid.c](image/screenshot_1.png){#fig:001 width=90%}

## Ход работы


Выполним команды ./simpleid и id и убедимся, что полученные данные совпадают.

![Использование команд ./simpleid и id](image/screenshot_2.png){#fig:002 width=90%}

## Ход работы


Усложним программу и запишем ее в файл simpleid2.c. Запустим получившуюся программу.

![Создание и запуск программы simpleid2](image/screenshot_3.png){#fig:003 width=90%}

## Ход работы


От имени суперпользователя установим новые атрибуты и сменим владельца файла simpleid2.

![Установки новых атрибутов и смена владельца файла simpleid2](image/screenshot_4.png){#fig:004 width=90%}

## Ход работы


Выполним команды ./simpleid2 и id и убедимся, что полученные данные совпадают.

![Использование команд ./simpleid2 и id](image/screenshot_5.png){#fig:005 width=90%}

## Ход работы


Проделаем то же самое относительно SetGID-бита.

![Операции с SetGID-битом](image/screenshot_6.png){#fig:006 width=90%}

## Ход работы


Создадим и скомпилируем программу readfile.c.

![Создание и компиляция программы readfile.c](image/screenshot_7.png){#fig:007 width=90%}

## Ход работы


Сменим владельца у файла readfile.c и изменим права так, чтобы только суперпользователь
(root) мог прочитать его, a guest не мог.

![Изменение владельца и прав файла readfile.c](image/screenshot_8.png){#fig:008 width=90%}

## Ход работы


Проверим, что пользователь guest не может прочитать файл readfile.c.

![Проверка, что пользователь guest не может прочитать файл readfile.c.](image/screenshot_9.png){#fig:009 width=90%}

## Ход работы


Сменим у программы readfile владельца и установим SetUID-бит.

![Работа с параметрами readfile](image/screenshot_10.png){#fig:010 width=90%}

## Ход работы


Проверим, может ли программа readfile прочитать файл readfile.c.

![Попытка прочитать файл readfile.c программой readfile](image/screenshot_11.png){#fig:011 width=90%}

## Ход работы


Проверим, может ли программа readfile прочитать файл /etc/shadow.

![Попытка прочитать файл /etc/shadow программой readfile](image/screenshot_12.png){#fig:012 width=90%}

## Ход работы


Выясним, установлен ли атрибут Sticky на директории /tmp.

![Чтение атрибутов директории /tmp](image/screenshot_13.png){#fig:013 width=90%}

## Ход работы

От имени пользователя guest создадим файл file01.txt в директории /tmp
со словом test. Просмотрим атрибуты у только что созданного файла и разрешим чтение и запись для категории пользователей «все остальные».

![Чтение атрибутов директории /tmp](image/screenshot_14.png){#fig:014 width=90%}

## Ход работы

От пользователя guest2 попробуем прочитать файл /tmp/file01.txt.

![Попытка прочтения файла /tmp/file01.txt](image/screenshot_15.png){#fig:015 width=90%}

## Ход работы

От пользователя guest2 попробуем дозаписать в файл /tmp/file01.txt слово test2.

![Попытка дозаписи в файл /tmp/file01.txt](image/screenshot_16.png){#fig:016 width=90%}

## Ход работы

От пользователя guest2 попробуем записать в файл /tmp/file01.txt слово test3, стерев при этом всю имеющуюся в файле информацию).

![Попытка записи в файл /tmp/file01.txt](image/screenshot_17.png){#fig:017 width=90%}

## Ход работы

От пользователя guest2 попробуем удалить файл /tmp/file01.txt.

![Попытка удаления файла /tmp/file01.txt](image/screenshot_18.png){#fig:018 width=90%}

## Ход работы

От имени суперпользователя снимем атрибут t с директории /tmp. От пользователя guest2 проверим, что атрибута t у директории /tmp нет.

![Удаление атрибута t директории /tmp](image/screenshot_19.png){#fig:019 width=90%}

## Ход работы


Повторим предыдущие шаги. Теперь мы можем удалить файл.

![Повторение предыдущих шагов](image/screenshot_20.png){#fig:020 width=90%}

## Ход работы


Повысим свои права до суперпользователя и вернем атрибут t на директорию /tmp.

![Возвращение атрибута t директории /tmp](image/screenshot_21.png){#fig:021 width=90%}


## Результаты

В рамках данной лабораторной работы были изучены механизмы изменения идентификаторов, применения SetUID- и Sticky-битов. Получены практические навыков работы в консоли с дополнительными атрибутами. Рассмотрены принципы работы механизма
смены идентификатора процессов пользователей, а также влияние бита
Sticky на запись и удаление файлов.
