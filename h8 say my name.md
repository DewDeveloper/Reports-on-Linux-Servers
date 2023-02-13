<h1>h8 Say my name</h1>

<h3>a) Domain-nimen vuokraaminen  ja asettaminen virtuaaliserveriä varten</h3>

[03:05] Koska olen se kitupiikki mikä olen, katsoin ensimmäisenä, mitä Github Education -etuohjelmalla oli tarjota. Löysin NameCheapin tarjouksen .me-domaineista, joten tartuin siihen.

![namecheap](https://user-images.githubusercontent.com/105177604/218389094-f1fdae37-75e5-46b4-86bf-572076b0bf34.jpg)

[03:08] Ajattelin ensin, että ottaisin sukunimi.me-domainin, koska se oli vapaana. Mutta sitten ajattelin, että voisin ottaa paremmin sivuston luonnetta kuvaavan domainin. Testasin, olisiko testworld.me vielä vapaana. Se oli, joten otin sen.

![testworld](https://user-images.githubusercontent.com/105177604/218389227-9a3299d9-e230-486a-8bfb-d4b5e8abb69e.JPG)

[03:16] Kuljin rekisteröitymisprosessin läpi ja törmäsin sellaiseen ongelmaan, ettei koulun email kelvannut (poistin kuvasta tunnistetiedot, ml. sähköpostiosoitteen alkuosan).

![fail](https://user-images.githubusercontent.com/105177604/218389286-828f71b3-c1ae-42be-805e-bfb685555686.JPG)

[03:17] Päätin, että käytän jotakin toista palveluntarjoajaa, koska olin saanut Namecheapilta huonoa palvelua.

[03:19] Valitsin Github Educationista Name.comin, joka myös tarjosi ilmaista domainia. Kirjauduin sivustolle Github-tililläni.

![namecom](https://user-images.githubusercontent.com/105177604/218389744-753fbb14-b0b4-488c-a276-13d2106d2ccd.jpg)

[03:20] Pienen pallottelun jälkeen valitsin domainiksi testworld.engineer. Sivusto tarjosi myös kuukauden ilmaista pilveä DigitalOceanista, mutta jätin väliin.

![namecom 1](https://user-images.githubusercontent.com/105177604/218389869-b1a26c75-a9bb-47af-bfbe-b9da0208e7ae.JPG)

[03:23] Loin tunnuksen. Sivusto ei kysynyt kuin käyttäjää/henkilöä koskevat tiedot, luottokorttia ei tarvittu. Sen jälkeen tuli alapuolinen vahvistussivu.

![namecom 2](https://user-images.githubusercontent.com/105177604/218390034-2b6eb865-98a0-4fcb-990d-1fdcae00c322.JPG)

[03:25] Sain ilmoituksen, että tarvitaan vielä vahvistus sähköpostitse tai puhelimitse. Valitsin sähköpostin, sain vahvistuskoodin ja syötin sen sivustolle.
 
![icann vaatii](https://user-images.githubusercontent.com/105177604/218390148-39ff123f-c15d-4e1c-b7ea-6861ec78c7d1.JPG)

![namecom 3](https://user-images.githubusercontent.com/105177604/218390417-4d18922d-a422-4f6c-86df-7ba58acfe548.jpg)

[03:28] Etsiskelin vähän aikaa oikeaa tapaa asettaa domain osoittamaan virtuaalipalvelimen ip-osoitteeseen. Ensin yritin "URL FORWARDING" -nappulaa, mutta sitä kautta en onnistunut. Menin ylälaidan "My domain" -linkistä sivulle, jolla domain näkyi. Manage-kohdan alta valitsin Manage DNS Records. Poistin valmiiksi olleet "" ja "*" -tiedot, jotka osoittivat ip-osoitteeseen 75.126.101.237. Sitten asetin alapuolisen kuvan mukaisesti uudet ohjaukset virtuaalipalvelimelle.

![dns manage 1](https://user-images.githubusercontent.com/105177604/218390527-933ede35-f9cf-4ba1-aad6-43bb65646653.jpg)

[03:47] Muutaman minuutin odottelun jälkeen domain osoitti virtuaalipalvelimelleni.

![toimii](https://user-images.githubusercontent.com/105177604/218390574-efc57d1f-5555-457f-9380-601792556852.JPG)

Voit vierailla sivustollani [tästä linkistä](http://www.testworld.engineer).

<h3>b) Nimen tietojen tutkiminen käyttäen komentoja "host" ja "dig"</h3>

[04:05] <code>Host testworld.engineer</code> -komento toimi suoraan. Se kertoo domainiin liittyvän isännän ip-osoitteen.

![host](https://user-images.githubusercontent.com/105177604/218391010-fe46dadd-a9ed-40ee-88f6-576e9b74953b.JPG)

[04:08] <code>dig testworld.engineer</code> -komentoa ei tunnistettu. Yritin asentaa Digin, mutta se ei onnistunut.

[04:10] Luin phoenixNAP:n sivuilta Digistä[1]. Asensin sen komennolla <code>sudo-apt-get install dnsutils</code>. Komennolla <code>dig testworld.engineer</code> sain aikaiseksi raportin.

![dig onnistui](https://user-images.githubusercontent.com/105177604/218390646-f6d90c2e-7a19-4c61-8cbf-9206dfc96d99.JPG)

[04:24] Käytin tulkinnassa apuna phoenixNAP:n verkkosivua[1].

<ul>
<li>Ensimmäisenä kerrotaan Digin versionumero ja domain, jota "kaivellaan". </li>
<li>"->>HEADER<<-" sisältää palvelimelta saadun vastauksen. </li>
<li>"OPT PSEUDOSECTION" sisältää DNS:n mahdollisen laajennusjärjestelmän ("EDNS"), mahdolliset liput ("flags") ja UDP-paketin koon. </li>
<li>"QUESTION SECTION" sisältää kyselyn sisällön, ensin domainnimen, sitten kyselyn tyypin (tässä "IN", Internet) ja kirjauksen (tässä "A", Address). </li>
<li>"ANSWER SECTION" sisältää kyselyn kohteena olleen palvelimen, tietueen päivitysaikavälin, tyypin (tässä "IN"), kyselyn tyypin (tässä "A") ja domainnimeen yhdistyvän palvelimen IP-osoitteen. </li>
<li>Lopussa on vastauksen saamiseen kulunut aika, nimipalvelimen ip-osoite ja portti, aikaleima ja nimipalvelimelta saadun vastauksen koko.</li>
</ul>

<h3>Lähteet:</h3>

<ol>
<li>PhoenixNAP. How to Use Linux dig Command (DNS Lookup). 2020. Luettavissa: https://phoenixnap.com/kb/linux-dig-command-examples. Luettu: 13.2.2023.</li>
</ol>
