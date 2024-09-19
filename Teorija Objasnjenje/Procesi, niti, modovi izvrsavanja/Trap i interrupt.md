
Postoje dve vrsite sistemskih prekida, trap i interrupt

Interrupt potice on neke vrste dogadjaja koji je nezavisan i izvan procesa koji se trenutno izvrsava, kao sto je zavrsetak neke U/I operacije.
Kada nastane kontrola se prebacuje hendleru pa se onda prebacaju u OS rutina. Primeri mogu biti:
- Vremenski prekid
- U/I Prekid
- Memorijska greska

Trap se odnosi na stanje greske ili izuzetka generisanog unutar procesa koji se trenutno izvrsava, kao sto je pokusaj nedozvoljevog pristupa fajlu.
Kada se desi OS utvrdjuje da li je to stanje greske ili izuzetka fatalno. Ako jeste, proces koji se trenutno izvrsava se prebvacuje u stanje *Zavrsen* i nastupa zamenjivanje procesa. U suprotom, akcija OS-a ce zavisiti od prirode greske i od dizajna OS-a. On moze da pokusa neki postupak oporavka, ili da jednostavno obavesti korisnika. On moze da izvrsi zamenjivanje procesa, ili da nastavi proces koji se trenutno izvrsava