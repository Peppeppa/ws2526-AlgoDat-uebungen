# komplexere Prozeduren



# Primzahlen aus Polynomen
~~~
#lang racket
;readme

;Der Algorithmus testet dein Polynom f ab n=0 auf aufeinanderfolgende
;Primzahlen und gibt das letzte n zurück, für das f(n) noch prim war.

;Voraussetzng
(define (prime? n)
  (cond
    ((<= n 1) #f)
    (else (check-div n 2))))

(define (check-div n k)
  (cond
    ((= k n) #t)
    ((= (remainder n k) 0) #f)
    (else (check-div n (+ k 1)))))

; Algorithmus
   
(define (primzahlen f)
  (let loop ((n 0))
    (cond
      ((not (prime? (f n)))
       (if (= n 0)
           #f
           (- n 1)))
      (else
       (loop (+ n 1))))))

; Übergebene Polynome

(define (f n)
   (+ (+ n n ) n 41))

(define (poly n)
  (+ (* n n) (* -79 n) 1601))

(define (euler n)
  (+ (* n n) n 41))


(primzahlen poly)
(primzahlen euler)
~~~



