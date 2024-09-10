
**POSIX Thread**

***pthread_t*** -> Tip promenljive koji se dodeljuje thread-u. U sustini to je ID za thread.

***int pthread_create(pthread_t *restrict tid, const pthread_attr_t 
    *restrict tattr, void*(*start_routine)(void *), void *restrict arg);*** -> tid je promenljiva koja pamti thread, start_routine je funkcija koju thread izvrsava, kada se ta funkcija zavrsi thread izlazi sa statusom koju vraca ta funkcija i terminise se. Kad pthread_create vrati 0 znaci je sve u redu, ako ne vraca neki od status kodova.

***int pthread_join(pthread_t tid, void status)*** -> blokira pozivajuci thread dok se thread sa *tid* ne terminise.