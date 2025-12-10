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



# Ableiten

~~~

#lang racket


(define (liste-ref element n)
  (if (= n 1)
      (car element)
      (liste-ref (cdr element)(- n 1))))

(liste-ref (list 1 2 3 4) 3)

(define (laenge elemente)
  (if (null? elemente) 0
      (+ 1 (laenge (cdr elemente)))))

(laenge (list 1 2 3))


;(define (laenge2 elemente)
;  (define (laenge-iter a zaehler)
;    (if (null? a)
;        zaehler
;        (laenge2 (cdr a) (+ 1 zaehler))))
;  (laenge-iter elemente 0))

(define (laenge3 elemente)
  (define (laenge-iter a zaehler)
    (if (null? a)
        zaehler
        (laenge-iter (cdr a) (+ 1 zaehler))))
  (laenge-iter elemente 0))

(laenge3 (list 1 2 3 4 5))

(define (variable? x ) (symbol? x))
(define (gleiche-variable? v1 v2)
  (and (variable? v1) (variable? v2) (eq? v1 v2)))
(define (summe? x)
  (and (pair? x) (eq? (car x) '+)))
(define (addend x) (cadr x))
(define (augend x) (caddr x))
(define (produkt? x)
  (and (pair? x) (eq? (car x) '*)))
(define (multiplikant x) (cadr x))
(define (multiplikator x) (caddr x))
(define (=number? exp num)
  (and (number? exp) (= exp num)))
;(define (konstr-summe a1 a2) (list '+ a1 a2))
(define (konstr-summe a1 a2)
  (cond ((=number? a1 0) a2)
        ((=number? a2 0) a1)
        ((and (number? a1) (number? a2)) (+ a1 a2))
        (else (list '+ a1 a2))))
;(define (konstr-produkt a1 a2) (list '* a1 a2))
(define (konstr-produkt a1 a2)
  (cond ((=number? a1 0) a2)
        ((=number? a2 0) a1)
        ((and (number? a1) (number? a2)) (* a1 a2))
        (else (list '* a1 a2))))
  

 
(define (ableiten ausdruck var)
  (cond ((number? ausdruck) 0)
        ((variable? ausdruck) (if (gleiche-variable? ausdruck var)
                                  1
                                  0)) 
        ((summe? ausdruck) (konstr-summe (ableiten (addend ausdruck) var)
                                         (ableiten (augend ausdruck) var)))
        ((produkt? ausdruck) (konstr-summe
                              (konstr-produkt (ableiten (multiplikant ausdruck) var)
                                             (ableiten (multiplikator ausdruck) var))
                              (konstr-produkt (ableiten (multiplikant ausdruck) var)
                                             (ableiten (multiplikator ausdruck) var))))
        (else
         display "error" ausdruck)))


(ableiten '(* x 3) 'x)

(ableiten '(* (* x y) (+ x 3)) 'x)


(ableiten '(* x y) 'x)







          
~~~
