# Listen in Racket



# zugriff auf das n-te element in einer liste

~~~

; operationen auf listen

;zugriff auf n-tes element
;Nummerierung beginnt bei 0
;Idee:
;   if    n=1 -> car der liste als Ergebnis
;   else  (n - 1)te element des cdr der liste

(define (liste-ref elemente n)
  (if (= n 1)
      (car elemente)
      (liste-ref (cdr elemente) (- n 1))))

(liste-ref (list 1 4 9 16 25) 6)

~~~


# Anzahl der Elemente in einer liste

~~~

;operation: Anzahl der Elemente in einer Liste

;- Prädikat "null?" prüft ob ein Element die leere Liste ist
;- Nutzt Prädikat um bis zum Ende der Liste zu laufen und die Elemente zu zählen
;- Rekursiv

(define (laenge elemente)
  (if (null? elemente)
      0
      (+ 1 (laenge (cdr elemente)))))


(laenge (list 1 4 9 16 25))

#|
(laenge (list 1 4 9 16 25)
  (if (null? elemente)
      0
      (+ 1 (laenge (cdr elemente)
      (+ 1 (laenge (4 9 16 25)))
         (+ 1 (laenge ( 9 16 25)
             (+ 1 (laenge ( 16 25)
                (+ 1 (laenge ( 25)
                   ( + 1 (laenge ()
                      (0)
|#

~~~

# verkettung 2er listen

~~~

;Operation Verketten zweier Listen "liste 1" und "liste 2"
; Falls Liste 1 leer ist, gibt Liste 2 zurück
; Sonst verkette den Rest von Liste 1 mit Liste 2 und Konstruiere das erste Element von Liste 1 an den Anfang

(define (verketten liste1 liste2)
  (if (null? liste1)
      liste2
      (cons (car liste1)
            (verketten (cdr liste1) liste2))))

(verketten (list 1 2 3 4) (list 6 7 8 9))
~~~
