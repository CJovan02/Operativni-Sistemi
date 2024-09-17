
Inode (index node) je kontrolna struktura koja sadrzi kljucne informacije potrebne operativnom sistemu za neki fajl. Nekoliko imena fajlova mogu da budu asocirani za jedna inode, ali jedan aktivan inode je asociran za tacno jedan fajl, i jedan fajl je kontrolisan sa tacno jednim inode-om.

U sustini radi se o indeksnom alociranju fajla gde se fajl alocira na vise blokova ali su ti blokovi nisu kontinuirani (jedna za drugim na fizickom disku) ali su indeksirani uz pomoz inode-a ali na vrlo specifican nacin. Velicina bloka je uglavnom 512 bajta.

![[Inode.png]]

**Prvih 12 adresa pokazuje na prvih 12 blokova podataka tog fajla**, sto se vidi sa slike (mada sa slike se vidi da su to 13 ali ovako pise u knjizi). 

Ako je za fajl potrebno vise od 12 blokova podataka, koristi se jedan ili vise nivoa indirektnosti, kao sto sledi:
- Trinaesta adresa u i-cvoru pokazuje na blok na disku koji sadrzi sledecu deo indeksa. To se zove **jednostruki indirektni pokazivac** blokova (engl. *single indirect block*). Ovaj blok sadrzi pokazivace na sledece blokove fajla.
- Ako fajl zadrzi jos vise blokova, cetrnaesta adresa u i-cvoru pokazuje na **dvostruki indirektni blok** (engl. *double indirect block*). Taj blok sadrzi listu adresa dodatnih jednostrukih indirektnih pokazivaca blokova. Svaki jednostruki indirektni pokazivac blokova zatim sadrzi pokazivace blokova fajla.
- Ako fajl sadrzi jos vise blokova, petnaesta adresa u i-cvorui pokazuje na **trostruki indirektni blok** (engl. *triple indirect block*), a to je treci nivu indeksiranja. Ovaj blok pokazuje na dodatne dvostruke indirektne blokove.

![[Kapacitet freeBST fajla.png]]

**BItno za teorijsko pitanje:** Na disku postoji tabela i-cvorova, ili lista i-cvorova, koja sadrzi i-cvorove svih fajlova u sistemu fajlova. Kada se fajl otvori, njegov i-cvor se unosi u glavnu memoriju i cuva se u tabeli i-cvorova koja je rezidentna u memoriji. 