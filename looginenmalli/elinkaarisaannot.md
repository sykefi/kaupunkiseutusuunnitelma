---
layout: "default"
description: ""
id: "elinkaarisaannot"
status: "Keskeneräinen"
---

1. 
{:toc}

## Johdanto

Kaupunkiseutusuunnitelmilla ja niiden suunnitelmakohteilla on Kaupunkiseutusuunnitelman tietomallissa elinkaari, joka määrää miten kyseiset tietokohteet syntyvät, miten ne voivat muuttua kaupunkiseutusuunnittelun prosessin aikana ennen niiden voimassaolon alkua, ja miten ne kumoutuvat johtaen niiden voimassaolon päättymiseen. Elinkaarisääntöjen määrittely liittyy olennaisesti tietokohteiden versionhallintaan, eli miten yksittäisten tietokohteiden niiden elinkaaren aikana muodostettavat versiot voidaan tallentaa ja yksilöidä viittauskelpoisten pysyvien tunnusten avulla. Tässä annetut säännöt pohjautuvat paikkatietokohteiden yksilöivien tunnusten ja elinkaarisääntöjen periaatteisiin, jotka on kuvattu jukishallinnon suosituksessa [JHS 193 - Paikkatiedon yksilöivät tunnukset](http://www.jhs-suositukset.fi/suomi/jhs193).

### HTTP URI -tunnukset

HTTP URI -muotoiset tunnukset ovat [RFC 3986 -standardiin](https://tools.ietf.org/html/rfc3986) perustuvia HTTP(S) -protokollan mukaisia URI-osoitteita (Uniform Resource Identifier), joiden globaali yksilöivyys varmistetaan Internetin DNS-nimipalveluun rekisteröityjen domain-nimien avulla. Kullakin DNS-palveluun rekisteröidyllä domain-nimellä (esim. ```uri.suomi.fi```) on yksiselitteinen omistaja, joka on suoraan tai välillisesti vastuussa ko. domain-nimen alla julkaistavasta sisällöstä. Nimen omistaja on myös ainoa taho, joka voi päättää ko. domain-nimeä käyttävien osoitteiden ohjautumisesta haluttuihin resursseihin, mikä tekee siitä luontevan perustan yksilöivien tunnusten nimiavaruuksille (esim. <http://uri.suomi.fi/object/rytj/kaupunkiseutusuunnitelma>). HTTP URI -muotoisen tunnuksen yksilöivyys perustuu siis domain-nimien ja siten niihin perustuvien nimiavaruuksien keskitettyyn hallintaprosessiin.

URI-tunnuksen ei tarvitse viitata konkreettiseen sijaintiin internetissä, vaan se voi olla abstraktimpi tunnus. [JHS 193 Paikkatiedon yksilöivät tunnukset](http://www.jhs-suositukset.fi/suomi/jhs193) määrittelee paikkatiedon yksilöiville tunnuksille muodon <http://paikkatiedot.fi/{tunnustyyppi}/{aineistotunnus}/{paikallinen tunnus}>, jossa paikkatietokohteiden ```tunnustyyppi``` on ```so```. Kaavatietomallissa on esimerkkinä käytetty tunnusmuotoa 
<http://uri.suomi.fi/object/rytj/{aineistotyyppi}/{TietotyypinNimi}/{paikallinenTunnus}>. HTTP URI -muotoisen tunnuksen etuna on luettavuus sekä DNS- ja HTTP-protokollien tarjoama kyky ratkaista (resolve) tunnus ja ohjata kysyjä sitä kuvaavaan Internet-resurssiin ilman tarvetta erityiselle keskitetylle tunnusrekisterille ja siihen perustuvalle ratkaisupalvelulle.

Kaupunkiseutusuunnitelman tietomallissa HTTP URI -muotoa käytetään [/viittausTunnus](#viittaustunnus)-attribuutissa, jonka avulla viitataan tiettyyn versioon tietokohteesta suunnitelman ulkopuolelta.

### UUID-tunnukset
UUID (Universally Unique Identifier) on OSF:n (Open Software Foundation) määrittelemä standardoitu tunnusmuoto, jonka avulla voidaan luoda vakiokokoisia, hyvin suurella todennäköisyydellä yksilöiviä tunnuksia ilman keskitettyä hallintajärjestelmää. UUID-tunnukset voivat perustua satunnaislukuihin, aikaleimoihin, tietokoneiden verkkokorttien MAC-osoitteisiin tai merkkijonomuotoisiin nimiavaruuksiin eri yhdistelmissä. UUID-tunnukset erityisen hyvin tietojärjestelmissä, joissa uusia globaalisti pysyviä ja yksilöiviä tunnuksia on tarpeen luoda hajautetusti ilman keskitettyä tunnusrekisteriä.

Kaupunkiseutusuunnitelman tietomallissa UUID-muotoisia tunnuksia suositellaan käytettäväksi [identiteettiTunnus](#identiteettitunnus) <!-- -, [kaavatunnus](#kaavatunnus)- -->ja [tuottajakohtainenTunnus](#tuottajakohtainen-tunnus) -attribuuttien arvoina.


## Kaupunkiseutusuunnitelman tietomallin kohteiden elinkaaren hallinnan periaatteet
Kaupunkiseutusuunnitelman tietomallin elinkaarisäännöt mahdollistavat tietomallin tietokohteiden käsittelyn, tallentamisen ja muuttamisen hallitusti sekä niiden laatimis- että voimassaolovaiheissa. Kaupunkiseutusuunnitelman tietomallin mukaiset tietosisällöt ovat <!-- merkittäviä oikeusvaikutuksia aiheuttavia, juridisesti päteviä -->aineistoja, joita käsitellään hajautetusti eri toimijoiden tietojärjestelmissä. Tämän vuoksi niiden tunnusten, viittausten ja versionnin hallintaan on syytä kiinnittää erityistä huomiota.

Seuraavat keskeiset periaatteet ohjaavat kaupunkiseutusuunnitelman tietomallin elinkaaren hallintaa:
* Kukin kaupunkiseutusuunnitelman tietovarastoon tallennettu versio suunnitelmasta ja sen sisältämistä yksittäisistä tietokohteista saa pysyvän, versiokohtaisen tunnuksen.
* Kuhinkin kaupunkiseutusuunnitelman tietovarastoon tallennettun tietokohteen versioon voidaan viitata sen pysyvän tunnuksen avulla.
* Kaupunkiseutusuunnitelman tietomallin tietokohteiden väliset viittaukset toteutetaan hallitusti sekä kaupunkiseutusuunnitelman tietoa tuottavissa tietojärjestelmissä että yhteisissä kaupunkiseutusuunitelman tietovarastoissa.
* Kaupunkiseutusuunnitelman tietovarasto vastaa pysyvien tunnusten luomisesta ja antamisesta tallennettaville tietokohteille.
<!--* Lainvoiman saaneita kaavoja ei voi muuttaa kaavatietovarastossa muilta osin kuin niiden tai niiden osien kumoamiseen liittyen. -->

Kaupunkiseutusuunnitelman tietomallin mukaisten aineistojen tallentamisessa erotetaan toisistaan tietojen tuottaminen ja muokkaus sisäisesti niiden tuottamiseen ja muokkaamiseen käytettävissä tietojärjestelmissä ja niiden hallinta yhteisessä versiohallitussa kaupunkiseutusuunnitelman tietovarastossa. Kaupunkiseutusuunnitelman tietomallin ei ole mielekästä asettaa vaatimuksia suunnitelmatietoa tuottavien tietojärjestelmien tunnusten ja versioden hallintaan, vaan tietomallissa tulee varautua siihen, että yhteiseen tietovarastoon tallennettavia tietoja on muokattu ja tallennettu sisäisesti tuntematon määrä kertoja ennen ensimmäistä viemistä yhteiseen tietovarastoon, ja samoin tuntematon määrä kertoja kunkin yhteiseen varastoon vietävän version välillä. Näin ollen on mahdollista, että suunnitelmasta voi olla joissain tietojärjestelmissä tallennettuna paikallisia versiota, joita ei ole koskaan viety yhteiseen kaupunkiseutusuunnitelman tietovarastoon.

## Tunnukset ja niiden hallinta

### Identiteettitunnus
Identiteettitunnus yhdistää saman tunnistettavan suunnitelman tietokohteen kehitysversiot toisiinsa.

{% include common/clause_start.html type="req" id="elinkaari/vaat-identiteettitunnus-maar" %}
Kaupunkiseutusuunnitelman tietomallin tietokohteissa identiteettitunnus kuvataan attribuutilla ```identiteettiTunnus```. Kahdella kaupunkiseutusuunnitelman tietomallin versioitavalla objektilla voi olla sama ```identiteettiTunnus```-attribuutin arvo ainoastaan, mikäli kaikki seuraavista ehdoista ovat tosia:
* Molemmat objektit kuvaavat saman suunnitelman tai sen sisältämän, nimettävissä olevan tietokohteen kehityskaaren eri tiloja.
* Molemmat objektit liittyvät samaan suunnitelmaan.
* Molemmat objektit ovat saman loogisen tietomallin luokan edustajia.
{% include common/clause_end.html %}

Yksittäisen suunnitelman tietokohteen koko ko. tietojärjestelmään tallennettu kehityshistoria saadaan noutamalla kaikki ko. tyyppisen tietokohteen objektit, joilla on sama ```identiteettiTunnus```-attribuutin arvo.

Yhteinen kaupunkiseutusuunnitelman tietovarasto on vastuussa uusien identiteettitunnusten luomisesta tarvittaessa tallennustapahtumien yhteydessä, ja niiden välittämisestä tiedoksi tallentavalle tietojärjestelmälle. Tallentavan tietojärjestelmän tulee tallentaa itselleen kopiot tietovaraston tallennustapahtuman yhteydessä palautamistä suunnitelman ja sen tietokohteiden identiteettitunnuksista, sillä ne tulee sisällyttää ko. tietokohteiden seuraavien versioden tallennettavaksi lähetettäviin objekteihin.

{% include common/clause_start.html type="req" id="elinkaari/vaat-identiteettitunnus-gen" %}
* Mikäli tallennettavalle tietokohteelle ei ole annettu ```identiteettitunnus```-attribuuttia, tai tietovarasto ei sisällä sellaista saman luokan tietokohdetta, jolla sama ```identiteettiTunnus```-attribuutin arvo, kaupunkisuunnitelman tietovarasto luo ko. objektille uuden identiteettitunnuksen, joka korvaa tuottavan tietojärjestelmän objektille mahdollisesti antaman ```identiteettiTunnus```-attribuutin arvon. Tällöin objektia pidetään uuden tietokohteen ensimmäisenä versiona.
* Mikäli tietovarasto sisältää saman luokan tietokohteen, jolla on sama ```identiteettiTunnus```-attribuutin arvo kuin tallennetavalla objektilla, objekti tallennetaan kaupunkiseutusuunnitelman tietovarastoon ko. tietokohteen uutena versiona. Tällöin tallennettavan objektin ```identiteettiTunnus```-attribuutin arvo ei muutu.
{% include common/clause_end.html %}

<!--
{% include common/clause_start.html type="req" id="elinkaari/vaat-kaavan-identiteettitunnus" %}
[Kaava](../../looginenmalli/dokumentaatio/#kaava)-luokan tietokohteen tallennuksen yhteydessä kaupunkiseutusuunnitelman tietovarasto tarkistaa, että sen attribuutti [kaavaTunnus](#kaavatunnus) on annettu ja validi.
* Mikäli kohde katsotaan sen ```identiteettiTunnus```-attribuutin arvon perusteella uudeksi tietokohteeksi, sama ```kaavaTunnnus```-attribuutti ei saa olla käytössä kaavatietovaraston muilla [Kaava](dokumentaatio/#kaava)-luokan objekteilla.
* Mikäli kohde katsotaan sen ```identiteettiTunnus```-attribuutin arvon perusteella aiemmin tallennetun tietokohteen uudeksi versioksi, aiemmin tallennetun version ```kaavaTunnnus```-attribuutin tulee olla sama kuin tallennettavassa objektissa.
{% include common/clause_end.html %}
-->

{% include common/clause_start.html type="rec" id="elinkaari/suos-identiteettitunnus-form" %}
Identiteettitunnuksen suositeltu muoto on UUID.
{% include common/clause_end.html %}

Esimerkki: ```640bff6b-c16a-4947-af8d-d86f89106be1```

### Paikallinen tunnus
Paikallinen tunnus yksilöi tietokohteen yhden version kaupunkiseutusuunnitelman tietovaraston sisällä. 

{% include common/clause_start.html type="req" id="elinkaari/vaat-paikallinentunnus-maar" %}
Kaupunkiseutusuunnitelman tietomallin tietokohteissa paikallinen tunnus kuvataan attribuutilla ```paikallinenTunnus```. Kaikilla saman kaupunkiseutusuunnitelman tietovaraston objekteilla (ml. saman tietokohteen eri versiot) tulee olla eri ```paikallinenTunnus```-attribuutin arvo.
{% include common/clause_end.html %}

{% include common/clause_start.html type="req" id="elinkaari/vaat-paikallinentunnus-gen" %}
Tietokohteiden paikallinen tunnus muuttuu sen jokaisen version tallennuksen yhteydessä. Kaupunkiseutusuunnitelman tietovarasto vastaa paikallisten tunnusten luomisesta tallennustapahtuman yhteydessä. Tuottavan tietojärjestelmän mahdollisesti asettamat arvot korvataan.
{% include common/clause_end.html %}

{% include common/clause_start.html type="req" id="elinkaari/vaat-paikallinentunnus-form" %}
Paikallinen tunnus koostuu identiteettitunnuksesta ja siihen erotinmerkillä liitetystä versiokohtaisesta, esimerkiksi tarkkaan tallennusajanhetkeen perustuvasta merkkijonosta.
{% include common/clause_end.html %}

{% include common/clause_start.html type="rec" id="elinkaari/suos-paikallinentunnus-merk" %}
Paikallisen tunnuksen muodostamisessa tulee välttää merkkejä, jotka joudutaan URL-koodaamaan rajapintapalvelujen kutsuissa. Paikkatietokohteen paikallista tunnusta käytetään fyysisten tietomallien pääavaimena, esim. GeoJSON Feature ```id```-omaisuuden ja GML:n ```gml:id```-attribuutin arvona, ja siten esimerkiksi OGC Web Feature Service (WFS) - ja OGC API - Features -rajapintapalvelujen paikkatietokohteen yksilöivissä kyselyissä.
{% include common/clause_end.html %}

Tallennusajanhetkeen päättyvää paikallista tunnusta voidaan käyttää ilman sekaannusmahdollisuuksia samalla logiikalla myös paikallisissa versionneissa, eli sellaisissa suunnitelman versioiden tallennuksissa, joita ei viedä lainkaan kaupunkiseutusuunnitelman tietovarastoon.

Esimerkki: ```640bff6b-c16a-4947-af8d-d86f89106be1.b05cf48d46d8c905c54522f44b0a12daff11604e```

{% include common/note.html content="Käyttämällä paikallisena tunnuksena pelkkää identiteettitunnuksesta riippumatonta UUID-tunnusta päästäisiin lyhyempiin tunnuksiin, mutta menetetään yhteys identiteettitunnusten ja paikallisten tunnusten välillä, mikä saattaa hankaloittaa erilaisten vikatilanteiden selvitystä ja toimintavarmuuden testaamista, kun pelkkien tunnusten perusteella ei voida päätellä ovatko kaksi objektia saman tietokohteen eri versioita." %}

### Nimiavaruus
{% include common/clause_start.html type="req" id="elinkaari/vaat-nimiavaruus-maar" %}
Nimiavaruus määrää kaupunkiseutusuunnitelman tietomallin kaikkien tietokohteiden viittaustunnusten alkuosan yhden kaupunkiseutusuunnitelman tietovaraston sisällä. Kaupunkiseutusuunnitelman tietomallin tietokohteissa paikallinen tunnus kuvataan attribuutilla ```nimiavaruus```.
{% include common/clause_end.html %}

{% include common/clause_start.html type="req" id="elinkaari/vaat-nimiavaruus-form" %}
Nimiavaruus on HTTP URI -muotoinen.
{% include common/clause_end.html %}

Nimiavaruus on syytä valita huolella siten, että se olisi mahdollisimman pysyvä, eikä sitä tarvitsisi tulevaisuudessa muuttaa esimerkiksi valtionhallinnon virastojen tai ministeriröiden mahdollisten uudelleenorganisointien ja -nimeämisten johdosta. Valittu URL-osoite tulee myös voida aina tarvittaessa ohjata kulloinkin käytössä olevaan rajapintapalveluun (HTTP redirect). 

{% include common/clause_start.html type="req" id="elinkaari/vaat-nimiavaruus-gen" %}
Kaupunkiseutusuunnitelman tietovarasto vastaa ```nimiavaruus```-attribuuttien asetamisesta tallennustapahtuman yhteydessä. Tuottavan tietojärjestelmän mahdollisesti antamat arvot korvataan.
{% include common/clause_end.html %}

Esimerkki: ```http://uri.suomi.fi/object/rytj/alueidenkayttojarakentamisasia```

### Viittaustunnus
{% include common/clause_start.html type="req" id="elinkaari/vaat-viittaustunnus-maar" %}
Viittaustunnus yksilöi suunnitelman tietokohteen yhden, keskitettyyn kaupunkiseutusuunnitelman tietovaraston tallentun kehitysversion globaalisti. Kaupunkiseutusuunnitelman tietomallin tietokohteissa paikallinen tunnus kuvataan attribuutilla ```/viittausTunnus```.
{% include common/clause_end.html %}

{% include common/clause_start.html type="req" id="elinkaari/vaat-viittaustunnus-form" %}
Viittaustunnus on HTTP URI -muotoinen ja se muodostuu nimiavaruudesta, tietokohteen luokan nimestä ja paikallisesta tunnuksesta yhdessä kauttaviivoilla (```/```) erotettuina.
{% include common/clause_end.html %}

{% include common/clause_start.html type="req" id="elinkaari/vaat-nimiavaruus-gen" %}
Kaupunkiseutusuunnitelman tietovarasto vastaa ```/viittausTunnus```-attribuuttien asetamisesta tallennustapahtuman yhteydessä. Tuottavan tietojärjestelmän mahdollisesti antamat arvot korvataan.
{% include common/clause_end.html %}

Tallentavan tietojärjestelmän ei siis tarvitse tallentaa luotuja viittaustunnuksia itselleen seuraavia tallennuksia varten.

{% include common/clause_start.html type="rec" id="elinkaari/suos-viittaustunnus-ohj" %}
Viittaustunnuksen on suositeltavaa ohjautua aina ko. tietokohteen version tietosisältöön kulloinkin toiminnassa olevassa kaupunkiseutusuunnitelman tietovaraston latauspalvelussa.
{% include common/clause_end.html %}

<!--Esimerkki: ```http://uri.suomi.fi/object/rytj/kaava/SpatialPlan/640bff6b-c16a-4947-af8d-d86f89106be1.b05cf48d46d8c905c54522f44b0a12daff11604e```-->

### Tuottajakohtainen tunnus

{% include common/clause_start.html type="req" id="elinkaari/vaat-tuottajakohtainen-tunnus-maar" %}
Suunnitelmatietoa tuottavat järjestelmät voivat niin halutessaan käyttää tuottajakohtaista tunnusta niiden omien tietojärjestelmäspesifisten tunnusten antamiseen kaupunkiseutusuunnitelman tietomallin tietokohteille. Kaupunkiseutusuunnitelman tietomallin tietokohteissa tuottajakohtainen tunnus kuvataan attribuutilla ```tuottajakohtainenTunnus```.
{% include common/clause_end.html %}

{% include common/clause_start.html type="req" id="elinkaari/vaat-tuottajakohtainen-tunnus-gen" %}
Kaupunkiseutusuunnitelman tietovarasto ei koskaan muuta tuottavan tietojärjestelmän mahdollisesti asettamia tuottajakohtaisia tunnuksia, ja ne palautetaan sellaisenaan latattaessa tietokohteita tietovarastosta.
{% include common/clause_end.html %}

Tietojärjestelmät voivat käyttää tuottajakohtaisia tunnuksia kohdistamaan kaupunkiseutusuunnitelman tietovarastoon ja paikallisiin tietojärjestelmiin tallennettuja tietokohteita toisiinsa esimerkiksi päivitettäessä niiden tallennuksen yhteydessä syntyneitä tunnuksia, vertailtaessa kaupunkiseutusuunnitelman tietovarastoon tallennettuja kohteita ja paikallisia kohteita toisiinsa, sekä esitettäessä validointipalvelun tuloksia suunnitteluohjelmiston käyttäjälle.

Tuottajakohtaisilta tunnuksilta ei vaadita yksilöivyyttä tai mitään tiettyä yhtenäistä muotoa, mutta UUID-muodon käyttäminen tarjoaa hyvin määritellyn ja standardoidun tavan luoda tuottajakohtaisista tunnuksista yksilöiviä eri tietojärjestelmien kesken. Tästä saattaa olla etua haluttaessa tehdä tuotettavista suunnitelmatiedoista mahdollisimman järjestelmäriippumattomia ja esimerkiksi taata tuottajakohtaisten tunnusten yksilöivyys yli mahdollisten suunnitelmatietoa tuottavien tietojärjestelmien vaihdosten ja päivitysten. 

{% include common/clause_start.html type="rec" id="elinkaari/suos-tuottajakohtainen-tunnus-form" %}
Tuottajakohtaisen tunnuksen suositeltu muoto on UUID.
{% include common/clause_end.html %}

Esimerkki: ```k-123445```
<!--
### Kaavatunnus
{% include common/clause_start.html type="req" id="elinkaari/vaat-kaavatunnus-maar" %}
Kaavatunnus on kaavalle ennakolta haettava, kaavan kansallisesti yksilöivä tunnus. Kaatatietomallissa kaavatunnus kuvataan [Kaava](dokumentaatio/#kaava)-luokan attribuutilla ```kaavaTunnus```.
{% include common/clause_end.html %}

{% include common/clause_start.html type="req" id="elinkaari/vaat-kaavatunnus-gen" %}
Tuottava tietojärjestelmän vastaa kaavatunnuksen asettamisesta [Kaava](dokumentaatio/#kaava)-luokan attribuutiksi. Se tulee olla asetettuna myös kaavan ensimmäisen kaavatietovarastoon tallennuksen yhteydessä.
{% include common/clause_end.html %}

{% include common/clause_start.html type="req" id="elinkaari/vaat-kaavatunnus-yks" %}
Kaavatunnus on Kaava-luokan objekteille globaalisti yksilöivä, eikä muutu saman kaavan eri elinkaaren aikaisten versioiden tallennuksen yhteydessä.
{% include common/clause_end.html %}

 Käytännössä myönnetyt kaavatunnukset kannattaa tallentaa valmiiksi kaavatietovarastoon, jotta voidaan tarkistaa onko tallennettavaksi tarkoitettu kaavatunnus myönnetty organisaatiolle, jonka kaavaa ollaan tallentamassa. Kuntakoodin tai muun hallinnollisen alueen tunnuksen käyttö osana kaavatunnusta ei ole suositeltavaa, sillä hallinnolliset alueet muuttuvat ajan kuluessa. Kun sidos tunnuksen ja hallinnollisen alueen välillä ei näy tunnuksessa, voidaan kaavan hallinnollista aluetta muuttaa joustavammin kaavan elinkaaren aikana.

{% include common/clause_start.html type="rec" id="elinkaari/suos-kaavatunnus-form" %}
Kaavatunnuksen suositeltu muoto on UUID.
{% include common/clause_end.html %}

Esimerkki: ```df5b2d6f-d6d6-4695-938c-dd7c4c784c28``` -->

### Pysyvien tunnusten palauttaminen tuottavalle järjestelmälle

Versionhallinnan näkökulmasta on tärkeää, että suunnitelman tuottava tietojärjestelmä käyttää saman suunnitelman seuraavan version tallentamisessa suunnitelman ensimmäisen version tallennuksen yhteydessä luotua identiteettitunnusta. Vastaavasti kaikkien suunnitelman tietokohteiden osalta käytetään niiden ensimmäisen tallennuksen yhteydessä luotuja identiteettitunnuksia, mikäli objektin katsotaan kuvaavan ko. tietokohteen uutta versiota.

{% include common/clause_start.html type="req" id="elinkaari/vaat-tunnusten-palautus" %}
Tietovaraston tallennusrajapinta palauttaa tallennetun suunnitelman tiedot tuottavalle tietojärjestelmälle tallennusoperaation yhteydessä siten, että ne sisältävät yllä mainittujen tunnustenhallintasääntöjen mukaisesti mahdollisesti generoidut tai muokatut identiteettitunnukset, paikalliset tunnukset, nimiavaruudet ja viittaustunnukset kaikille tallennetuille tietokohteille.
{% include common/clause_end.html %}

### Suunnitelman tietokohteisiin viittaaminen ja viitteiden ylläpito

{% include common/clause_start.html type="req" id="elinkaari/vaat-suunnitelman-sisaiset-viittaukset" %}
Saman suunnitelman tietokohteiden keskinäiset assosiaatiot toteutetaan viitattavan tietokohteen [paikallinenTunnus](#paikallinen-tunnus)-attribuuttia käyttäen.
{% include common/clause_end.html %}

{% include common/clause_start.html type="req" id="elinkaari/vaat-tietovaraston-sisaiset-viittaukset" %}
Kaupunkiseutusuunnitelman tietokohteen luokkien assosiaatiot eri suunnitelmien välillä tai suunnitelmien ja muiden maankäyttöasiakirjojen tietokohteiden välillä toteutetaan viitattavan tietokohteen [/viittausTunnus](#viittaustunnus)-attribuuttia käyttäen.
{% include common/clause_end.html %}

{% include common/clause_start.html type="req" id="elinkaari/vaat-viittaukset-ulkoa" %}
Pysyvät viittaukset Kaupunkiseutusuunnitelman tietomallin ulkopuolelta tietomallin tietokohteisiin toteutetaan viitattavan tietokohteen [/viittausTunnus](#viittaustunnus)-attribuuttia käyttäen.
{% include common/clause_end.html %}

{% include common/clause_start.html type="req" id="elinkaari/vaat-viittaukset-tallennettaessa" %}
Tallennettaessa Kaupunkiseutusuunnitelman tietomallin tietokohteita kaupunkiseutusuunnitelman tietovarastoon tietokohteiden tunnukset muuttuvat niiden pysyvään muotoon, kuten kuvattu luvussa [Tunnukset ja niiden hallinta](#tunnukset-ja-niiden-hallinta). Kaupunkiseutusuunnitelman tietovaraston vastuulla on päivittää kunkin paikallisen tunnuksen muuttamisen yhteydessä myös kaikkien ko. tietokohteen versioon sen paikallisen tunnuksen avulla viittaavien muiden ko. suunnitelman tietokohteiden viittaukset käyttämään tietokohteen muutettua paikallista tunnusta.   
{% include common/clause_end.html %}

### Koodistojen koodien tunnuksiin liittyvät vaatimukset

{% include common/clause_start.html type="req" id="elinkaari/vaat-koodien-yksiloivat-tunnukset" %}
Kullakin koodiston koodilla on oltava pysyvä tunnus, joka sellaisenaan yksilöi kyseisen koodin globaalisti ilman erilistä tietoa koodistosta, johon koodi kuuluu. Koodin tunnus on HTTP URI -muotoinen.
{% include common/clause_end.html %}

{% include common/clause_start.html type="req" id="elinkaari/vaat-alakoodi-maar" %}
Olkoon koodi ```A``` mikä tahansa hierarkkisen koodiston sisältämä koodi. Koodin ```A``` alakoodilla tarkoitetaan koodia, joka on hierakkiassa sijoitettu koodin ```A``` alle. Koodi voi olla useamman ylemmän tason koodin alakoodi vain mikäli ko. ylemmän tason koodit ovat alakoodisuhteessa keskenään.
{% include common/clause_end.html %}

Käytännössä tietyn koodin alakoodit voidaan tunnistaa vertaamalla niiden tunnuksia:

{% include common/clause_start.html type="req" id="elinkaari/vaat-alakoodi-tunnus" %}
Koodin ```A``` alakoodin ```B``` tunnus alkaa koodin ```A``` tunnuksella ja sisältää sen jälkeen yhden tai useamman merkin.
{% include common/clause_end.html %}

## Muutokset ja tietojen versionti
{% include common/clause_start.html type="req" id="elinkaari/vaat-pysyva-sisalto" %}
Kukin suunnitelman tai sen osien tallennusoperaatio yhteiseen tietovarastoon muodostaa uuden version tallennettavista tietokohteista, mikäli yksittäinen tietokohde on miltään osin muuttunut verrattuna sen edelliseen versioon. Myös muutokset muissa kaupunkiseutusuunnitelman tietomallin tietokohteissa, joihin tietokohteesta on viittaus, lasketaan tietokohteen muutoksiksi. Tallennetun tietokohteen version sisältö ei voi muuttua tallennuksen jälkeen, poislukien sen voimassaolon päättymiseen, seuraavaan versioon linkittämiseen ja elinkaaritilaan liittyvät attribuutit, joita kaupunkiseutusuunnitelman tietovarasto itse päivittää tietyissä tilanteissa.
{% include common/clause_end.html %}

Näin taataan ulkoisten viittausten eheys, sillä suunnitelman kaikkien kohteiden paikalliset ja viittaustunnukset viittaavat aina vain tiettyn, sisällöllisesti muuttumattomaan versioon viittatusta kohteesta. Suositeltavaa on, että kaikki tallennusversiot myös pidetään pysyvästi tallessa, jotta mahdolliset keskenäiset ja ulkopuolelta tulevat linkit eivät mene rikki muutosten yhteydessä.

### Muutosten leviäminen viittausten kautta
Kaupunkiseutusuunnitelman tietomallin tietokohteiden keskinäiset viittaukset kohdistuvat aina viitattavien tietokohteiden tiettyyn versioon, ja toisaalta kaikki kohteiden sisällölliset muutokset johtavat uusien versioiden tallentamiseen. Siten kohteiden välisten linkkien kohdetietoa täytyy muuttaa mikäli halutaan viitata jollain tapaa muuttuneeseen kohteeseen. Tämä päivitystarve johtaa edelleen myös viittaavan tietokohteen uuden version luomiseen, vaikka ainoa muuttunut tieto olisi linkki uuteen versioon viitatusta tietokohteesta. Molempiin suuntiin tietokohteiden välillä tehty linkitys saattaa siten johtaa hyvin laajalle leviävään muutosketjuun. Muutosten leviämistä voidaan rajoittaa  kaikkiin suunnitelman tietokohteisiin tekemällä linkitys tietokohteiden välillä vain yhteen suuntaan, esimerkiksi vain joko suunnitelmasta suunnitelmakohteisiin ja suunnitelmakohteista kohteen toimintoihin (ylhäältä alas), tai toisinpäin (alhaalta ylös). 

Kaupunkiseutusuunnitelmantietomallissa kukin [Suunnitelmakohde](dokumentaatio/#suunnitelmakohde) on linkitetty kahdensuuntaisesti suunnitelmaan ja kukin [KohteenToiminto](dokumentaatio/#kohteentoiminto) kahdensuuntaisesti <!--joko pelkästään suoraan suunnitelmaan  (yleismääräys/yleissuositus) tai myös--> suunnitelmakohteisiin, joiden alueita ne koskevat. Tällöin yhden kohteen toiminnon muuttaminen johtaa uuden version luomiseen muutettavan kohteen toiminnon lisäksi myös siihen linkitetyistä suunnitelmakohteista, ja edelleen niihin linkitetystä kaupunkiseutusuunnitelma-objektista, mikä puolestaan johtaa lopulta uusien versioiden luomiseen kaikista ko. suunnitelman muistakin suunnitelmakohteista ja kohteen toiminnoista, koska kaupunkiseutusuunnitelma-objektiin päin osoittavat linkit pitää muuttaa osoittamaan sen uuteen versioon.

<!--Minkä tahansa kohteen toiminnon muuttaminen johtaa siis kaikkien muidenkin ko. kaupunkiseutusuunnitelman suunnitelmakohteiden ja kohteen toimintojen uusiin versiohin, mikä on hieman ongelmallista todellisten suunnitelman muutosten seurannan kannalta. Kahdensuuntainen linkitys on kuitenkin tässä perusteltavissa. Suorat linkit suunnitelmakohteista ja kohteen toiminnoista ylöspäin Kaupunkiseutusuunnitelma-luokan objektiin mahdollistavat tehokkaat ja yksikertaiset hakuoperaatiot tiettyyn suunnitelman versioon liittyvien kohteen toimintojen noutamiseksi. Toisaalta Kaupunkiseutusuunnitelma-luokan viittaukset alaspäin sen sisältämiin suunnitelmakohteisiin ja kohteen toimintoihin helpottavat kaikkien suunnitelmaan liittyvien kohteen toimintojen poimintaa, kun ne voidaan löytää iteratiivisesti puumaista rakennetta seuraamalla.-->

Linkit kaupunkiseutusuunnitelma-objektista alaspäin mahdollistavat myös kaupunkiseutusuunnitelmaan liittyvien suunnitelmakohteiden ja kohteen toimintojen poistamisen suunnitelmaluonnoksesta tai ehdotuksesta vain jättämällä ne yksinkertaisesti pois seuraavasta suunnitelman tallennusversiosta: Mikäli kaupunkiseutusuunnitelma-objektissa ei olisi suoria linkkejä sen sisältämiin suunnitelmakohteisiin, voisi se säilyä tallennuksessa muuttumattomana, vaikka tallennuksesta puuttuisikin yksi tai useampi aiempaa suunnitelma-versioon sisältynyt suunnitelmakohde. Muuttumattomasta kaupunkiseutusuunnitelma-objektista ei tällöin luotaisi uutta versiota, ja siten uudesta versiosta pois jätetytkin suunnitelmakohteet viittaisivat edelleen uusimpaan (muuttumattomaan) suunnitelman versioon yhdessä muutettujen ja uusien suunnitelmakohteiden kanssa. Vastaavasti kohteen toimintojen poistaminen tietystä suunnitelmakohteesta voidaan tehdä yksinkertaisesti jättämällä ne pois suunnitelman seuraavasta tallennusversiosta.

[Kaupunkiseutusuunnitelma](dokumentaatio/#alueidenkayttojarakentamisasia)-luokan assosiaatiot [SuunnitelmanSelostus](dokumentaatio/#suunnitelmanselostus)- ja [Vuorovaikutussuunnitelma](dokumentaatio/#vuorovaikutussuunnitelma)-luokkiin ovat yksisuuntaisia. Tallennettu versio suunnitelman selostuksesta tai vuorovaikutussuunnitelmasta voi pysyä samana suunnitelman uuden version tallennuksen yhteydessä, jolloin niistä ei ole tarpeen luoda uusia versiota. Sama suunnitelman selostuksen tai vuorovaikutussuunnitelman versio voi siis liittyä useampaan saman suunnitelman tallennusversioon.

**Esimerkki**:

Tallennuspalveluun viedään suunnitelmaehdotus, jonka yhteen suunnitelmakohteeseen liittyvää mitoitussuureen lajia [Uutta asuinkerrosalaa (k-m2)](http://uri.suomi.fi/codelist/rytj/RY_MitoitussuureenLaji/code/14) on muutettu siten, että sen numeerinen arvo muuttuu arvosta ```1000 k-m2``` arvoon ```1500 k-m2```. Kaikki suunnitelman muut tietokohteet ovat identtisiä suunnitelman edellisen tallennusversion kanssa.

* Muuttuvasta mitoitussuureen laji-tietokohteesta luodaan uusi versio.
* Suunnitelmakohteesta, johon muuttunut mitoitussuureen laji kohdistuu, luodaan uusi versio, jossa muuttuu vain linkki, viitaten nyt mitoitussuureen lajin uuteen versioon.
* Kaikista muista suunnitelman tietokohteista, joista on viittaus kyseiseen suunnitelmakohteeseen, luodaan uudet versiot, joissa muuttuvat vain linkit, viitaten nyt suunnitelmakohteen uuteen versioon, mukaan lukien suunnitelma-objekti ja ko. suunnitelmakohteen kaikki muut tiedot.
* Kaikista ko. suunnitelman muistakin suunnitelmakohteista ja kohteen toiminnoista luodaan uudet versiot, koska niiden viittaukset muuttuneeseen suunnitelma-tietokohteeseen pitää muuttaa.
* Suunnitelmaan mahdollisesti liittyvistä suunnitelman selostus- ja vuorovaikutussuunnitelma -tietokohteista ei luoda uusia versiota, vaan sekä uusi että vanha suunnitelman versio viittaavat samoihin selostus- ja vuorovaikutussuunnitelma-tietokohteiden versioihin.


### Yksittäisen suunnitelman elinkaaren vaiheisiin liittyvät muutokset
Kaupunkiseutusuunnitelman tietomalli mahdollistaa tunnistettavien suunnitelman tietokohteiden eri kehitysversioiden erottamisen toisistaan. Kullakin tietomallin kohteella on sekä sen tosimaailman identiteettiin liittyvä ns. identiteettitunnus että yksittäisen tallennusversion tunnus (paikallinen tunnus). Tallennettaessa uutta versiota samasta suunnitelmasta tai sen sisältämästä tietokohteesta, sen identiteettitunnus pysyy ennallaan, mutta sen paikallinen tunnus muuttuu. Tallennettaessa Kaupunkiseutusuunnitelma-luokan objektia se katsotaan saman tietokohteen uudeksi versioksi, mikäli sen suunnitelmatunnus on sama. Muiden kaupunkiseutusuunnitelman tietomallin versioitavien objektien suhteen samuuden määritteleminen on tietoja tuottavien järjestelmien vastuulla: mikäli objektilla on tallennettavaksi lähetettäessä saman ```identiteettiTunnus```-attribuutin arvo kuin aiemmin tallennetulla, samantyyppisellä tietokohteella, katsotaan uusi objekti on saman tietokohteen uudeksi versioksi.


{% include common/clause_start.html type="req" id="elinkaari/vaat-version-korvaus" %}
Kun suunnitelman tietokohteesta tallennetaan uusi muuttunut versio, tulee tietokohteen edellisen version ```korvattuObjektilla```-assosiaatio asettaa viittaamaan tietokohteen uuteen versioon. Uuden tietokohteen version ```korvaaObjektin```-assosiaatio puolestaan asetetaan viittaamaan tietokohteen edelliseen, korvattavaan versioon. Molempien kohteiden ```tallennusAika```-attribuutin arvoksi asetetaan ajanhetki, jolloin tallennus ja muutos kaupunkiseutusuunnitelman tietovarastoon on tehty.
{% include common/clause_end.html %}


Yksittäisen tietokohteen yksityiskohtainen muutoshistoria kaupunkiseutusuunnitelman tietovarastossa saadaan seuraavalla sen ```VersioituObjekti``` -assosiaatioita. Ainoa muutos, joka ei näy tietokohteen omana versionaan, on kohteen kumoaminen, jolloin sen viimeisimmän version tietoja päivitetään sen elinkaaritilan, voimassaolon ja tallennusajan osalta.

{% include common/question.html content="Pitääkö [VersioituObjekti](dokumentaatio/#versioituobjekti)-luokalle lisätä attribuutti ```ensimmainenTallennusAika```, joka kertoo ko. version alkuperäisen tallennusajan? Kumoamisen yhteydessä ```tallennusAika```-attribuutin arvoa muutetaan, jolloin hukkuu tieto ko. version alkuperäisestä tallennusajankohdasta." %}

Attribuutin ```viimeisinMuutos``` arvo kuvaa ajanhetkeä, jolloin ko. tietokohteeseen on tehty sisällöllinen muutos tiedontuottajan tietojärjestelmässä. Tiedontuottajan järjestelmän osalta ei vaadita tiukkaa versiontipolitiikkaa, eli ```paikallinenTunnus```-attribuutin päivittämistä jokaisen tietokohteen muutoksen johdosta. ```viimeisinMuutos```-attribuutin päivittämien riittää kuvaamaan tiedon todellisen muuttumisajankohdan.

<!--
### Suunnitelman käsittely- ja vuorovaikutustapahtumien elinkaari
Suunnitteluprosessin historian yhdessä kuvaavat [AbstraktiTapahtuma](dokumentaatio/#abstraktitapahtuma)-luokasta perityt [Kasittelytapahtuma](dokumentaatio/#kasittelytapahtuma)- ja [Vuorovaikutustapahtuma](dokumentaatio/#vuorovaikutustapahtuma)-luokan tietokohteet linkitetään yksisuuntaisesti [AbstraktiMaankayttoasia](dokumentaatio/#abstraktimaankayttoasia)-luokkaan (Kaava-luokan yläluokka) päin. Tapahtumatietokohteiden uusina versiona tallennettavat muutokset eivät koskaan johda uuden version luomiseen Kaava-luokan tietokohteesta, sen kaavakohteista, kaavamääräyksistä tai -suosituksista. Syy tähän on se, että käsittely- ja vuorovaikutustapahtumien on tärkeää kohdistua nimenomaan tiettyyn, pysyvään versioon kaavasta.

Kulloinkin nähtävillä olevien kaavojen poimiminen on eräs kaavatietovaraston keskeisistä käyttötapauksista. Tiettyllä ajanhetkellä nähtävillä olevat tai nähtävillä olleet kaavojen versiot voidaan poimia valitsemalla ne kaavat, joihin kohdistuu [Vuorovaikutustapahtuma](dokumentaatio/#vuorovaikutustapahtuma), jonka ```laji```-attribuutin arvo on [Nähtävilläolo](http://uri.suomi.fi/codelist/rytj/RY_KaavanVuorovaikutustapahtumanLaji/code/01), ```tapahtumaAika```-attribuuttin aikaväli kattaa halutun ajankohdan ja ```peruttu```-attribuutin arvo on ```false```. Näiden vuorovaikutustapahtumien ```liittyvaAsia```-assosiaatio viittaa siihen [AbstraktiMaankayttoasia](dokumentaatio/#abstraktimaankayttoasia)-luokan instanssiin, joka ko. aikaan on nähtävillä. Katso kaavaehdotuksen ja tarkistetun kaavaehdotuksen nähtävilläolon ilmoittamiseen liittyvät vaatimukset kohdasta [Kaavan elinkaaritilan muutoksiin liittyvät käsittely- ja vuorovaikutustapahtumat](#kaavan-elinkaaritilan-muutoksiin-liittyvät-käsittely--ja-vuorovaikutustapahtumat).

{% include common/clause_start.html type="req" id="elinkaari/vaat-tapahtumien-poistaminen" %}
Kerran tallennettuja [AbstraktiTapahtuma](dokumentaatio/#abstraktitapahtuma)-luokan tietokohteita ei voi poistaa kaavatietovarastosta. Mikäli suunniteltu vuorovaikutustapahtuma ei syystä tai toisesta toteudu tai käsittelytapahtumaan liittyvä päätös kumotaan, tulee sen attribuutti ```peruttu``` asettaa arvoon ```true```.
{% include common/clause_end.html %} -->
<!--
### Kaavan ja sen tietokohteiden voimaantulo
Kaavan ```voimassaoloAika``` -attribuutin alkuaika on ajanhetki, jolloin kaava sen valitusajan umpeuduttua ja mahdollisten valitusten ja oikaisukehotusten käsittelyn jälkeen kuulutetaan voimaantulleeksi.

{% include common/clause_start.html type="req" id="elinkaari/vaat-kaavan-voimaantulo" %}
Voimaantulemisen kuuluttamisen yhteydessä kaavasta tallennetaan kaavatietovarastoon uusi versio, jossa sen 
* [Kaava](dokumentaatio/#kaava)-luokan objektin ```elinkaaritila```-attribuutin arvoksi on asetettu [Voimassa](http://uri.suomi.fi/codelist/rytj/RY_KaavanElinkaariTila/code/10),
* [Kaava](dokumentaatio/#kaava)-luokan objektin ```voimassaoloAika```-attribuutin alkuajaksi on asetettu kuulutuksen ajanhetki ja loppuaikaa ei ole annettu, ja
* Kunkin kaavan [Kaavamaarays](dokumentaatio/#kaavamaarays)- ja [Kaavasuositus](dokumentaatio/#kaavasuositus)-luokan objektin ```elinkaaritila```-attribuuttien arvoksi [Voimassa](http://uri.suomi.fi/codelist/rytj/RY_KaavanElinkaariTila/code/01) ja ```voimassaoloAika```-attribuutin alkuajaksi kuulutuksen ajanhetki ilman loppuaikaa.
{% include common/clause_end.html %}

{% include common/clause_start.html type="req" id="elinkaari/vaat-voimassaoloaika" %}
Kaava ja sen kaavamääräykset ja -suositukset ovat voimassa niiden ```voimassaoloAika```-attribuuttien määräämillä aikaväleillä. Mikäli ```voimassaoloAika```-attribuutin loppuaika puuttuu, on tietokohde voimassa toistaiseksi.
{% include common/clause_end.html %}

{% include common/clause_start.html type="req" id="elinkaari/vaat-elinkaaritila-voimassaoloaika" %}
 Kaava ja sen kaavamääräykset ja -suositukset voivat olla elinkaaritilassa [Voimassa](http://uri.suomi.fi/codelist/rytj/RY_KaavanElinkaariTila/code/10) ainoastaan, mikäli niiden ```voimassaoloAika``` on annettu ja sisältää vain alkuajan ilman loppuaikaa. Kaavan ja sen kaavamääräysten ja -suositusten ```voimassaoloAika``` voi olla annettu vain mikäli ne ovat joko elinkaaritilassa [Voimassa](http://uri.suomi.fi/codelist/rytj/RY_KaavanElinkaariTila/code/10) tai [Kumottu](http://uri.suomi.fi/codelist/rytj/RY_KaavanElinkaariTila/code/11). Kaavan ja sen kaavamääräysten ja -suositusten ```voimassaoloAika``` sisältää sekä alku- että loppuajan vain, kun ne ovat elinkaaritilassa [Kumottu](http://uri.suomi.fi/codelist/rytj/RY_KaavanElinkaariTila/code/11).
 {% include common/clause_end.html %}


### Kaavan määrääminen voimaan osittain
[Maankäyttö- ja rakennuslain pykälässä 201](https://www.finlex.fi/fi/laki/ajantasa/1999/19990132#L26P201) (säädös 132/1999) säädetään mahdollisuudesta määrätä kaava osittain voimaan:
> Kunnanhallitus voi valitusajan kuluttua määrätä yleis- ja asemakaavan tulemaan voimaan ennen kuin se on saanut lainvoiman kaava-alueen siltä osalta, johon valitusten tai oikaisukehotuksen ei voida katsoa kohdistuvan.

{% include common/clause_start.html type="req" id="elinkaari/vaat-osittainen-voimaantulo" %}
Tallennettaessa osittain voimaan määrättävä kaava, tulee tuottavassa tietojärjestelmässä asettaa [Kaava](dokumentaatio/#kaava)-luokan objektin ja sen sisältämien tietokohteiden attribuuttien arvot seuraavasti:
* [Kaava](dokumentaatio/#kaava)-luokan objektin ```elinkaaritila```-attribuutin arvoksi asetetaan [Osittain voimassa](http://uri.suomi.fi/codelist/rytj/RY_KaavanElinkaariTila/code/09).
* [Kaava](dokumentaatio/#kaava)-luokan objektin ```voimassaoloAika```-attribuutin alkuajaksi asetaan voimaantulevaksi määräämisen ajanhetki, ja loppuaikaa ei anneta.
* Kunkin kaavan [Kaavamaarays](dokumentaatio/#kaavamaarays)- ja [Kaavasuositus](dokumentaatio/#kaavasuositus)-luokan objektin ```elinkaaritila```-attribuuttien arvoksi asetaan joko [Voimassa](http://uri.suomi.fi/codelist/rytj/RY_KaavanElinkaariTila/code/10) tai [Kumottu](http://uri.suomi.fi/codelist/rytj/RY_KaavanElinkaariTila/code/11) riippuen siitä katsotaanko valitusten tai oikaisukehotusten kohdistuvan ko. kaavamääräykseen tai kaavasuositukseen vai ei.
* ```elinkaaritila```-attribuutin arvon [Kumottu](http://uri.suomi.fi/codelist/rytj/RY_KaavanElinkaariTila/code/11) saavien [Kaavamaarays](dokumentaatio/#kaavamaarays)- ja [Kaavasuositus](dokumentaatio/#kaavasuositus)-luokan objektien ```voimassaoloAika```-attribuuteille ei anneta lainkaan arvoa.
* ```elinkaaritila```-attribuutin arvon [Voimassa](http://uri.suomi.fi/codelist/rytj/RY_KaavanElinkaariTila/code/10) saavien [Kaavamaarays](dokumentaatio/#kaavamaarays)- ja [Kaavasuositus](dokumentaatio/#kaavasuositus)-luokan objektien ```voimassaoloAika```-attribuuteille annetaan alkuajaksi asetaan voimaantulevaksi määräämisen ajanhetki, ja loppuaikaa ei anneta.
{% include common/clause_end.html %}

Kaavamääräysten ja -suositusten kumoaminen kaavan osittaisen voimaan määräyksen yhteydessä saattaa johtaa tilanteeseen, jossa tietyn [Kaavakohde](dokumentaatio/#kaavakohde)-luokan objektin alueelle ei enää kohdistu lainkaan kumoamattomia määräyksiä tai suosituksia. Tästä ei kuitenkaan automaattisesti aiheudu "reikää" kaava-alueeseen, sillä kaavan yleismääräykset voidaan edelleen haluta saattaa voimaan myös ko. kaavakohteen alueella.

{% include common/clause_start.html type="req" id="elinkaari/vaat-osittainen-voimaantulo-aluerajaus" %}
[Kaava](dokumentaatio/#kaava)-luokan tietokohteen uuden version ```aluerajaus```-attribuuttin arvo päivitetään poistamalla siitä ainoastaan kumottavia kaavamääräyksiä sisältävien kaavakohteiden geometriat vain siinä tapauksessa, että kyseinen osa kaavan alkuperäisestä alueesta halutaan jättää kokonaan kaavan suunnittelualueen ulkopuolelle. Suunnitelualueen ulkopuolelle jätettävälle alueelle ei saa olla kohdistua kumoamattomia kaavamääräyksiä tai -suosituksia.
{% include common/clause_end.html %}

### Kaavamuutokset ja vaihekaavat
Hyväksyttyjen kaavojen sisältämiä kaavamääräyksiä voidaan kumota tai korvata laatimalla kaavamuutos tai vaihekaava. Kaavatietomallissa sekä kaavamuutos että vaihekaava toteutetaan [Kaava](dokumentaatio/#kaava)-luokan avulla samoin kuin ensimmäinenkin tietylle alueelle laadittava kaava. Vaihekaavat erotetaan ensimmäisistä kaavoista ja kaavamuutoksista Kaava-luokan attribuutin ```laji``` (arvona koodisto [Kaavalaji](http://uri.suomi.fi/codelist/rytj/RY_Kaavalaji)) avulla. Vaihekaavat sisältävät tyypillisesti vain vähäisiä ja rajattuja muutoksia kaavoihin, joita niillä muutetaan. Muutettavien kaavojen kaavamääräykset säilyvät vaihekaavan alueella tyypillisesti pääosin ennallaan, ja niitä kumotaan ja korvataan vaihekaavassa vain tarpeellilta osin. Kaavamuutos puolestaan kumoaa voimaan tullessaan tyypillisesti yhden tai useamman aiemmin hyväksytyn kaavan kaikki kaavamääräykset ```aluerajaus```-attribuuttinsa määrittämällä alueella. 

{% include common/clause_start.html type="req" id="elinkaari/vaat-kumoamistieto-per-kaava" %}
Sekä kaavamuutosten että vaihekaavojen tapauksessa kaavalla kaikki kumottavat, aiemmin hyväksyttyjen kaavojen kaavamääräykset tulee yksilöidä kumoavassa kaavassa. Kutakin kaavaa kohti tulee antaa yksi [Kaava](dokumentaatio/#kaava)-luokan attribuutin ```kumoamistieto``` arvo tyyppiä [KaavanKumoamistieto](dokumentaatio/#kaavankumoamistieto), jonka ```kumottavanKaavanTunnus```-attribuutin arvo on kumottavan kaavan [viittaustunnus](#viittaustunnus)).
{% include common/clause_end.html %}

{% include common/clause_start.html type="req" id="elinkaari/vaat-kumottava-maarayksen-tunnus" %}
Kumottavat kaavamääräykset kuvataan ensisijaisesti ```kumoattavanMaarayksenTunnus```-attribuutin arvojen avulla. Attribuutin arvo on kumottavan [Kaavamaarays](dokumentaatio/#kaavamaarays)-luokan tietokohteen [viittaustunnus](#viittaustunnus).
{% include common/clause_end.html %}

 Mikäli kumottavalle kaavamääräykselle ei kumottavassa kaavavassa ole määritelty yksilöivää ja yksiselitteistä tunnusta, ei kumoamista voi kohdistaa siihen ```kumoattavanMaarayksenTunnus```-attribuutin avulla. Näin voi olla esimerkiksi kun kumottava kaava tai sen yksittäiset kaavamääräykset eivät ole saatavissa Kaavatietomallin mukaisessa muodossa. Tässä tapauksessa kaavan kumottavat alueet kuvataan ```kumottavaKaavanAlue```-attribuutin määrittämän aluerajauksen avulla.
 
{% include common/clause_start.html type="req" id="elinkaari/vaat-kumottava-kaavan-alue" %}
Kumottavasta kaavasta kumotaan kaikki kaavamäärykset, jotka on kohdistettu kokonaan ```kumottavaKaavanAlue```-attribuutin määrittämän alueen sisälle. ```kumottavaKaavanAlue```-attribuutin avulla ei voi kumota kaavan yleismääräyksiä.
 {% include common/clause_end.html %}
 
{% include common/clause_start.html type="req" id="elinkaari/vaat-kumoaa-kaavan-kokonaan" %}
 Mikäli kaavamuutoksella tai vaihekaavalla halutaan kumota kokonainen hyväksytty kaava kaikkine kaavamääräyksineen, käytetään ```kumoaaKaavanKokonaan```-attribuutin arvoa ```true```. Tällöin attribuutteja ```kumoattavanMaarayksenTunnus``` ja ```kumottavaKaavanAlue``` ei käytetä.
 {% include common/clause_end.html %}

{% include common/clause_start.html type="req" id="elinkaari/vaat-kaavamuutoksen-voimaantulo" %}
 Kun kaavamuutoksesta tai vaihekaavasta tallennetaan versio, jonka ```elinkaaritila```-attribuutin arvo on [Voimassa](http://uri.suomi.fi/codelist/rytj/RY_KaavanElinkaariTila/code/10), kaavatietovarasto päivittää niiden siinä kumottaviksi asetettujan kaavamääräysten, joiden ```elinkaaritila```-attribuutin arvo on [Voimassa](http://uri.suomi.fi/codelist/rytj/RY_KaavanElinkaariTila/code/10), attribuutteja seuraavasti *luomatta niistä uusia versioita*:
 * ```voimassaoloAika```-attribuutin päättymisaika asetetaan samaksi kuin kaavamuutoksen tai vaihekaavan ```voimassaoloAika```-attribuutin alkamisaika.
 * ```elinkaaritila```-attribuutin arvoksi asetetaan [Kumottu](http://uri.suomi.fi/codelist/rytj/RY_KaavanElinkaariTila/code/11).
 * ```tallennusAika```-attribuutin arvoksi asetetaan ajanhetki, jolloin kaavamuutos tai vaihekaava tallennettiin kaavatietovarastoon elinkaaritilassa [Voimassa](http://uri.suomi.fi/codelist/rytj/RY_KaavanElinkaariTila/code/10).
 {% include common/clause_end.html %}

 Kaavatietomalli ei sisällä omaa tietorakennettaan ajantasaiselle kaava-aineistolle, joka sisältää annetun alueella tietyllä ajanhetkellä voimassaolevat kaavamääräykset (ns. ajantasakaava), huomioiden kaavamuutosten ja vaihekaavojen vaikutukset niiltä osin kun ne ovat ko. ajanhetkellä voimassa. Tällainen toiminnallisuus on kuitenkin aivan ilmeisesti yhteisen kaavatietovaraston palveluna erittäin hyödyllinen. Kaavamääräysten ```voimassaoloAika```-attribuutin arvojen avulla tällainen ajantasainen "kaavamatto" voidaan laskea mille tahansa ajanhetkelle, olettaen, että kaikki kyseisen alueen kaavat on viety tietovarastoon kaavatietomallin mukaisessa muodossa.
 
 On huomattava, että pelkän ```elinkaaritila```-attribuutin avulla ei voida tietää, onko kaavamääräys tietyllä tarkasteluajanhetkellä lainvoimainen vai ei: Mikäli ajanhetkellä ```x``` voimaan tullut kaavamääräys on kumottu kaavamuutoksella, joka on tullut lainvoimaiseksi ajanhetkellä ```y```, on kaavamääräyksen ```elinkaaritila```-attribuutin arvo muutettu arvoon [Kumottu](http://uri.suomi.fi/codelist/rytj/RY_KaavanElinkaariTila/code/11). Kyseinen kaavamääräys on tällöin kuitenkin edelleen lainvoimainen millä tahansa ajanhetkellä ```t, x <= t < y```.

Kunkin voimassaolevan kaavamääräyksen osalta voidaan tarkastella onko se asetettu kumottavaksi vireillä olevassa, vielä ei-lainvoimaisessa kaavamuutoksessa ja vaihekaavassa hakemalla siihen sen sisältävään kaavan kohdistuvat kaavamuutokset ja vaihekaavat, ja vertaamalla niiden ```kumoamistieto```-attribuuttien arvoja kaavamäääräyksen tietoihin.

{% include common/question.html content="Pitääkö kaavakohteessa olla tieto siitä, onko kyseessä alue, jolla kyseinen kaava on ensimmäinen (koodisto 'Aiempi kaavoitustilanne', arvot esim. 'Alueella on voimassaoleva saman tasoinen kaava', 'Alueella ei ole voimassaolevaa saman tasoista kaavaa')?" %}

{% include common/question.html content="Pitäisikö yleismääräyksiä voida kumota myös sisällyttämällä koko kumottavan yleismääräystekstin? Ei-tietomallipohjaisissa kaavoissa kumottavien yleismääräysten yksilöiminen voi muutoin olla mahdotonta." %}

{% include common/question.html content="Kaavamuutoksella tai vaihekaavalla ei näiden vaatimusten mukaan voi kumota alkuperäisen kaavan yleismääräyksiä vain kaavamuutoksen tai vaihekaavana suunnittelualueen sisältä, vaikka tämä olisi tarpeen. Miten tulisi toteuttaa?" %}
-->

## Kaupunkiseutusuunnitelman elinkaaren vaiheet ja elinkaaritila-attribuutin käyttö
Kaupunkiseutusuunnitelman ja sen sisältämien suunnitelmakohteiden elinkaareen liittyvää tilaa hallitaan ko. tietokohteiden ```KaupunkiseutusuunnitelmanElinkaaritila```-attribuutin ja sen mahdolliset arvot kuvaavan [Kaupunkiseututuunnitelman tila](http://uri.suomi.fi/codelist/rytj/RY_KaupunkiseutusuunnitelmanElinkaariTila)-koodiston avulla.<!-- [Kaava](dokumentaatio/#kaava)-, [Kaavamaarays](dokumentaatio/#kaavamaarays)-, ja [Kaavasuositus](dokumentaatio/#kaavasuositus)-luokkien ```elinkaaritila```-attribuutit ovat pakollisia.-->

[Kaupunkiseutusuunnitelman elinkaaren tila](http://uri.suomi.fi/codelist/rytj/RY_KaupunkiseutusuunnitelmanElinkaaritila)-koodisto kuvaa 9 mahdollista tilaa, joissa suunnitelma voi olla sen elinkaaren eri vaiheissa:
* [Valmistelu](http://uri.suomi.fi/codelist/rytj/RY_KaupunkiseutusuunnitelmanElinkaaritila/code/01)
* [Luonnos](http://uri.suomi.fi/codelist/rytj/RY_KaupunkiseutusuunnitelmanElinkaaritila/code/02)
* [Ehdotus](http://uri.suomi.fi/codelist/rytj/RY_KaupunkiseutusuunnitelmanElinkaaritila/code/03)
* [Hyväksytty](http://uri.suomi.fi/codelist/rytj/RY_KaupunkiseutusuunnitelmanElinkaaritila/code/04)
* [Hylätty](http://uri.suomi.fi/codelist/rytj/RY_KaupunkiseutusuunnitelmanElinkaaritila/code/05)
* [Osittain voimassa](http://uri.suomi.fi/codelist/rytj/RY_KaupunkiseutusuunnitelmanElinkaaritila/code/06)
* [Voimassa](http://uri.suomi.fi/codelist/rytj/RY_KaupunkiseutusuunnitelmanElinkaaritila/code/07)
* [Kumoutunut](http://uri.suomi.fi/codelist/rytj/RY_KaupunkiseutusuunnitelmanElinkaaritila/code/08)
* [Rauennut](http://uri.suomi.fi/codelist/rytj/RY_KaupunkiseutusuunnitelmanElinkaaritila/code/09)

<!--{% include common/question.html content="Mitkä ovat ```Kumoutunut```-, ```Kumottu```-, ```Rauennut```- ja ```Hylätty``` -tilojen tarkat määritelmät ja erot?" %}

{% include common/question.html content="Kaavan pitäisi voida olla yhtäaikaa sekä ```Oikaisukehotuksen alainen``` että ```Valituksen alainen```, tämä koodisto ei mahdollista sitä. Tuleeko valitus-oikaisitilat ilmaista jotenkin muuten?" %}

Kaavojen, joiden elinkaaritila on Kaavoitusaloite,  Vireilletullut, Valmistelu, Kaavaehdotus, Tarkistettu kaavaehdotus, Hyväksytty kaava, Oikaisukehotuksen alainen tai Valituksen alainen, laadinta- ja päätösprosessi on kesken, eli niiden kaavamääräykset eivät (vielä) ole lainvoimaisia. Kaavat, jotka ovat elinkaaritilassa Osittain voimassa tai Voimassa sisältävät nykyajanhetkellä rajaamallaan alueella voimassa olevia kaavamääräyksiä. Koodit Kumottu, Kumoutunut, Rauennut ja Hylätty kuvaavat kaavan tiloja, joissa olevan kaavan elinkaari on päättynyt.-->

### Sallitut suunnitelman elinkaaren tilan muutokset
Suunnitelman elinkaaritila voi <!--sen laadinta-, päätös-, valitus-, voimassaolo- ja kumoutumisvaiheidensa-->esiintyä ja muuttua vain tässä luvussa kuvatuilla tavoilla.
<!--
{% include common/clause_start.html type="req" id="elinkaari/vaat-ensimmainen-elinkaaritila" %}
Kaavan elinkaaritila tallennettaessa kaava ensimmäistä kertaa kaavatietovarastoon voi olla jokin seuraavista riippuen Kaavan ```digitaalinenAlkupera```-attribuutin arvosta:
   * [Tietomallin mukaan laadittu](http://uri.suomi.fi/codelist/rytj/RY_DigitaalinenAlkupera/code/01): tilat Kaavoitusaloite, Vireilletullut, Valmistelu, Kaavaehdotus, Tarkistettu kaavaehdotus tai Hyväksytty kaava.
   * [Kokonaan digitoitu](http://uri.suomi.fi/codelist/rytj/RY_DigitaalinenAlkupera/code/02), [Osittain digitoitu](http://uri.suomi.fi/codelist/rytj/RY_DigitaalinenAlkupera/code/03) tai [Kaavan rajaus digitoitu](http://uri.suomi.fi/codelist/rytj/RY_DigitaalinenAlkupera/code/04): tilat Osittain voimassa, Voimassa, Kumottu, Kumoutunut tai Rauennut.
{% include common/clause_end.html %}
-->
{% include common/clause_start.html type="req" id="elinkaari/vaat-elinkaaritila-siirtymat" %}
```KaupunkiseutusuunnitelmanElinkaaritila```-attribuutin arvo voi kahden sen peräkkäisen tallennusversion välillä vain seuraavilla tavoilla:
* Tilasta ```Valmistelu``` tilaan ```Luonnos```, ```Ehdotus```, ```Hyväksytty``` tai ```Hylätty```.
* Tilasta ```Luonnos``` tilaan ```Ehdotus```, ```Hyväksytty```, tai ```Hylätty```.
* Tilasta ```Ehdotus``` tilaan ```Hyväksytty``` tai ```Hylätty```.
* Tilasta ```Hyväksytty``` tilaan ```Osittain voimassa```, ```Voimassa``` tai ```Kumoutunut```.
* Tilasta ```Osittain voimassa``` tilaan ```Kumoutunut``` tai ```Rauennut```.
* Tilasta ```Voimassa``` tilaan ```Kumoutunut``` tai ```Rauennut```.
* Tilasta ```Kumoutunut``` ei sallittuja siirtymiä.
* Tilasta ```Rauennut``` ei sallittuja siirtymiä.
{% include common/clause_end.html %}
<!--
{% include common/question.html content="Onko kaava heti lainvoimainen (ja siis sen voimassaoloaika alkanut), kun se on päätetty määrätä osittain voimaan? Vai seuraako osittain voimaan määräämispäätöksestä vielä valitusaika, jonka jälkeen kaava tulee vielä erikseen kuuluttaa lainvoimaiseksi? Jos erillinen lainvoimaiseksi kuuluttaminen on tarpeen, tulee sallia myös tilamuutos ```Osittain voimassa -> Voimassa```" %}

### Kaavamääräysten ja -suositusten elinkaaren tila
Tavallisesti kaavan sisältämien kaavamääräysten ja -suositusten elinkaaritilan arvo on sama kuin koko kaavalla, mutta ne voivat erota toisistaan kahdessa tapauksessa:
* Kaavan osittaisen voimaan määräämisen tapauksessa osa kaavamääräyksistä ja -suosituksista voidaan kumota (ks. [Kaavan osittainen määrääminen voimaan](#elinkaari-vaat-osittainen-voimaantulo))
* Kaavamuutoksen tai vaihekaavan voimaantulo aiheuttaa siinä kumottaviksi yksilöityjen kaavamääräysten ja -suositusten kumoamisen (ks. [Kaavamuutokset ja vaihekaavat](#elinkaari-vaat-kaavamuutoksen-voimaantulo))-->

### Kaupunkiseutusuunnitelman elinkaaritilan muutoksiin liittyvät käsittely- ja vuorovaikutustapahtumat
Kun kaupunkiseutusuunnitelmasta viedään kaupunkiseutusuunnitelman tietovarastoon uusi versio, jossa sen elinkaaritila on muuttunut, liittyy kyseisen suunnitelman version syntymiseen tyypillisesti jokin käsittelytapahtuma.

{% include common/clause_start.html type="req" id="elinkaari/vaat-elinkaaritilan-muutostapahtumat" %}
[Kaupunkiseutusuunnitelman](dokumentaatio/#kaupunkiseutusuunnitelma) ```KaupunkiseutusuunnitelmanElinkaaritila```-attribuutin arvon seuraavaan muutokseen tulee aina liittyä [KaupunkiseutusuunnitelmanKäsittelytapahtumanLaji](dokumentaatio/#kaupunkiseutusuunnitelmankäsittelytapahtumanlaji), jonka attribuutin arvo tulee olla elinkaarimuutosta vastaava:
<!--* Muutos tilaan [Vireilletullut](http://uri.suomi.fi/codelist/rytj/RY_KaavanElinkaariTila/code/02): Liityttävä käsittelytapahtuman laji [Kaava virelletulo](http://uri.suomi.fi/codelist/rytj/RY_KaavanKasittelytapahtumanLaji/code/04)-->
* Muutos tilaan [Hyväksytty](http://uri.suomi.fi/codelist/rytj/RY_KaupunkiseutusuunnitelmanElinkaariTila/code/04): Liityttävä käsittelytapahtuman laji [Hyväksyminen](http://uri.suomi.fi/codelist/rytj/RY_KaupunkiseutusuunnitelmanKasittelytapahtumanLaji/code/05).
<!--* Muutos tilaan [Voimassa](http://uri.suomi.fi/codelist/rytj/RY_KaavanElinkaariTila/code/07): Liityttävä käsittelytapahtuman laji [Kaavan voimaantulo](http://uri.suomi.fi/codelist/rytj/RY_KaavanKasittelytapahtumanLaji/code/13).-->

Yllä lueteltu käsittelytapahtuma tulee tallentaa samaan aikaan elinkaaritilaltaan muuttuneen suunnitelman kanssa.
{% include common/clause_end.html %}

<!--{% include common/clause_start.html type="req" id="elinkaari/vaat-ehdotuksen-nahtavilleasettaminen" %}
[Kaavan](dokumentaatio/#kaava) ```elinkaaritila```-attribuutin arvon muuttuminen arvosta [Kaavaehdotus](http://uri.suomi.fi/codelist/rytj/RY_KaavanElinkaariTila/code/04) arvoon [Tarkistettu kaavaehdotus](http://uri.suomi.fi/codelist/rytj/RY_KaavanElinkaariTila/code/05) tai [Hyväksytty kaava](http://uri.suomi.fi/codelist/rytj/RY_KaavanElinkaariTila/code/06) vaatii, että kaavatietovarastossa on sekä [Kasittelytapahtuma](dokumentaatio/#kasittelytapahtuma) lajia [Kaavaehdotuksen nähtäville asettaminen](http://uri.suomi.fi/codelist/rytj/RY_KaavanKasittelytapahtumanLaji/code/06) että [Vuorovaikutustapahtuma](dokumentaatio/#vuorovaikutustapahtuma) lajia [Nähtävilläolo](http://uri.suomi.fi/codelist/rytj/RY_KaavanVuorovaikutustapahtumanLaji/code/01), joista molemmat viittavat johonkin ko. kaavan aiemmista [Kaavaehdotus](http://uri.suomi.fi/codelist/rytj/RY_KaavanElinkaariTila/code/04)-tilassa olevista versioista assosiaatiolla ```liittyvaAsia```. Vuorovaikutustapahtuman attribuutin ```tapahtumaAika``` tulee kuvata aikaväli, jonka aikana kaavaehdotus on ollut nähtävillä.
{% include common/clause_end.html %}

{% include common/clause_start.html type="req" id="elinkaari/vaat-tarkistetun-ehdotuksen-nahtavilleasettaminen" %}
[Kaavan](dokumentaatio/#kaava) ```elinkaaritila```-attribuutin arvon muuttuminen arvosta [Tarkistettu kaavaehdotus](http://uri.suomi.fi/codelist/rytj/RY_KaavanElinkaariTila/code/05) arvoon [Hyväksytty kaava](http://uri.suomi.fi/codelist/rytj/RY_KaavanElinkaariTila/code/06) vaatii, että kaavatietovarastossa on sekä [Kasittelytapahtuma](dokumentaatio/#kasittelytapahtuma) lajia [Tarkistetun kaavaehdotuksen nähtäville asettaminen](http://uri.suomi.fi/codelist/rytj/RY_KaavanKasittelytapahtumanLaji/code/07) että [Vuorovaikutustapahtuma](dokumentaatio/#vuorovaikutustapahtuma) lajia [Nähtävilläolo](http://uri.suomi.fi/codelist/rytj/RY_KaavanVuorovaikutustapahtumanLaji/code/01), joista molemmat viittavat johonkin ko. kaavan aiemmista [Tarkistettu kaavaehdotus](http://uri.suomi.fi/codelist/rytj/RY_KaavanElinkaariTila/code/05)-tilassa olevista versioista assosiaatiolla ```liittyvaAsia```. Vuorovaikutustapahtuman attribuutin ```tapahtumaAika``` tulee kuvata aikaväli, jonka aikana tarkistettu kaavaehdotus on ollut nähtävillä.
{% include common/clause_end.html %}

{% include common/clause_start.html type="rec" id="elinkaari/suos-nahtavillaolopaikka" %}
Mikäli kaavaehdotus tai tai tarkistettu kaavaehdotus on nähtävillä tietyssä fyysisessä paikassa, on suositeltavaa ilmaista kyseisen paikan sijainti [Vuorovaikutustapahtuma](dokumentaatio/#vuorovaikutustapahtuma)-luokan attribuutin ```sijainti```-attribuutin avulla.
{% include common/clause_end.html %}

{% include common/question.html content="Pitäiskö olla käsittelytapahtuman laji ```Kaavan määrääminen voimaan osittain```? Osittaisesta määrämisestä voimaan tulee kuitenkin tehdä päätös, jolle ei nyt ole oikein luontevaa käsittelytapahtuman lajia" %}

Huomaa, että muutos tilaan [Kumottu](http://uri.suomi.fi/codelist/rytj/RY_KaavanElinkaariTila/code/11) voi liittyvä joko käsittelytapahtuman lajiin [Kaavan kumoaminen](http://uri.suomi.fi/codelist/rytj/RY_KaavanKasittelytapahtumanLaji/code/11) tai kaavan kumoamiseen [kaavamuutokseen tai vaihekaavan](#kaavamuutokset-ja-vaihekaavat) lainvoimaiseksi tulon yhteydessä.
-->


<!--
## Esimerkkejä elinkaaritapahtumista

### Kaavan luominen ja muokkaus ennen ensimmäistä tallennusta kaavatietovarastoon

### Kaavan ensimmäinen tallennus kaavatietovarastoon

### Kaavan muokatun version tallennus kaavatietovarastoon

### Käsittely- tai vuorovaikutustapahtuman lisääminen

### Kaavan hyväksyminen

### Kaavan määrääminen voimaan osittain

### Kaavan voimaantulosta kuuluttaminen

### Kaavan, sen yksittäisten kaavamääräysten tai -suositusten kumoaminen
-->