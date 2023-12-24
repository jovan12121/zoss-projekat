## Sybil attack

#### Šta je Sybil

Sybil je sigurnosna pretnja pri kojoj maliciozni korisnik kontroliše nekoliko node-ova unutar mreže, i ostvaruje disproporcionalan uticaj. Ovaj napad je dobio ime po karakteru Sybil Dorsett-u iz knjige "Sybil", koji je imao poremećaj višestruke ličnosti.
U kontekstu blockchain-a i PoS mehanizma, Sybil napad podrazumeva da napadač kreikra veliki broj pseudonimnih identiteta kako bi zadobio veliku prisutnost u mreži. Cilj je kompromizacija integriteta sistema kontrolisanjem značajnog dela mreže i potencijalna manipulacija transakcija ili dostizanje konsenzusa.
U PoS, nodovi se biraju kako bi kreirali nove blokove i validirali transakcije, bazirano na količini valute koji su spremni da založe kao kolateral. Sybil napadač bi mogao da kreira veliki broj lažnih identiteta, kako bi zadobio većinu stake-a, što bi mu omogućilo da kontroliše konsenzus proces.

#### PoS i Sybil

Od prve implementacije, PoS je evoluirao u različite forme. Iako se konstantno pojavljuju novi PoS algoritmi, ključ koncepta koji dozvoljava mehanizmu da spreči Sybil napade ostaje isti. U mnogim PoS mrežama, količina moći korisnika proporcionalna je njegovom udelu u kapitalu celog sistema.
Pošto je Sybil zaista kritična pretnja, PoS sistemi se oslanjaju na distribuciju i povećan nivo verifikacije node-ova kako bi se zaštitili.
Distribuiranje sredstava jedan je od načina kako bi se sprečio pokušaj Sybil napada, pošto je u sistemu sa dobrom distribucijom tokena i moći, takav napad teže izršiti.

##### Primer

Recimo da je u P2P mreži prisutno nekoliko node-ova. Iskrene, odnosno nemaliciozne node-ove ćemo nazvati node H. Sybil node-ove ćemo nazvati S, a napadački node ćemo nazvati A. Kako bi se inicirao napad, napadač mora kreirati nekolicinu S node-ova i povezati ih sa H node-om, tako da H node-ovi oslabe procenat svojih pravih, ispravih konekcija sa ostalim H node-ovima. Napadač A ovim dolazi do disproporcionalno velikog uticaja u mreži. Algoritam napada bi izgledao ovako

```
H ← Nemaliciozni node-ovi;
S ← Sybil node-ovi;
A ← Napadački node;
while (true) do
    A Kreira S;
    A Povezuje S sa H;
    A Dobija frakciju sistema ← Δ;
    if (Δ == true) then
        A Koristi metod napada;
        A Aktivira pretnju;
        A Narušava integritet i reputaciju sistema;
    end
end
```

### Zaštita

Distribuiranje tokena u početnoj fazi mreže svakako predstavlja izazov u PoS mreži. PoS po svojoj prirodi, zahteva početnu, unapred pripremljenu distribuciju izvornih tokena, za razliku od PoW, za koji nije potrebna značajna distribucija[[13]]. Ta distribucija služi upravo kako bi se distribuirala i moć unutar P2P PoS mreže, i ograničila šansa za ovakav i slične napade. Osim toga, poznati su još neki vidovi zaštite.

#### 1. Staking uslov

Sistem zahteva node-ove da založe neku minimalnu količinu izvorne valude kao kolateral kako bi učestvovali u konsenzus procesu. Ovo čini napad skupim, i zahteva da napadač izdvoji pozamašnu sumu kako bi kreirao veliki broj lažnih i neiskrenih node-ova

#### 2. Reputacioni sistem

Neki sistemi implementiraju mehanizam reputacije kako bi identifikovali i kaznili maliciozne node-ove. Kažnjavanje može podrazumevati oduzimanje celog ili dela založenog kolaterala.

#### 3. Verifikacija identiteta

Neki sistemi implementiraju verifikaciju identiteta kako bi se osigurali da svaki identitet korespondira pravom korisniku. Ovo je otežavajuća okolnost za napadača koji pravi nekoliko identiteta

#### 4. Randomizacija

Često se koristi funkcija nasumičnog odabira validatora za kreiranje blokova. Ovim činom napadaču postaje teže da da predvidi koji će node biti odabran, ali ipak povećanom količinom svojih, malicioznih node-ova, ipak može povećati svoje šanse.
