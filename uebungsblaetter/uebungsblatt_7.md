

# Aufgabe 1 

~~~


(define (loesche liste praedikat)
  (cond ((null? liste) #f)
        ((not (praedikat (car liste))) liste)
        (else (loesche (cdr liste)praedikat))))

(loesche (list 4 6 8 3 2 4 5) even?)

~~~

# Aufgabe 2

~~~

(define (drehe liste)
  (let loop ((rest liste)
             (ergebnis '()))
    (if (null? rest)
        ergebnis
        (loop (cdr rest)
              (cons (car rest)
                    ergebnis)))))

(define (drehe2 liste)
  (define (loop rest ergebnis)
    (if (null? rest)
        ergebnis
        (loop (cdr rest)
              (cons (car rest)
                    ergebnis))))
  (loop liste '()))

(drehe (list 1 2 3))
(drehe2 (list 1 2 3))

~~~

# Aufgabe 3

~~~

(define (typ-or? typ1 typ2)
  (lambda (x)
    (or (typ1 x)(typ2 x))))
(define paar-oder-liste? (typ-or? pair? list?))
(define integer-or-bool? (typ-or? integer? boolean?))
(integer-or-bool? (paar-oder-liste? (cons 1 2)))

~~~

# Aufgabe 4

~~~



~~~
