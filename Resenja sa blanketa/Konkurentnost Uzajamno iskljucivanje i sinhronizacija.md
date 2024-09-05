
**Napomena:** u knjizi se ovo zove *Medjusobno iskljucivanje*
Medjusobno iskljucivanje - *Mutual Exclusion*

[[Pthread Library]]

1. ![[Semafori zad1.png]]
	1. Kreiramo globalnu promenljivu *semaphore*
	2. U main programu semafor inicijalizujemo na 0
	3. Iznad linije gde pise *glob_data = 10* u main programu dodamo *semWait(semaphore)* sto ce blokirati glavni thread.
	4. Na kraju funkcije *kidfunc* dodamo *semSignal(semaphore)* koja ce odblokirati main thread nakon sto upise 10 u glob_data