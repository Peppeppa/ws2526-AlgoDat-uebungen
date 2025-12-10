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


