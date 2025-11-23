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

# einstellige quersumme

 ~~~
(define (einstellige-quersumme zahl)
  (define (iter zahl ergebnis)
           (if (= 0 zahl)
               ergebnis
               (iter (quotient zahl 10) (+ ergebnis (remainder zahl 10)))))
  (iter zahl 0))

(einstellige-quersumme 123)

~~~


# Palindrom?

~~~
  (define (umdrehen n)
    (define (rev n new)
      (if (= n 0)
          new
          (rev (quotient n 10)(+ (* 10 new) (remainder n 10)))))
    (rev n 0))

(define (palindrom n)
  (if (= n (umdrehen n))
      #t
      (- n (umdrehen n))))


(palindrom 123)
(palindrom 12321)
(palindrom 123211)
~~~

# vergleich mit Zähler

~~~

(define (vergleich zahl op)
  (let loop ((n zahl)
             (count 0))
    (let * ((rechts (remainder n 10))
            (rest (quotient n 10)))
      (if (= rest 0)
          count
          (let ((links (remainder rest 10)))
            (loop rest
                  (if (op links rechts)
                      (+ 1 count)
                      count)))))))

(vergleich 112233 <)
(vergleich 112233 =)

~~~


# Einstellige Quersumme

~~~
(define (einstellige-quersumme zahl)
  (let loop ((n zahl)
             (sum 0))
    (if (= n 0)
        sum
        (loop (quotient n 10)
              (+ sum (remainder n 10))))))

(einstellige-quersumme 123)


~~~


