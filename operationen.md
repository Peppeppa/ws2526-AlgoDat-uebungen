
#




#lang racket
# Arithmetik
~~~
; + - * / 
; abs                     Betrag
; sqrt                    Square Root
; expt                    Potenz
; exp                     e^x
; log                     natürlicher Logarithmus
; sin cos tan
; asin acos atan
; (ceiling 3.1) -> 4      Nächst größere Zahl runden
; (floor 3.7) -> 3        Abrunden
; (round 3.5) -> 4        Mathematisches Runden
; (truncate -3.9) -> -3   Dezimalteil abschneiden (Java (int))
~~~
# Ganzzahloperationen
~~~
; quotient        Ganzzahliger Quotient (ohne Rest)
; remainder       Rest von quotient                 (remainder -5 3) -> -2
; modulo          Vorzeichen wie Divisor            (modulo -5 3)    -> -5 = 3*(-2) +1 -> 1
~~~
# Boolean
~~~
; and   Sonderform
; or    Sonderform
; not
; if           <Prädikat> <Folge> <Alternative>
; cond         <Prädikat-N> <Folge-N>
~~~

# Test
~~~
; equal?          Gleichheit von Symbolen und Listen
; number?         (5)
; symbol?         ('x)
; odd?            ungerade
; even?           gerade
; integer?        ganzzahlig
; rational?
; real?
; complex?
~~~
# Prozeduren
~~~
; define
; (lambda (x) (* x x))        Anonyme Funktion
; (let ((a 2) (b 3))          Lokale Variablen
;    (+ a b))
; (let* ((a 2) (b (+ a 3)))   Abhängige Definition
;    b)
~~~

# "Unbekannt"

~~~
; (begin (display "Hi")
; (quote (+ 1 2))  ; ergibt (+ 1 2)
; (letrec ((f (lambda (n)        ;Rekursive lokale Funktion
;               (if (= n 0) 1 (* n (f (- n 1)))))))
;   (f 5))



~~~
