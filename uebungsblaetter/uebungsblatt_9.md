# Aufgabe 1 

~~~
(define (move n from via to)
  (if (= n 1)
      (list (cons from to))
      (append
       (move (- n 1) from to via)
       (list (cons from to))
       (move (- n 1) via from to))))

(define (tuerme-von-hanoi n)
  (move n 'a 'b 'c))

~~~

# Aufgabe 2

~~~

(define (liste-teilen eingabe)
  (define (loop old new1 new2 hilfs)
    (cond ((null? old) (list new1 new2))
          ((= hilfs 1) (loop (cdr old)
                             (append new1 (list (car old)))
                             new2
                             2))
          ((= hilfs 2) (loop (cdr old)
                             new1
                             (append new2 (list(car old)))
                             1))))
    (loop eingabe '() '() 1))

( liste-teilen '(1 2 3 4 5 6 7 8 9))


~~~

# Aufgabe 3

~~~

(define (listen-verschmelzen eingabe)
  (define (loop alt1 alt2 neu hilfs)
    (cond ((and (null? alt1)(null? alt2)) neu)
          ((= hilfs 1) (loop (cdr alt1)
                             alt2
                             (append neu (list (car alt1)))
                             2))
          ((= hilfs 2) (loop alt1
                             (cdr alt2)
                             (append neu (list (car alt2)))
                             1))))
  (loop (car eingabe)(cadr eingabe)'()1))

(listen-verschmelzen '((1 3 5 7 9) (2 4 6 8 10))) 

~~~



# Aufgabe 4

~~~
(define (hamming a b)
  (cond ((null? a) 0)
        ((= (car a)(car b)) (hamming (cdr a)(cdr b)))
        (else (+ 1 (hamming (cdr a)(cdr b))))))

(hamming '(1 0 0 1 0 1 0 1) '(0 1 1 1 0 1 0 0))

~~~


