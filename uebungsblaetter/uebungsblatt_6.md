# Aufgabe 1

~~~



#lang racket/base
(define (zaehlen start ende n)  ; äußere Definition 
  (let loop ((ziffer start)    ; let loop -> rekursive funktion mit 2 Laufvariablen, 
             (count 0))        ; Ziffer: aktuelle zahl, start: 0 count -> bisherige anzahl an treffern 
    (cond                       ; Fallunterscheidung
      ((> ziffer ende) 0)        ;Fall 1 -> Bereich zuende
      ((= (remainder ziffer 21) 0); Fall 2 -> Ziffer ist vielfaches von 21 (3 und 7) a-> n-te? -> count +1 weil nur count die bis jetzt gefundenen sind 
       (if (= (+ count 1) n)       ; b -> weiter gehts ziffer + 1 count +1
           ziffer
           (loop (+ ziffer 1) (+ count 1))))
      (else
       (loop (+ ziffer 1) count)))))   ; ziffer ist kein vielfaches von 21-> ziffer +1 count bleibt weil nichts gefunden wurde, rekursion geht weiter


(zaehlen 10 100 1)


~~~




# Aufgabe 2 

~~~

(define (gleiche-ziffern zahl)
  (define (loop n)
    (if (< n 10)
        n
        (loop (quotient n 10))))

  (define (passt? n)
    (= (loop n) (remainder n 10)))

  (if (passt? zahl)
      zahl
      (gleiche-ziffern (+ zahl 1))))

(gleiche-ziffern 32431548)


~~~
