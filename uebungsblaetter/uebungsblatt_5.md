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

# Aufgabe 3

~~~


(define (osterformeldef j)
  (let ((a (remainder j 19))
        (b (remainder j 4))
        (c (remainder j 7))
        (k (floor (/ j 100))))
    (define (ohelp j a b c k)
          (let ((p (floor (/ (+ (* 8 k ) 13)25)))
                (q (floor (/ k 4))))
            (define (ohelpzwo j a b c k q p)
              (let ((M (remainder (- (+ 15 k) p q) 30))
                    (N (remainder (- (+ 4 k) q) 7)))
                (define (ohelpdrei j a b c k q p M N)
                  (let ((d (remainder (+ (* 19 a) M) 30)))
                    (define (ohelpvier j a b c k q p M N d)
                      (let ((e (remainder (+ (* 2 b) (* 4 c) (* 6 d) N) 7)))
                        (+ 22 d e)))
                    (ohelpvier j a b c k q p M N d)))
                (ohelpdrei j a b c k q p M N)))
            (ohelpzwo j a b c k q p)))
    (ohelp j a b c k)))
                
         
(osterformeldef 2025)

(define (osterformellet j)
  (let ((a (remainder j 19))
        (b (remainder j 4))
        (c (remainder j 7))
        (k (floor (/ j 100))))
    (let ((p (floor (/ (+ (* 8 k) 13) 25)))
          (q (floor (/ k 4))))
      (let ((M (remainder (- (+ 15 k) p q) 30))
            (N (remainder (- (+ 4 k) q) 7)))
        (let ((d (remainder (+ (* 19 a) M) 30)))
          (let ((e (remainder (+ (* 2 b) (* 4 c) (* 6 d) N) 7))
                (o (+ 22 d (remainder (+ (* 2 b) (* 4 c) (* 6 d) N) 7))))
            o))))))


(osterformellet 2025)

(define (osterformellet* j)
  (let* ((a (remainder j 19))
         (b (remainder j 4))
         (c (remainder j 7))
         (k (floor (/ j 100)))
         (p (floor (/ (+ (* 8 k) 13) 25)))
         (q (floor (/ k 4)))
         (M (remainder (- (+ 15 k) p q) 30))
         (N (remainder (- (+ 4 k) q) 7))
         (d (remainder (+ (* 19 a) M) 30))
         (e (remainder (+ (* 2 b) (* 4 c) (* 6 d) N) 7))
         (o (+ 22 d e)))
    o))

(osterformellet* 2025)

~~~

# Aufgabe 4

~~~

(define (maxziffer n)
  (define (loop rest max)
    (if (= rest 0)
        max
        (let* ((ziffer (remainder rest 10))
               (max-neu (if (> ziffer max)ziffer max))
               (naechste (quotient rest 10)))
          (loop naechste max-neu))))
  (loop n 0))




~~~

# Aufgabe 5

~~~

(define (n x)
  (+ x 1))

(define (sum x y)
  (if (= y 0)
      x
      (n (sum x (- y 1)))))

(sum 0 2)

~~~

# Aufgabe 6

~~~

(define (n x)
  (+ x 1))

(define (sum x y)
  (if (= y 0)
      x
      (n (sum x (- y 1)))))

(define (mul x y)
  (if (= y 0)
      0
      (sum x (mul x (- y 1)))))

(mul 4 2)


~~~

# Aufgabe 7

~~~

(define (q n)
  (cond
    ((= n 1) 1)
    ((= n 2) 1)
    (else (+ (q (- n (q (- n 1)))) (q (- n (q (- n 2))))))))
 
(q 15)
(q 16)
(q 35)

~~~
