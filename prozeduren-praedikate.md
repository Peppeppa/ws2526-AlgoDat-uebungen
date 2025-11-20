# Prädikate






# Prime?
-> #f #t
-> checkt übergebene Zahl ob es eine Primzahl ist 

~~~
(define (prime? n)
  (cond
    ((<= n 1) #f)
    (else (check-div n 2))))

(define (check-div n k)
  (cond
    ((= k n) #t)
    ((= (remainder n k) 0) #f)
    (else (check-div n (+ k 1)))))


~~~



