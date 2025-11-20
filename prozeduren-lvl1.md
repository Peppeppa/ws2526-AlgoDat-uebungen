# einfache Prozeduren


# binär -> dezimal umrechner

~~~
(define (binaer-umrechner bin)
  (if (< bin 0)   ; edge case negative eingabe
      #f
      (let loop ((ergebnis 0)
                 (n bin)
                 (zaehler 1))
        (if (= n 0 )
            ergebnis
            (loop (+ ergebnis (*(remainder n 10) zaehler))(quotient n 10)(+ zaehler zaehler))))))


(binaer-umrechner 10010)
(binaer-umrechner 0000)
(binaer-umrechner -101)
(binaer-umrechner 10010)
~~~

# zählerteiler
-> zählt wie oft n restlos geteilt werden kann

~~~
(define (zaehlerteiler n)
  (define (iter ergebnis n zaehler)
    (if (= zaehler n)
        ergebnis
        (iter (if (= 0 (remainder n zaehler))
                  (+ 1 ergebnis)
                  ergebnis)
              n
              (+ 1 zaehler))))
  (iter 0 n 2))
 
(zaehlerteiler 20)


~~~



