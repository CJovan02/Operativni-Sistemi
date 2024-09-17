
Najjednostavniji oblik politike casovnika zahteva da se svakom okviru pridruzi jedan dodatni bit, koji se zove bit koriscenja ili bit referenciranja (use bit).

Cim se stranica ucita neki okvir memorije, bit koriscenja za taj okvir se postavlja na vrednost 1.

Kad god se stranica kasnije referencira (posle reference koja je okinula gresku stranice), njen bit koriscenja se postavlja na vrednost 1.

Za algoritam zamenjivanja stranica, skup okvira koji su kandidati za zamenjivanje se smatra cirkularnim baferom sa pridruzenim pokazivanjem. Kada se neka stranica zameni, pokazivac se usmeri na okvir u baferu odmah posle upravo azuriranog okvira.

Kada dodje vreme da se neka stranica zameni, OS pretrazi bafer da bi pronasao okvir ciji je bit koriscenja jedna 0. Kad god naidje na okvir ciji je bit koriscenja jednak 1, on mu promeni taj bit na 0 i nastavi trazenje. Ako prvi okvir na koji pokazuje pokazivac ima bit 0 onda se stranicu u njemu odmah zamenjuje.