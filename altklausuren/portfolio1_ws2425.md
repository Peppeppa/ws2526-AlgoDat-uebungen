#lang racket

# 1
~~~
(define (f a b c d)
  (or (and a b d) a (and c d) (not (and a c))))

;(f #f #f #f #t)
~~~
# 2
~~~
(define (pruefeZahl n)
  (and (> n 12) (<= (* n n) 999) (= (remainder n 3) 0)))

;(pruefeZahl 11)
;(pruefeZahl 15)
;(pruefeZahl 30)
~~~
# 3
~~~
(define (skonto betrag anzahltage)
  (cond ((<= anzahltage 10) (abzug betrag 3))
        ((and (<= anzahltage 20) (>= anzahltage 11)) (abzug betrag 2))
        ((>= anzahltage 21) betrag)))


(define (abzug betrag skontoprozent)
  (* (/ betrag 100) (- 100 skontoprozent)))

(skonto 100 5)
(skonto 100 9)
(skonto 100 10)
(skonto 100 11)
(skonto 100 15)
(skonto 100 19)
(skonto 100 20)
(skonto 100 21)
(skonto 100 22)
(skonto 100 0)
(skonto 100 -5)

   ;10. Tag -> -3%
   ;20. Tag -> -2%
~~~
