
## FIFO - First-In-First-Out

Posmatra okvire stranica dodeljene jednom procesu kao cirkularni bafer, a stranice se uklanjaju u stilu round robin. Zamenjuje se ona stranice koja je se najduze nalazi u memoriji: stranica koja je odavno doneta u memoriju mozda sada nije vise potrebna.
To razmisljanje ce cesto biti pogresno, jer se odredjeni resursi procesa cesto koriste i moraju stalno da budu u memoriji.

FIFO se lako implementira i ne opterecuje sistem.

**Za zadatke** se gleda red koji se uglavnom zove *"Vreme ucitavanja"* i bira se u sustini stranica koja najduze stoji u memoriji.