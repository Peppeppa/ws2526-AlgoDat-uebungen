# Aufgabe 1

~~~
(define (fakultaet n)
  (fak-iter 1 1 n))

(define (fak-iter produkt zaehler n)
  (if (> zaehler n)
      produkt
      (fak-iter (* zaehler produkt) (+ zaehler 1) n)))


(define (euler-n n)
  (euler-iter 0 0 n))

(define (euler-iter zaehler summe n)
  (if (> zaehler n)
      summe
      (euler-iter (+ zaehler 1.0)
                  (+ summe (/ 1.0 (fakultaet zaehler)))
                  n)))


(euler-n 0)
(euler-n 1)
(euler-n 2)
(euler-n 27)

~~~~

# Aufgabe 2

~~~
(define (ackermann n m)
  (cond ((= n 0) (+ m 1))
        ((and (> n 0) (= m 0))(ackermann (- n 1) 1))
        ((and (> n 0) (> m 0))(ackermann (- n 1) (ackermann n (- m 1))))))

(ackermann 0 0)
(ackermann 0 1)
(ackermann 4 0)
(ackermann 3 1)
(ackermann 3 9)
(time(ackermann 4 1))

 

~~~
