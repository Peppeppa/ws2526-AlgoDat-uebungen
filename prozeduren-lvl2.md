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

# schneide die linken 2 ziffern ab 

-> schneidet die linken 2 ziffern einer gegebenen zahl ab
~~~
(define (2linweg n)
  (define (laengezahl y)                                    ;anzahl der stellen von n
    (if (< y 10)
        1
        (+ 1 (laengezahl (quotient y 10)))))
  
  (define (exponent z)                                      ;hier kann statt 2 die stellen angegeben 
    (- (laengezahl z) 2))                                   ;werden wie viele links abgeschnitten werden
                                                            ;diese zahl wird dann umgerechnet für den remainder 
  (define (createRemainder v ergebnis)                      
    (if (= 1 v)                                             ;loopt "exponent" mal 10*ergebnis (startet bei 10)
        ergebnis                                            ;damit wir eine schöne Zahl haben die wir mit n 
        (createRemainder (- v 1) (* 10 ergebnis))))         ; in den remainder werfen können

(remainder n (createRemainder (exponent n) 10)))
                         
              
(2linweg 123456)

~~~


# Zählen mit zwei Prädikaten
-> Zählt von start bis ende und gibt den nten wert aus der entweder f1 oder f2 erfüllt.

~~~


(define (zaehlen start ende n f1 f2)
  (if (< n 0)
      #f
      (let loop ((next start)
                 (count n))
        (cond
          ((= count 0) (- next 1))
          ((> next ende) #f)
          ((or
            (and (f1 next)
                 (not (f2 next)))
            (and (not (f1 next))
                      (f2 next)))
           (loop (+ next 1)(- count 1)))
          (else
           (loop (+ next 1) count))))))
                   
(define (teilt5 x)
  (= 0 (remainder x 5)))

(zaehlen 1 100 10 odd? teilt5)


~~~

