# 1
 ~~~
(define (anpassen liste)
  (define (loop alt neu)
    (cond ((null? alt) neu)
          ((odd? (car alt))(loop (cdr alt) neu))
          ((= (remainder (car alt) 10) 0) (loop (cdr alt)
                                                (append neu (list (* (car alt)(car alt))))))
          (else (loop (cdr alt)
                      (append neu (list (car alt)))))))
  (loop liste '()))

(anpassen (list 5 9 10 12 20))
~~~
# 2
~~~
(define (gleich? liste)
  (define (help liste pos neg)
    (cond ((null? liste) (= pos neg))
          ((< (car liste) 0)(help (cdr liste)pos(+ neg 1)))
          ((> (car liste) 0)(help (cdr liste)(+ pos 1)neg))
          (else (help (cdr liste) pos neg))))
  (if (null? liste)
      #f      
      (help liste 0 0)))

(gleich? (list 1 -1 0))
~~~
# 2
~~~

(define (sortieren liste praedikat)
  (define (loop alt neu hinten praed)
    (cond ((null? alt) (append neu hinten))
          ((praed (car alt))(loop (cdr alt)(append neu (list (car alt))) hinten praed))
          (else (loop (cdr alt) neu (append hinten (list (car alt))) praed))))
  (loop liste '() '() praedikat))

(sortieren (list 1 2 3 4 5 6 7 8 9) odd?) 

~~~
