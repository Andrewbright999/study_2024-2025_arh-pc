---
## Front matter
title: "Лабораторная работа №4"
subtitle: "Создание и процесс
обработки программ на языке ассемблера NASM"
author: "Бочаров Андрей"

## Generic otions
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

## Pdf output format
toc: true # Table of contents
toc-depth: 2
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
mainfont: IBM Plex Serif
romanfont: IBM Plex Serif
sansfont: IBM Plex Sans
monofont: IBM Plex Mono
mathfont: STIX Two Math
mainfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
romanfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
sansfontoptions: Ligatures=Common,Ligatures=TeX,Scale=MatchLowercase,Scale=0.94
monofontoptions: Scale=MatchLowercase,Scale=0.94,FakeStretch=0.9
mathfontoptions:
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
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Целью работы является освоение процедуры компиляции и сборки программ, написанных на ассемблере NASM.

# Выполнение лабораторной работы
Создал папку для лабараторной работы и перешел в нее, создал файл hello.asm командой touch (рис. [-@fig:001]).

![Создание папки и файла](image/1.png){#fig:001 width=70%}

Переписал программный код для выполнения (рис. [-@fig:002]).

![Листинг кода](image/2.png){#fig:002 width=70%}

Создал объектный файл hello.o при помощи ассемблера nasm и файл obj.o при помощи его расширенного синтаксиса команды. Проверил их наличие (рис. [-@fig:003]).

![Объектные файлы obj и hello](image/3.png){#fig:003 width=70%}

При помощи объктново компоновщика ld сделал исполняемый файл hello (рис. [-@fig:004]).

![Исполняемый файл hello](image/4.png){#fig:004 width=70%}

Запустил исполняемый файл, он работает (рис. [-@fig:005]).

![Выполнение файла](image/5.png){#fig:005 width=70%}

# Выполнение самостоятельной работы
Сделал копию файла hello.asm с названием lab04 (рис. [-@fig:006]).

![Копирование файла lab04](image/6.png){#fig:006 width=70%}

Изменил код для вывода строчки с фамилией и именем (рис. [-@fig:007]).

![Листинг кода](image/7.png){#fig:007 width=70%}

Создал объектный файл lab04.o при помощи ассемблера nasm. При помощи объктново компоновщика ld сделал исполняемый файл lab04 Проверил их наличие. (рис. [-@fig:008]).

![Объектный и исполняемый файлы](image/8.png){#fig:008 width=70%}

Запустил исполняемый файл, он работает (рис. [-@fig:009]).

![Выполнение файла](image/9.png){#fig:009 width=70%}

# Выводы
Выполнив данную лабораторную работу я обрел теоретические и практические знания в использовании разметки Markdown. При помощи консоли я научился компилировать отчет с использованием команды Makefile.
Здесь кратко описываются итоги проделанной работы.
