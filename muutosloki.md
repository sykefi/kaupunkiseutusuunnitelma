---
layout: "default"
description: "Tietomallin muutokset versiosta toiseen"
id: "muutosloki"
---
# Muutosloki
{:.no_toc}

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