# QR-codes---Reader-and-generator-
QR code reader and generator in python which does not use functions from libraries that directly manipulate QR codes.

Cristea Andrei - grupa 134
Nicula Andrei  - grupa 134


Construim un qr reader si qr generator hardcodat pentru
versiunea 2(25*25) si pt nivelul L de error_correction(low = 7%)


READER

Folosesc functii din biblioteca cv2 pentru a transforma o imagine cu un qr code intr o matrice numpy cu valori de 0 pentru un modul negru si 255 pentru un modul alb. Practic, functia qr_to_matrix imi ia imaginea o centreaza, o imparte in 25*25 de patrate egal si se intreaba daca in fiecare patrat e mai mult alb sau negru. Astfel, imi construieste exact matricea cu care pot lucra formata din 255 si 0.

1.Initial incerc sa aflu tipul mastii folosindu ma de cei 3 biti din format bits sii de o hardcodare specifica fiecarei masti in parte
2.Dupa ce am aflat tipul mastii xorez matricea cu masca respectiva si obtin astfel matricea initala(a xor masca xor masca = a)
3.Citesc din cod si decodific incepand de la primul byte de continut si ma opresc cand ajung la terminatorul 0000
4.Afisez outputul
5.Nota: Mentionez ca inainte sa implementez functia qr_to_matrix am folosit functii din biblioteca qrcode pentru a creea matricea respectiva si a face debug pe cod.

GENERATOR

Folsesc matrici din biblioteca numpy si functii din matplotlib pentru ca la final sa pot transforma matricea intr o imagine.
1.Initializez matricea cu elementele comune pentru orice cod qr de versiune 2: finding_patterns, orientation_pattern, timing_patern
2.Iau string ul din input si il transform in binar, iar inaintea lui adaug cei 4 biti de datatype(hardcoded) si byte ul care specifica lungimea stringului. Adaug bitii de corectie folosind algoritmul lui reedsolomon si functii din aceasta biblioteca, iar la fina   adaug bitii de padding
Nota: algoritmul lui reed solomon se bazeaza pe faptul ca exista un singur polinom grad n-1 care sa treaca prin n puncte. Asadar, daca construiesc acest polinom nu doar ca voi stii sigur ce biti au fost corupti dar voi avea si o metoda pentru a afla ce valoare transmiteau initial(gasind valoarea polinomului in punctul respectiv)
3.Xorez cu toate cele 8 masti si calculez scorul pentru fiecare
4.Afisez qr ul cu scorul de penalizare cel mai mic.


SURSE:

Am cautat informatii pe diverse site-uri si am vizionat videoclipuri pe youtube pentru a intelege cum functioneaza codurile qr. Dau mai jos lista link-urilor catre acestea:

https://www.nayuki.io/page/creating-a-qr-code-step-by-step

https://www.researchgate.net/figure/The-structure-of-QR-code-in-version-2-M_fig5_333611998

https://www.youtube.com/watch?v=w5ebcowAJD8&t=1716s&ab_channel=Veritasium

https://www.youtube.com/watch?v=Rc3ul6RRANU&ab_channel=ProfessorJulioLombaldo

https://www.youtube.com/watch?v=sRgUrKWiXQs&ab_channel=NoOneAsked

https://www.youtube.com/watch?v=1pQJkt7-R4Q&t=650s&ab_channel=vcubingx
