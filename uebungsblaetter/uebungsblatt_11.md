# Aufgabe 1 

~~~
nur mit gpt :/ 

(define (lookup sym zuweisungen)
  (cond
    [(null? zuweisungen) (error "Unbekanntes Symbol" sym)]
    [(eq? sym (car (car zuweisungen))) (cadr (car zuweisungen))]
    [else (lookup sym (cdr zuweisungen))]))

(define (operand->zahl op zuweisungen)
  (cond
    [(number? op) op]
    [(symbol? op) (lookup op zuweisungen)]
    [else (error "Ungültiger Operand" op)]))

(define (werte-aus term zuweisungen)
  (let* ((op (car term))
         (a  (operand->zahl (cadr term) zuweisungen))
         (b  (operand->zahl (caddr term) zuweisungen)))
    (cond
      [(eq? op '+) (+ a b)]
      [(eq? op '-) (- a b)]
      [(eq? op '*) (* a b)]
      [(eq? op '/) (/ a b)]
      [else (error "Unbekannter Operator" op)])))


~~~


# Aufgabe 2 

~~~
(define (deep-memq element liste)
  (cond
    ((null? liste) #f)
    ((list? (car liste))
     (or (deep-memq element (car liste))
         (deep-memq element (cdr liste))))
    (else
     (if (eq? element (car liste))
         #t
         (deep-memq element (cdr liste))))))


(deep-memq 2 '(1 2 3)) 
(deep-memq 3 '(1 (2 (4 5) 3))) 
(deep-memq 3 '((1 5) (2 (7 2 6 4 (4 5) (2 4))))) 
~~~




#Aufgabe 3 

~~~



~~~


