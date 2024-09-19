
Performanse diska dosta zavise od vremena pozicioniranja, da bi poboljsalji vreme pozicioniranja glave, kako bi ona nakon svakog novog citanja/pisanja prelazila sto manju distancu koriste se nakoliko algoritama rasporedjivanja.

* FIFO - ne potrebe da se objasnjava, stavke iz reda cekanja obradjujemo redom, ko prvi stigne taj se prvi usluzi
* Prioritet (PRI)
* LIFO - ko zadnji stigne taj se uzluzi
* [[SSTF]]
* [[SCAN]] 
* [[C-SCAN]]

Glava diska se na **pocetku nalazi na stazi 100**, imamo **maksimalno 200 staza**.
Zahtevane staze, u redosledu kako ih je primio rasporedjivac diska su:
**55, 58, 39, 18, 90, 160, 150, 38, 184**.
![[Poredjenje algoritama za rasporedjivanje diska.png]]