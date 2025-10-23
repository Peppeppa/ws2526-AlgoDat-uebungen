# Aufgabe 1



~~~
(define (nat-wurzel x)
  (define (iter odd sum count)
    (cond ((= sum x) count)
          ((< sum x) (iter (+ odd 1) (+ sum odd) (+ count 1)))
          (else #f)))
    (iter 1 1 1))

(nat-wurzel 2)
(nat-wurzel -2)
(nat-wurzel 0)
(nat-wurzel 1)
(nat-wurzel 16)
~~~



# Aufgabe 2

~~~
(define (zahl-umdrehen x)
  (define (loop abzubauen umgedreht)
    (if (= abzubauen 0)
        umgedreht
        (loop (quotient abzubauen 10) (+ (* 10 umgedreht) (remainder abzubauen 10)))))
  (loop x 0))


(zahl-umdrehen 123)
(zahl-umdrehen 4497821)
(zahl-umdrehen 597050)
~~~

# Aufgabe 3

~~~


(define ( aufsteigendes-produkt? a b c d)
  (and (< a b c) (= (* a b c) d)))



(aufsteigendes-produkt? 1 2 3 6) ;#t
(aufsteigendes-produkt? 2 1 3 6) ;#f
(aufsteigendes-produkt? 2 3 5 11);#f


~~~


# Aufgabe 4

~~~
(define (f1 a b)
  (and (and (and (not (or a b))(or a b)) a) (not b)))


(define (f2 a b c)
  (or (or (or a (and a b (not c)))(and (not a) c))(and (not (and a b)) c)))



(define (xor a b)
  (and (or a b) (not (and a b))))

(define (f3 a b c d)
  (and (and (xor (not a) b) (not (or a (not b) c)))(or (not d) (not c) (not b) (not a))))
~~~
