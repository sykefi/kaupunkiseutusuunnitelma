---
layout: "default"
description: "Tietomallin muutokset versiosta toiseen"
id: "muutosloki"
---
# Muutosloki
{:.no_toc}

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