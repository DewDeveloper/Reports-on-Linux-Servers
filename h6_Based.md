<h1>h6 Based</h1>

<h3>x) Tiivistelmät</h3>

<h5>Apache Software Foundation 2023: Getting Started[1]</h5>

<ul>
<li>URL (Uniform Resource Locator) määrittää protokollan (esim. "http"), serverinimen (esim. "www.apache.org") ja polun ("URL path", esim. /docs/current/getting-started.html) sekä mahdollisesti serverille annettavia argumentteja (esim. "?arg=value")</li>
<li>Kun asiakas tekee pyynnön palvelimelle, polku selvittää, mitä asiakas pyytää</li>
<li>Palvelin lähettää vastauksen ("response"), jossa on statuskoodi ("status code") ja mahdollisesti "response body"</li>
<li>Otettaessa yhteys palvelimelle asiakkaan täytyy ensin selvittää palvelimen ip-osoite DNS:stä (Domain Name System)</li>
<li>Useampi isäntänimi ("hostname") voi viitata samaan ip-osoitteeseen, ja yhteen palvelimeen voi liittyä useampi kuin yksi ip-osoite</li>
<li>Paikallisessa testauksessa hosts-tiedostoon voi asettaa isäntänimiä ja niihin liittyviä ip-osoitteita</li>
<li>Apache konfiguroidaan tekstitiedostoilla, oletussijainti on "/usr/local/apache2/conf"</li>
<li>Konfigurointi tapahtuu asettamalla konfiguraatiodirektiivi ("configuration directives") näihin tiedostoihin</li>
<li>Konfiguroinnissa päätettävä, kuinka laajalti halutaan vaikuttaa ja sijoitettava konfiguraatiodirektiivi sen mukaan haluttuun paikkaan tiedostorakenteessa</li>
<li>Verkkosivun sisältö voidaan karkeasti jakaa staattiseen ja dynaamiseen sisältöön</li>
<li>Lokitiedostot tärkeitä adminille ongelmia ratkottaessa</li>
<li>Lokitiedostoihin voidaan sisällyttää tapahtumien id, jolloin on selvää, mikä virhe liittyy mihinkin tapahtumaan (esim. kirjautumiseen)</li>
</ul>

<h5>Apache Software Foundation 2023: Name-based Virtual Host Support[2]</h5>

<ul>
<li>Virtuaali-isäntä voidaan selvittää ip-osoitteen ("IP-based") tai isäntänimen ("hostname") pohjalta</li>
<li>Yleensä kannattaa käyttää nimiin pohjautuvaa järjestelyä, koska silloin omalla DNS-palvelimella voi kartoittaa jokaisen isäntänimen oikeaan IP-osoitteeseen ja sitten konfiguroida Apachen tunnistamaan eri isäntänimet</li>
<li>Tärkeää muistaa, että nimiin pohjautuvassa isännän selvityksessä selvitetään ensin nimen perusteella oikea IP-osoite ja vasta oikeassa IP-osoitteessa olevalla palvelimella oikea isäntä, johon pyyntö kohdistuu</li>
<li>Palvelinpäässä pyyntö voi ohjautua myös pyynnössä olevan ip-osoitteen ja portin perusteella, jos on ilmeistä, mihin isäntään pyyntö kohdistuu</li>
<li>Jos pyynnön palvelinnimeä ei löydy, niin pyyntö ohjautuu listan ensimmäiselle virtuaali-isännälle</li>
<li>"VirtualHost"-koodiblokki jokaiselle eri isännälle ja sen sisään ainakin "ServerName" ja "DocumentRoot"</li>
<li>"ServerAlias"-direktiivi mahdollistaa saman palvelimen tavoittamisen useammalla nimellä (esim. .fi ja .com -domainpäätteet?)</li>
</ul>

<h3>a) Apachen etusivun vaihto</h3>

[11:27] Menin pääkäyttäjälläni ("matiask") käyttäjän "esimerkki1" "public_html"-kansioon ja yritin poistaa "index.html"-tiedoston. Se epäonnistui, mutta sudona uudelleen yrittäessäni onnistuin.

![1](https://user-images.githubusercontent.com/105177604/216962125-3c21cb5a-6d6f-43ed-ab0b-af5100e2e3ae.JPG)

[11:30] Vaihdoin käyttäjää ja selasin itseni "public_html"-kansioon. Tein sinne uuden "index.html"-tiedoston mukaillen Karvisen esimerkkiä[3]. Tallensin näppäinyhdistelmällä CTRL + S.

![2](https://user-images.githubusercontent.com/105177604/216962185-403488e7-c0e0-4886-8e27-66c3ccb6ae2f.JPG)


[11:36] Menin selaimella localhostiin, mutta siellä näkyi vielä vanha sivu. 

[11:38] Kävin tarkastamassa "frontpage.conf"-tiedostosta, että etusivu on oikeassa paikassa. Jouduin käyttämään "matiask"-tunnustani. Se oli.

[12:17] Palasin harharetkiltäni koskien tehtävänannon ihmettelyä ("Vaihda Apachelle uusi etusivu" - MIKÄ etusivu??? Localhostin? Käyttäjän?). 

[12:19] Käyttäjän kohdalla näkyy oikea etusivu. 

![2](https://user-images.githubusercontent.com/105177604/216962556-7828566d-1eb3-49bf-8827-1e0cb7065a1e.JPG)

[12:27] Editoin sivua Microlla "esimerkki1"-tunnusta käyttäen. Tallensin muutokset näppäinyhdistelmällä CTRL + S. Sivunäkymä oli muuttunut vieraillessani siellä uudestaan.

![3](https://user-images.githubusercontent.com/105177604/216962607-42d65fba-eb10-45a5-90d0-6849e6bf795d.JPG)

![4](https://user-images.githubusercontent.com/105177604/216962686-01d1c87c-d754-4e17-9473-ffcc3e702577.JPG)

<h3>b) Kirjoitusvirhe Apachen asetustiedostossa</h3>

[12:45] Apachen asetustiedosto "apache2.conf" löytyi polusta /etc/apache2.

[12:48] En taaskaan ymmärrä tehtävänantoa[4]: "Tee Apachen asetustiedostoon kirjoitusvirhe. Etsi se työkalujen avulla." Työkalujen?

[12:52] Räpelsin asetustiedostoa Microlla. Muokkasin riviä

<code>IncludeOptional sites-enabled/*.conf</code>

muotoon

<code>IncludeOptional sites-enabled/*.confVIRHE</code>

ja tallensin.

[12:58] Menin kansioon "/var/log" ja annoin komennon

<code>sudo tail -10 apache2/error.log</code>

Sitten tein testin komennolla:

<code>sudo apache2ctl configtest</code>

Mitään ei kuitenkaan löytynyt. Tarkistin vielä cat-komennolla asetustiedoston, että olin varmasti muistanut tallentaa tiedoston. 

![5](https://user-images.githubusercontent.com/105177604/216962868-b53fc145-c875-47e0-9db4-2e0512965c01.JPG)

[13:31] Käynnistin varmuudeksi Apachen uudelleen ja tein testit uusiksi, mutta ei edelleenkään mitään.

![6](https://user-images.githubusercontent.com/105177604/216962917-a870dd92-3d09-4e21-877e-8c9accc6ea16.JPG)

<h3>Lähteet</h3>

<ol>
<li> Apache Http Server Project. Getting Started. Luettavissa: https://httpd.apache.org/docs/2.4/getting-started.html. Luettu: 4.2.2023. </li>
<li> Apache Http Server Project. Name-based Virtual Host Support. Luettavissa: https://httpd.apache.org/docs/current/vhosts/name-based.html. Luettu: 4.2.2023. </li>
<li> Karvinen, Tero. Short HTML5 page. 2012. Luettavissa: https://terokarvinen.com/2012/short-html5-page/. Luettu: 6.2.2023. </li>
<li> Karvinen, Tero. h6 Based. 2023. Luettavissa: https://terokarvinen.com/2023/linux-palvelimet-2023-alkukevat/#laksyt. Luettu: 6.2.2023.</li>
</ol>
