# basic prozeduren


# Anzahl der ziffern in einer Zahl

~~~
(define (anzahl-ziffern n)
  (if (< n 10)
      1
      (+ 1 (anzahl-ziffern (quotient n 10)))))

(anzahl-ziffern 123)
(anzahl-ziffern 123456)
~~~

# Ziff Iter Link -> Rechts
- iteriert über eine gegebene Zahl von links nach rechts

~~~
(define (ziffIternachR n)
  (if (= n 0)
      0   ; hier wird das ergebnis dann ausgegeben wenn fertig
      (ziffIternachR (quotient n 10))))

(ziffIternachR 12345)
~~~
