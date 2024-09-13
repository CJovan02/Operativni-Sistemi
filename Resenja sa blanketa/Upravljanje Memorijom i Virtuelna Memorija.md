
1. Operativni sistem implementira segmentaciju sa stranicenjem i virtuelni adresni prostor procesa od maksimalno **128** segmenata, svaki segment ima maksimalno **2^12** stranica od **2KB**. Koji je format virtuelne adrese i koliki je maksimalni adresi prostor procesa u bajtovima.

Za adresiranje segmenta su nam potrebna 7 bitova => 2^7 = 128
Za adresiranje stranica nam je potrebno 12 bitova
Za pomeraj nam je potrebno 11 bita => 2KB = 2 * 2^10 = 2^11 

Adresni prostor izgleda ovako:

| Segment | Stranica | Pomeraj |
| ------- | -------- | ------- |
| 7 bita  | 12 bita  | 11 bita |
Jedan segment zadrsi 2^12 stranica od po 2^11 bajtova, pa onda dobijamo sledece:
2^7 * 2^12 * 2^11 B = 2^30 B = 1GB.

**Maksimalni adresni prostor je 1GB.**

2. Operativni sistem implementira **segmentaciju sa stranicenjem** i virtuelni adresni prostor procesa od maksimalno **1024** segmenata, svaki segment ima maksimalno **2^13 stranica od 2KB**, smesta se u fizicku memoriju od **2^25 stranicnih okvira**.

| Segment | Stranica | Pomeraj |
| ------- | -------- | ------- |
| 10 bita | 13 bita  | 11 bita 
2^10 * 2^13 * 2^11 = 2^34 B = 2^4 GB = **16GB**
a) Koliko stavki ima u tabeli segmenata za svaki proces -> ***Svakom procesu je pridruzena vlasitita tabela segmenta**, sto znaci da broj stavki u tabeli segmenta zavisi od toga koliko segmenta svaki proces zauzima u memoriji*
b) Koliko bajtova je stranicnom okviru -> *Velicina stranice je ista kao i velicina okvira, 2KB*
c) Koji je format virtuelne adrese i koliko je maksimalni adresni prostor procesa u bajtovima -> *Format je dat u tabeli a velicina adresnog prostora je 16GB*
d) Koliko stavki je u tabeli stranica -> *2^13 jer svaki segment sadrzi svoju tabelu stranica a tabela stranica pokazuje kom okviru pripada koja stranica*
e) Koliko bitova je u svakoj stavci tabele stranica -> *25 bitova, jer imamo 2^25 okvira, za adresiranje stranica plus kontrolni bitovi (ne znam koliko ih ima u knjizi se spominju P (Present) i M (Modified)), tako da bi bilo minimalno 27 bitova je u svakoj stavci*

3. Nacrtati format virtuelne adrese u sistemu koji implementira segmentaciju sa stranicenjem u tri nivoa, ukoliko proces moze imate maksimalno **256 segmenta**, velicine stranice je **8Kb**, a stavka u tabeli stranice je **4B**.

256 = 2^8 
8KB/4B = 2K = 2^11 
8K = 2^10 * 2^3 = 2^13 

| Segment | Prvi Nivo | Drugi Nivo | Treci Nivo | Pomeraj |
| ------- | --------- | ---------- | ---------- | ------- |
| 7 bita  | 11        | 11         | 11         | 13      |
