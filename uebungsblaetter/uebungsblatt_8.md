# Aufgabe 1 

~~~
(define (compress liste)
  (define (loop rest current count)
    (cond
      ; liste leer? wenn rest komplett fertig -> letzte stelle oder counter + letzte stelle
      [(null? rest)
       (if (= count 1)
           (list current)
           (list count current))]

      ; nächste stelle ist gleich der aktuellen -> nur counter +1 kein aufbauen neue liste
      ; fortfahren mit nächster stelle der restlichen liste
      
      [(eq? (car rest) current)
       (loop (cdr rest) current (+ count 1))]

      ; nächste stelle ist ungleich der aktuellen-> baue neue liste!
      ; APPEND -> car-teil -> if count >1 counter + aktuelle stelle
      ;                          count =1 nur aktuelle stelle
      ;           cdr teil -> loop restliche liste SETZE COUNTER AUF 1
      
      [else
       (append (if (= count 1)
                   (list current)
                   (list count current))
               (loop (cdr rest) (car rest) 1))]))

  
                    ;beginn, erstaufruf loop aber nur wenn liste nicht null
  (if (null? liste)
      '()
      (loop (cdr liste) (car liste) 1)))



(compress '(a b b c c c (list 1 2 3 )))
(compress '(a b b b c))
~~~


