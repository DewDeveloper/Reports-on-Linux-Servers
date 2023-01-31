<h1>h4 Tukki</h1>

<h3>Tiivistelmät</h3>

<p>Tein tiivistelmät kahdesta Hckrnews-sivuston uutisesta kommentteineen.

<h4>US Marines defeat DARPA robot by hiding under a cardboard box[1]</h5>

<ul>
<li>Yhdysvaltain puolustusministeriön Defense Advanced Research Projects Agendy (DARPA) kehitti robotin, jonka pitäisi tunnistaa ihminen.</li>
<li>Robottin koulutettiin kävelyttämällä ihmisiä sen näkökentässä.</li>
<li>Testissä merijalkaväen sotilaiden piti kävellä robotin luo tulematta havaituksi ja koskettaa robottia.</li>
<li>Näin ei kuitenkaan käynyt, vaan Metal Gear Solid -pelissäkin käytetty pahvilaatikkoon piiloutuminen mahdollisti robottia lähestymisen sen huomaamatta.</li>
</ul>

<h4>Kommentit[2]</h4>
<ul>
<li>AI:n ongelma on, että se ei osaa sopeutua uusiin tilanteisiin, vaan on vain yhtä hyvä kuin sille annettu data.</li>
<li>Jos kolmivuotiaalle lapselle näyttää sotilaan ryömimässä laatikon alle ja kysyy sotilaan piilouduttua kokonaan laatikon alle, missä tämä on, niin lapsi luultavasti vastaa oikein - ongelma on siinä, että AI ei tunnista tilan ("state") muutosta, vaan se ymmärtää ainoastaan olioita ("object").</li>
<li>Koneoppiminen voi luoda assosiaatioita, mutta usein samalla asialla voi olla monia merkityksiä ja tulkinta riippuu kontekstista.</li>
<li>Vahvistusoppimisen pitäisi ratkaista ongelma - robottien pitää saada kokeilla asioita ja oppia virheistä, kuten lasten.</li>

</ul>

<h4>How NASA Solved a $100 Million Problem for Five Bucks[3]</h3>

<ul>
<li>NASA:n Constellation ohjelman Ares 1 -raketissa havaittiin ongelma, joka vaaransi koko hankkeen.</li>
<li>Laukaisun loppuvaiheissa rakettimoottori saisi koko raketin, ml. miehistökapselin, värähtelemään niin ettei astronautit pystyisi lukemaan näyttölaitteita.</li>
<li>Värähtelyä simuloitiin huvipuistolaitteen istuimella ja todettiin, ettei näyttöä pystytä lukemaan.</li>
<li>Piirustuspöydälle otettiin jousia ja vastakkaiseen suuntaan vaikuttavia moottoreita värähtelyn vähentämiseksi - satojen miljoonien dollarien hintalapulla.</li>
<li>Sitten näyttö asetettiinkin värähtelemään samalla 12 Hz taajuudella kuin mitä astronauttienkin odotettiin kokevan.</li>
<li>Koska värähtely ei kuitenkaan ollut aivan tahdissa, istuimeen asetettiin kiihtyvyysantureita, joiden mittausdatalla näytön värähtely synkronoitiin ja näytöstä tuli täysin luettava.</li>
<li>NASA hakee ratkaisulle patenttia, ja odottaa, että ratkaisua voitaisiin soveltaa myös esimerkiksi turbulenssista värähteleviin helikoptereihin ja muihin lentolaitteisiin.</li>
</ul>

<h4>Kommentit[4]</h4>

<ul>
<li>Tiheäsilmäisen verkkoaidankin läpi näkee paremmin, kun ei katso sitä paikaltaan, vaan liikkuu aidan suuntaisesti katsoessaan.</li>
<li>Väitetysti murotehtaalla kehitettiin monimutkainen punnitusjärjestelmä, joka varmisti, ettei pakkaus ollut tyhjä muropussin pudottua sen sisältä - myöhemmin kävi ilmi, että työntekijät olivat jo asettaneet linjastolle tuulettimen, joka puhalsi tyhjät laatikot sivuun linjastolta.</li>
<li>Ratkaisu tuskin oli viiden dollarin arvoinen. Mikropiirit ehkä maksoivat alle satasen, mutta suunnittelu, asennus ja laadunvarmistus huomioiden luultavammin kuusi- tai seitsemännumeroisen määrän dollareita.</li>
<li>Se on kuin sanoisi open source -kielistä ja -kirjastoista rakennetun ohjelmiston olevan ilmainen.</li>
<li>5 taalaa materiaaleihin, miljoonia taaloja sellaisia ratkaisuja löytävien insinöörien koulutukseen, palkkaamiseen ja pitämiseen.</li>
<li>[Nimimerkki Tezzer väittää olleensa osa koetta. Tietty värähtelytaajuus sentrifugissa koettuna aiheuttaisi samanlaista hätäännystä kuin tietty infraääni. (Dyatlov Pass Incident -Oma huomio)]</li>
<li>Neuvostoliitto käytti lyijykynää, NASA käytti miljoonia kehittääkseen painottomuudessa toimivan kuulakärkikynän.</li>
</ul>

<h3>Tukki</h3>

<h4>/var/log/syslog</h4>

Päädyin analysoimaan seuraavan rivin: </br>

<code>Jan 30 11:31:41 matias-virtualbox systemd[1]: Stopped User Manager for UID 117.</code>

Päivämäärä ja kello on oikein, aikavyöhyke GMT+2. "Matias-virtualbox" on hostname, tietokoneeseen liittyvä nimi. "Systemd[1]" on Linux-käyttöjärjestelmien järjestelmän- ja palveluidenhallintatyökalu[5]. Hakasulkeissa on prosessin identifiointinumero, ja kyseessä on ensimmäinen Linux-ytimen (kernelin) käynnistämä prosessi[6].
Viimeisenä on se mitä tehtiin, eli pysäytettiin käyttäjänhallinta käyttäjä-ID:lle[7] 117.


<h4>/var/log/auth.log</h4>

Päädyin analysoimaan seuraavan rivin:</br>

<code>Jan 30 11:31:21 matias-virtualbox lightdm: gkr-pam: unable to locate daemon control file</code></br>

Alkuosan rakenne noudattaa samaa kaavaa ja on oikein kuin edellisestäkin lokista valitsemassani rivissä. Tällä kertaa ohjelma on kuitenkin "lightdm", display manager[8]. Se mahdollistaa sisäänkirjautumisen graafisesta käyttöliittymästä.
Yritin etsiä terminaalin avulla tietoa gkr-pamista, mutta en onnistunut. 

![gkr pam](https://user-images.githubusercontent.com/105177604/215694397-50824012-76e8-4cb2-8d40-7a84be2ea7ea.JPG)

Googlen perusteella gkr-pam viitannee "GNOME keyring" -kokoelmaan[9], jossa on salasanoja ym. salaista tietoa varastoivia ja välittäviä komponentteja.
Se epäonnistui Daemon-järjestelmäpalvelun, joka odottaa asioiden tapahtumista ja tarjoaa sitten palveluita[10], hallintatiedoston löytämisessä. En äkkiseltään löytänyt tietoa, mikä tämän hallintatiedoston merkitys on.

<h4>/var/log/apache2/access.log</h4>

Päädyin analysoimaan seuraavan rivin (maalattu kuvassa):

![apache2](https://user-images.githubusercontent.com/105177604/215694489-865e7f48-bb83-4c49-9ced-eae126f3c003.JPG)

<p>Ensimmäisenä on ip-osoite, josta pyyntö on lähetetty serverille. Ensimmäisen tavuviivan kohdalle tulisi asiakkaan identiteetti ja seuraavan tavuviivan kohdalle pyynnön tehneen käyttäjän id. Sitten tulee pyynnön päivämäärä ja aikavyöhyke (GMT+2), jotka ovat oikein. GET-kertoo pyynnön tyypin, ja kyse on 1.1-standardia noudattavasta HTTP-pyynnöstä. Statuskoodi "200" kertoo pyynnön onnistuneen. 3380 kertoo pyynnön lähettäjälle toimitetun objektin koon bitteinä. Tavuviivan paikalle kuuluisi osoite, jonka kautta pyyntö tehtiin (usein verkkosivu/domain). Sen jälkeen tulee "käyttäjäagentti" ("User Agent"), joka kertoo tunnistetietoja pyynnön lähettäjästä. </p> 

Käytin analysoinnin tukena verkosta löytämääni Scott Fitzpatrickin blogipostausta[11].

<h4>/var/log/apache2/error.log</h4>

Päädyin analysoimaan seuraavan rivin (maalattu kuvassa):

![apache error log](https://user-images.githubusercontent.com/105177604/215694511-49c730df-1804-403a-8314-671423d2552f.JPG)

Ensimmäisenä kerrotaan hakasulkeissa tapahtuma-aika. Sen jälkeen lokiviestin tuottava moduuli ja tapahtumataso ("log level"), joka ilmentää tapahtuman tärkeyttä[12]. Tässä tapauksessa lokitapahtuma on siis seurausta mpm_eventistä ja se on luokitukseltaan huomautus ("notice"). Tämän jälkeen tulee prosessin id-numero ("pid") ja säikeen id-numero ("tid"). Sitten kerrotaan virheen statuskoodi ("AH00492") ja nimi (caught SIGWINCH) ja kerrotaan "sammutettavan armollisesti". Viimeksi mainittu viitannee siihen, että asiat tapahtuvat hyvässä järjestyksessä eikä koko palvelin kaadu hallitsemattomasti virheen seurauksena.

Käytin analysoinnin tukena dokumentaatiota[13] ja Baeldung-sivustoa[14].

<h4>Aiheuta</h4>

Aiheutin ensimmäisenä epäonnistumisen. Yritin pysäyttää serverin, mutta annoin tahallani väärän salasanan. Se aiheutti kuvanmukaisen tapahtuman auth.logiin. 

![aiheutettu epäonnistuminen](https://user-images.githubusercontent.com/105177604/215694567-513f1a20-13c0-4639-88bd-eb7516ed7672.JPG)

Ensimmäisenä näkyy tapahtuman päivämäärä ja kellonaika. Seuraavana hostname. Sen jälkeen mikä ohjelma tekee (sudo eli pääkäyttäjän oikeuksilla asioita suorittava ohjelma). Sudo on nähtävästi käytellyt "pam_unix":ia ja päättelisin sudon antaneen parametrina "auth". On syntynyt todennusvirhe ("authentication failure"), kirjautumisnimenä ("logname") ei näy mitään, ilmeisesti sen vuoksi ettei mitään kirjautumisnimeä annettu. "UID" eli user-id on 1000 - kuulemma useimmat Linux-distrot aloittavat normaalien käyttäjien listaamisen 1000:sta[15]. "Euid" ("Effective User ID") on user id, jota prosessi suorittaa[16] (mitä tämä oikeastaan tarkoittaa?). "Tty" ("virtual TeleTYpe") kertoo käytettävän rajapinnan. "Ruser" listaa paikallisessa verkossa olevan/olevat käyttäjät. "Rhost" listaa isäntä-käyttäjä yhdistelmät. "User" kertoo nimensä mukaisesti käyttäjän.

Seuraavaksi aiheutin onnistumisen. Pysäytin Apachen ja se tuotti kuvanmukaista /var/log/syslog-lokiin.

![aiheutettu onnistuminen](https://user-images.githubusercontent.com/105177604/215694586-6af41afe-78ce-4f20-ab23-18fb2a2f0dc9.JPG)

Ensimmäisinä näkyy päivämäärä ja kellonaika. Ne ovat oikein. Sitten tulee "hostname" ("matias-virtualbox"), suoritettava prosessi ("systemd") ja hakasulkeissa sen PID eli prosessi-identifikaationumero, joka on tässä tapauksessa "1". Sitten on ilmoitus, jossa todetaan, että palvelun ("apache2.service") pysäyttäminen onnistui ("Succeeded.").

<h3>Ongelmat</h3>

Kesken lokitehtävien virtuaalikone kaatui ja uudelleenkäynnistyksen yhteydessä päädyin alapuoliseen tilanteeseen. Uudelleenkäynnistykset eivät auttaneet. Perustelen myöhäistä palautustani osin tällä, tosin on kyseenalaista, olisinko tullut valmiiksi ajoissa muutenkaan. Mutta onko kukaan koskaan kuullut it-projektista, joka olisi valmistunut aikataulussa?

![KAATUI](https://user-images.githubusercontent.com/105177604/215706508-e4b51edd-554d-4d6b-92c7-508b1a2a9f89.JPG)

Ratkaisin ongelman luomalla uuden virtuaalikoneen ja asentamalla Debianin uusiksi. Debianin toiminta nopeutui huomattavasti aiemmasta, kun laitoin virtuaalikoneeseen 8 GB RAM-muistia, 4 prosessoriydintä ja määritin "kiintolevyn" SSD-levylle. Aiempi virtuaalikone 4 GB RAM-muistilla, 2 prosessoriytimellä ja "kiintolevy" USB-muistitikulle määritettynä ei toiminut likimainkaan tyydyttävästi. 

<h3>Lähteet</h3>
<ol>
<li> ExtremeTech. US Marines Defeat DARPA Robot by Hiding Under a Cardboard Box. Luettavissa: https://www.extremetech.com/extreme/342413-us-marines-defeat-darpa-robot-by-hiding-under-a-cardboard-box. Luettu: 28.1.2023.</li>
<li> Hacker News. US Marines defeat DARPA robot by hiding under a cardboard box. Luettavissa: https://news.ycombinator.com/item?id=34518299. Luettu: 28.1.2023.</li>
<li> Gizmodo. How NASA Solved a $100 Million Problem for Five Bucks. 2012. Luettavissa: https://gizmodo.com/how-nasa-solved-a-100-million-problem-for-five-bucks-5880850. Luettu: 29.1.2023.</li>
<li> Hacker News. NASA solved a $100M problem for five bucks (2012). 2023. Luettavissa: https://news.ycombinator.com/item?id=34490298. Luettu: 29.1.2023.
<li> Debian. Luettavissa: https://manpages.debian.org/testing/systemd/systemd.1.en.html. Luettu: 30.1.2023.
<li> Vaga. What's Special With Pid 1? Luettavissa: https://vagga.readthedocs.io/en/latest/pid1mode.html. Luettu: 30.1.2023.
<li> Linux.fi. UID. Luettavissa: https://www.linux.fi/wiki/UID. Luettu: 30.1.2023.
<li> Debian. LightDM. Luettavissa: https://wiki.debian.org/LightDM. Luettu: 30.1.2023.
<li> Gnome. GNOME Keyring. Luettavissa: https://wiki.gnome.org/Projects/GnomeKeyring. Luettu: 30.1.2023.
<li> Debian. Daemon. Luettavissa: https://wiki.debian.org/Daemon. Luettu: 30.1.2023.
<li> Sumo logic. Scott Fitzpatrick. 2020. Luettavissa: https://www.sumologic.com/blog/apache-access-log/. Luettu: 30.1.2023.
<li> Sematext. Understanding Logging Levels: What They Are & How To Use Them. 2020. Luettavissa: https://sematext.com/blog/logging-levels/. Luettu: 30.1.2023.
<li> APACHE HTTP SERVER PROJECT. Apache Core Features. Luettavissa: https://httpd.apache.org/docs/2.4/mod/core.html#errorlogformat. Luettu: 30.1.2023.
<li> Baeldung. Differences between PID, TID and PPID in Linux. 2022. Luettavissa: https://www.baeldung.com/linux/pid-tid-ppid. Luettu: 30.1.2023.
<li> LinuxQuestions. What is the user 1000? Luettavissa: https://www.linuxquestions.org/questions/linux-general-1/what-is-the-user-1000-a-4175510196/. Luettu: 31.1.2023.
<li> Stackoverflow. Difference between EUID and UID? Luettavissa: https://stackoverflow.com/questions/27669950/difference-between-euid-and-uid. Luettu: 31.1.2023.
 </ol>
