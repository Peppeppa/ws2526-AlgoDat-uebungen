

# Aufgabe 1

~~~
(define (ganzzahlige-wurzel? n)
(integer? (sqrt n)))


 
(ganzzahlige-wurzel? 25) 
(ganzzahlige-wurzel? 24)
~~~

# Aufgabe 2

~~~
(define (ganzzahlige-wurzel? n)     ;hilfsfunktion  aus Aufgabe 1 nur besser
  (let ((wurzel (sqrt n)))
    (= wurzel (floor wurzel))))

(define (fakt n)                     ; "main" edgecase check loop eingang
  (if (even? n)
      2
      (loop (ceiling (sqrt n)) (- (* (ceiling (sqrt n)) (ceiling (sqrt n))) n) n))) 
     ;    arg1: a setzen      |   arg2: init von b²                   | n wird mitgenommen
(define (loop a b2 n)
  (if (ganzzahlige-wurzel? b2)    ; check
      (- a (sqrt b2))             ; Exit -> Rückgabewert
      (let* ((a+1 (+ a 1))        ; Rekursion, a+1, neues b²
             (b2neu (- (* a+1 a+1) n)))
        (loop a+1 b2neu n))))


(fakt 11)
(fakt 2183) 
(fakt 25)
(fakt 100) 
(fakt 11) 

~~~

# Aufgabe 3
 ~~~


(define (ganzzahlige-wurzel? n)     ;hilfsfunktion 
  (let ((wurzel (sqrt n)))
    (= wurzel (floor wurzel))))

(define (fakt n)                     ; "main" edgecase check loop eingang
  (if (even? n)
      2
      (loop (ceiling (sqrt n)) (- (* (ceiling (sqrt n)) (ceiling (sqrt n))) n) n))) 
     ;    arg1: a setzen      |   arg2: init von b²                   | n wird mitgenommen
(define (loop a b2 n)
  (if (ganzzahlige-wurzel? b2)    ; check
      (- a (sqrt b2))             ; Exit -> Rückgabewert
      (let* ((a+1 (+ a 1))        ; Rekursion, a+1, neues b²
             (b2neu (- (* a+1 a+1) n)))
        (loop a+1 b2neu n))))
                    


(define (primzahl? n)
  (and (>= n 2) (= (fakt n) 1)))
     
      
  
(primzahl? 11) ;#t
(primzahl? 26737) ;#t
(primzahl? 200) ;#f
(primzahl? 121)


~~~


# Aufgabe 4

~~~
(define (kubiksumme n)
  (define (loop ergebnis zaehler)         ; erstelle loop -> 2 vars ergebnis und zaehler
    (if (= zaehler 0)                     ; check exit
        (* ergebnis ergebnis ergebnis)    ; exit ³
        (loop (+ (remainder zaehler 10) ergebnis)    ; loop zum durchiterieren der einzelnen zahlen.
              (quotient zaehler 10))))               ; in ergebnis mit remainder die letzte zahl rausfinden
    (loop 0 n))                                      ; und aufs ergebnis addieren
 

( kubiksumme 101042) 
( kubiksumme 34567) 

 ~~~


# Aufgabe 5

~~~

(define (caesar_encrypt n k)
  (define (loop rest faktor ergebnis)
    (if (= rest 0)
        ergebnis
        (let* ((ziffer (remainder rest 10))
               (crypt (modulo (+ ziffer k) 10)))
          (loop (quotient rest 10)
                (* faktor 10)
                (+ ergebnis (* crypt faktor))))))
  (loop n 1 0))

(caesar_encrypt 1234 1) ;2345
(caesar_encrypt 7901 2) ;9123
(caesar_encrypt 987 1) ;98

~~~

