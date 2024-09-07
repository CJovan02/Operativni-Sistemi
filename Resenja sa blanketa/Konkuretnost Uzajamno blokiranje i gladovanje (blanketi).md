
**Napomena:** U Knjizi se ova oblast zove *Kruzna blokada i izgladnjivanje*.
Uzajamno Blokiranje; Kruzna blokada - *Deadlock*

Objasnjenje za [[Matrice i vektori dodeljenosti]]
[[Kako proceniti stanje sistema na osnovu Grafa dodeljivanja resursa]]

1. ![[Graf dodeljivanja resursa zad1.png]]
Postoji deadlock. Svi procesi su blokirani.

|     | Ra  | Rb  | Rc  | Rd  |
| --- | --- | --- | --- | --- |
| R = | 1   | 1   | 1   | 1   |

|     | Ra  | Rb  | Rc  | Rd  |
| --- | --- | --- | --- | --- |
| V = | 0   | 0   | 0   | 0   |

| A   | Ra  | Rb  | Rc  | Rd  |
| --- | --- | --- | --- | --- |
| P1  | 1   | 0   | 0   | 0   |
| P2  | 0   | 1   | 0   | 0   |
| P3  | 0   | 0   | 1   | 0   |
| P4  | 0   | 0   | 0   | 1   |

| C   | Ra  | Rb  | Rc  | Rd  |
| --- | --- | --- | --- | --- |
| P1  | 1   | 1   | 0   | 0   |
| P2  | 0   | 1   | 1   | 0   |
| P3  | 0   | 0   | 1   | 1   |
| P4  | 1   | 0   | 0   | 1   |


| C - A | Ra  | Rb  | Rc  | Rd  |
| ----- | --- | --- | --- | --- |
| P1    | 0   | 1   | 0   | 0   |
| P2    | 0   | 0   | 1   | 0   |
| P3    | 0   | 0   | 0   | 1   |
| P4    | 1   | 0   | 0   | 0   |

2. ![[Graf dodeljivanja resursa zad2.png]]

|     | R1  | R2  | R3  |
| --- | --- | --- | --- |
| R = | 1   | 2   | 1   |

|     | R1  | R2  | R3  |
| --- | --- | --- | --- |
| V = | 0   | 0   | 0   |

| C   | R1  | R2  | R3  |
| --- | --- | --- | --- |
| P1  | 1   | 1   | 0   |
| P2  | 1   | 1   | 1   |
| P3  | 0   | 1   | 1   |

| A   | R1  | R2  | R3  |
| --- | --- | --- | --- |
| P1  | 0   | 1   | 0   |
| P2  | 1   | 1   | 0   |
| P3  | 0   | 0   | 1   |

| C - A | R1  | R2  | R3  |
| ----- | --- | --- | --- |
| P1    | 1   | 0   | 0   |
| P2    | 0   | 0   | 1   |
| P3    | 0   | 1   | 0   |
Iz C - A matrice i vektora V vidimo da svaki od procesa trazi neki resurs a da je taj resurs vec zauzet, znaci da je doslo do kruzne blokade/uzajamnog blokiranja/deadlock-a. Takodje je svaki od procesa blokiran.

3. ![[proizvodjac-potrosac zad1.png]]
Ne dolazi do deadlock-a (ovo je primer iz knjige gde se kaze da je ovo ispravno resenje).
Da bi kreirali deadlock mozemo kod consumera da izostavimo semSignal(n). To dovodi do sledeci situacije:
Consumer se odmah blokira jer je n = 0  i ostaje blokiran zauvek jer se n nikad ne poveca.
Producer nastavlja da smanjuje vrednost *e* dok ne dodje do nula i nakon toga se i on blokira zauvek jer se *e* nikad vise ne poveca.

4.  ![[Mat i vektori dodeljenosti zad1.png]]
[[Stanje sistema na osnovu matrica]]
![[Resenje mat i vektori dodeljenosti.png]]
U bezbednom je stanju sistem.
Valjda nisam zajebao racunicu.