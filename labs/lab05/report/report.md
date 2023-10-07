---
## Front matter
title: "Лабораторная работа № 5"
subtitle: "Дискреционное разграничение прав в Linux. Исследование влияния дополнительных атрибутов"
author: "Юрченко Артём Алексеевич"

## Generic otions
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

## Pdf output format
toc: true # Table of contents
toc-depth: 2
lof: true # List of figures
lot: false
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n polyglossia
polyglossia-lang:
  name: russian
  options:
	- spelling=modern
	- babelshorthands=true
polyglossia-otherlangs:
  name: english
## I18n babel
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
## Biblatex
biblatex: true
biblio-style: "gost-numeric"
biblatexoptions:
  - parentracker=true
  - backend=biber
  - hyperref=auto
  - language=auto
  - autolang=other*
  - citestyle=gost-numeric
## Pandoc-crossref LaTeX customization
figureTitle: "Рис."
tableTitle: "Таблица"
listingTitle: "Листинг"
lofTitle: "Список иллюстраций"
lotTitle: "Список таблиц"
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---


# Цель работы

Изучение механизмов изменения идентификаторов, применения
SetUID- и Sticky-битов. Получение практических навыков работы в консоли с дополнительными атрибутами. Рассмотрение работы механизма
смены идентификатора процессов пользователей, а также влияние бита
Sticky на запись и удаление файлов.

# Задание

1. Исследовать SetUID- и SetGID-биты.

2. Исследовать Sticky-бит.

# Теоретическое введение

- Операционная система — это комплекс программ, предназначенных для управления ресурсами компьютера и организации взаимодействия с пользователем [1].

- Права доступа определяют, какие действия конкретный пользователь может или не может совершать с определенным файлами и каталогами. С помощью разрешений можно создать надежную среду — такую, в которой никто не может поменять содержимое ваших документов или повредить системные файлы. [2].

# Выполнение лабораторной работы

1. От имени пользователя guest создадим программу simpleid.c, скомпилируем ее и убедимся, что файл создан (@fig:001).

![Создание файла simleid.c](image/screenshot_1.png){#fig:001 width=90%}

2. Выполним команды ./simpleid и id и убедимся, что полученные данные совпадают (@fig:002).

![Использование команд ./simpleid и id](image/screenshot_2.png){#fig:002 width=90%}

3. Усложним программу и запишем ее в файл simpleid2.c. Запустим получившуюся программу (@fig:003).

![Создание и запуск программы simpleid2](image/screenshot_3.png){#fig:003 width=90%}

4. От имени суперпользователя установим новые атрибуты и сменим владельца файла simpleid2 (@fig:004).

![Установки новых атрибутов и смена владельца файла simpleid2](image/screenshot_4.png){#fig:004 width=90%}

5. Выполним команды ./simpleid2 и id и убедимся, что полученные данные совпадают (@fig:005).

![Использование команд ./simpleid2 и id](image/screenshot_5.png){#fig:005 width=90%}

6.  Проделаем то же самое относительно SetGID-бита (@fig:006).

![Операции с SetGID-битом](image/screenshot_6.png){#fig:006 width=90%}

7. Создадим и скомпилируем программу readfile.c (@fig:007).

![Создание и компиляция программы readfile.c](image/screenshot_7.png){#fig:007 width=90%}

8. Сменим владельца у файла readfile.c и изменим права так, чтобы только суперпользователь
(root) мог прочитать его, a guest не мог(@fig:008).

![Изменение владельца и прав файла readfile.c](image/screenshot_8.png){#fig:008 width=90%}

9. Проверим, что пользователь guest не может прочитать файл readfile.c. (@fig:009).

![Проверка, что пользователь guest не может прочитать файл readfile.c.](image/screenshot_9.png){#fig:009 width=90%}

10. Сменим у программы readfile владельца и установим SetUID-бит (@fig:010).

![Работа с параметрами readfile](image/screenshot_10.png){#fig:010 width=90%}

11. Проверим, может ли программа readfile прочитать файл readfile.c (@fig:011).

![Попытка прочитать файл readfile.c программой readfile](image/screenshot_11.png){#fig:011 width=90%}

12. Проверим, может ли программа readfile прочитать файл /etc/shadow (@fig:012).

![Попытка прочитать файл /etc/shadow программой readfile](image/screenshot_12.png){#fig:012 width=90%}

13. Выясним, установлен ли атрибут Sticky на директории /tmp (@fig:013).

![Чтение атрибутов директории /tmp](image/screenshot_13.png){#fig:013 width=90%}

14. От имени пользователя guest создадим файл file01.txt в директории /tmp
со словом test. Просмотрим атрибуты у только что созданного файла и разрешим чтение и запись для категории пользователей «все остальные» (@fig:014).

![Чтение атрибутов директории /tmp](image/screenshot_14.png){#fig:014 width=90%}

15. От пользователя guest2 попробуем прочитать файл /tmp/file01.txt (@fig:015).

![Попытка прочтения файла /tmp/file01.txt](image/screenshot_15.png){#fig:015 width=90%}

16. От пользователя guest2 попробуем дозаписать в файл /tmp/file01.txt слово test2 (@fig:016).

![Попытка дозаписи в файл /tmp/file01.txt](image/screenshot_16.png){#fig:016 width=90%}

17. От пользователя guest2 попробуем записать в файл /tmp/file01.txt слово test3, стерев при этом всю имеющуюся в файле информацию (@fig:017).

![Попытка записи в файл /tmp/file01.txt](image/screenshot_17.png){#fig:017 width=90%}

18. От пользователя guest2 попробуем удалить файл /tmp/file01.txt (@fig:018).

![Попытка удаления файла /tmp/file01.txt](image/screenshot_18.png){#fig:018 width=90%}

19. От имени суперпользователя снимем атрибут t с директории /tmp. От пользователя guest2 проверим, что атрибута t у директории /tmp нет (@fig:019).

![Удаление атрибута t директории /tmp](image/screenshot_19.png){#fig:019 width=90%}

20. Повторим предыдущие шаги. Теперь мы можем удалить файл (@fig:020).

![Повторение предыдущих шагов](image/screenshot_20.png){#fig:020 width=90%}

21. Повысим свои права до суперпользователя и вернем атрибут t на директорию /tmp (@fig:020).

![Возвращение атрибута t директории /tmp](image/screenshot_21.png){#fig:021 width=90%}

# Выводы

В рамках данной лабораторной работы были изучены механизмы изменения идентификаторов, применения SetUID- и Sticky-битов. Получены практические навыков работы в консоли с дополнительными атрибутами. Рассмотрены принципы работы механизма
смены идентификатора процессов пользователей, а также влияние бита
Sticky на запись и удаление файлов.

# Список литературы{.unnumbered}

[1] https://blog.skillfactory.ru/glossary/operaczionnaya-sistema/

[2] https://codechick.io/tutorials/unix-linux/unix-linux-permissions
