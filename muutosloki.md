---
layout: "default"
description: "Tietomallin muutokset versiosta toiseen"
id: "muutosloki"
---
# Muutosloki
{:.no_toc}


## 21.10.2002

* Lisätty käsitemalli-sivulle käsitteet kehittämisperiaate, toiminnon infrastruktuurilaji, toiminnon kehittämisperiaate, toiminnon toimintolaji. Siirretty kehittämistoimenpide ja toimenpiteen toteutusaikataulu seurannan käsitteiden alle. Ydinkäsitteiden kaavio päiviteytty vastaamaan kehitysprojektin lopullista, UML-malln kanssa yhdenmukaista käsitemallia. Looginen malli / dokumentaatio -sivu muutettu tilaan Ehdotus.   

## 12.10.2022

* Täydennetty dokumentaatiosivun koodistoluokkien linkit Yhteentoimivuusalustan koodistoihin.
* Poistettu tarpeettomaksi jäänyt koodistoluokka ToimenpiteenLaji.

## 28.9.2022

* Lisätty attribuutti Kehittämisperiaate.nimi.
* Lisätty uusi koodisto-luokka MitoitussuureenLaji.
* Poistettu luokka SuunniteltuToimenpide.
* Muutettu KohteenToiminto stereotyyppi DataType -> FeatureType, periytyy nyt VersioituKohde-luokasta.
* Lisätty attribuutti KohteenToiminto.nimi.
* Lisätty attribuutti KohteenToiminto.kuvaus.
* Poistettu attribuutti SuunnitelmanKohde.toiminto, korvattu kompositioassosiaatiolla luokkaan KohteenToiminto. Vähintään yksi KohteenToiminto on pakollinen kullekin SuunnitelmanKohteelle.
* Muutettu yksisuuntainen assosiaatio KohteenToiminto.kehittämisperiaate:ToiminnonKehittämisperiaate kaksisuuntaiseksi: Yksi ToiminnonKehittämisperiaate voi liittyä moneen KohteenToimintoon (ja sitä kautta moneen SuunnitelmanKohteeseen).
* Muutettu yksisuuntainen assosiaatio KohteenToiminto.toiminnonTavoite kaksisuuntaiseksi (liittyväToiminto-liittyväTavoite).
* Poistettu virheellinen kohdistus-assosiaatioon liittynyt rajoitus Kehittämisperiaate-luokasta (ei periytynyt enää Tietoyksikkö-luokasta).
* Lisätty attribuutti Mittari.nimi.


## 15.9.2022

* Lisätty koodisto-luokka SelostuksenOsanLaji.
* Muutettu attribuutin KohteenToiminto.elinkaarimuutoksenTyyppi 1 -> 0..1 (ei enää pakollinen)
* Korjattu dokumentaatiossa TavoitteenLähteenLaji-koodiston laajennettavuustieto Ei laajennettavissa -> Laajennettavissa kaikilla tasoilla.

## 12.9.2022

* Poistettu YleinenKehittämisperiaate.laji ja sen koodisto YleisenKehittämisperiaatteenLaji.

## 9.9.2022

* Kehittämisperiaate muutettu abstraktiksi ja jaettu kahteen konkreettiseen luokkaan YleinenKehittämisperiaate ja ToiminnonKehittämisperiaate. Kaupunkiseutusuunnitelma liittyy suoraan vain YleiseenKehittämisperiaatteeseen, ja KohteenToiminto vain ToiminnonKehittämisperiaatteeseen.
* Lisätty uusi attribuutti Toiminnonkehittämisperiaate.merkittävyys: KehittämisperiaatteenMerkittävyys.
* Lisätty uusi assosiaatio SuunniteltuToimenpide.toimenpiteenTavoite:Tavoite
* Lisätty uusi attribuutti KohteenToiminto.infrastruktuurilaji.
* Lisätty uusi attribuutti teema:KaupunkiseutusuunnittelunTeema luokkiin KohteenToiminto, SuunniteltuToimenpide ja SeudullinenTietoaineisto.
* Lisätty kahdensuuntainen assosiaatio (toteuttavaPeriaate-toteutettavaPeriaate) YleisenKehittämisperiaatteen ja ToiminnonKehittämisperiaatteen välille.
* Lisätty uusi assosiaatio Kehittämisperiaate.hyväksyjä:Toimija
* Lisätty uusi assosiaatio Tavoite.asettaja:Toimija
* Lisätty uusi assosiaatio SuunniteltuToimenpide.hyväksyjä:Toimija
* Muutettu Kaupunkiseutusuunnitelma.laatija-assosiaation kohde Organisaatio -> Toimija.
* Lisätty rajoitus, joka kieltää Suunnitelmakohde.pystysuuntainenRajaus-attribuutin käytön.


## 7.9.2022

* Poistettu Toimintokohde ja Kehittämisvyöhyke, muutettu niiden yhteinen yläluokka Suunnitelmakohde takaisin ei-abstraktiksi. Toimintokohde-luokan attribuutit toiminto ja elinkaaritila on siirretty takaisin Suunnitelmakohde-luokkaan.
* KohteenToiminto-luokkaan lisätty uusi attribuutti infrastruktuurilaji ja sille koodisto Infrastruktuurilaji.
* KohteenToiminto.toimintolaji ei enää ole pakollinen.
* Lisätty assosiaatiot kohdistettuPeriaate ja kohdistettuTavoite. Nämä ovat nyt ainoa tapa yhdistää kehittämisperiaatteet ja tavoitteet (toimintojen kautta) suunnitelmakohteisiin.
* Lisätty uusi attribuutti Suunnitelmakohde.kehittämisenOhjelmointi:SuunniteltuToimenpide ja uusi DataType-luokka SuunniteltuToimenpide.
* Poistettu assosiaatio Suunnitelmakohde.kohdistettuToimenpide -> Kehittämistoimenpide ja Suunnitelmakohde.liittyväTavoite -> Tavoite.
* Muutettu Kehittämistoimenpide-luokan nimeksi Kehittämisperiaate, ja lisätty attribuutti laji:KehittämisperiaatteenLaji.
* Kielletty kohdistus-assosiaation käyttö Kehittämisperiaate- ja Tavoite-luokilta (rajoitus).

## 31.8.2022

* Lisätty käsitemallin kuvaus, tarkennettu loogisen tietomallin kuvausta.

## 30.8.2022

* Lisätty uudet luokat Toimintokohde ja Kehittämisvyöhyke, muutettu niiden yhteinen yläluokka Suunnitelmakohde abstraktiksi. Suunnitelmakohde-luokan attribuutit toiminto, sijainninTulkintatapa, kohteenLaji ja elinkaaritila on siirretty Toimintokohde-luokkaan.
* Poistettu Muutosajuri-luokka kokonaan, käsite toteutuu kuvaamalla muutosajurit selostuksessa.
* Luotu uusi luokka Vuorovaikutussuunnitelma korvaamaan OsallistumisJaArviointisuunnitelma-luokan, sama tietosisältö, eri määritelmä. Attribuutti Kaupunkiseutusuunnitelma.osallistumisJaArviointisuunnitelma uudelleennimetty vuorovaikutussuunnitelma-nimiseksi.
* Poistettu assosiaatio Kaupunkiseutusuunnitelma.osallinen tarpeettomana.
* Korjattu Kehittämistoimenpide- ja Tavoite-luokkien Suunnittelukohde-luokkaan liitetyt rajoitukset Suunnitelmakohde-luokkaan. 
* Tuotettu tekstimuotoinen UML-luokkien dokumentaatio.

## 22.6.2022

* Uudelleennimetty Suunnittelukohde -> Suunnitelmakohde. Neutraali kohteen kehittämisen osalta.
* Uudelleennimetty koodisto SuunnittelukohteenLaji -> KohteenLaji
* Lisätty kahdensuuntainen assosiaatio KaupunkiseudunMuutosajuri <-> Tavoite
* Lisätty kahdensuuntainen assosiaatio KaupunkiseudunMuutosajuri <-> Kehittämistoimenpide

## 10.6.2022

* Korvattu OsallistumisJaArviointisuunnitelma-luokka Yhteiset tietokomponentit -paketin samalla luokalla