
## Ovo je moja logika za izradu ovih tipova zadataka. Nisam 100% siguran da li se ovako rade.

![[dirinode.jpg]]

Linux inode na isti nacin pamti fajlove i foldere, sem sto folderi zadrze informacije u pokazivacima na inode fajlova koje sadrzi.

Ako imamo, na primer, putanju /a/b/c.c kao na slici logika bi isla ovako:
***Svaki put kada zelimo da procitamo ili obradimo fajl ili folder moramo prvo da njegov inode prebacimo iz diska u glavnoj memoriji sto zahteva 1 dodatnu memorijsku lokaciju.***
Zatim,
***Kada ucitamo inode direktorijuma u glavnu memoriju moramo sve njegove blokove da procitamo kako bi smo nasli sledeci fajl/folder u hijerarhiji (ovo se obicno da u zadatku koliko direktorijum ima blokova, medjutim nisam siguran da li moraju svi blokovi da se procitaju)***
Zatim,
***Kada pronadjemo fajl koji trazimo gledamo koliko blokova zauzima taj fajl i na osnovu toga znamo koliko memorijskih pristupa imamo (ako [[Inode]] ima 12 direktnih adresa a fajl zauzima 13 onda se on adresira preko single indirect koji zahteva 1 mem pristup za citanje bloka pokazivaza za njegove blokove, znaci 14 pristupa memoriji)