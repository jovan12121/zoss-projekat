# Konsenzus algoritmi

## Uvod

Konsenzus mehanizam je jezgro svakog blockchain sistema i važan pružalac garancije sigurnosti u sistemu. Ovim mehanizmom se postiže da se decentralizovan računarski sistem, čiji su učesnici raspoređeni po celom svetu, usaglase pri kreaciji blokova. Zbog visokog mrežnog delay-a u peer-to-peer mreži, red transakcija između različitih node-ova možda ne bude konzistentan. Zbog toga je potreban mehanizam kako bi se svi učesnici dogovorili o redu transakcija koje su se desile unutar sličnog vremenskog prozora. Za centralizaciju mreža različitih vrsta, nivoa i potreba, potrebne su različite strategije za implementaciju konsenzus algoritma kako bi se osigurala bezbednost. <br/> [[3]](https://iopscience.iop.org/article/10.1088/1742-6596/1437/1/012007/pdf)
Neki od algoritama su PoW (Proof of Work), PoS (Proof of Stake), DPOS (Delegated Proof of Stake), PBFT

### Proof of Work

Pri iskopavanju bloka korišteći PoW mehanizam, u odgovarajućoj heš vrednosti bloka, prvih N cifara mora biti 0. N je vrednost koja je zavisna od indeksa težine kopanja mreže, koji je i sam zavistan od količine računara u mreži koji trenutno kopaju. Da bi se dobila odgovarajuća heš vrednost bloka, potrebno je mnogo pokušaja heširanja, gde računar koji kopa, ukoliko rezultirajući heš ne odgovara, menja "nonce" vrednost koja ulazi u heš funkciju, pa zatim pokušava ponovo. Ukoliko uspe da pronađe takvu vrednost, koja kada bude heširana zajedno sa blokom i njegovim transakcija, rezultira u heš vrednost čijih je prvih N cifara zaista 0, to znači da je računar zaista morao da se potrudi, i računa vrednost dovoljan broj pokušaja. Ukoliko računar poseduje k% računarske moći unutar mreže računara, statistička verovatnoća da će baš on biti taj koji će pronaći odgovarajuću "nonce" vrednost je k/100. <br/>
Računar koji učestvuje u konsenzusu dobija novonastali nepotvrđen blok koji sadrži transakcijske vrednosti, i menja "nonce" vrednost unutar zaglavlja bloka dok ne pronađe takvu vrednost, koja kada se hešira dobije se vrednost manja od tražene. Kada takvu vrednost pronađe, blok se može raširiti eksterno, ostalim učesnicima u mreži, kako bi ga i oni verifikovali i potvrdili. Kada se uspešno doda na glavni lanac, odnosno blockchain, pronalazač "nonce" vrednosti dobija nagradu u vidu tokena, odnosno mrežne valute.
Blok možemo predstaviti kao skup tri elementa <b>B=(h', txs, nonce)</b>, gde je h' heš vrednost prethodnog bloka, a txs transakcijski rekordi unutar novog bloka, a nonce je 32-bitna vrednost.<br/>
Proces integracije PoW mehanizma u sistem digitalne valute:

1. Novonastala transakcija se emituje celoj mreži kopača
2. Svaki kopač sakuplja transakcije i pomoću njih konstruiše [Merkle stablo](blockchain.md#merkle-stablo)
3. Kopač koristi svoju računarsku moć kako bi pronašao odgovarajuću vrednost Nonce promenljive koja odgovara trenutnoj težini iskopavanja
4. Kopač pronalazi odgovarajuću vrednost, i emituje svim učesnicima mreže
5. Ostali učesnici verifikuju novonastali blok
6. Ukoliko su transakcije unutar bloka validne, heš bloka zadovoljava trenutnu težinu iskopavanja, i lista transakcija u bloku je najduža među svim "forkovima" mreže, nemaliciozni učesnici mreže će konstruisati sledeći blok nakon ovog.

#### Prednosti

1. Visok nivo decentralizacije. Algoritam je jednostavan i lak za implementaciju, pridruživanje novih nodova sistemu je jednostavan
2. Visok nivo bezbednosti. Narušavanje sistema zahteva veliku investiciju.
3. Poverenje. Izbor kreatora bloka se rešava tako što nodovi rešavaju heš funkcije. Finalni proces generisanja i verifikacije konsenzusa je čisto matematički problem. Mreža se može uskladiti i postići konsenzus bez potrebe za razmenjivanjem dodatnih informacija. U celom procesu, nije potrebna ljudska uključenost.

#### Mane

1. Dugačko vreme potvrde bloka. Kako bi se sigurno obezbedio nivo decentralizacije, vreme potvrde bloka je izazovno i teško svesti i skratiti.
2. Trošenje resursa. Računarska moć se troši u trci između kopača u mreži, gde će samo jedan uspeti da pronađe odgovarajuću vrednost.

### PoS in detail

### DPOS in detail

### tabelarno poredjenje i razlozi
