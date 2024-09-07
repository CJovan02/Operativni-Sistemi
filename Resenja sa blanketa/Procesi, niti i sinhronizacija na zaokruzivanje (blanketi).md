
1. U kom modu se nalazi sistem, a u kom stanju proces kada izvrsi: 
	a) pthread_create - *user; running*
	b) semsignal(s) - *s <= 0 kernel, inace user;
	semSignal povecava vrednost semafora za 1, ako je manje ili jednako 0 onda je proces blokiran ako je vece od 0 proces je odblokiran odnosno prelazi u ready stanje*
	c) exchange(a, b) [[Atomicne funkcije]] - user mode; running
	d) sqrt() - user mode; running
	e) martrix_multiplication(A, B, C) - user mode; running

2. U kom stanju je proces, a u kom modu je sistem (kernel, korisnicki) nakon sto tekuci proces izvrsi:
	a) execvp(command, argv) - sistemski poziv, znaci kernel mod; 
	b) strcmp(x1, x2) - user; running;
	c) fgets(str, n, stream) - kernel; blocked;
	d) csignal(c) ([[Monitori]]) - c se odnosi na uslov za monitor i procesi pozivaju cwait(c) za neki uslov, ako taj proces za taj uslov ne postoji trenutni proces ne menja stanje (running state) i mod je user, a ako pronadje proces vezan za c onda nastavlja izvrsenje tog procesa nalazi se u kernel modu i stanje procesa prelazi iz running u ready
	e) exchange(reg, mem) [[Atomicne funkcije]] - user mode; running
	
3. U kom je stanju proces kada:
	a) se nalazi na sekundarnoj memoriji spreman da bude izabran za izvrsavanje - ready/suspend
	b) ceka na zavrsetak funkcije fscanf() - blocked
	c) primi signal SIGKILL - exit
	d) izvrsi test_and_set() instrukciju [[Atomicne funkcije]] - running
	e) njegova nit implementirana kao ULT zavrsi vremenski kvant dodeljen u biblioteci niti - running

4. U kom je stanju bio i u koje stanje prelazi proces kada:
	a) izvrsi read() funkciju - running -> blocked
	b) izvrsi semsignal(s), pri cemu je proces blokiran na semaforu viseg prioriteta - blocked -> blocked (ne menja stanje)
	c) izvrsi test&set() [[Atomicne funkcije]] funkciju - running -> running
	d) izvrsi exit funkciju - running -> exit (terminated)
	e) izvrsi monitor.produce() funkciju dok drugi proces izvrsava monitor.consume funkciju - running -> blocked ([[Producer consumer problem]])
	
5. U koje stanje prelazi nit, a u koje proces kada se desi sledeci dogadjaj (objasni ukratko):
	a) ULT nit pozove f-ju write() (implementiran jacketing) - nit prelazi u blocked; ako ima vise niti u procesu proces ostaje u running a ako ima samo jedna nit prelazi u blocked
	b) KLT nit pozove sem_wait(1) - nit prelazi u blocked (jer se 1 smanjuje na 0); proces ostaje u running (kod KLT thread ne blokira proces)
	c) ULT nit kad se desi clock interrupt -  proces prelazi u ready (takva je rutina kod prekida clock-a); a nit ne menja stanje (jer stanje niti ne zavisi od procesa);
	d) KLT nit pozove funkciju exchange(b, k) - i nit i proces ostaju u running (exchange funckija nije blokirajuce jer je iz standardne biblioteke ili je korisnicka funkcija)
	e) ULT nit pozove funkciju fork() - nit ostaje u istom stanju; proces ostaje u running a novi proces je u ready stanju.
	
6. U sistemu se izvrsava proces sa vise niti P(T1, T2). U koje stanje prelazi niti i koja se nit moze sledeca izvrsavati?
	a) Nit T1, pozove funkciju semWait() nad semaforom s=0, a niti su implementirane na nivou kernela (KLT) - *T1 se blokira jer s je sad -1, T2 se izvrsava i ako ona pozove semWait() i ona se blokira*
	b) Nit T2, pozove receive() funkciju, a niti su implementirane na nivou korisnika (ULT) - *Ako receive() nije implementirana kao blokirajuca onda T2 ostaje u running, ako je kao blokirajuca implementirana onda se blokira sve dok ne se primi poruka, a T1 nastavlja da se izvrsava. To vazi ako je implementiran jacketing za ULT a ako nije onda ce T2 da blokira ceo proces (ako je receive() implementirana kao blokirajuci naravno)*
	c) Istekao je vremenski kvant dodeljen niti T1, a niti su implementirane na nivou korisnika (ULT) - *T1 prelazi iz running u ready a T2 iz ready u running (u drugom resenju pise da ceo proces prelazi u ready stanje, to se desi kada za proces istekne vremenski kvant a u zadatku pise da je za thread istekao a ne za proces)*
	d) Nit T2 poziva pthread_create() funkciju, a niti su implementirane na nivou kernela (KLT) - *Nit T2 nastavlja da se izvrsava normalno a T1 ostaje u istom stanju. Sistem prelazi u kernel mod da bi kreirao novu nit T3*
	e) Nit T1 poziva malloc() funkciju, a niti su implementirane na nivou kernela (KLT) - *T1 ostaje u running stanju a T2 u istom stanju kao i pre poziva funkcije*

7. Na sledeca pitanja odgovoriti sa Da ili Ne + objasnjenje od 1 recenice...
	a) Prelaz iz stanja *izvrsava se* u stanje *blokiran* je uvek preko kernel moda -> *Da. Running stanje znaci da je se proces trenutno izvrsava na CPU i kada se njegovo stanje promenu u blocked mora se taj proces zameniti nekim drugim, sto zahteva promenu u kernel mod.*
	b) Kada proces zapocinje izvrsavanje, environment promenljive se smestaju na pocetak steka procesa -> ***GPT ODGOVOR:** Ne. Environment promenljive se smeštaju u segment podataka procesa (u tzv. **environment segment**), a ne na stek.*
	c) Fork() sistemski poziv izvrsava programski kod naveden kao oargument u vidu path do izvrsne datoteke -> *Ne. Fork() kreira novi proces gde on deli programski kod parent procesa i kopira se process image (bez deljene memorije)*
	d) Prilikom startovanja C programa, lokalne promenljive funkcije main() se smestaju na stek procesa -> ***GPT ODGOVOR:** Da. Lokalne promenljive funkcije, uključujući funkciju main(), smeštaju se na **stack** (stack segment) procesa.*
	e) U sistemu sa 3 nivoa stranicenja (bez kesa i TLB) pribavljanje i izvrsenje instrukcija koja sabira vrednost registra sa sadrzajem memorijske lokacije zahteva 3 pristupa memoriji -> **Nisam stigo dotle**

8. U kom modu je sistem (kernel, korisnicki), a u koje stanje prelazi aktivni proces nakon sto se dogodi:
	a) Prekid takta -> *Misli se verovatno na clock interrupt - kernel; ready*
	b) Pozove cwait() [[Monitori]] -> *kernel; blocked*
	c) exchange(a, b) [[Atomicne funkcije]] -> *user; running*
	d) strcpy(s1, s2) -> *user; running*
	e) zavrsena je funkcija *write()* koju je pozvao proces viseg prioriteta -> *user; running (**GPT**:  Kada funkcija **write()** završi, proces koji je čekao na nju prelazi iz **blocked** u **ready** stanje. Ako je taj proces višeg prioriteta, operativni sistem može preemptovati trenutno izvršavani proces, a taj proces može preći u **ready** dok proces višeg prioriteta prelazi u **running**. Dakle, u zavisnosti od prioriteta, **trenutni proces** može ostati u **running** ili biti prebačen u **ready**.)*