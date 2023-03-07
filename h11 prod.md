<h1>h11 prod</h1>

<h3>Laitteisto</h3>

Tehtävä tehtiin DigitalOceanista vuokratulla virtuaalikoneella, johon otin yhteyden Windows 10:n PowerShellillä läppäriltäni.

<h3>a) Djangon tuotantoasennus</h3>

Aloitin tutustumalla Karvisen oppaaseen[1]. Päätin ohittaa Apachen asennuksen, koska minulla oli se jo valmiiksi.

[00:28] Ajoin komennon <code>sudo apt-get update</code>.

[00:29] Ajoin komennot <code>sudo apt-get -y install micro bash-completion</code> ja <code>export EDITOR=micro</code>.

[00:31] Menin home-kansioon ja yritin ajaa komennon <code>mkdir -p publicwsgi/tuotantoasennus/static/</code>. Sain "permission denied" -ilmoituksen. Sudona kansion luonti onnistui.

![3](https://user-images.githubusercontent.com/105177604/222707079-2c2853a9-1aab-425b-814a-630b29ae46d4.JPG)

[01:17] Yritin ajaa alapuolisen kuvan mukaisia komentoja, mutta oikeudet puuttuivat niin sudolla kuin ilman.

![4](https://user-images.githubusercontent.com/105177604/222707101-d7057930-7ff1-4a9c-a57d-142fd18269ef.JPG)

[02:24] Ihmettelyn jälkeen menin ja loin tiedoston Microlla. Tarkastin luomani tiedoston sisällön komennolla <code>cat index.html</code>.

![5](https://user-images.githubusercontent.com/105177604/222707120-e8ea643c-5c74-487f-b11f-4cf3cc889ca6.JPG)

[02:46] Selasin itseni juureen ja ajoin komennon <code>sudoedit /etc/apache2/sites-available/tuotantoasennus.conf</code>. Muokkasin tiedostoa, tallensin ja luin tiedoston hyödyntäen <code>cat</code>-komentoa.

![6](https://user-images.githubusercontent.com/105177604/222707137-e01ce057-fdef-4bea-90c0-f5db8baa5a96.JPG)

[03:17] Ajoin komennot <code>sudo a2ensite tuotantoasennus.conf</code> ja <code>sudo a2dissite 000-default.conf</code>. Sain kehotuksen aktivoida uusi konfiguraatio komennolla <code>systemctl reload apache2</code>, jonka ajaminen onnistui sudona.

![7](https://user-images.githubusercontent.com/105177604/222707154-8663c3bf-11f1-47c5-af68-eba249499134.JPG)

[03:47] Ajoin komennon <code>/sbin/apache2ctl configtest</code>.

![8](https://user-images.githubusercontent.com/105177604/222707190-f419f866-4d53-4da0-9034-754ffef5c23a.JPG)

[04:01] Ajoin komennon <code>sudo systemctl restart apache2</code>.

[04:23] Kävin katsomassa staattisia tiedostoja ("static files") niin w3m:llä kuin curl:illakin. Oikeuksia ei ollut.

![9](https://user-images.githubusercontent.com/105177604/222707220-9762799f-9f1b-4d04-8450-62365efc2597.JPG)

[04:25] Tutkin Apachen virhelokia. Näytti siltä, että ongelma olisi  publicwsgi:ssä. En kuitenkaan löytänyt koko kansiota.

![10](https://user-images.githubusercontent.com/105177604/222707235-a12aa243-90f3-4594-b86c-0f97f0c0cdd1.JPG)

[05:49] Huomasin, että aiemmin ohittamassani ohjeiden kohdassa "Install Apache 2" oli myös index.html-sivun muokkaus. Tein sen.

![11](https://user-images.githubusercontent.com/105177604/222707253-e7bafc11-85fe-4585-a022-6dc902f575a6.JPG)

[11:50] Päätin tutkia, onko kollegoilla esiintynyt vastaavaa. 

[12:09] Menin polkuun <code>/home/publicwsgi/tuotantoasennus/static</code>. Avasin index.html-tiedoston Microlla ja otin alussa ja lopussa olleet lainausmerkit pois, vaikka en uskonutkaan, että sillä olisi merkitystä. Tiedosto oli pakko tallentaa sudona, minkä päättelin voivan liittyä siihen, ettei oikeuksia lukea kansion sisältöä verkon yli ole.

![kuva 12](https://user-images.githubusercontent.com/105177604/222707279-ac94fa51-47c0-484b-84fd-2a1bbcd18a8c.JPG)

[12:13] Vertasin tuotantoasennus.conf-tiedoston sisältöä kollegani Romeo Rusin raporttiin[2]. Hänellä kun vastaavaa ongelmaa ei esiintynyt. Sekin kuitenkin mukaili omaa vastaavaa konffitiedostoani ja Karvisen esimerkkiä. Sen sijaan tein havainnon, että Rusi oli ajanut komennon <code>sudo a2dissite frontpage.conf</code>. Tämä oli hyvin mielenkiintoista, koska tätä ei ollut Karvisen ohjeissa eikä Rusi ollut ajanut Karvisen ohjeissa ollutta komentoa <code>sudo a2dissite 000-default.conf</code>.

[12:21] Tässä vaiheessa on tosin mainittava, että myös kollegani Lauri Törmä on raportissaan ajanut komennon <code>sudo a2dissite 000-default.conf</code>. Hänellä static-kansio näkyi kuitenkin yhtä hyvin kuin Rusillakin.

[12:26] Käynnistin Apachen uudelleen komennolla <code>sudo systemctl restart apache2</code>. Ajoin komennon <code>curl http://localhost/static/</code> vailla muutosta.

![13](https://user-images.githubusercontent.com/105177604/222707295-1c9fdff6-fff6-41eb-9e03-b45a55968d73.JPG)

[12:35] Yritin ajaa Rusin käyttämän komennon <code>sudo a2dissite frontpage.conf</code>. Sain virheilmoituksen, ettei frontpagea ole.

![14](https://user-images.githubusercontent.com/105177604/222707312-8a559fed-ca9e-4bc4-8395-ffdc6689d149.JPG)

[12:45] Vilkuilin Apachen asetustiedostoja, mutta ei sieltä mitään fiksunoloista löytynyt.

![15](https://user-images.githubusercontent.com/105177604/222707335-6d49ed57-b4e3-45e8-9324-7b7d19257754.JPG)

[13:00] Katsoin lokitiedostoja. Ilmeisesti näihin permission denied -ongelmiin liittyy alapuolinen vikakoodi.

![16](https://user-images.githubusercontent.com/105177604/222707355-b77dd484-63e8-4fea-bfd5-80df0368a6c9.JPG)

[13:20] Tutustuin Karvisen ohjeiden vianselvitys-osioon. Se ei ollut kovin hyödyllinen, mutta selvisi, ettei kansiota ole. Olin tehnyt kansion väärään paikkaan eli ohjeiden mukaisesti suoraan home-kansioon, kun sen olisi pitänyt olla home/matiask-kansiossa. Aivan älytön ohjeistus. Tein sen sitten oikeaan paikkaan.

![17](https://user-images.githubusercontent.com/105177604/222710174-5d4ed129-4873-4915-a8dc-65711cca6213.JPG)

[13:34] Tarkistin komennolla <code>curl http://localhost/static/</code>, toimisiko nyt. Toimi.

![18](https://user-images.githubusercontent.com/105177604/222710753-eae0bc29-5b5b-4200-a978-2fa781bd2517.JPG)

[13:36] Ohjeiden mukaisesti ajoin paljon komentoja. Virtualenv olikin jo olemassa vanhempien harjoitusten jäljiltä.

![19](https://user-images.githubusercontent.com/105177604/222711212-e81e6ec1-0841-4160-acbb-222227a1b5af.JPG)

[13:39] Ajoin komennon <code>source env/bin/activate</code> siirtyäkseni virtuaaliympäristöön.

![20](https://user-images.githubusercontent.com/105177604/222711514-cb9c748a-74a7-48f1-8e0c-e94a565a5a2d.JPG)

[13:40] Ajoin komennon <code>which pip</code> tarkistaakseni, että käytettävä paketinasennusohjelma on virtuaaliympäristöstä. Se oli.

![21](https://user-images.githubusercontent.com/105177604/222712388-b7c7c623-9193-44ec-a463-484008712658.JPG)

[13:45] Ajoin komennon <code>micro requirements.txt</code> ja kirjoitin sinne "django" ja tallensin tiedoston. Ajoin komennon <code>pip install -r requirements.txt</code>. Tarkistin Djangon version komennolla <code>django-admin --version</code>.

![22](https://user-images.githubusercontent.com/105177604/222713162-360e2289-4fbf-48fa-a410-1b9722deac8e.JPG)

[13:49] 


<h2>TEHTÄVÄ KESKEN, palautettu 3.3.2023 n. 1355, jatketaan luultavastimyöhemmin</h2>

[01:45] Päätin hyödyntää edellisen tehtäväkierroksen Django-projektiani. Annoin komennon <code>sudoedit /etc/apache2/sites-available/tuotantoasennus.conf</code>, editoin tiedosto ja tallensin sen.

![23](https://user-images.githubusercontent.com/105177604/223415392-b6844518-4ccc-498f-9bb8-dafdb5072d65.JPG)

[02:09] Ajoin komennon <code>sudo apt-get -y install libapache2-mod-wsgi-py3</code>. Jotakin meni vikaan.

![24](https://user-images.githubusercontent.com/105177604/223415413-3daaf3eb-e5d2-4013-a83e-66b9089ae994.JPG)

[02:17] Selvitin, että vika on kirjoitusviheessä ("WSGIDaemonpocess" vrt. "WSGIDaemonprocess") ja kävin korjaamassa sen. Ajoin äskeisen komennon uudestaan ilman virheitä.

[02:22] Ajoin komennon <code>/sbin/apache2ctl configtest</code>. Sain virheilmoituksen <code>AH00543: apache2: bad user name Toimitusjohtaja</code>. Selasin itseni takaisin tuotantoasennus.conf-tiedostoon ja vaihdoin käyttäjäksi "matiask" sekä tallensin tiedoston.

[03:18] Ajoin uudestaan komennon <code>/sbin/apache2ctl configtest</code>. Syntaksi oli ok, tosin sain AH00558-virheilmoituksen, jonka jätin huomioimatta.

[03:19] Käynnistin Apachen uudelleen komennolla <code>sudo systemctl restart apache2</code>. Käytin komentoa <code>curl -s localhost|grep title</code>. Sain jälleen ilmoituksen "403 Forbidden", sama vika siis kuin aiemminkin.

![25](https://user-images.githubusercontent.com/105177604/223415435-421ece58-4826-4036-942e-1196575fda16.JPG)

[Päivä vaihtui, 7.3. 04:49] Ajoin summassa hirveän määrän komentoja uusiksi eri kansioissa.

![26](https://user-images.githubusercontent.com/105177604/223415456-b73182f2-2f89-4b01-8e00-997800ad3c20.JPG)

[05:22] Nyt näyttää hyvältä, pip on oikeassa paikassa

![27](https://user-images.githubusercontent.com/105177604/223415477-6f0739e7-6b7f-4c30-9c2f-a3c59beb38b5.JPG)

[05:25] Ajoin lisää komentoja.

![28](https://user-images.githubusercontent.com/105177604/223415505-d8ca6f4d-444d-4292-bf3b-b5f75bd6db8c.JPG)

[12:40] 

Tutkin lokitiedostoja. Virheilmoitus AH01630: client denied by server configuration: /home/matiask/publicwsgi/tuotantoasennus/tuotantoasennus.

![29](https://user-images.githubusercontent.com/105177604/223415527-3eebdac4-6b90-4e35-a3cd-8c3167a2f357.JPG)

[13:30] Päättelin, että olen linkittänyt Apachen konffitiedostossa TDIR:n väärään paikkaan.

[13:31] Muokkasin tiedostoa komennolla <code>sudoedit /etc/apache2/sites-available/tuotantoasennus.conf</code>. TDIR-poluksi muutin <code>/home/matiask/harjoituscompany</code>.

![30](https://user-images.githubusercontent.com/105177604/223415555-0440c6b5-8099-43d9-9dc1-1811f5461d25.JPG)

[13:46] Yritin Apachen uudelleenkäynnistystä, mutta mikään ei muuttunut. Arvelin, että myös wsgi.py-tiedoston pitäisi olla "samasta" paikasta kuin TDIR. (/home/matiask/harjoituscompany/harjoituscompany)

![31](https://user-images.githubusercontent.com/105177604/223415582-1e5bc1c7-1263-4e4d-873f-e9b423e8ef00.JPG)

[13:50] Käynnistin Apachen uudelleen. Käytin Curlia. Se toimi!

![32](https://user-images.githubusercontent.com/105177604/223415601-d36f7934-02a2-4895-8348-aaaea5ce466a.JPG)

<h3>Päivitetty palautusta 7.3. 1358. Jatkuu taas joskus... </h3>

<h3>Lähteet</h3>

<ol>
<li>Karvinen, Tero. Deploy Django 4 - Production Install. Luettavissa: https://terokarvinen.com/2022/deploy-django/. Luettu: 2.3.2023.</li>
<li>Romeo, Rusi. Viikko6Tunti1.md. Luettavissa: https://github.com/romeorusi/LinuxPalvelimet23/commit/c6c8802b34216d1a25f106f191e43da7a66d7028?short_path=dcf45bc#diff-dcf45bc571adde771a8eb7e50c6ec6f7b96791bbb3f7a804080e86d7a2fc5a1b. Luettu: 3.3.2023.</li>
<li>Törmä, Lauri. h11 Prod. Luettavissa: https://github.com/lauritorma/Linux-palvelimet-kurssi/blob/main/h11-prod.md. Luettu: 3.3.2023.</li>
</ol>
