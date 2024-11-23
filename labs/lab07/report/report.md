---
## Front matter
title: "Лабораторная работа №7"
subtitle: "Команды безусловного и условного переходов в Nasm. Программирование ветвлений."
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

Целью работы является приобретение практических навыков работы и изучение команд условного и безусловного переходов. Приобретение навыков написания программ с использованием переходов. А так же знакомство с назначением и структурой файла листинга.

# Выполнение лабораторной работы
Создал и першел в каталог для 7 лабораторной работы и командой touch сделал файл lab7-1.asm (рис. [-@fig:001]).

![Каталог lab07](image/1.png){#fig:001 width=70%}

Переписал код из листинга 7.1 (рис. [-@fig:002]).

![Листинг кода](image/2.png){#fig:002 width=70%}

Листинг кода 7.1:

```
%include 'in_out.asm' ; подключение внешнего файла

SECTION .data
msg1: DB 'Сообщение № 1',0
msg2: DB 'Сообщение № 2',0
msg3: DB 'Сообщение № 3',0
SECTION .text
GLOBAL _start
_start:

jmp _label2

_label1:
mov eax, msg1 ; Вывод на экран строки
call sprintLF ; 'Сообщение № 1'

_label2:
mov eax, msg2 ; Вывод на экран строки
call sprintLF ; 'Сообщение № 2'

_label3:
mov eax, msg3 ; Вывод на экран строки
call sprintLF ; 'Сообщение № 3'

_end:
call quit ; вызов подпрограммы завершения
```

Создал исполняемый файл и запустил его. (рис. [-@fig:003]).

![Работает](image/3.png){#fig:003 width=70%}	

Переписал код в файле с листинга 7.2 (рис. [-@fig:004]).

![Обновленный код](image/4.png){#fig:004 width=70%}

Листинг кода 7.2.1:

```
%include 'in_out.asm' ; подключение внешнего файла

SECTION .data
msg1: DB 'Сообщение № 1',0
msg2: DB 'Сообщение № 2',0
msg3: DB 'Сообщение № 3',0
SECTION .text
GLOBAL _start
_start:

jmp _label2

_label1:
mov eax, msg1 ; Вывод на экран строки
call sprintLF ; 'Сообщение № 1'
jmp _end

_label2:
mov eax, msg2 ; Вывод на экран строки
call sprintLF ; 'Сообщение № 2'
jmp _label1

_label3:
mov eax, msg3 ; Вывод на экран строки
call sprintLF ; 'Сообщение № 3'

_end:
call quit ; вызов подпрограммы завершения
```

Создал исполняемый файл и запустил его. (рис. [-@fig:005]).

![Результат работы файла](image/5.png){#fig:005 width=70%}

Переписал код так, что бы он выводил сообщения в необходимом порядке (рис. [-@fig:006]).

![Листинг кода](image/6.png){#fig:006 width=70%}

Листинг кода 7.2.2:

```
%include 'in_out.asm' ; подключение внешнего файла

SECTION .data
msg1: DB 'Сообщение № 1',0
msg2: DB 'Сообщение № 2',0
msg3: DB 'Сообщение № 3',0
SECTION .text
GLOBAL _start
_start:

jmp _label3

_label1:
mov eax, msg1 ; Вывод на экран строки
call sprintLF ; 'Сообщение № 1'
jmp _end

_label2:
mov eax, msg2 ; Вывод на экран строки
call sprintLF ; 'Сообщение № 2'
jmp _label1

_label3:
mov eax, msg3 ; Вывод на экран строки
call sprintLF ; 'Сообщение № 3'
jmp _label2

_end:
call quit ; вызов подпрограммы завершения
```

Создал исполняемый файл и запустил его. (рис. [-@fig:007]).

![Работает](image/7.png){#fig:007 width=70%}

Создал новый файл и переписал в него код с листинга 7.3 (рис. [-@fig:008]).

![Листинг кода](image/8.png){#fig:008 width=70%}

Листинг кода 7.3:

```
%include 'in_out.asm'
section .data
    	msg1 db 'Введите B: ',0h
    	msg2 db "Наибольшее число: ",0h
	A dd '20'
	C dd '50'
	
section .bss
	max resb 10
	B resb 10
	
section .text
global _start

_start:
; ---------- Вывод сообщения 'Введите B: '
mov eax,msg1
call sprint
; ---------- Ввод 'B'
mov ecx,B
mov edx,10
call sread
; ---------- Преобразование 'B' из символа в число
mov eax,B
call atoi ; Вызов подпрограммы перевода символа в число
mov [B],eax ; запись преобразованного числа в 'B'
; ---------- Записываем 'A' в переменную 'max'
mov ecx,[A] ; 'ecx = A'
mov [max],ecx ; 'max = A'
; ---------- Сравниваем 'A' и 'С' (как символы)
cmp ecx,[C] ; Сравниваем 'A' и 'С'
jg check_B ; если 'A>C', то переход на метку 'check_B',
mov ecx,[C] ; иначе 'ecx = C'
mov [max],ecx ; 'max = C'
; ---------- Преобразование 'max(A,C)' из символа в число

check_B:
mov eax,max
call atoi ; Вызов подпрограммы перевода символа в число
mov [max],eax ; запись преобразованного числа в `max`
; ---------- Сравниваем 'max(A,C)' и 'B' (как числа)
mov ecx,[max]
cmp ecx,[B] ; Сравниваем 'max(A,C)' и 'B'
jg fin ; если 'max(A,C)>B', то переход на 'fin',
mov ecx,[B] ; иначе 'ecx = B'
mov [max],ecx
; ---------- Вывод результата
fin:
mov eax, msg2
call sprint ; Вывод сообщения 'Наибольшее число: '
mov eax,[max]
call iprintLF ; Вывод 'max(A,B,C)'
call quit ; Выход
```

Создал исполняемый файл и запустил его. Проверил с случайным введенным числом. (рис. [-@fig:009]).

![Результат работы](image/9.png){#fig:009 width=70%}

Создал и открыл листинг кода lab7-2.lst при помощи команды nasm. В листинге кода присутсвует код из файла in_out.asm помимо основной программы. (рис. [-@fig:010]).

![Листинг кода](image/10.png){#fig:010 width=70%}

Выбрал инструкцию в которой есть несколько операнд. (рис. [-@fig:011]).

![Листинг кода](image/11.png){#fig:011 width=70%}

Удалил один из операндов (рис. [-@fig:012]).

![Обновленный листинг](image/12.png){#fig:012 width=70%}

Создал исполняемый файл и запустил его. В листинге теперь нет удаленного операнда (рис. [-@fig:013]).

![Результат выполения](image/13.png){#fig:013 width=70%}

При создании появлиось 3 файла: объектный, исполняемый и листинг. (рис. [-@fig:014]).

![Созданные файлы](image/14.png){#fig:014 width=70%}

# Выполнение самостоятельной работы

Создал и написал код в файле `lab7-4.asm` для нахождения наименьшей из 3 целочисленных переменных 𝑎,𝑏  (рис. [-@fig:015]).

![Листинг кода](image/15.png){#fig:015 width=70%}

Листинг кода:

```
%include 'in_out.asm'

section .data
    ;msg1 db 'Введите B: ',0h
    msg2 db "Наименьшее число: ",0h
	A dd '84'
	C dd '32'
	B dd '77'
section .bss
	min resb 10
section .text
global _start
_start:
; ---------- Записываем 'A' в переменную 'min'
	mov ecx,[A] ; 'ecx = A'
	mov [min],ecx ; 'min = A'
; ---------- Сравниваем 'A' и 'С' (как символы)
	cmp [C],ecx ; Сравниваем 'С' и 'A'
	jg check_B ; если 'С>A', то переход на метку 'check_B',
	mov ecx,[C] ; иначе 'ecx = C'
	mov [min],ecx ; 'min = C
; ---------- Преобразование 'min(A,C)' из символа в число
check_B:
	mov eax,min
	call atoi ; Вызов подпрограммы перевода символа в число
	mov [min],eax ; запись преобразованного числа в `min`
; ---------- Сравниваем 'min(A,C)' и 'B' (как числа)
	mov ecx,[min]
	cmp [B],ecx ; Сравниваем 'min(A,C)' и 'B'
	jg fin ; если 'min(A,C)<B', то переход на 'fin',
	mov ecx,[B] ; иначе 'ecx = B'
	mov [min],ecx
; ---------- Вывод результата
fin:
	mov eax, msg2
	call sprint ; Вывод сообщения 'Наименьшее число: '
	mov eax,[min]
	call iprintLF ; Вывод 'min(A,B,C)'
	call quit ; Выход
```
	
Создал исполняемый файл и запустил его. Результат совпадает с ожидаемым. (рис. [-@fig:016]).

![Результат выполнения](image/16.png){#fig:016 width=70%}

Создал файл variant.asm и переписал в него листинг кода 6.4 (рис. [-@fig:017]).

![Работает файла](image/17.png){#fig:017 width=70%}


Листинг 6.4:

```
%include 'in_out.asm'

section .data
    msg1 db 'Введите A: ',0h
	msg2 db 'Введите x: ',0h
	msg_res db 'Результат: ',0h
	
section .bss
	res resb 10
	A resb 10
	x resb 10
section .text
global _start
_start:

; ---------- Вывод сообщения 'Введите A: '
mov eax,msg1
call sprint
; ---------- Ввод 'A'
mov ecx,A
mov edx,10
call sread
; ---------- Преобразование 'A' из символа в число
mov eax,A
call atoi ; Вызов подпрограммы перевода символа в число
mov [A],eax ; запись преобразованного числа в 'A'

; ---------- Вывод сообщения 'Введите B: '
mov eax,msg2
call sprint
; ---------- Ввод 'x'
mov ecx,x
mov edx,10
call sread
; ---------- Преобразование 'x' из символа в число
mov eax,x
call atoi ; Вызов подпрограммы перевода символа в число
mov [x],eax ; запись преобразованного числа в 'x'

; ---------- Сравниваем 'A' и 7 

mov ecx,'7'
cmp [A],ecx ; Сравниваем 'A' и 'С'
jg check_B ; если 'A>7', то переход на метку 'check_B',
mov eax,[A] ; иначе 'f = ax'
mov ecx,[x]
mul ecx
mov [res], eax
jmp fin

; ---------- Вычитание '7 из А' 
check_B:
mov eax, [A]
sub S, '7'
mov [res], eax
jmp fin

; ---------- Вывод результата
fin:
mov eax, msg_res
call sprint ; Вывод сообщения 'Результат: '
mov eax,[res]
call iprintLF ; Вывод 'f(x)='
call quit ; Выход
```

Создал исполняемый файл и запустил его. Результат совпадает с ожидаемым. (рис. [-@fig:018]).

![Работает файла](image/18.png){#fig:018 width=70%}


# Выводы
Выполнив данную лабараторную работу, я обрел практические навыки работы и изучение команд условного и безусловного переходов. Приобретение навыков написания программ с использованием переходов. А так же знакомство с назначением и структурой файла листинга.
