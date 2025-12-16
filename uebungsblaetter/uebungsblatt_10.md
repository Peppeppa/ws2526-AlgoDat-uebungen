# Aufgabe 1

~~~
(define (removeFirstLast string)
  (list->string (rfliter (string->list string))))

(define (rfliter list)
  (cond ((or (null? list) (null? (cdr list))) '())
        (else
         (let loop ((rest (cdr list)))
           (cond ((or (null? rest) (null? (cdr rest))) '())
                 (else (cons (car rest)
                             (loop (cdr rest)))))))))

(removeFirstLast "Hallo Welt")


~~~


