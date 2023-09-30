---
## Front matter
title: "Лабораторная работа № 4"
subtitle: "Дискреционное разграничение прав в Linux. Расширенные атрибуты"
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

Целью данной работы является получение практических навыков работы в консоли с расширенными атрибутами файлов.

# Задание

1. Исследовать доступность команд при установленном расширенном aтрибуте a.

2. Исследовать доступность команд при установленном расширенном aтрибуте i.



# Выполнение лабораторной работы

1. От имени пользователя guest определим расширенные атрибуты файла /home/guest/dir1/file1  (@fig:001).

![Расширенные атрибуты файла /home/guest/dir1/file1](image/screenshot_1.png){#fig:001 width=90%}

2. Установим командой на файл file1 права, разрешающие чтение и запись для владельца файла (@fig:002).

![Установка прав на файл /home/guest/dir1/file1](image/screenshot_2.png){#fig:002 width=90%}

3. Попробуем установить на файл /home/guest/dir1/file1 расширенный атрибут a от имени пользователя guest (@fig:003).

![Попытка установки атрибута а на файл /home/guest/dir1/file1 от имени пользователя guest](image/screenshot_3.png){#fig:003 width=90%}

4. Откроем еще одну консоль с правами администратора. Установим на файл /home/guest/dir1/file1 расширенный атрибут a (@fig:004).

![Установка атрибута а на файл /home/guest/dir1/file1](image/screenshot_4.png){#fig:004 width=90%}

5. От пользователя guest проверим правильность установления атрибута (@fig:005).

![Атрибуты на файл /home/guest/dir1/file1](image/screenshot_5.png){#fig:005 width=90%}

6.  Выполним дозапись в файл file1 слова «test» и выполним чтение файла file1 (@fig:006).

![Запись и чтение файла /home/guest/dir1/file1](image/screenshot_6.png){#fig:006 width=90%}

7. Попробуем стереть имеющуюся в файле информацию и переименовать его(@fig:007).

![Попытка удаления информации и переименования файла /home/guest/dir1/file1](image/screenshot_7.png){#fig:007 width=90%}

8. Попробуем установить на файл file1 права, запрещающие чтение и запись для владельца файла. Этого сделать не удалось(@fig:008).

![Попытка устанавления прав на файл /home/guest/dir1/file1](image/screenshot_8.png){#fig:008 width=90%}

9. Снимем расширенный атрибут a с файла /home/guest/dirl/file1 от
имени суперпользователя (@fig:008).

![Снятие атрибута а с файла /home/guest/dir1/file1](image/screenshot_9.png){#fig:009 width=90%}

10. Повторим операции, которые нам ранее не удавалось выполнить. Теперь все операции выполняются (@fig:010).

![Повторение операций после снятия атрибута а](image/screenshot_10.png){#fig:010 width=90%}

11. Повторим действия по шагам, заменив атрибут «a» атрибутом «i» (@fig:011 - @fig:014).

![Установка атрибута i на файл /home/guest/dir1/file1](image/screenshot_11.png){#fig:011 width=90%}

![Повторение операций после установки атрибута i](image/screenshot_12.png){#fig:012 width=90%}

Дозаписать информацию в файл не удалось

![Снятие атрибута i с файла /home/guest/dir1/file1](image/screenshot_13.png){#fig:013 width=90%}


# Выводы

В рамках данной лабораторной работы были получены практические навыки работы в консоли с расширенными атрибутами файлов.

# Список литературы{.unnumbered}

[1] https://blog.skillfactory.ru/glossary/operaczionnaya-sistema/

[2] https://codechick.io/tutorials/unix-linux/unix-linux-permissions
