# Listen

~~~

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


~~~
