<h1>h5 Hello Web</h5>

<h3>Indie Hackers -podcastin kuuntelu ja tiivistäminen </h3>

Valitsin kuunneltavakseni jakson "How to Make Millions by Writing Online with Sam Parr of The Hustle"[1].

<ul>
<li>Haastateltava Sam Parr the Hustle -mediayrityksen takana</li>
<li>Ensimmäisenä kuukautena liki miljoona käyntiä sivustolla, vaikka kirjoitti yksin (Oma huomio: moniko oli robotti?)</li>
<li>Pitää olla erinomainen copywriter, joka ymmärtää ihmisten käyttäytymistä, haluja ja tarpeita, ja joka kykenee manipuloimaan ihmiset tekemään jotain (ostamaan, yleensä)</li>
<li>Suositellaan Advertising Secrets of the Written Word -kirjaa Joseph Sugarmanilta</li>
<li>AIDA - Attention, Interest, Desire, Action</li>
<li>Hinnoittelun voi laittaa korkeammalle kuin ajattelisi, heillä on kallein tilaus 300 dollaria vuodessa ja aikovat korottaa sitä</li>
<li>Vuosittainen laskutus on kannattavaa</li>
<li>Freemium - try for free, ei, älä tee sitä</li>
<li>Kova maksumuuri</li>
<li>Kun haluaa tietää jotakin, niin kehuu hieman kohdetta ja sitten kysyy</li>
<li>Jos olisi perustamassa uutiskirjettä tyhjästä, niin se käsittelisi erittäin pientä, mutta voimakkaasti kasvavaa trendiä</li>
<li>Kirjoittajan pitää osata kertoa tarina, kirjoittaminen on paljon vähemmän tärkeää</li>
<li>Mainostajia pitää ajatella - kirjoitti v. 2016 uutiskirjeen kuin se olisi Trumpin suusta, koska piti sitä hauskana ja söpönä, mutta mainostajat tykkäsivät huonoa</li>
<li>Launch something tomorrow</li>
</ul>

<h3>Apachen esimerkkisivun vaihto</h3>

Siirryin terminaalissa kansioon "/var/www/html/". Avasin kansiossa olleen "index.html"-tiedoston Microlla ja kirjoitin sisällön uusiksi ja tallensin. Localhostiin selaimella mennessäni minulle näytettiin juuri kyseinen muokattu sivu.

![apachen esimerkkisivu vaihdettu](https://user-images.githubusercontent.com/105177604/216299808-28d47269-9c7e-4613-a54d-56e87803eca2.JPG)

<h3>Käyttäjien kotisivujen asennus</h3>

Siirryin terminaalissa "public_html"-kansioon, tarkistin tiedoston sisällön Microlla ja surffasin Firefoxilla kyseiselle sivulle.

![käyttäjäsivu toimii](https://user-images.githubusercontent.com/105177604/216299992-f6aa96a7-e5c2-4cd3-b468-537ad14e159b.JPG)

<h3>Uuden käyttäjän luominen ja kotisivu</h3>

Tein uuden käyttäjän Linuxize-sivustolta löytämieni ohjeiden[3] mukaisesti nimellä "esimerkki1". Kirjauduin ulos.

![käyttäjän luonti](https://user-images.githubusercontent.com/105177604/216300071-916f502c-8064-4178-a334-64e45072c9f8.JPG)

Kirjautuminen epäonnistui. Luettuani ohjeita[3] tarkemmin, päädyin kirjautumaan pääasiallisilla tunnuksillani ja loin uudelle käyttäjälle oman kansion "/home"-kansioon. 

![loin kansion](https://user-images.githubusercontent.com/105177604/216300872-a9d39fc0-4d7e-4d7b-91de-0dcdb49970cc.JPG)

Sekään ei auttanut, "esimerkki1"-tunnuksella kirjautuminen epäonnistui edelleen. Sitten luin Stackexchange-sivustolta[4], miten asia korjataan. Kirjauduin takaisin "matiask"-tunnuksella, poistin tekemäni kansion ja loin uuden. Tarkistin dir-komennolla, että kansio syntyi. Sitten kirjauduin ulos.

![poistin kansion ja loin uusiksi](https://user-images.githubusercontent.com/105177604/216301327-dba01d38-a93e-463f-9603-5aecf36f439c.JPG)

Nyt onnistuin kirjautumaan sisään "esimerkki1"-tunnuksella. Loin kotihakemistooni "public_html"-kansion ja tein sinne Microlla "index.html"-tiedoston. Sivu aukesi nätisti selaimessa.

![esimerkki1 kotisivu](https://user-images.githubusercontent.com/105177604/216300999-d73d7dfc-e886-42b6-8fc1-58d2b62052e7.JPG)

<h3>Validi HTML5 sivu</h3>

Päädyin tekemään sivun edellisessä tehtävässä käyttämälläni "esimerkki1"-tunnuksella samaan "public_html"-kansioon. Mukailin sivun Tero Karvisen esimerkistä[5].

![uusi sivu](https://user-images.githubusercontent.com/105177604/216301062-4d711e35-849d-4618-8b7a-859d56ab8910.JPG)

Yritin validoida sivun tehtävänannossa annetulla sivustolla syöttämällä localhostin tilalle ip-osoitteeni. Se ei kuitenkaan tuntunut pääsevän sivulle. Sitten ymmärsin, ettei Apache ehkä ole käynnissä ja yritin käynnistää sen. Saamani ilmoitus oli kuin "mene suoraan kybervankilaan kulkematta lähtöruudun kautta".

![iik](https://user-images.githubusercontent.com/105177604/216301471-30288390-b7c8-4c64-b56e-a0d2edc4607c.JPG)

Kirjauduin ulos "esimerkki1"-tunnukselta ja takaisin sisään "matiask"-tunnuksella. Terminaalissa käynnistin Apachen. Yritin validoida viimeisimmän sivun W3-sivustolla[6], mutta se ei onnistunut.

![validointi epäonnistui](https://user-images.githubusercontent.com/105177604/216301654-347d38d7-4665-45c0-87e9-527585062e69.JPG)

Tein sitten validoinnin lataamalla sivustolle ko. tiedoston saaden seuraavan raportin.

![validointi tiedostosta](https://user-images.githubusercontent.com/105177604/216301722-060a74a2-e5d8-47c4-8914-d47ebabd1ac2.JPG)

<h3>Lähteet</h3>

<ol>
<li>Indiehackers. How to Make Millions by Writing Online with Sam Parr of The Hustle. 2020. Kuunneltavissa:  https://www.indiehackers.com/podcast/161-sam-parr-of-the-hustle. Kuunneltu: 2.2.2023.</li>
<li>Karvinen, Tero. Install Apache Web Server on Ubuntu. 2008. Luettavissa: https://terokarvinen.com/2008/install-apache-web-server-on-ubuntu-4/. Luettu: 2.2.2023.</li>
<li>Linuxize. How to Create Users in Linux (useradd Command). 2020. Luettavissa: https://linuxize.com/post/how-to-create-users-in-linux-using-the-useradd-command/. Luettu: 2.2.2023</li>
<li>Stackexchange. How can I retrospectively create a default home directory for an existing user in terminal? https://askubuntu.com/questions/335961/how-can-i-retrospectively-create-a-default-home-directory-for-an-existing-user-i. Luettu: 2.2.2023.</li>
<li>Karvinen, Tero. Short HTML5 page. 2012. Luettavissa: https://terokarvinen.com/2012/short-html5-page/. Luettu: 2.2.2023.</li>
<li>Markup Validation Service. https://validator.w3.org/. Käyty: 2.2.2023</li>
</ol>
