# Aufgabe 1



~~~
(define ( nat-wurzel x)
  (define (loop odd sum count)
  (cond ((= sum x) count)
        ((> sum x) #f)
        (else (loop (+ odd 2)
                    (+ sum (+ odd 2))
                    (+ count 1)))))
  (loop 1 1 1))
~~~



# Aufgabe 2

~~~
;(define ( zahl-umdrehen x)
;  (dreh-iter x))
;(define dreh-iter 


;  (define xzerlegt (quotient x 10))
;  (define letzteStelle (remainder x 10)


  ;(define vorletztestelle (xzerlegt letztestelle)
  ;  (define (remainder xzerlegt 10)

      
  ;(define neuesx (+ letzteStelle (* 10 vorletztestelle)


;   letztestelle                  remainder x 10                 stellenzähler beginnt bei 0 -> *10 hoch0
;  +vorletztestelle*expt 10 n     quotient x 10 ->               stellenzähler +1


;   bau neue x
;     (* letztestelle  (expt 10 stellenzähler))

;neue letzte stelle
;define eineweniger (quotient x 10)
;(remainder (qu
~~~
