
Hard Disk se deli na **staze** koje su koncentricni prsteni oko diska koju su medjusobno odvojieni i iste su sirine kao glava

Svaka staza se deli na **sektore** koji su uglavnom fiksnih duzina od po 512 bajtova.


![[Vreme transfera i trazenja formule.png]]

Ova donja formula se koristi za zadatke gde je
**Ta -  srednje vreme pristupa (access time)**
**Ts - srednje vreme trazenja/pozicioniranja (seek time)**

**Vreme trazenja (ili vreme pozicioniranja, eng. seek time)** je vreme potrebno da se rucica diska pomeri za zeljenu stazu.

**Rotaciono kasnjenje** je vreme potrebno da adresirano podrucje diska rotira do pozicije na kojoj je dostupno glavi za citanje/pisanje. Odnosno, vreme potrebno da pocetak sektora stigne do glave.

Zbir vremena pozicioniranja, ako postoji, i rotacionog kasnjenja jednako je **vremenu pristupa (access time)**, a to je vreme potrebno za stizanje na poziciju za citanje ili pisanje.

Kad se glava nadje na poziciji, operacija citanja ili pisanja se vresi dok se sektor krece ispod glave; taj deo operacije je transfer podataka. Vreme potrebno za transfer je **vreme transfera**.

## Bitno za zadatke

Kolko sam ja stigo da razumem imamo 3 slucaja:

1. **Sekvencijalna (kontinualna) rasporeda blokova jednog fajla** - svi blokovi jednog fajla idu jedan za drugim, ovo je najlaksi primer, samo primenimo formulu Ta (b je broj blokova * velicina jednog bloka)
2. **Koristi se indeksiranje (ili Linux inode isto je)** - kod indeksiranja blokovi nisu jedan za drugim nego su rastrkani po memoriji, odnosno glava mora prvo da se pozicionira na jedna blok pa da se pomeri na drugi pa na treci itd... Odnosno racunamo *Ta* za samo jedan blok (b sada nije broj blokova * velicina bloka nego **samo velicina jednog bloka**) pa onda sve to pomnozimo sa brojem blokova
3.  **Kombinovano (NTFS) - u zadatku se kaze, na primer, 16 nezavisnih grupa od po 32 bloka** - znaci mi izracunamo *Ta* za jednu grupu (16 bloka * velicina jednog bloka za ovaj primer) pa taj *Ta* pomozimo sa brojem grupa