
## Feedback - Povratna Sprega

U sustini isti je kao [[Round Robin]] medjutim koriste se **vise redova cekanja**

Kada proces prvi put dodje u sistem on se stavlja u **red najviseg prioriteta**, zatim, kada istekne njegov kvantum on se vraca nazad u red cekanja ali u **red sa manjim prioritetom** i tako svaki put kada on ne stigne za njegov kvantum da zavrsi posao pomera se u red sa manjim prioritetom.

Postoje dve verzije, jedan sa **fiksnim kvantumom** a drugi sa kvantumom u **zavisnosti od toga u kom redu se nalazi proces** (2^i, gde je *i* indeks reda cekanja).

![[Primer iz knjige vrednosti.png]]

![[Feedback.png]]