---
## Front matter
title: "Отчёт по лабораторной работе 8"
subtitle: "Дисциплина: архитектура компьютера"
author: "Маныев Ресулбег Алексеевич"

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
lot: true # List of tables
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
  - parentracker=trueЗырянов Артём Алексеевич	НБИбд-01-22

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

Целью работы является приобретение навыков написания программ с использованием циклов и обработкой аргументов командной строки..

# Выполнение лабораторной работы

## Реализация циклов в NASM

Был создан каталог для выполнения лабораторной работы № 8, а также создан файл с именем lab8-1.asm. 

При использовании инструкции loop в NASM для реализации циклов, 
необходимо помнить о следующем: данная инструкция использует регистр ecx 
в качестве счетчика и на каждой итерации уменьшает его значение на единицу. 

Для лучшего понимания этого процесса, рассмотрим пример программы, 
которая выводит значение регистра ecx.

Написал в файл lab8-1.asm текст программы из листинга 8.1. (рис. [-@fig:001])
Создал исполняемый файл и проверил его работу. (рис. [-@fig:002])

![Код программы lab8-1.asm](image/01.png){ #fig:001 width=70%, height=70% }

![Компиляция и запуск программы lab8-1.asm](image/02.png){ #fig:002 width=70%, height=70% }

В данном примере демонстрируется, что использование регистра ecx в инструкции 
loop может привести к неправильной работе программы. В тексте программы были внесены
 изменения, которые включают изменение значения регистра ecx внутри цикла. (рис. [-@fig:003])

Программа запускает бесконечный цикл при нечетном значении N и 
выводит только нечетные числа при четном значении N. (рис. [-@fig:004])

![Код программы lab8-1.asm](image/03.png){ #fig:003 width=70%, height=70% }

![Компиляция и запуск программы lab8-1.asm](image/04.png){ #fig:004 width=70%, height=70% }

Для того чтобы использовать регистр ecx в цикле и обеспечить корректность работы программы, 
можно применить стек. Внесены изменения в текст программы, добавив команды 
push и pop для сохранения значения счетчика цикла loop в стеке. (рис. [-@fig:005])

Был создан исполняемый файл и проверена его работа. 
Программа выводит числа от N-1 до 0, где количество проходов цикла соответствует значению N.(рис. [-@fig:006])

![Код программы lab8-1.asm](image/05.png){ #fig:005 width=70%, height=70% }

![Компиляция и запуск программы lab8-1.asm](image/06.png){ #fig:006 width=70%, height=70% }

## Обработка аргументов командной строки

Создал файл lab8-2.asm в каталоге ~/work/arch-pc/lab08 и ввел в него 
текст программы из листинга 8.2. (рис. [-@fig:007])

Создал исполняемый файл и запустил его, указав аргументы.
Программа обработала 5 аргументов. Аргументами считаются слова/числа, разделенные пробелом. (рис. [-@fig:008])

![Код программы lab8-2.asm](image/07.png){ #fig:007 width=70%, height=70% }

![Компиляция и запуск программы lab8-2.asm](image/08.png){ #fig:008 width=70%, height=70% }

Рассмотрим еще один пример программы которая выводит сумму чисел,
которые передаются в программу как аргументы. (рис. [-@fig:009]) (рис. [-@fig:010])

![Код программы lab8-3.asm](image/09.png){ #fig:009 width=70%, height=70% }

![Компиляция и запуск программы lab8-3.asm](image/10.png){ #fig:010 width=70%, height=70% }

Изменл текст программы из листинга 8.3 для вычисления произведения
аргументов командной строки. (рис. [-@fig:011]) (рис. [-@fig:012])

![Код программы lab8-3.asm](image/11.png){ #fig:011 width=70%, height=70% }

![Компиляция и запуск программы lab8-3.asm](image/12.png){ #fig:012 width=70%, height=70% }

## Задание для самостоятельной работы

Напишите программу, которая находит сумму значений функции 
$f(x)$ для $x = x_1, x_2, ..., x_n$, т.е. программа должна выводить значение 
$f(x_1) + f(x_2)+ ... +f(x_n)$. 
Значения $x$ передаются как аргументы. 
Вид функции $f(x)$ выбрать из таблицы 8.1 вариантов заданий в соответствии с вариантом, 
полученным при выполнении лабораторной работы № 7. 
Создайте исполняемый файл и проверьте его работу на нескольких наборах $x$.(рис. [-@fig:013]) (рис. [-@fig:014])

Мой вариант 11: $$f(x) = 15x + 2$$ 

![Код программы prog.asm](image/13.png){ #fig:013 width=70%, height=70% }

Для проверки я запустил сначала с одним аргументом. Так, при подстановке $f(1)=17, f(5)=77$

Затем подал несколько аргументов и получил сумму значений функции.

![Компиляция и запуск программы prog.asm](image/14.png){ #fig:014 width=70%, height=70% }

# Выводы

Освоили работы со стеком, циклом и аргументами на ассемблере nasm.