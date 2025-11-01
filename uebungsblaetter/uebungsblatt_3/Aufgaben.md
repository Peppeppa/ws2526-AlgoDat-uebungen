

# Aufgabe 1

~~~
(define (sinus-approx x)
  (if (<= x 0.1)
      x
      (- (* 3 (sinus-approx (/ x 3)))
         (* 4 (sinus-approx (/ x 3))
            (sinus-approx(/ x 3))
            (sinus-approx(/ x 3))))))

(sinus-approx 10) 
(sin 10)

~~~


# Aufgabe 2


~~~
(define (count-perm x)
  (if (not (>= x 2))
      0
      (count-iter 2 x 1)))

(define (count-iter zaehler x ergebnis)
  (if (> zaehler x)
      ergebnis
      (count-iter (+ zaehler 1) x (* ergebnis zaehler ))))


(count-perm 2)
(count-perm 3)
(count-perm 5)

~~~

# Aufgabe 3

~~~

(define (isbn-test isbn)               ;(isbn-iter 0 9 isbn) berechnet die Summe
  (if (= (remainder (isbn-iter 0 9 isbn) 11) 10)       ; if checkt ob Rest der Division der Summe durch 11 gleich 10 ist
      "X"                     ; wenn ja gib X aus
      (remainder (isbn-iter 0 9 isbn) 11)))      ;wenn nein gib den Rest aus

(define (isbn-iter ergebnis zaehler x)
  (if (= zaehler 0)                      ;wenn der Zähler = 0 ist gib das Ergebnis aus
      ergebnis                           ;wenn nicht dann iteriere
      (isbn-iter (+ ergebnis (* zaehler (remainder x 10)))    
                 (- zaehler 1)
                 (quotient x 10))))



(isbn-test 344615497)
(isbn-test 026201153)
(isbn-test 392511825) 

~~~


# Aufgabe 4

~~~

(define ( zylinder-kegel radius-zylinder hoehe-zylinder radius-kegel hoehe-kegel )
  (define pi 3.1415926535897932384626433832795)
  (define (zylinder r h pi)
    (* pi h (* r r)))
  (define (kegel r h pi)
    (* (/ 1 3) pi (* r r) h)) 
  (/ (zylinder radius-zylinder hoehe-zylinder pi)(kegel radius-kegel hoehe-kegel pi)))

( zylinder-kegel 3 5 3 5)


~~~


