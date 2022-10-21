---
layout: "default"
description: ""
id: "dokumentaatio"
status: "Ehdotus"
---

# Loogisen tason kaupunkiseutusuunnitelman tietomalli
{:.no_toc}

1. 
{:toc}

## Yleistä
Loogisen tason kaupunkiseutusuunnitelman tietomalli määrittelee tietomallimuotoisen kaupunkiseutusuunnitelman tietorakenteet ja sisällöt mahdollisimman riippumattomasti tietystä toteutusteknologiasta tai tiedon fyysisestä esitystavasta (esim. relaatiotietokanta, tietyn ohjelmointikielen tietorakenteet, XML, JSON). Tämä tietomallikuvaus mahdollistaa kaupunkiseutusuunnitelman tietojen tuottamisen, tallentamisen ja siirtämisen järjestelmästä toiseen ilman siten, että tietosisältö ja sen merkistys säilyy.

Tietomalli on kuvattu UML-kielellä ja sen graafinen luokkakaavioesitys on nähtävillä [omalla sivullaan](../uml/). Tietomallissa hyödynnetään luokkia {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/" title="RY-yhteisistä komponenteista" %}.

## Normatiiviset viittaukset
Seuraavat dokumentit ovat välttämättömiä tämän dokumentin täysipainoisessa soveltamisessa:

* [ISO 639-2:1998 Codes for the representation of names of languages — Part 2: Alpha-3 code][ISO-639-2]
* [ISO 8601-1:2019 Date and time — Representations for information interchange — Part 1: Basic rules][ISO-8601-1]
* [ISO 19103:2015 Geographic information — Conceptual schema language][ISO-19103]
* [ISO 19107:2019 Geographic information — Spatial schema][ISO-19107]
* [ISO 19108:2002 Geographic information — Temporal schema][ISO-19108]
* [ISO 19109:2015 Geographic information — Rules for application schema][ISO-19109]
* [ISO 19505-2:ISO/IEC 19505-2:2012, Information technology — Object Management Group Unified Modeling Language (OMG UML) — Part 2: Superstructure][ISO-19505-2]
* [ISO 19156 Geographic information — Observations, measurements and samples][ISO-19156]
* {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/" title="RY-yhteiset komponentit" %}

## Standardienmukaisuus
Looginen kaupunkiseutusuunnitelman tietomalli perustuu [ISO 19109][ISO-19109]-standardin yleinen kohdetietomalliin (General Feature Model, GFM), joka määrittelee rakennuspalikat paikkatiedon ISO-standardiperheen mukaisten sovellusskeemojen määrittelyyn. GFM kuvaa muun muassa metaluokat ```FeatureType```, ```AttributeType``` ja ```FeatureAssociationType```.  Kaikki tietokohteet, joilla on tunnus ja jota voivat esiintyä erillään toisista kohteista on määritelty kohdetyypeinä (stereotyyppi ```FeatureType```. Sellaiset tietokohteet, joilla ei ole omaa tunnusta ja jotka voivat esiintyä vain kohdetyyppien attribuuttien arvoina on määritelty [ISO 19103][ISO-19103]-standardin ```DataType```-stereotyypin avulla.

[ISO 19109][ISO-19109] -standardin lisäksi tietomalli perustuu muihin paikkatiedon ISO-standardeihin, joista keskeisimpiä ovat [ISO 19103][ISO-19103] (UML-kielen käyttö paikkatietojen mallinnuksessa), [ISO 19107][ISO-19107] (sijaintitiedon mallintaminen) ja [ISO 19108][ISO-19108] (aikaan sidotun tiedon mallintaminen).

Tietomallin [Mittaus](#mittaus)- ja [Mittari](#mittari)-luokat on mallinnettu [ISO 19156][ISO-19156]-standardin käsitteisiin perustuen.

### Rakennetun ympäristön yhteisistä komponenteista hyödynnetyt luokat

#### VersioituObjekti

Katso {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#versioituobjekti" title="Yhteiset tietokomponentit::Versioituobjekti" %}.

#### AlueidenkäyttöJaRakentamisasia

Katso {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#alueidenkäyttöjarakentamisasia" title="Yhteiset tietokomponentit::AlueidenkäyttöJaRakentamisasia" %}.

#### Alueidenkäyttöasia

Katso {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#alueidenkäyttöjasia" title="Yhteiset tietokomponentit::Alueidenkäyttöasia" %}.

#### Alueidenkäyttösuunnitelma

Katso {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#alueidenkäyttösuunnitelma" title="Yhteiset tietokomponentit::Alueidenkäyttösuunnitelma" %}.

#### Toimija

Katso {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#toimija" title="Yhteiset tietokomponentit::Toimija" %}.

#### HallinnollinenAlue

Katso {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#hallinnollinenalue" title="Yhteiset tietokomponentit::HallinnollinenAlue" %}.

#### AlueidenkäyttöJaRakentamispäätös

Katso {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#alueidenkäyttöjarakentamispäätös" title="Yhteiset tietokomponentit::AlueidenkäyttöJaRakentamispäätös" %}.

#### Tietoyksikkö

Katso {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#tietoyksikkö" title="Yhteiset tietokomponentit::Tietoyksikkö" %}.

#### RakennetunYmpäristönKohde

Katso {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#rakennetunympäristönkohde" title="Yhteiset tietokomponentit::RakennetunYmpäristönKohde" %}.

#### Lähtötietoaineisto

Katso {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#lähtötietoaineisto" title="Yhteiset tietokomponentit::Lähtötietoaineisto" %}.

#### Asiakirja

Katso {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#asiakirja" title="Yhteiset tietokomponentit::Asiakirja" %}.

#### Tapahtuma

Katso {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#tapahtuma" title="Yhteiset tietokomponentit::Tapahtuma" %}.

#### AbstraktiSuureenArvo

Katso {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#abstraktiasuureenarvo" title="Yhteiset tietokomponentit::AbstraktiSuureenArvo" %}.

#### SuureenArvo

Katso {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#suureenarvo" title="Yhteiset tietokomponentit::SuureenArvo" %}.

#### Suure

Katso {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#suure" title="Yhteiset tietokomponentit::Suure" %}.

#### OminaisuudenArvo

Katso {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#ominaisuudenarvo" title="Yhteiset tietokomponentit::OminaisuudenArvo" %}.

#### Ajanhetkiarvo

Katso {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#ajanhetkiarvo" title="Yhteiset tietokomponentit::Ajanhetkiarvo" %}.

#### Aikaväliarvo

Katso {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#aikaväliarvo" title="Yhteiset tietokomponentit::Aikaväliarvo" %}.

#### GeometriaArvo

Katso {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#geometriaarvo" title="Yhteiset tietokomponentit::GeometriaArvo" %}.

#### Koodiarvo

Katso {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#koodiarvo" title="Yhteiset tietokomponentit::Koodiarvo" %}.

#### NumeerinenArvo

Katso {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#numeerinenarvo" title="Yhteiset tietokomponentit::NumeerinenArvo" %}.

#### Korkeuspiste

Katso {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#korkeuspiste" title="Yhteiset tietokomponentit::Korkeuspiste" %}.

#### NumeerinenArvoväli

Katso {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#numeerinenarvoväli" title="Yhteiset tietokomponentit::NumeerinenArvoväli" %}.

#### Korkeusväli

Katso {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#korkeusväli" title="Yhteiset tietokomponentit::Korkeusväli" %}.

#### Tunnusarvo

Katso {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#tunnusarvo" title="Yhteiset tietokomponentit::Tunnusarvo" %}.

#### Tekstiarvo

Katso {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#tekstiarvo" title="Yhteiset tietokomponentit::Tekstiarvo" %}.

#### AbstraktiAsianElinkaaritila

Katso {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#abstraktiasianelinkaaritila" title="Yhteiset tietokomponentit::AbstraktiAsianElinkaaritila" %}.

#### AbstraktiAsiakirjanLaji

Katso {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#abstraktiasiakirjanlaji" title="Yhteiset tietokomponentit::AbstraktiAsiakirjanLaji" %}.

#### AbstraktiLähtötietoaineistonLaji

Katso {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#abstraktilähtötietoaineistonlaji" title="Yhteiset tietokomponentit::AbstraktiLähtötietoaineistonLaji" %}.

#### AbstraktiVuorovaikutustapahtumanLaji

Katso {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#abstraktivuorovaikutustapahtumanlaji" title="Yhteiset tietokomponentit::AbstraktiVuorovaikutustapahtumanLaji" %}.

#### AbstraktiKäsittelytapahtumanLaji

Katso {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#abstraktikäsittelytapahtumanlaji" title="Yhteiset tietokomponentit::AbstraktiKäsittelytapahtumanLaji" %}.



### Muulla määritellyt luokat ja tietotyypit

#### CharacterString

Kuvaa yleisen merkkijonon, joka koostuu 0..* merkistä, merkkijonon pituudesta, merkistökoodista ja maksimipituudesta. Määritelty rajapinta-tyyppisenä [ISO 19103][ISO-19103]-standardissa.

#### LanguageString

Kuvaa kielikohtaisen merkkijonon. Laajentaa [CharacterString](#characterstring)-rajapintaa lisäämällä siihen ```language```-attribuutin, jonka arvo on ```LanguageCode```-koodiston arvo. Kielikoodi voi [ISO 19103][ISO-19103]-standardin määritelmän mukaan olla mikä tahansa ISO 639 -standardin osa.

#### Number

Kuvaa yleisen numeroarvon, joka voi olla kokonaisluku, desimaaliluku tai liukuluku. Määritelty rajapintana [ISO 19103][ISO-19103]-standardissa.

#### Integer

Laajentaa [Number](#number)-rajapintaa kuvaamaan numeron, joka on kokonaisluku ilman murto- tai desimaaliosaa. Määritelty rajapintana [ISO 19103][ISO-19103]-standardissa.

#### Decimal

Laajentaa [Number](#number)-rajapintaa kuvaamaan numeron, joka on desimaaliluku. Decimal-rajapinnan toteuttava numero voidaan ilmaista virheettä yhden kymmenysosan tarkkuudella. Määritelty rajapintana [ISO 19103][ISO-19103]-standardissa. Decimal-numeroita käytetään, kun desimaalien käsittelyn tulee olla tarkkaa, esim. rahaan liityvissä tehtävissä.

#### Real

Laajentaa [Number](#number)-rajapintaa kuvaamaan numeron, joka on tarkkudeltaan rajoitettu liukuluku. Real-rajapinnan numero voi ilmaista tarkasti vain luvut, jotka ovat 1/2:n (puolen) potensseja. Määritelty rajapintana [ISO 19103][ISO-19103]-standardissa. Käytännössä esitystarkkuus riippuu numeron tallentamiseen varattujen bittien määrästä, esim. ```float (32-bittinen)``` (tarkkuus 7 desimaalia) ja ```double (64-bittinen)``` (tarkkuus 15 desimaalia).

#### TM_Object

Aikamääreiden yhteinen yläluokka, käytetään, mikäli arvo voi olla joko yksittäinen ajanhetki tai aikaväli. Määritelty luokkana [ISO 19108][ISO-19108]-standardissa. 

#### TM_Instant

Kuvaa yksittäisen ajanhetken 0-ulotteisena ajan geometriana, joka vastaa pistettä avaruudessa. Määritelty luokkana [ISO 19108][ISO-19108]-standardissa. Aikapisteen arvo on määritelty ```TM_Position```-luokalla yhdistelmänä [ISO 8601][ISO-8601-1]-standin mukaisia päivämäärä- tai kellonaika-kenttiä tai näiden yhdistelmää, tai muuta ```TM_TemporalPosition```-luokan avulla kuvattua aikapistettä. Viimeksi mainitun luokan attribuutti ```indeterminatePosition``` mahdollistaa ei-täsmällisen ajanhetken ilmaisemisen liittämällä mahdolliseen arvoon luokittelun tuntematon, nyt, ennen, jälkeen tai nimi.

#### TM_Period

Kuvaa aikavälin [TM_Instant](#tm_instant)-tyyppisten ```begin```- ja ```end```-attribuuttien avulla. Molemmat attribuutit ovat pakollisia, mutta voivat sisältää tuntemattoman arvon  ```indeterminatePosition = unknown``` -attribuutin arvon avulla annettuna. Määritelty luokkana [ISO 19108][ISO-19108]-standardissa.

#### URI

Määrittää merkkijonomuotoisen Uniform Resource Identifier (URI) -tunnuksen [ISO 19103][ISO-19103]-standardissa. URIa voi käyttää joko pelkkänä tunnuksena tai resurssin paikantimena (Uniform Resource Locator, URL).

#### Geometry

Kaikkien geometria-tyyppien yhteinen rajapinta [ISO 19107][ISO-19107]-standardissa. Tyypillisimpiä [ISO 19107][ISO-19107]-standardin Geometry-rajapintaa laajentavia rajapintoja ovat ```Point```, ```Curve```, ```Surface``` ja ```Solid``` sekä ```Collection```, jota käyttämällä voidaan kuvata geometriakokoelmia (multipoint, multicurve, multisurface, multisolid).

#### Point
Täsmälleen yhdestä pisteestä koostuva geometriatyyppi. Määritelty rajapintana [ISO 19107][ISO-19107]-standardissa.


## Tietomallin yleispiirteet

Kaavatietomallin UML-luokkakaaviot ovat saatavilla erillisellä [UML-kaaviot](../uml/)-sivulla.

## Luokat

### Kaupunkiseutusuunnitelma

Erikoistaa luokkaa [Alueidenkäyttösuunnitelma](#alueidenkäyttösuunnitelma), stereotyyppi: FeatureType (kohdetyyppi).

Kuvaa käsitteen [Kaupunkiseutusuunnitelma](../../kasitemalli/#kaupunkiseutusuunnitelma).

**Assosiaatiot**

Roolinimi        | Kohde               | Kardinaliteetti | Kuvaus
-----------------|---------------------|-----------------|------------------------------------
vuorovaikutussuunnitelma | [Vuorovaikutussuunnitelma](#vuorovaikutussuunnitelma) | 0..1 | Kaupunkiseutusuunnitelman laadintavaiheen vuorovaikutuksen suunnitelma.
selostus         | [SuunnitelmanSelostus](#suunnitelmanselostus) | 0..1 | Kaupunkiseutusuunnitelman selostusosa.
suunnitelmanTavoite | [Tavoite](#tavoite) | 0..*         | Suunnitelmaan sisältyvä tavoite.
kehittämisperiaate | [YleinenKehittämisperiaate](#yleinenkehittämisperiaate) | 0..* | Suunnitelman yleinen kehittämisperiaate.
suunnitelmanKohde | [Suunnitelmakohde](#suunnitelmakohde) | 0..* | Suunnitelman paikkatietokohde, johon sisältyy yksi tai useampi toiminto.
laatija          | [Toimija](#toimija) | 0..*            | Suunnitelman laatija.

Peritty attribuutti ```elinkaaritila``` on rajoitettu tyyppiin [KaupunkiseutusuunnitelmanElinkaaritila](#kaupunkiseutusuunnitelmanelinkaaritila).

### Vuorovaikutussuunnitelma

Erikoistaa luokkaa [VersioituObjekti](#versioituobjekti), stereotyyppi: FeatureType (kohdetyyppi).

Kuvaa käsitteen [Vuorovaikutussuunnitelma](../../kasitemalli/#vuorovaikutussuunnitelma).

**Ominaisuudet**

Nimi             | Tyyppi              | Kardinaliteetti | Kuvaus
-----------------|---------------------|-----------------|------------------------------------
tiedosto         | [Asiakirja](#asiakirja) | 0..*        | Asiakirjat, jotka kuvaavat kaupunkiseutusuunnitelman vuorovaikutussuunnitelman.

**Assosiaatiot**

Roolinimi        | Kohde               | Kardinaliteetti | Kuvaus
-----------------|---------------------|-----------------|------------------------------------
suunnitelma      | [Kaupunkiseutusuunnitelma](#kaupunkiseutusuunnitelma) | 1 | Kaupunkiseutusuunnnitelma, jonka vuorovaikutusta kuvataan.

### SuunnitelmanSelostus

Erikoistaa luokkaa [VersioituObjekti](#versioituobjekti), stereotyyppi: FeatureType (kohdetyyppi).

Kuvaa käsitteen [Suunnitelman selostus](../../kasitemalli/#suunnitelman-selostus).

**Ominaisuudet**

Nimi             | Tyyppi              | Kardinaliteetti | Kuvaus
-----------------|---------------------|-----------------|------------------------------------
tiedosto         | [Asiakirja](#asiakirja) | 0..*        | Asiakirjat, jotka kuvaavat kaupunkiseutusuunnitelman selostuksen.

**Assosiaatiot**

Roolinimi        | Kohde               | Kardinaliteetti | Kuvaus
-----------------|---------------------|-----------------|------------------------------------
suunnitelma      | [Kaupunkiseutusuunnitelma](#kaupunkiseutusuunnitelma) | 1 | Kaupunkiseutusuunnnitelma, jota selostetaan.

### Suunnitelmakohde

Erikoistaa luokkaa [RakennetunYmpäristönKohde](#rakennetunympäristönkohde), stereotyyppi: FeatureType (kohdetyyppi).

Kuvaa käsitteen [Suunnitelman kohde](../../kasitemalli/#suunnitelman-kohde).

**Ominaisuudet**

Nimi             | Tyyppi              | Kardinaliteetti | Kuvaus
-----------------|---------------------|-----------------|------------------------------------
elinkaaritila    | [KohteenElinkaaritila](#kohteenelinkaaritila) | 0..1 | Kohteen olemassaolotieto suunnitelman laadinnan aikana.


**Assosiaatiot**

Roolinimi        | Kohde               | Kardinaliteetti | Kuvaus
-----------------|---------------------|-----------------|------------------------------------
suunnitelma      | [Kaupunkiseutusuunnitelma](#kaupunkiseutusuunnitelma) | 1 | Kaupunkiseutusuunnnitelma, johon kohde kuuluu.
toiminto         | [KohteenToiminto](#kohteentoiminto) | 1..*        | Kohteeseen liitetty toiminto.

Perityn attribuutin ```geometria``` kardinaliteetti on rajoitettu yhteen (attribuutti on pakollinen). Perityn attribuutin ```pystysuuntainenRajaus``` käyttö on kielletty.

### KohteenToiminto

Erikoistaa luokkaa [VersioituObjekti](#versioituobjekti), stereotyyppi: FeatureType (kohdetyyppi).

Kuvaa käsitteen [Kohteen toiminto](../../kasitemalli/#kohteen-toiminto).

**Ominaisuudet**

Nimi             | Tyyppi              | Kardinaliteetti | Kuvaus
-----------------|---------------------|-----------------|------------------------------------
nimi             | [LanguageString](#languagestring) | 0..* | Toiminnon nimi.
kuvaus           | [LanguageString](#languagestring) | 0..* | Toiminnon kuvausteksti.
toimintolaji     | [Toimintolaji](#toimintolaji) | 0..1  | Toimintoa kuvaava luokka.
infrastruktuurilaji | [Infrastruktuurilaji](#infrastruktuurilaji) | 1 | Toiminnon infrastruktuuriluokitus.
elinkaarimuutoksenTyyppi | [ElinkaarimuutoksenLaji](#elinkaarimuutoksenlaji) | 0..1 | Toiminnon suunniteltua muutosta ko. kohteessa kuvaava luokka.
teema            | [KaupunkiseutusuunnittelunTeema](#kaupunkiseutusuunnittelunteema) | 0..* | Teemaluokittelu.

**Assosiaatiot**

Roolinimi        | Kohde               | Kardinaliteetti | Kuvaus
-----------------|---------------------|-----------------|------------------------------------
kohde            | [SuunnitelmanKohde](#suunnitelmakohde) | 1 | Kohde, jonka toiminto on kyseessä.
kehittämisperiaate | [ToiminnonKehittämisperiaate](#toiminnonkehittämisperiaate) | 0..* | Toimintoon liittyvä kehittämisperiaate.
liittyväTavoite  | [Tavoite](#tavoite) | 0..* | Toimintoon liittyvä tavoite.

### Kehittämisperiaate

Erikoistaa luokkaa [VersioituObjekti](#versioituobjekti), stereotyyppi: FeatureType (kohdetyyppi). Luokka on abstrakti.

Kuvaa käsitteen [Kehittämisperiaate](../../kasitemalli/#kehittämisperiaate).

**Ominaisuudet**

Nimi             | Tyyppi              | Kardinaliteetti | Kuvaus
-----------------|---------------------|-----------------|------------------------------------
nimi             | [LanguageString](#languagestring) | 0..* | Periaatteen nimi.
kuvaus           | [LanguageString](#languagestring) | 0..* | Periaatteen sanallinen kuvaus.
teema            | [KaupunkiseutusuunnittelunTeema](#kaupunkiseutusuunnittelunteema) | 0..* | Teemaluokittelu.

**Assosiaatiot**

Roolinimi        | Kohde               | Kardinaliteetti | Kuvaus
-----------------|---------------------|-----------------|------------------------------------
liittyväTavoite  | [Tavoite](#tavoite) | 0..*            | Tavoite, johon kehittämisperiaate liittyy.
hyväksyjä        | [Toimija](#toimija) | 0..*            | Toimija, joka on hyväksynyt periaatteen. 

### YleinenKehittämisperiaate

Erikoistaa luokkaa [Kehittämisperiaate](#kehittämisperiaate), stereotyyppi: FeatureType (kohdetyyppi).

**Assosiaatiot**

Roolinimi        | Kohde               | Kardinaliteetti | Kuvaus
-----------------|---------------------|-----------------|------------------------------------
toteuttavaPeriaate  | [ToiminnonKehittämisperiaate](#toiminnonkehittämisperiaate) | 0..* | Toiminnon kehittämisperiaate, joka toteuttaa tätä yleistä periaatetta.
suunnitelma      | [Kaupunkiseutusuunnitelma](#kaupunkiseutusuunnitelma) | 1 | Suunnitelma, johon tämä kehittämisperiaate kuuluu.

### ToiminnonKehittämisperiaate

Erikoistaa luokkaa [Kehittämisperiaate](#kehittämisperiaate), stereotyyppi: FeatureType (kohdetyyppi).

**Ominaisuudet**

Nimi             | Tyyppi              | Kardinaliteetti | Kuvaus
-----------------|---------------------|-----------------|------------------------------------
laji             | [ToiminnonKehittämisperiaatteenLaji](#toiminnonkehittämisperiaatteenlaji) | 1 | Kehittämisperiaatteen luokka.
merkittävyys     | [KehittämisperiaatteenMerkittävyys](#kehittämisperiaatteenmerkittävyys) | 0..1 | Kuvaa kehittämisperiaatteen merkittävyyttä suhteessa muihin kehittämisperiaatteisiin.
toteutusaikataulu | [Aikataulu](#aikataulu) | 0..1       | Kehittämisperiaatteen toteutuksen tavoiteaikataulu.

**Assosiaatiot**

Roolinimi        | Kohde               | Kardinaliteetti | Kuvaus
-----------------|---------------------|-----------------|------------------------------------
toteutettavaPeriaate  | [YleinenKehittämisperiaate](#yleinenkehittämisperiaate) | 0..* | Yleinen kehittämisperiaate, jota  tämä toiminnon kehittämisperiaate toteuttaa.
toiminto         | [KohteenToiminto](#kohteentoiminto) | 1..* | Toiminto, johon kehittämisperiaate kohdistetaan.


### Tavoite

Erikoistaa luokkaa [Tietoyksikkö](#tietoyksikkö), stereotyyppi: FeatureType (kohdetyyppi).

Kuvaa käsitteen [Tavoite](../../kasitemalli/#tavoite).

**Ominaisuudet**

Nimi             | Tyyppi              | Kardinaliteetti | Kuvaus
-----------------|---------------------|-----------------|------------------------------------
kuvaus           | [LanguageString](#languagestring) | 0..* | Tavoitteen sanallinen kuvaus.
lähde            | [TavoitteenLähteenLaji](#tavoitteenlähteenlaji) | 0..* | Kertoo minkä tyyppisestä lähteestä tavoite on peräisin.
teema            | [KaupunkiseutusuunnittelunTeema](#kaupunkiseutusuunnittelunteema) | 0..* | Teemaluokittelu.
toteutumisaikataulu | [Aikataulu](#aikataulu) | 0..1       | Tavoitteen toteutumisen tavoiteaikataulu.


**Assosiaatiot**

Roolinimi        | Kohde               | Kardinaliteetti | Kuvaus
-----------------|---------------------|-----------------|------------------------------------
suunnitelma      | [Kaupunkiseutusuunnitelma](#kaupunkiseutusuunnitelma) | 0..1 | Kaupunkiseutusuunnnitelma, jonka tavoite kuuluu koko suunnitelman tavoitteena. Tavoite voi liittyä suunnitelmaan myös vain KohteenToimintojen kautta.
liittyväPeriaate | [Kehittämisperiaate](#kehittämisperiaate) | 0..*          | Kehittämisperiaate, joka liittyy tavoitteeseen.
lähtötilanMittaus | [Mittaus](#mittaus) | 0..1 | Tavoitteseen liitetyn ominaisuuden arvon lähtöarvion määrittämiseksi tehty mittaus tai arviointi ja mitattu arvo.
osatavoite       | [Tavoite](#tavoite) | 0..* | Viittaus tämän tavoitteen osatavoitteisiin, joiden saavuttamisesta tämän tavoitteen saavuttaminen riippuu.
kokonaistavoite  | [Tavoite](#tavoite) | 0..1 | Viittaus tavoitteeseen, jonka tavoittaminen riippuu tämän tavoitteen saavuttamisesta.
asettaja         | [Toimija](#toimija) | 0..* | Tavoitteen asettaja.
perustelevaAineisto | [SeudullinenTietoaineisto](#seudullinentietoaineisto) | 0..* | Tavoitteen asettamiseen liittyä, perusteleva tietoaineisto.
liittyväToiminto | [KohteenToiminto](#kohteentoiminto) | 0..* | KohteenToiminto, johon tavoite on kohdistettu.

Perityn assosiaation ```kohdistus``` käyttö on kielletty rajoituksella. Kohdistus [Suunnitelmakohteeseen](#suunnitelmakohde) vain [KohteenToiminnon](#kohteentoiminto) kautta.

### SeudullinenTietoaineisto

Erikoistaa luokkaa [Lähtötietoaineisto](#lähtötietoaineisto), stereotyyppi: FeatureType (kohdetyyppi).

Kuvaa käsitteen [Seudullinen tietoaineisto](../../kasitemalli/#seudullinen-tietoaineisto).

**Ominaisuudet**

Nimi             | Tyyppi              | Kardinaliteetti | Kuvaus
-----------------|---------------------|-----------------|------------------------------------
teema            | [KaupunkiseutusuunnittelunTeema](#kaupunkiseutusuunnittelunteema) | 0..* | Teemaluokittelu.

Peritty attribuutti ```laji``` on rajoitettu tyyppiin [SeudullisenTietoaineistonLaji](#seudullisentietoaineistonlaji) tai sen alityyppeihin.

### Mittaus

Erikoistaa luokkaa [Tapahtuma](#tapahtuma), stereotyyppi: FeatureType (kohdetyyppi). Vastaa ISO 19156 Observations, measurements and samples -standardin (OMS) Observation-käsitettä.

Kuvaa käsitteen [Mittaustapahtuma](../../kasitemalli/#mittaustapahtuma).

**Ominaisuudet**

Nimi             | Tyyppi              | Kardinaliteetti | Kuvaus
-----------------|---------------------|-----------------|------------------------------------
mittausAika      | [TM_Object](#tm_object) | 0..1         | Ajanhetki tai aikaväli, jonka aikaista suureen arvoa mittauksen tai arvioinnin tulos kuvaa. Vastaa OMS-standardin ```phenomenonTime```-attribuuttia.
tulosAika        | [TM_Instant](#tm_instant) | 1          | Ajanhetki, jolloin mittauksen tulos on kirjattu muistiin tai julkaistu. Vastaa OMS-standardin ```resultTime```-attribuuttia.
tulos            | [SuureenArvo](#suureenarvo) | 1       | Mittauksen tuloksena saatu suureen arvo. Vastaa OMS-standardin ```result```-assosiaatiota ja ```observedProperty```-attribuuttia yhdessä.

**Assosiaatiot**

Roolinimi        | Kohde               | Kardinaliteetti | Kuvaus
-----------------|---------------------|-----------------|------------------------------------
käytettyMittari  | [Mittari](#mittari) | 0..1            | Menetelmä tai väline, jolla mittaus tai arviointi on tehty. Vastaa OMS-standardin ```observingProcedure```-attribuuttia.
käytettyAineisto | [SeudullinenTietoaineisto](#seudullinentietoaineisto) | 0..* | Aineisto, jota on käytetty mittauksen tai arvionnin pohjana.

OMS-standardin ```featureOfInterest```-assosiaatio toteutuu joko Tavoitteen ```kohdistus```- (Suunnitelmakohteet) tai ```suunnitelma```-asssosiaation (koko Kaupunkiseutusuunnitelma) kautta.

### Mittari

Erikoistaa luokkaa [VersioituObjekti](#versioituobjekti), stereotyyppi: FeatureType (kohdetyyppi). Vastaa ISO 19156 Observations, measurements and samples -standardin (OMS) ObservationProcedure-käsitettä.

Kuvaa käsitteen [Mittari](../../kasitemalli/#mittari).

**Ominaisuudet**

Nimi             | Tyyppi              | Kardinaliteetti | Kuvaus
-----------------|---------------------|-----------------|------------------------------------
nimi             | [LanguageString](#languagestring) | 0..* | Mittarin nimi.
kuvaus           | [LanguageString](#languagestring) | 0..* | Mittarin sanallinen kuvaus.
ulkoinenTunnus   | [Tunnusarvo](#tunnusarvo) | 0..*      | Mittarin tunnus tunnettujen mittarien kokoelmassa.
tuotettavaSuure  | [Suure](#suure)     | 1               | Suure, jonka arvoja mittari tuottaa. 

**Assosiaatiot**

Roolinimi        | Kohde               | Kardinaliteetti | Kuvaus
-----------------|---------------------|-----------------|------------------------------------
mittaus          | [Mittaus](#mittaus) | 0..*            | Mittaus, joka on tehty käyttäen tätä mittaria.

### Aikataulu

Stereotyyppi: DataType (tietotyyppi).

Kuvaa käsitteen [Tavoitteen toteutumisaikataulu](../../kasitemalli/#tavoitteen-toteutumisaikataulu) yhdessä luokan [Vaihe](#vaihe) kanssa.

**Ominaisuudet**

Nimi             | Tyyppi              | Kardinaliteetti | Kuvaus
-----------------|---------------------|-----------------|------------------------------------
aikataulunVaihe  | [Vaihe](#vaihe)     | 0..*            | Suunniteltuun aikatauluun sisällytetty ajallinen vaihe.

### Vaihe

Stereotyyppi: DataType (tietotyyppi).

Aikaväli, jonka aikana jotakin on määrä tapahtua tai jonkin [Tietoyksikön](#tietoyksikkö) ominaisuuden on määrä saavuttaa tietty tavoitearvo.

**Ominaisuudet**

Nimi             | Tyyppi              | Kardinaliteetti | Kuvaus
-----------------|---------------------|-----------------|------------------------------------
otsikko          | [LanguageString](#languagestring) | 0..* | Vaiheen nimi.
aloitusAika      | [TM_Instant](#tm_instant) | 0..1       | Aikavälin alku.
päättymisAika    | [TM_Instant](#tm_instant) | 0..1       | Aikavälin loppu.
kuvaus           | [LanguageString](#languagestring) | 0..* | Vaiheen sanallinen kuvaus.
tavoitearvo      | [AbstraktiSuureenArvo](#abstraktisuureenarvo) | 0..1 | Suureen arvo, joka on määrä saavuttaa vaiheen aikana.



### Koodistot

#### KaupunkiseutusuunnitelmanElinkaaritila

Erikoistaa luokkaa [AbstraktiAsianElinkaaritila](#abstraktiasianelinkaaritila), stereotyyppi: CodeList (koodisto)

Laajennettavuus: [Ei laajennettavissa](http://inspire.ec.europa.eu/registry/extensibility/none)

{% include common/codelistref.html registry="rytj" id="RY_KaupunkiseutusuunnitelmanElinkaaritila" name="Kaupunkiseutusuunnitelman elinkaaren tila" %}

#### KaupunkiseutusuunnitelmanAsiakirjanLaji

Eriskoistaa luokkaa [AbstraktiAsiakirjanLaji](#abstraktiasiakirjanlaji), stereotyyppi: CodeList (koodisto)

Laajennettavuus: [Ei laajennettavissa](http://inspire.ec.europa.eu/registry/extensibility/none)

{% include common/codelistref.html registry="rytj" id="RY_KaupunkiseutusuunnitelmanAsiakirjanLaji" name="Kaupunkiseutusuunnitelman asiakirjan laji" %}

#### SeudullisenTietoaineistonLaji

Erikoistaa luokkaa [AbstraktiLähtötietoaineistonLaji](#abstraktilähtötietoaineistonlaji), stereotyyppi: CodeList (koodisto)

Laajennettavuus: [Laajennettavissa kaikilla tasoilla](http://inspire.ec.europa.eu/registry/extensibility/open)

{% include common/codelistref.html registry="rytj" id="RY_SeudullisenTietoaineistonLaji" name="Seudullisen tietoaineiston laji (kaupunkiseutusuunnitelma)" %}

#### KaupunkiseutusuunnitelmanVuorovaikutustapahtumanLaji

Erikoistaa luokkaa [AbstaktiVuorovaikutustapahtumanLaji](#abstraktivuorovaikutustapahtumanlaji), stereotyyppi: CodeList (koodisto)

Laajennettavuus: [Ei laajennettavissa](http://inspire.ec.europa.eu/registry/extensibility/none)

{% include common/codelistref.html registry="rytj" id="RY_KaupunkiseutusuunnitelmanVuorovaikutustapahtumanLaji" name="Kaupunkiseutusuunnitelman vuorovaikutustapahtuman laji" %}

#### KaupunkiseutusuunnitelmanKäsittelytapahtumanLaji

Erikoistaa luokkaa [AbstaktiKäsitteltapahtumanLaji](#abstraktikäsittelytapahtumanlaji), stereotyyppi: CodeList (koodisto)

Laajennettavuus: [Ei laajennettavissa](http://inspire.ec.europa.eu/registry/extensibility/none)

{% include common/codelistref.html registry="rytj" id="RY_KaupunkiseutusuunnitelmanKasittelytapahtumanLaji" name="Kaupunkiseutusuunnitelman käsittelytapahtuman laji" %}

#### KaupunkiseutusuunnittelunTeema

Stereotyyppi: CodeList (koodisto)

Laajennettavuus: [Laajennettavissa kaikilla tasoilla](http://inspire.ec.europa.eu/registry/extensibility/open)

{% include common/codelistref.html registry="rytj" id="RY_KaupunkiseutusuunnittelunTeema" name="Kaupunkiseutusuunnittelun teema" %}


#### Toimintolaji

Stereotyyppi: CodeList (koodisto)

Laajennettavuus: [Laajennettavissa kaikilla tasoilla](http://inspire.ec.europa.eu/registry/extensibility/open)

{% include common/codelistref.html registry="rytj" id="RY_Toimintolaji" name="Toimintolaji (kaupunkiseutusuunnitelma)" %}

#### Infrastruktuurilaji

Stereotyyppi: CodeList (koodisto)

Laajennettavuus: [Laajennettavissa kaikilla tasoilla](http://inspire.ec.europa.eu/registry/extensibility/open)

{% include common/codelistref.html registry="rytj" id="RY_Infrastruktuurilaji" name="Infrastruktuurilaji (kaupunkiseutusuunnitelma)" %}

#### ToiminnonKehittämisperiaatteenLaji

Stereotyyppi: CodeList (koodisto)

Laajennettavuus: [Laajennettavissa kaikilla tasoilla](http://inspire.ec.europa.eu/registry/extensibility/open)

{% include common/codelistref.html registry="rytj" id="RY_ToiminnonKehittamisperiaatteenLaji" name="Toiminnon kehittämisperiaatteen laji (kaupunkiseutusuunnitelma)" %}

#### KohteenElinkaaritila

Stereotyyppi: CodeList (koodisto)

Laajennettavuus: [Ei laajennettavissa](http://inspire.ec.europa.eu/registry/extensibility/none)

{% include common/codelistref.html registry="rytj" id="RY_KohteenElinkaaritila" name="Kohteen elinkaaritila (kaupunkiseutusuunnitelma)" %}

#### ElinkaarimuutoksenLaji

Stereotyyppi: CodeList (koodisto)

Laajennettavuus: [Ei laajennettavissa](http://inspire.ec.europa.eu/registry/extensibility/none)

{% include common/codelistref.html registry="rytj" id="RY_ElinkaarimuutoksenLaji" name="Elinkaarimuutoksen laji (kaupunkiseutusuunnitelma)" %}

#### KehittämisperiaatteenMerkittävyys

Stereotyyppi: CodeList (koodisto)

Laajennettavuus: [Ei laajennettavissa](http://inspire.ec.europa.eu/registry/extensibility/none)

{% include common/codelistref.html registry="rytj" id="RY_KehittamisperiaatteenMerkittavyys" name="Kehittämisperiaatteen merkittävyys (kaupunkiseutusuunnitelma)" %}

#### TavoitteenLähteenLaji

Stereotyyppi: CodeList (koodisto)

Laajennettavuus: [Laajennettavissa kaikilla tasoilla](http://inspire.ec.europa.eu/registry/extensibility/open)

{% include common/codelistref.html registry="rytj" id="RY_TavoitteenLahteenLaji" name="Tavoitteen lähteen laji (kaupunkiseutusuunnitelma)" %}

#### SelostuksenOsanLaji

Koodisto, joka kuvaa myöhemmin rakenteistettavan kaupunkiseutusuunnitelman selostuksen osien lajit.

Stereotyyppi: CodeList (koodisto)

Laajennettavuus: [Laajennettavissa kaikilla tasoilla](http://inspire.ec.europa.eu/registry/extensibility/open)

{% include common/codelistref.html registry="rytj" id="RY_SelostuksenOsanLaji" name="Selostuksen osan laji (kaupunkiseutusuunnitelma)" %}

#### MitoitussuureenLaji

Koodisto kaupupunkiseutusuunnitelmien mitoitussuureiden vakiointia ja kuvaamista varten.

Stereotyyppi: CodeList (koodisto)

Laajennettavuus: [Laajennettavissa kaikilla tasoilla](http://inspire.ec.europa.eu/registry/extensibility/open)

{% include common/codelistref.html registry="rytj" id="RY_MitoitussuureenLaji" name="Mitoitussuureen laji (kaupunkiseutusuunnitelma)" %}

[ISO-8601-1]: https://www.iso.org/standard/70907.html "ISO 8601-1:2019 Date and time — Representations for information interchange — Part 1: Basic rules"
[ISO-639-2]: https://www.iso.org/standard/4767.html "ISO 639-2:1998 Codes for the representation of names of languages — Part 2: Alpha-3 code"
[ISO-19103]: https://www.iso.org/standard/56734.html "ISO 19103:2015 Geographic information — Conceptual schema language"
[ISO-19107]: https://www.iso.org/standard/66175.html "ISO 19107:2019 Geographic information — Spatial schema"
[ISO-19108]: https://www.iso.org/standard/26013.html "ISO 19108:2002 Geographic information — Temporal schema"
[ISO-19109]: https://www.iso.org/standard/59193.html "ISO 19109:2015 Geographic information — Rules for application schema"
[ISO-19505-2]: https://www.iso.org/standard/52854.html "ISO/IEC 19505-2:2012, Information technology — Object Management Group Unified Modeling Language (OMG UML) — Part 2: Superstructure"
[ISO-19156]: https://www.iso.org/standard/82463.html "ISO/DIS 19156 Geographic information — Observations, measurements and samples"
