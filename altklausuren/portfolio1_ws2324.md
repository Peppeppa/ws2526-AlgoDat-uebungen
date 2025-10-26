
# 1 
~~~
(define (f a b c d e)
  (or (and a b d e) (not (or (and c a d) (not (and a c))))))

(f #f #f #f #t #t)
~~~

# 2 
~~~

(define (tetraederzahl n)
  (/ (* n (+ n 1) (+ n 2)) 6))
(tetraederzahl 7)
(tetraederzahl 1)
(tetraederzahl 6)
(tetraederzahl 8000)
~~~

# 3 

~~~
; Grundpreis     pro kwh   0,20
;  Jahresverbrauch unter 2000 ->  Grundpreis +10%
;  Jahresverbraucht >= 3500 -> grundpreis -5%

(define (preis kwh)
  (cond ((< kwh 2000) (* kwh (* (/ 0.2 100) 110)))
        ((and (>= kwh 2000) (< kwh 3500))(* kwh 0.2))
        ((>= kwh 3500) (* kwh (* (/ 0.2 100)95)))))


(preis 1999)
(preis 2000)
(preis 2001)
(preis 3499)
(preis 3500)
(preis 3501)  
~~~

