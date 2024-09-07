
1. Proces pocinje sa CPU fazom od 120ms i zavrsava se sa CPU fazom od 240ms, izmedju kojih je U/I faza od 200ms. Koliko puta ce se proces brze izvrsiti ako je omoguceno multi-programiranje, a programski kod procesa se izvrsava paralelno u 4 niti, ako racunar ima a) 2 jezgra b) 4 jezgra (Podrazumevati da nema drugih procesa u sistemu).

Ako se podje od toga da u sistemu imamo 4 niti i da jedno jezgro moze po jednu nit istovremeno da izvrsava, onda CPU faze mogu da se podele na 4 dela i da se svaki deo paralelno izvrsava na osnovu broja jezgra.

120 / 4 = 30
240 / 4 = 60

a) 2 jezgra
30 30 200 60 60    = 380ms
30 30         60 60

b) 4 jezgra
30 200 60     = 290ms
30         60
30         60
30         60