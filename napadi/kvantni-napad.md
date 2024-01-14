## Kvantni napad [[10]](https://sci-hub.se/https://ieeexplore.ieee.org/abstract/document/9068181)

Kvantni napad se izvršava korišćenjem kvantnog računara za rešavanje složenih matematičkih problema koji se koriste za šifrovanje podataka. Odnosno, ovi problemi su napravljeni tako da su izuzetno teški za rešavanje sa klasičnim računarima, dok bi kvantni računari mogli da ih reše za nekoliko sekundi. Za razliku od klasičnih računara, kvantni računari koriste kvantne bitove ili qubite. Zbog, potpuno različite arhitekture, kvantni bitovi mogu koristiti kvantno-mehaničke pojave kao što su superpozicija i povezanost. Kvantni sistem koji sadrži N qubite-a može generisati do  $2^N$ kvantnih stanja koristeći superpoziciju i izvoditi operacije na svim stanjima istovremeno. Dok klasični pandan može raditi samo na jednom stanju u jednom trenutku. Samim tim, kvantni računar je eksponencijalno brži od klasičnih. 

Kao što je poznato, u PoS sistemu, određeni broj kriptovaluta se zaključava, staking, kao ulog za održavanje mreže i tokom stakinga javni ključ korisnika se otkriva, što može dovesti do problema. Kvantni računari bi mogli da iskoriste ovu ranjivost, i da putem javnog ključa izračunaju privatni ključ korisnika i samim tim pristupe kriptovalutama korisnika, što predstavlja rizik za sigurnost PoS sistema.

### Kvantni algoritmi

Groverov i Shorov algoritam su dva poznata kvantna algoritma koja se mogu koristiti za izvođenje kvantnih napada. <br/> <br/>
Groverov algoritam za pretragu pruža kvadratno ubrzanje u odnosu na poznate klasične algoritme, odnosno može se koristiti za brzu pretragu nesortirane baze podataka. On pruža bržu pretragu upita protiv kriptografskih hash funkcija, koje se koriste za generisanje adresa za kriptovalute i za obezbeđivanje sigurnosti transakcija i blokova u blockchainu.<br/><br/>
Shorov algoritam efikasno rešava probleme diskretnog logaritma i faktorizacije, koji predstavljaju dva problema na kojima se zasnivaju mnogi kriptografski sistemi. Ako bi napadač mogao da faktoriše javni ključ validatora, mogao bi potencijalno da preuzme kontrolu nad ulogom i manipuliše blockchainom.<br/><br/>
Bitno je napomenuti da su algoritmi inherentno probablistički, sto znači da njihovi rezultati neće uvek biti isti svaki put kada se izvrše. 

### Mitigacije

Što se dizajna sistema tiče postoji nekoliko načina za zaštitu:
- Kako simetrična kriptografija koristi isti ključ za šifrovanje i dešifrovanje podataka, da bi se zaštitili od napada Groverovog algoritmom, koji može potencijalno da prepolovi broj koraka potrebnih za pronalaženje ključa u odnosu na klasične metode, dovoljno je da se veličina ključa udvostruči kako bi se održao isti nivo sigurnosti. Što se tiče hash funkcija, udvostručavanje bitova hash izlaza je protivmera.
- Upotreba adrese umesto javnog ključa je jedna od opcija. Deljenje javnog ključa može potencijalno da omogući kvantnim napadima da izračunaju odgovarajući privatni ključ. Adresa je heširana verzija javnog ključa, i ukoliko neko i ima adresu, ne može tako lako da izračuna javni ključ koji je korišten za generisanje adrese. 
- Sprečavanje korišćenja iste adrese je jedna od mera zaštite kako od kvantnih napada, tako i od drugih. Upotreba iste adrese za više transakcija, otkriva javni ključ koji je povezan sa tom adresom i ugrožava sigurnost sredstava povezanih sa tom adresom.
- Razmatranje nove šeme digitalnih potpisa. Postkvantna kriptografija se ubrzano razvija i može zameniti postojeće šeme potpisa koje su ranjive na kvantne napade. One su kategorisane u multivarijantne, rešetkaste, hash-bazirane, kod-bazirane i supersingularne eliptične krive.
