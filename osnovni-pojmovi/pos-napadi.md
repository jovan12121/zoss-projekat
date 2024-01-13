## Napadi na proof of stake

Jedan od glavnih prioriteta blockchain-a je sigurnost i očekivano je da će se svaki sistem suočiti sa napadima koji će pokušati da kompromituju koncenzus i ukradu sredstva od korisnika.<br/>

### [Double spend](#double-spending)

Double spend(duplo trošenje) je jedan od problema koji blockchain tehnlogije pokušavaju da reše od njihovog nastanka.Većina(ako ne i svi) napadi pokušavaju da iskoriste duplo trošenje u nekom trenutku izvršavanja. U ovakvim napadima napadač pokušava da potroši istu količinu sredstava 2 ili više puta. Napadač pokušava da izvrši transakciju, sačeka drugu stranu da potvrdi da je transakcija uspešna, a zatim je poništi i pokuša da potroši ta ista sredstva u drugoj transakciji .<br/>

### [Sybil](/napadi/sybil.md)

U sybil napadu napadač koristi više identita kako bi poremetio odluke u mreži. U blockchain-u ovo može izazvati razne probleme kao što su završavanje bloka, grananje blockchain-a, odabir validatora,itd. U PoW sistemima napadač bi morao posedovati različite identite sa dovoljnom računarskom snagom da bi imao uticaj na sistem. Protokol za postizanje koncenzusa pobija ovaj argument jer raspoređivanjem svojih računarskih resursa napadač ne bi povećao svoju računarsku moć. Umesto toga računarska moć napadača bi ostala ista. Slično tome, u PoS sistemima, napadača direktno sprečava protokol za postizanje koncenzusa. Proces izbora validatora i "glasačka moć" su srazmerni veličinom uloga kog napadač poseduje, te bi napadač imao istu "glasačku moć" i sa jednim i sa više identiteta.<br/>

### Bribery napad

Bribery napad(short-range napad) se oslanja na podmićivanje validatora da rade na određenim blokovima ili granama. Time napadač može predstaviti proizvoljne transakcije validnim i platiti onda nepoštenim validatorima da ih potvrde. Plaćanjem jednakog ili većeg iznosa od nagrada za validaciju bloka(u slučaju da mreža poništi blok), pruža dovoljan podsticaj validatorima da rade za njega.<br/>

### [Liveness attack](/napadi/liveness-attack.md)

Liveness denial je forma Denial of Service napada u PoS sistemima. U ovakvom napadu, neki ili svi validatori namerno blokiraju transakcije tako što prestanu da objavljuju blokove. Time će doći do zastoja u blockchain-u, jer time prestaje validiranje novih blokova i oni neće biti objavljeni u blockchain-u.<br/>

### [51% napad](/napadi/51%25-napad.md)

51% napadi su pretnja svakom koncenzus protokolu. U PoW sistemima entitet koji ima većinu računarske moći u sistemu može preuzeti kontrolu nad celim sistemom. U PoS sistemima ovaj napada je idalje moguć ali uz drugačije posledice. Moguće je da jedan validator ili skup validatora imaju deo koji je veći od 51%(ako je u pitanju BFT PoS 34%), u tom slučaju napadač može kontrolisati odabir novih blokova, odobravanje transakcija ili čak pokušaj manipulacije istorijom blockchain-a.<br/>

### Cenzorship(cenzura)

Cenzura u blockchain-u je zanimljiv problem je jer može biti posmatrana kao mana sistema ili kao prednost sistema. Validatori imaju kontrolu nad izborom transakcija koje će biti dodate u blok, što im daje mogućnost da određene transakcije ignorišu. Ako jedan validator vrši cenzuru neke transakcije mogu biti odložene ili poništene zbog vremenskih ograničenja. Opasnost postaje veća ako se više validatora bavi cenzurom.<br/>

### [Nothing At Stake](/napadi/nothing-at-stake.md)

U PoS sistemima validatori obično moraju "zaključati" određenu količinu kripto valute da bi učestvovali u procesu kreiranja blokova i validacije. Ako validatori nemaju šta da izgube(nothing to lose), to znači da se mogu ponašati maliciozno bez suočavanja sa značajnim finansijskim posledicama i to može predstavljati pretnju za sigurnost blockchain-a.

### [Long-range napadi](/napadi/Long-range%20napadi.md)

Long-range napadi su napadi gde napadač ide do početnog bloka(genesis block) i pravi nova grananja blockchain-a. Nova grana obično biva popunjena delimično ili potpuno drugačijom istorijom u odnosu na glavni lanac. Napad uspeva kada grana koja je napravljena od strane napadača postane glavna grana u blockchain-u. Long-range napadi mogu biti: jednostavni, posterior corruption i stake bleeding [[7]](https://sci-hub.se/10.1109/access.2019.2901858).

### [Kvantni napad](/napadi/kvantni-napad.md)

Kvantni napad je napad koji koristi kvantne računare za rešavanje složenih matematičkih problema koji se koriste za šifrovanje podataka, i koji te probleme rešavaju znajačno brže od običnih računara. Uz primenu određenih algoritama mogu efikasno rešavati probleme pretrage i faktorizacije, što ugrožava sigurnost PoS sistema.

### [Napadi iscrpljivanja resursa](/napadi/napadi-iscrpljivanja-resursa.md)

Napad iscrpljivanja resursa iskorištava proces validacije PoS blokova, i dovodi do preopterećenja resursa na sistemu žrtve. Napad može prouzrokovati pad sistema, degradaciju performansi i novčane gubitke, a takođe može biti iskorišten i za neke složenije napade.

### [Short selling napad](/napadi/short-selling-napad.md)
Napad skraćivanjem ili shorting je složena strategija koja se koristi za manipulaciju tržištem kriptovaluta. Napadač prvo preuzima kontrolu nad značajnim delom uloga u PoS sistemu, zatim prodaje kriptovalutu po višoj ceni. Nakon toga sabotira sistem, dovodeći do pada vrednosti valute. Kada vrednost valute dovoljno opadne, napadač otkupljuje nazad valute po boljoj ceni i na taj način uspešno izvršava svoj napad.
