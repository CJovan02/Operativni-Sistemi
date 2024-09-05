**cwait(c)** - Suspenduje izvrsavanje pozivajuceg procesa za uslov c. Monitor je sada dostupan da ga koristi drugi proces.

**csignal(c)** - *Nastavlja izvrsavanje nekog procesa blokiranog posle cwait za isti uslov. Ako ima nekoliko takvih procesa, bira jedan od njih; ako nema takvih procesa, ne radi nista.*