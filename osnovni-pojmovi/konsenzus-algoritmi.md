# Konsenzus algoritmi

## Uvod

Značenje reči konsenzus je postizanje dogovora. U konteksu blockchain mreža, ovo znači da se svi računari u mreži slože oko prihvatanja podataka kao tačnih, odnosno prihvatanje i dodavanje novoiskopanog bloka u već postojeći niz blokova.
Konsenzus mehanizam je jezgro svakog blockchain sistema i važan pružalac garancije sigurnosti u sistemu. Ovim mehanizmom se postiže da se decentralizovan računarski sistem, čiji su učesnici raspoređeni po celom svetu, usaglase pri kreaciji blokova. Zbog visokog mrežnog delay-a u peer-to-peer mreži, red transakcija između različitih node-ova možda ne bude konzistentan. Zbog toga je potreban mehanizam kako bi se svi učesnici dogovorili o redu transakcija koje su se desile unutar sličnog vremenskog prozora. Za centralizaciju mreža različitih vrsta, nivoa i potreba, potrebne su različite strategije za implementaciju konsenzus algoritma kako bi se osigurala bezbednost. <br/> [[3]](https://iopscience.iop.org/article/10.1088/1742-6596/1437/1/012007/pdf)
Neki od algoritama su PoW (Proof of Work), PoS (Proof of Stake), DPOS (Delegated Proof of Stake), PBFT

## Proof of Work

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
3. Povećavanjem količine računarske moći povećava se verovatnoća pobede u trci za iskopavanjem novog bloka, što može dovesti do centralizacije i kontrole nad mrežom. Pogotovo kada se node-ovi udruže zajedno u mining pool. Ukoliko bi se potom više mining pool-ova udružilo, i posedovalo 51% računarske moći mreže, definitivno bi mogli da je kontrolišu i dozvole maliciozne transakcije. Ovo se zove 51% napad.

## Proof of Stake

Zbog specifične strukture podataka i arhitekture blockchain sistema, proces postizanja konsenzusa se može predstaviti kao mehanizam izbora lidera, gde se nasumično bira lider, odnosno računar koja generiše novi blok, i time se izbegava situacija gde jedna osoba ili mašina dugoročno kontroliše blockchain, i podatke u njemu, što je i cilj decentralizacije. Razvijanjem blockchain sistema, primećeno je da Proof of Work konsenzus mehanizam ima odgovarajuće nedostatke. Prvi od njih je potrošnja nepotrebne energije. To je čak dovelo i do toga da se pojedina postrojenja za kopanje grade pored hidroelektrana kako bi se potrošnja svela na minimum. Osim toga, bezbednost takvog mehanizma nije toliko visoka koliko je prvobitno zamišljena. U teoriji, postoje napadi koji mogu postići da maliciozni učesnik kontroliše blockchain podatke, bez potvrde 51% korisnika mreže.

#### Staking

Pod ovim terminom podrazumevamo da je korisnik PoS mreže svoja sredstva, odnosno tokene založio u zajednički fond (stake pool), i tamo ih čuva duži vremenski period u zamenu za nagradu (u valuti koju je založio), ukoliko je on ili neko iz tog pool-a izabran da validira blok. U daljem tekstu će ovaj proces biti detaljnije objašnjen.

#### Implementacija

PoS zamenjuje PoW-ovo takmičenje za pronalazak bloka tako što nasumično izabira učesnika koji je svoja sredstva založio u neki "stake pool", da bude onaj koji validira i kreira novi blok koji se dodaje na blockchain. Korisnika koji je izabran da kreira novi blok, nazivamo validator. Najjednostavija implementacija ovoga je poznata kao Follow-the-Satoshi (FTS) algoritam[6](https://www.researchgate.net/profile/Fahad-Saleh/publication/325891130_Blockchain_Without_Waste_Proof-of-Stake/links/60998115a6fdccaebd208b08/Blockchain-Without-Waste-Proof-of-Stake.pdf).

##### Follow the Satoshi

- FTS algoritam deli vreme u diskretne periode koji se nazivaju slotovi. Algoritam nemeće pravilo da se u okviru jednog slota ne može iskopati više od jednog bloka. U bitcoin mreži, najmanja moguća novčana jedinica se zove Satoshi. FTS je algoritam koji izabira neku najmanju moguću vrednost K iz založenih (stake-ovanih) sredstava, potpuno nasumično. Kada se izabere ta vrednost, vlasnik vrednosti K, odnosno učesnik mreže u čijem novčaniku se nalazi K postaje lider slota i validator, i može da sluša sve transakcije koje ostali učesnici objavljuju, napravi blok od tih transakcija, potpiše ih svojim tajnim ključem i objavi taj blok ostatku mreže. Naravno, to ne čini vlasnik novčanika ručno, već njegov računar, koji je node na mreži. Taj korisnik, kao validator, dobija nagradu za novokreirani blok, koja se uglavnom delom sastoji od novokreiranih tokena, a delom od naknada za transakcije u mreži.
  FTS struktura dovodi do toga da je verovatnoća da će učesnik mreže biti izabran da iskopa blok jednaka proporciji količine ukupog broja svih tokena u mreži i tokena koju korisnik poseduje. Ukoliko korisnik A poseduje 8 tokena, a u cirkulaciji mreže postoji 10 tokena, verovatnoća da će korisnik A biti izabran za validatora je 8/10 = 80%.<br/>

Kako bi se osiguralo da validator ne bude maliciozan i lažira transakcije, zalog mora biti veći od nagrade. Ukoli bi bio maliciozan, mogao bi da izgubi zalog. Ukoliko node želi da prestane da bude validator, sredstva i nagrade će biti oslobođeni posle određenog vremenskog perioda, tek kada mreža bude sigurna da node nije validirao maliciozne transakcije.

#### Prednosti

1. Energetska efikasnost. Nema nepotrebne potrošnje računarske mreže kao u PoW.
2. Lako priključivanje Node-a mreži. Pošto računarska moć ne igra ulogu, gotovo svaki računar može biti node na mreži. Zanemarljiva cena kopanja daje svakome podjednaku šansu. U PoW, ukoliko bi neko imao pristup jeftinoj ili besplatnoj opremi i struji, imao bi veliku prednost nad ostalim kopačima.
3. Veoma je teško ostvariti 51% napad, pošto bi maliciozni pool morao posedovati 51% svih tokena u cirkulaciji na mreži, a ne 51% ukupne računarske moći kao u PoW.

#### Mane

1. Bezbednost. Pošto se svako može priključiti mreži i dobiti šansu da bude validator, ukoliko bi se napravio bezbednosni propust u implementaciji, maliciozni korisnik bi veoma lako mogao da ga iskoristi bez potrebe za skupom opremom.
2. Skalabilnost mreže. PoS je često kritikovan zbog skalabilnosti, jer često mehanizmi nisu dovoljno efikasni pri velikom broju transakcija, pa nekad PoS može imati sporije vreme procesiranja, a skuplje naknade za procesuiranu transakciju.

