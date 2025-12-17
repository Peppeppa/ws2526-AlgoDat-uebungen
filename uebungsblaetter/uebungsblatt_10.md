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

# Aufgabe 2

~~~

(define (sicheresPasswort passwort)
  (and (langGenug? (string->list passwort))(großKleiSonder? (string->list passwort))))

(define (langGenug? liste)
  (define (checkLength list count)
    (cond ((null? list) (if (>= count 8)
                            #t
                            #f))
          (else (checkLength (cdr list) (+ 1 count)))))
  (checkLength liste 0))


(define (großKleiSonder? liste)
  (define (loop l countKlein countGross countSonder)
    (cond ((null? l)(if (and (>= countKlein 1)(>= countGross 1)(>= countSonder 2))
                        #t
                        #f))
          ((and (char<=? #\a (car l))(char<=? (car l) #\z)) (loop (cdr l) (+ 1 countKlein) countGross countSonder))
          ((and (char<=? #\A (car l))(char<=? (car l) #\Z)) (loop (cdr l) countKlein (+ 1 countGross) countSonder))
          (else (loop (cdr l) countKlein countGross (+ 1 countSonder)))))
  (loop liste 0 0 0))



(sicheresPasswort "aUljsb!f/KasDhf")
(sicheresPasswort "ABC123") 

~~~

# Aufgabe 3

~~~

(define (loescheSpace s)
  (define (loop alt neu)
    (cond ((null? alt) neu)
          ((char=? (car alt) #\space) (loop (cdr alt) neu))
          (else (loop (cdr alt) (append neu (list (car alt)))))))
  (loop s '()))

(define (normalisiere chars)
  (cond
    [(null? chars) '()]
    [else
     (cons (char-downcase (car chars))
           (normalisiere (cdr chars)))]))

(define (laenge s1)
  (if (null? s1)
      0
      (+ 1 (laenge (cdr s1)))))

(define (char-in? current s2)
  (cond ((null? s2) #f)
        ((char=? current (car s2)) #t)
        (else (char-in? current (cdr s2)))))

(define (eins-weg current s2)
  (cond ((null? s2) '())
        ((char=? current (car s2)) (cdr s2))
        (else (cons (car s2)
                    (eins-weg current (cdr s2))))))

(define (anagramm s1 s2)
  (cond ((null? s1) #t)
        ((not (char-in? (car s1) s2)) #f)
        (else (anagramm (cdr s1) (eins-weg (car s1) s2)))))

(define (isAnagramm string1 string2) 
  (let* ((c1 (normalisiere (loescheSpace (string->list string1))))
         (c2 (normalisiere (loescheSpace (string->list string2)))))
    (if (not (= (laenge c1) (laenge c2)))
        #f
        (anagramm c1 c2))))


~~~

# Aufgabe 4

~~~

(define (vektor-add . vektoren)

  (define (summe-erste vs)
    (cond
      ((null? vs) 0)
      (else (+ (car (car vs))
               (summe-erste (cdr vs))))))

  (define (reste-vektoren vs)
    (cond
      ((null? vs) '())
      (else (cons (cdr (car vs))
                  (reste-vektoren (cdr vs))))))

  (define (add-loop vs)
    (if (null? (car vs))
        '()
        (cons (summe-erste vs)
              (add-loop (reste-vektoren vs)))))

  (add-loop vektoren))

~~~




