
1. U kom modu se nalazi sistem, a u kom stanju proces kada izvrsi: 
	a) pthread_create - user; running
	b) semsignal(s) - s <= 0 kernel, inace user;
	semSignal povecava vrednost semafora za 1, ako je manje ili jednako 0 onda je proces blokiran ako je vece od 0 proces je odblokiran odnosno prelazi u ready stanje
	c) exchange(a, b) - user mode; running
	d) sqrt() - user mode; running
	e) martrix_multiplication(A, B, C) - user mode; running

2. U kom stanju je proces, a u kom modu je sistem (kernel, korisnicki) nakon sto tekuci proces izvrsi:
	a) execvp(command, argv) - sistemski poziv, znaci kernel mod; 
	b) strcmp(x1, x2) - user; running;
	c) fgets(str, n, stream) - kernel; blocked;
	d) csignal(c) ([[Monitori]]) - c se odnosi na uslov za monitor i procesi pozivaju cwait(c) za neki uslov, ako taj proces za taj uslov ne postoji trenutni proces ne menja stanje (running state) i mod je user, a ako pronadje proces vezan za c onda nastavlja izvrsenje tog procesa nalazi se u kernel modu i stanje procesa prelazi iz running u ready
	e) exchange(reg, mem) - user mode; running
	
3. U kom je stanju proces kada:
	a) se nalazi na sekundarnoj memoriji spreman da bude izabran za izvrsavanje - ready/suspend
	b) ceka na zavrsetak funkcije fscanf() - blocked
	c) primi signal SIGKILL - exit
	d) izvrsi test_and_set() instrukciju - running
	e) njegova nit implementirana kao ULT zavrsi vremenski kvant dodeljen u biblioteci niti - running

4. U kom je stanju bio i u koje stanje prelazi proces kada:
	a) izvrsi read() funkciju - running -> blocked
	b) izvrsi semsignal(s), pri cemu je proces blokiran na semaforu viseg prioriteta - blocked -> blocked (ne menja stanje)
	c) izvrsi test&set() funkciju - running -> running
	d) izvrsi exit funkciju - running -> exit (terminated)
	e) izvrsi monitor.produce() funkciju dok drugi proces izvrsava monitor.consume funkciju - running -> blocked
	
5. U koje stanje prelazi nit, a u koje proces kada se desi sledeci dogadjaj (objasni ukratko):
	a) ULT nit pozove f-ju write() (implementiran jacketing) - nit prelazi u blocked; ako ima vise niti u procesu proces ostaje u running a ako ima samo jedna nit prelazi u blocked
	b) KLT nit pozove sem_wait(1) - nit prelazi u blocked (jer se 1 smanjuje na 0); proces ostaje u running (kod KLT thread ne blokira proces)
	c) ULT nit kad se desi clock interrupt -  proces prelazi u ready (takva je rutina kod prekida clock-a); a nit ne menja stanje (jer stanje niti ne zavisi od procesa);
	d) KLT nit pozove funkciju exchange(b, k) - i nit i proces ostaju u running (exchange funckija nije blokirajuce jer je iz standardne biblioteke ili je korisnicka funkcija)
	e) ULT nit pozove funkciju fork() - nit ostaje u istom stanju; proces ostaje u running a novi proces je u ready stanje
	
6. U sistemu se izvrsava proces sa vise niti P(T1, T2). U koje stanje prelazi niti i koja se nit moze sledeca izvrsavati?
	a) Nit T1, pozove funkciju semWait() nad semaforom s=0, a niti su implementirane na nivou kernela (KLT) - *T1 se blokira jer s je sad -1, T2 se izvrsava i ako ona pozove semWait() i ona se blokira*
	b) Nit T2, pozove receive() funkciju, a niti su implementirane na nivou korisnika (ULT) - **