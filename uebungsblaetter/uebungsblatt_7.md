

# Aufgabe 1 

~~~


(define (loesche liste praedikat)
  (cond ((null? liste) #f)
        ((not (praedikat (car liste))) liste)
        (else (loesche (cdr liste)praedikat))))

(loesche (list 4 6 8 3 2 4 5) even?)

~~~



