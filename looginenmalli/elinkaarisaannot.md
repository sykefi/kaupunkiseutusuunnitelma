---
layout: "default"
description: ""
id: "elinkaarisaannot"
status: "Ehdotus"
---

# Elinkaarisäännöt
{:.no_toc}

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

Kaupunkiseutusuunnitelman tietomallissa UUID-muotoisia tunnuksia suositellaan käytettäväksi [identiteettiTunnus](#identiteettitunnus) ja [tuottajakohtainenTunnus](#tuottajakohtainen-tunnus) -attribuuttien arvoina.


## Kaupunkiseutusuunnitelman tietomallin kohteiden elinkaaren hallinnan periaatteet
Kaupunkiseutusuunnitelman tietomallin elinkaarisäännöt mahdollistavat tietomallin tietokohteiden käsittelyn, tallentamisen ja muuttamisen hallitusti sekä niiden laatimis- että voimassaolovaiheissa. Kaupunkiseutusuunnitelman tietomallin mukaiset tietosisällöt ovat aineistoja, joita käsitellään hajautetusti kuntien tietojärjestelmissä. Tämän vuoksi niiden tunnusten, viittausten ja versionnin hallintaan on syytä kiinnittää erityistä huomiota.

Seuraavat keskeiset periaatteet ohjaavat kaupunkiseutusuunnitelman tietomallin elinkaaren hallintaa:
* Kukin kaupunkiseutusuunnitelman tietovarastoon tallennettu versio suunnitelmasta ja sen sisältämistä yksittäisistä tietokohteista saa pysyvän, versiokohtaisen tunnuksen.
* Kuhinkin kaupunkiseutusuunnitelman tietovarastoon tallennettun tietokohteen versioon voidaan viitata sen pysyvän tunnuksen avulla.
* Kaupunkiseutusuunnitelman tietomallin tietokohteiden väliset viittaukset toteutetaan hallitusti sekä kaupunkiseutusuunnitelman tietoa tuottavissa tietojärjestelmissä että yhteisissä kaupunkiseutusuunitelman tietovarastoissa.
* Kaupunkiseutusuunnitelman tietovarasto vastaa pysyvien tunnusten luomisesta ja antamisesta tallennettaville tietokohteille.

Kaupunkiseutusuunnitelman tietomallin mukaisten aineistojen tallentamisessa erotetaan toisistaan tietojen tuottaminen ja muokkaus sisäisesti niiden tuottamiseen ja muokkaamiseen käytettävissä tietojärjestelmissä ja niiden hallinta yhteisessä versiohallitussa kaupunkiseutusuunnitelman tietovarastossa. Kaupunkiseutusuunnitelman tietomallin ei ole mielekästä asettaa vaatimuksia suunnitelmatietoa tuottavien tietojärjestelmien tunnusten ja versioiden hallintaan, vaan tietomallissa tulee varautua siihen, että yhteiseen tietovarastoon tallennettavia tietoja on muokattu ja tallennettu sisäisesti tuntematon määrä kertoja ennen ensimmäistä viemistä yhteiseen tietovarastoon, ja samoin tuntematon määrä kertoja kunkin yhteiseen varastoon vietävän version välillä. Näin ollen on mahdollista, että suunnitelmasta voi olla joissain tietojärjestelmissä tallennettuna paikallisia versiota, joita ei ole koskaan viety yhteiseen kaupunkiseutusuunnitelman tietovarastoon.

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

Yhteinen kaupunkiseutusuunnitelman tietovarasto on vastuussa uusien identiteettitunnusten luomisesta tarvittaessa tallennustapahtumien yhteydessä, ja niiden välittämisestä tiedoksi tallentavalle tietojärjestelmälle. Tallentavan tietojärjestelmän tulee tallentaa itselleen kopiot tietovaraston tallennustapahtuman yhteydessä palauttamista suunnitelman ja sen tietokohteiden identiteettitunnuksista, sillä ne tulee sisällyttää ko. tietokohteiden seuraavien versioden tallennettavaksi lähetettäviin objekteihin.

{% include common/clause_start.html type="req" id="elinkaari/vaat-identiteettitunnus-gen" %}
* Mikäli tallennettavalle tietokohteelle ei ole annettu ```identiteettitunnus```-attribuuttia, tai tietovarasto ei sisällä sellaista saman luokan tietokohdetta, jolla sama ```identiteettiTunnus```-attribuutin arvo, kaupunkisuunnitelman tietovarasto luo ko. objektille uuden identiteettitunnuksen, joka korvaa tuottavan tietojärjestelmän objektille mahdollisesti antaman ```identiteettiTunnus```-attribuutin arvon. Tällöin objektia pidetään uuden tietokohteen ensimmäisenä versiona.
* Mikäli tietovarasto sisältää saman luokan tietokohteen, jolla on sama ```identiteettiTunnus```-attribuutin arvo kuin tallennetavalla objektilla, objekti tallennetaan kaupunkiseutusuunnitelman tietovarastoon ko. tietokohteen uutena versiona. Tällöin tallennettavan objektin ```identiteettiTunnus```-attribuutin arvo ei muutu.
{% include common/clause_end.html %}

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
Kaupunkiseutusuunnitelman tietovarasto vastaa ```nimiavaruus```-attribuuttien asettamisesta tallennustapahtuman yhteydessä. Tuottavan tietojärjestelmän mahdollisesti antamat arvot korvataan.
{% include common/clause_end.html %}

Esimerkki: ```http://uri.suomi.fi/object/rytj/alueidenkayttojarakentamisasia```

### Viittaustunnus
{% include common/clause_start.html type="req" id="elinkaari/vaat-viittaustunnus-maar" %}
Viittaustunnus yksilöi suunnitelman tietokohteen yhden, keskitettyyn kaupunkiseutusuunnitelman tietovaraston tallennetun kehitysversion globaalisti. Kaupunkiseutusuunnitelman tietomallin tietokohteissa paikallinen tunnus kuvataan attribuutilla ```/viittausTunnus```.
{% include common/clause_end.html %}

{% include common/clause_start.html type="req" id="elinkaari/vaat-viittaustunnus-form" %}
Viittaustunnus on HTTP URI -muotoinen ja se muodostuu nimiavaruudesta, tietokohteen luokan nimestä ja paikallisesta tunnuksesta yhdessä kauttaviivoilla (```/```) erotettuina.
{% include common/clause_end.html %}

{% include common/clause_start.html type="req" id="elinkaari/vaat-nimiavaruus-gen" %}
Kaupunkiseutusuunnitelman tietovarasto vastaa ```/viittausTunnus```-attribuuttien asettamisesta tallennustapahtuman yhteydessä. Tuottavan tietojärjestelmän mahdollisesti antamat arvot korvataan.
{% include common/clause_end.html %}

Tallentavan tietojärjestelmän ei siis tarvitse tallentaa luotuja viittaustunnuksia itselleen seuraavia tallennuksia varten.

{% include common/clause_start.html type="rec" id="elinkaari/suos-viittaustunnus-ohj" %}
Viittaustunnuksen on suositeltavaa ohjautua aina ko. tietokohteen version tietosisältöön kulloinkin toiminnassa olevassa kaupunkiseutusuunnitelman tietovaraston latauspalvelussa.
{% include common/clause_end.html %}

### Tuottajakohtainen tunnus

{% include common/clause_start.html type="req" id="elinkaari/vaat-tuottajakohtainen-tunnus-maar" %}
Suunnitelmatietoa tuottavat järjestelmät voivat niin halutessaan käyttää tuottajakohtaista tunnusta niiden omien tietojärjestelmäspesifisten tunnusten antamiseen kaupunkiseutusuunnitelman tietomallin tietokohteille. Kaupunkiseutusuunnitelman tietomallin tietokohteissa tuottajakohtainen tunnus kuvataan attribuutilla ```tuottajakohtainenTunnus```.
{% include common/clause_end.html %}

{% include common/clause_start.html type="req" id="elinkaari/vaat-tuottajakohtainen-tunnus-gen" %}
Kaupunkiseutusuunnitelman tietovarasto ei koskaan muuta tuottavan tietojärjestelmän mahdollisesti asettamia tuottajakohtaisia tunnuksia, ja ne palautetaan sellaisenaan ladattaessa tietokohteita tietovarastosta.
{% include common/clause_end.html %}

Tietojärjestelmät voivat käyttää tuottajakohtaisia tunnuksia kohdistamaan kaupunkiseutusuunnitelman tietovarastoon ja paikallisiin tietojärjestelmiin tallennettuja tietokohteita toisiinsa esimerkiksi päivitettäessä niiden tallennuksen yhteydessä syntyneitä tunnuksia, vertailtaessa kaupunkiseutusuunnitelman tietovarastoon tallennettuja kohteita ja paikallisia kohteita toisiinsa, sekä esitettäessä validointipalvelun tuloksia suunnitteluohjelmiston käyttäjälle.

Tuottajakohtaisilta tunnuksilta ei vaadita yksilöivyyttä tai mitään tiettyä yhtenäistä muotoa, mutta UUID-muodon käyttäminen tarjoaa hyvin määritellyn ja standardoidun tavan luoda tuottajakohtaisista tunnuksista yksilöiviä eri tietojärjestelmien kesken. Tästä saattaa olla etua haluttaessa tehdä tuotettavista suunnitelmatiedoista mahdollisimman järjestelmäriippumattomia ja esimerkiksi taata tuottajakohtaisten tunnusten yksilöivyys yli mahdollisten suunnitelmatietoa tuottavien tietojärjestelmien vaihdosten ja päivitysten. 

{% include common/clause_start.html type="rec" id="elinkaari/suos-tuottajakohtainen-tunnus-form" %}
Tuottajakohtaisen tunnuksen suositeltu muoto on UUID.
{% include common/clause_end.html %}

Esimerkki: ```k-123445```

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
Kullakin koodiston koodilla on oltava pysyvä tunnus, joka sellaisenaan yksilöi kyseisen koodin globaalisti ilman erillistä tietoa koodistosta, johon koodi kuuluu. Koodin tunnus on HTTP URI -muotoinen.
{% include common/clause_end.html %}

{% include common/clause_start.html type="req" id="elinkaari/vaat-alakoodi-maar" %}
Olkoon koodi ```A``` mikä tahansa hierarkisen koodiston sisältämä koodi. Koodin ```A``` alakoodilla tarkoitetaan koodia, joka on hierarkiassa sijoitettu koodin ```A``` alle. Koodi voi olla useamman ylemmän tason koodin alakoodi vain mikäli ko. ylemmän tason koodit ovat alakoodisuhteessa keskenään.
{% include common/clause_end.html %}

Käytännössä tietyn koodin alakoodit voidaan tunnistaa vertaamalla niiden tunnuksia:

{% include common/clause_start.html type="req" id="elinkaari/vaat-alakoodi-tunnus" %}
Koodin ```A``` alakoodin ```B``` tunnus alkaa koodin ```A``` tunnuksella ja sisältää sen jälkeen yhden tai useamman merkin.
{% include common/clause_end.html %}

## Muutokset ja tietojen versionti
{% include common/clause_start.html type="req" id="elinkaari/vaat-pysyva-sisalto" %}
Kukin suunnitelman tai sen osien tallennusoperaatio yhteiseen tietovarastoon muodostaa uuden version tallennettavista tietokohteista, mikäli yksittäinen tietokohde on miltään osin muuttunut verrattuna sen edelliseen versioon. Myös muutokset muissa kaupunkiseutusuunnitelman tietomallin tietokohteissa, joihin tietokohteesta on viittaus, lasketaan tietokohteen muutoksiksi. Tallennetun tietokohteen version sisältö ei voi muuttua tallennuksen jälkeen, poislukien sen voimassaolon päättymiseen, seuraavaan versioon linkittämiseen ja elinkaaritilaan liittyvät attribuutit, joita kaupunkiseutusuunnitelman tietovarasto itse päivittää tietyissä tilanteissa.
{% include common/clause_end.html %}

Näin taataan ulkoisten viittausten eheys, sillä suunnitelman kaikkien kohteiden paikalliset ja viittaustunnukset viittaavat aina vain tietyn, sisällöllisesti muuttumattomaan versioon viittausta kohteesta. Suositeltavaa on, että kaikki tallennusversiot myös pidetään pysyvästi tallessa, jotta mahdolliset keskinäiset ja ulkopuolelta tulevat linkit eivät mene rikki muutosten yhteydessä.

### Muutosten leviäminen viittausten kautta
Kaupunkiseutusuunnitelman tietomallin tietokohteiden keskinäiset viittaukset kohdistuvat aina viitattavien tietokohteiden tiettyyn versioon, ja toisaalta kaikki kohteiden sisällölliset muutokset johtavat uusien versioiden tallentamiseen. Siten kohteiden välisten linkkien kohdetietoa täytyy muuttaa, mikäli halutaan viitata jollain tapaa muuttuneeseen kohteeseen. Tämä päivitystarve johtaa edelleen myös viittaavan tietokohteen uuden version luomiseen, vaikka ainoa muuttunut tieto olisi linkki uuteen versioon viitatusta tietokohteesta. Molempiin suuntiin tietokohteiden välillä tehty linkitys saattaa siten johtaa hyvin laajalle leviävään muutosketjuun. Muutosten leviämistä voidaan rajoittaa  kaikkiin suunnitelman tietokohteisiin tekemällä linkitys tietokohteiden välillä vain yhteen suuntaan, esimerkiksi vain joko suunnitelmasta suunnitelmakohteisiin ja suunnitelmakohteista kohteen toimintoihin (ylhäältä alas), tai toisinpäin (alhaalta ylös). 

Kaupunkiseutusuunnitelmantietomallissa kukin [Suunnitelmakohde](dokumentaatio/#suunnitelmakohde) on linkitetty kahdensuuntaisesti suunnitelmaan ja kukin [KohteenToiminto](dokumentaatio/#kohteentoiminto) kahdensuuntaisesti suunnitelmakohteisiin, joiden alueita ne koskevat. Tällöin yhden kohteen toiminnon muuttaminen johtaa uuden version luomiseen muutettavan kohteen toiminnon lisäksi myös siihen linkitetyistä suunnitelmakohteista, ja edelleen niihin linkitetystä kaupunkiseutusuunnitelma-objektista, mikä puolestaan johtaa lopulta uusien versioiden luomiseen kaikista ko. suunnitelman muistakin suunnitelmakohteista ja kohteen toiminnoista, koska kaupunkiseutusuunnitelma-objektiin päin osoittavat linkit pitää muuttaa osoittamaan sen uuteen versioon.



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


Yksittäisen tietokohteen yksityiskohtainen muutoshistoria kaupunkiseutusuunnitelman tietovarastossa saadaan seuraavalla sen ```VersioituObjekti``` -assosiaatioita. Ainoa muutos, joka ei näy tietokohteen omana versionaan, on kohteen kumoutuminen, jolloin sen viimeisimmän version tietoja päivitetään sen elinkaaritilan, voimassaolon ja tallennusajan osalta.

{% include common/question.html content="Pitääkö [VersioituObjekti](dokumentaatio/#versioituobjekti)-luokalle lisätä attribuutti ```ensimmainenTallennusAika```, joka kertoo ko. version alkuperäisen tallennusajan? Kumoutumisen yhteydessä ```tallennusAika```-attribuutin arvoa muutetaan, jolloin hukkuu tieto ko. version alkuperäisestä tallennusajankohdasta." %}

Attribuutin ```viimeisinMuutos``` arvo kuvaa ajanhetkeä, jolloin ko. tietokohteeseen on tehty sisällöllinen muutos tiedontuottajan tietojärjestelmässä. Tiedontuottajan järjestelmän osalta ei vaadita tiukkaa versiontipolitiikkaa, eli ```paikallinenTunnus```-attribuutin päivittämistä jokaisen tietokohteen muutoksen johdosta. ```viimeisinMuutos```-attribuutin päivittämien riittää kuvaamaan tiedon todellisen muuttumisajankohdan.

## Kaupunkiseutusuunnitelman elinkaaren vaiheet ja elinkaaritila-attribuutin käyttö
Kaupunkiseutusuunnitelman ja sen sisältämien suunnitelmakohteiden elinkaareen liittyvää tilaa hallitaan ko. tietokohteiden ```KaupunkiseutusuunnitelmanElinkaaritila```-attribuutin ja sen mahdolliset arvot kuvaavan [Kaupunkiseututuunnitelman tila](http://uri.suomi.fi/codelist/rytj/RY_KaupunkiseutusuunnitelmanElinkaariTila)-koodiston avulla.

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

### Sallitut suunnitelman elinkaaren tilan muutokset
Suunnitelman elinkaaritila voi esiintyä ja muuttua vain tässä luvussa kuvatuilla tavoilla.

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

### Kaupunkiseutusuunnitelman elinkaaritilan muutoksiin liittyvät käsittely- ja vuorovaikutustapahtumat
Kun kaupunkiseutusuunnitelmasta viedään kaupunkiseutusuunnitelman tietovarastoon uusi versio, jossa sen elinkaaritila on muuttunut, liittyy kyseisen suunnitelman version syntymiseen tyypillisesti jokin käsittelytapahtuma.

{% include common/clause_start.html type="req" id="elinkaari/vaat-elinkaaritilan-muutostapahtumat" %}
[Kaupunkiseutusuunnitelman](dokumentaatio/#kaupunkiseutusuunnitelma) ```KaupunkiseutusuunnitelmanElinkaaritila```-attribuutin arvon seuraavaan muutokseen tulee aina liittyä [KaupunkiseutusuunnitelmanKäsittelytapahtumanLaji](dokumentaatio/#kaupunkiseutusuunnitelmankäsittelytapahtumanlaji), jonka attribuutin arvo tulee olla elinkaarimuutosta vastaava:
* Muutos tilaan [Hyväksytty](http://uri.suomi.fi/codelist/rytj/RY_KaupunkiseutusuunnitelmanElinkaariTila/code/04): Liityttävä käsittelytapahtuman laji [Hyväksyminen](http://uri.suomi.fi/codelist/rytj/RY_KaupunkiseutusuunnitelmanKasittelytapahtumanLaji/code/05).

Yllä lueteltu käsittelytapahtuma tulee tallentaa samaan aikaan elinkaaritilaltaan muuttuneen suunnitelman kanssa.
{% include common/clause_end.html %}