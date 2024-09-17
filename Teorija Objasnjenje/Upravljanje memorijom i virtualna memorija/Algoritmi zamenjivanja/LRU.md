
## LRU - Least Recently Used

**Ova politika zamenjuje onu stranicu u memoriji koja je u najduzem periodu nije referencirana.** 

Po principu lokalnosti, to bi trebalo da bude stranica sa najmanjom verovatnocom da bude referenciraan u bliskoj buducnosti.

Ovo je jako efektivan algoritam ali je problem sto se tesko implementira i opterecuje dosta sistem. Zbog ovoga je implementiran drugi algoritam koji bi trebao da uzme u obzir stranice koje se cesto koriste ([[FIFO]] ne uzima u obzir ovaj podatak) a da ne opterecuje sistem previse. Radi se o [[Clock]] algoritmu.

**Za zadatke** se gleda red sa nazivom *"Vreme referenciranja"* i trazi se stranica sa najmanjom vrednoscu.