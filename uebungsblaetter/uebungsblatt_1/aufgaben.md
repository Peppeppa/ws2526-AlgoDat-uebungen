# Aufgabe 1
~~~
(define x ( - ( / (+ 9 6) (* (- 3 1) 5 )) ( * ( -  7/8 2) 4)))
~~~

# Aufgabe 2
~~~
(define (g u v w)
  (+ (/ (- v (* 7 u)) (- u w)) (/ (+ u v) (- (* w 6) v ))))

(g 1 2 3)
2\frac{11}{16}
(g 3 11 2)
4
~~~

# Aufgabe 3
~~~
(define (my-max x y)
  (if (> x y) x y))

(my-max 5 2)
5
(my-max 10 23)
23
(my-max 4 4)
4
~~~

# Aufgabe 4
~~~
(define ( groesser-zehn? x)
  (> x 10))
(groesser-zehn? 4)
#f
(groesser-zehn? 10)
#f
(groesser-zehn? 15)
#t
~~~

# Aufgabe 5
~~~
(define ( groesserp? x y z)
  (> ( + x y ) z))

(groesserp? 0  5 6)
#f
(groesserp? 2 12 10)
#t
(groesserp? 3 3 6)
#f
~~~

# Aufgabe 6
~~~
(define (squared-max x y z)
  (max ( * x x ) (* y y) (* z z)))


( squared-max 2 -3 5)
25
~~~

# Tafelübung 1
~~~
a

b

c 
~~~
Exercise 1.1: Below is a sequence of expressions. What is
the result printed by the interpreter in response to each ex-
pression? Assume that the sequence is to be evaluated in
the order in which it is presented
( Zeilen mit "-" vornedran sind die Antworten auf die darüberstehenden expressions)

~~~

10
- 10

(+ 5 3 4)
- 12

(- 9 1)
- 8

(/ 6 2)
- 3

(+ (* 2 4) (- 4 6))
- 6

(define a 3)
- 

(define b (+ a 1))
- 

(+ a b (* a b))
- 19

(= a b)
- #f

(if (and (> b a) (< b (* a b)))
    b
    a)
- 4 

(cond ((= a 4) 6)
    ((= b 4) (+ 6 7 a))
    (else 25))
- 6

(+ 2 (if (> b a) b a))
- 6

(* (cond ((> a b) a)
        ((< a b) b)
        (else -1))
    (+ a 1))
- 16
~~~
