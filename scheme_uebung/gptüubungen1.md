# Aufgabe1

~~~

(define (f a b c)
  (and (or (not a) b)(or a (not b)(not c))))
(f #f #f #f)
(f #t #f #f)
(f #f #t #f)
(f #f #f #t)
(f #t #t #t)
(f #t #f #t)
~~~

# Aufgabe 2 

~~~

(define (parkgebuehr stunden)
  (cond (( < stunden 0)"kommst du aus der Zukunft?")
        ((and ( >= stunden 0)(< stunden 1)) "2")
        ((and ( >= stunden 1)(< stunden 3)) "4")
        ((and ( >= stunden 3)(< stunden 6)) "6")
        ((>= stunden 6) "10")))

(parkgebuehr 0.5)
(parkgebuehr 2)b
(parkgebuehr 5)
(parkgebuehr 7)
~~~

# Aufgabe 3 
~~~
(define (darf-durch? tueroffen alarm override akku)
  (and tueroffen (or  (not alarm)  override) (> akku 20)))


(darf-durch? #t #f #f 50)  ; erlaubt?
(darf-durch? #f #f #t 80)  ; erlaubt?
(darf-durch? #t #t #f 90)  ; erlaubt?
(darf-durch? #t #f #f 10)  ; erlaubt?
~~~


# Aufgabe 4 

~~~

(define (mitgliedsbeitrag alter typ)
  (cond ((< alter 18) (cond ((string=? typ "Standard") "20")
                            ((string=? typ "Premium") "nicht erlaubt")))
        ((and (>= alter 18)(<= alter 64)) (cond ((string=? typ "Standard") "35")
                                               ((string=? typ "Premium") "45")))
        ((>= alter 65) (cond ((string=? typ "Standard") "20")
                             ((string=? typ "Premium") "35")))))

(mitgliedsbeitrag 16 "Standard") ; ⇒ 20
(mitgliedsbeitrag 30 "Premium")  ; ⇒ 45
(mitgliedsbeitrag 70 "Standard") ; ⇒ 20
(mitgliedsbeitrag 65 "Premium")  ; ⇒ 35
~~~


# Aufgabe 5 

~~~
(define (ampel-entscheidung ampel abstand geschwindigkeit)
  (cond ((string=? ampel "rot")"Stop")
        ((string=? ampel "gelb") (if (and (> abstand 15)(> geschwindigkeit 40)) "Bremsen" "Langsam weiterfahren"))
        ((string=? ampel "gruen") (if (< abstand 10)"verlangsamen" "weiterfahren"))
        ((not (or (string=? ampel "rot")(string=? ampel "gelb")(string=? ampel "gruen")))"Ampel defekt")))

(ampel-entscheidung "rot" 50 30)     ; "Stop"
(ampel-entscheidung "gelb" 20 60)    ; "Bremsen"
(ampel-entscheidung "gelb" 5 20)     ; "Langsam weiterfahren"
(ampel-entscheidung "gruen" 8 40)    ; "Verlangsamen"
(ampel-entscheidung "gruen" 30 50)   ; "Weiterfahren"
(ampel-entscheidung "blau" 10 20)    ; "Ampel defekt"

~~~

# Aufgabe 6 

~~~
(define (note punkte bonus praxis)
  (if (< praxis 5)
      "nicht bestanden"
      (cond ((>= punkte (if bonus 85 90)) "1,0") 
            ((and (>= punkte (if bonus 75 80)) (< punkte (if bonus 85 90))) "2,0")
            ((and (>= punkte (if bonus 60 65)) (< punkte (if bonus 75 80))) "3,0")
            ((and (>= punkte (if bonus 45 50)) (< punkte (if bonus 60 65))) "4,0")
            ((< punkte (if bonus 45 50) "5,0 (nicht bestanden)")))))


(note 95 #f 8)   ; "1,0"
(note 82 #f 9)   ; "2,0"
(note 70 #t 6)   ; "3,0"
(note 48 #t 7)   ; "4,0"   ; (bonus rettet)
(note 60 #f 3)   ; "5,0 (nicht bestanden)" ; (Praxis zu schlecht)
~~~




                      
