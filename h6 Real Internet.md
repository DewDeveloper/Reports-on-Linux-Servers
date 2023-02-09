<h3>Alkusanat</h3>

Tämän oman virtuaalipalvelimen pystyttämiseen liittyvän tehtävän[1] voinee katsoa alkaneeksi jo oppitunnilla tiistai 7.2.2023.
Tein silloin DigitalOceaniin tunnuksen ja linkitin Github-tilini DigitalOcean-tunnukseeni sekä vuokrasin virtuaalipalvelimen.
Tätä kotitehtävää varten vuokrasin kuitenkin toisen virtuaalipalvelimen DigitalOceanilta, kun se onnistui "ilmaisilla" krediiteillä.



<h3>x) Tiivistelmä Tero Karvisen tekstistä[2]</h3>

<ul>
<li>Datakeskus valitaan läheltä asiakkaita</li>
<li>SSH sallittava läpi palomuurista ennen palomuurin käynnistämistä</li>
<li>Tehdään käyttäjä ja annetaan sille oikeuksia</li>
<li>Yhteyskokeilu ennen virtuaalikoneen "shell"in sulkemista</li>
<li>Ohjelmistojen päivittäminen <code>sudo apt-get update</code> <code>sudo apt-get upgrade</code></li>
</ul>

<h3>a) Oman virtuaalipalvelimen vuokraus</h3>

[22:35] Kirjauduin DigitalOceanin verkkosivustolle. Loin uuden projektin nimellä "Linux-palvelimet". Sitten valitsin ylälaidasta Create ja avautuneesta valikosta Droplets.

![1 droplets](https://user-images.githubusercontent.com/105177604/217737679-996719af-b106-4615-b8d2-4b56bea8e92c.JPG)

[22:36] Tein uuden palvelimen seuraavilla asetuksilla

![2 uusi droplet](https://user-images.githubusercontent.com/105177604/217737698-b25b79d1-fa00-484e-9e65-8922e9a4e5ea.JPG)

![3 uusi droplet 2](https://user-images.githubusercontent.com/105177604/217737735-c0354bc2-d2b4-4a68-be71-bcb88d8c6361.JPG)

![3 uusi droplet 3](https://user-images.githubusercontent.com/105177604/217737760-a7392136-35bf-4c3d-a2c6-98659b290b40.JPG)

![5 uusi droplet 4](https://user-images.githubusercontent.com/105177604/217737778-09c18171-5e74-4d69-9423-f874673af9f4.JPG)


<h3>b) Virtuaalipalvelimen käyttöönottotoimenpiteet</h3>

[07:28] Tein ensimmäisenä päivitykset komennoilla <code>sudo apt-get update</code> ja <code>sudo apt-get upgrade</code>.

![1 päivitykset ensin](https://user-images.githubusercontent.com/105177604/217738174-0ac66e03-9aad-4be3-ad1a-0fc51698a052.JPG)

[07:30] Tein palomuuriin muokkauksen komennolla <code>sudo ufw allow 22/tcp</code>. Tein käyttäjän ja annoin sille oikeuksia käyttäen komentoja <code>sudo adduser matiask</code>, <code>sudo adduser matiask adm</code> ja <code>sudo adduser matiask admin</code>.

![2 käyttäjän luonti](https://user-images.githubusercontent.com/105177604/217738189-f08e4c0c-f0a1-4f45-a889-6b9c7624db40.JPG)

[07:36] Käynnistin Windowsin Powershellin. Otin yhteyden palvelimeen komennolla <code>ssh matiask@46.101.227.139</code>.

![3 powershell](https://user-images.githubusercontent.com/105177604/217738202-82ad5c61-be43-4649-a825-4b1f4bb0b829.JPG)

[07:38] Annoin Powershellissä komennon <code>sudo usermod --lock root</code>.

![4 poweshell lock root](https://user-images.githubusercontent.com/105177604/217738221-0ffcd194-a27f-46f0-9bea-11c1346d64bb.JPG)

[07:40] Annoin Powershellissä komennon <code>sudoedit nano /etc/ssh/sshd_config</code>. Muutin tiedostosta kohdan <code>PermitRootLogin yes</code> muotoon <code>PermitRootLogin no</code>. Tallensin ja suljin tiedoston. Tarkistin vielä, että muutos oli onnistunut tiedostoon, koska virheilmoitus antoi ymmärtää muuta. Muutos näkyi tiedostossa.

![5 sudoedit](https://user-images.githubusercontent.com/105177604/217738259-af95efbb-941a-42a6-8201-2cc9cc0973f6.JPG)

[07:44] Annoin Powershellissä komennon <code>sudo service ssh restart</code>.

<h3>c) Apachen asentaminen virtuaalipalvelimelle</h3>

[07:45] Yritin käynnistää Apachen. Epäonnistuin, ilmeisesti, koska Apache ei ollut esiasennettu. Asensin Apachen komennolla <code>sudo apt-get install apache2</code>.

![6 apachen asennus](https://user-images.githubusercontent.com/105177604/217738619-150f2779-b2f4-4552-ab61-f917dfa1895e.JPG)

[07:47] Tein Apachelle aukon palomuuriin komennolla <code>sudo ufw allow 80/tcp</code>.

![8 apache aukko muuriin](https://user-images.githubusercontent.com/105177604/217738669-05be2e62-66ea-49ff-97a7-e5049ca4bf9a.JPG)

[08:00] Selasin itseni kansioon <code>/var/www/html</code>. Poistin siellä olleen "index.html"-tiedoston.

![9 vanhan oletussivun poisto](https://user-images.githubusercontent.com/105177604/217738719-5c5db974-1a22-4aca-a3bb-c5f0c7449c49.JPG)

[08:03] Tein uuden tiedoston Nanolla mukaillen W3Schoolsin mallia[3], ja tallensin sen nimellä index.html. Tämä epäonnistui, joten yritin seuraavaksi sudona (ei näy jostakin syystä ruutukaappauksessa). Sain sivun näkyviin paikallisesti.

![12 oletussivu näkyy paikallisesti](https://user-images.githubusercontent.com/105177604/217738998-e81ba563-c92d-478a-949c-df39b541f5b4.JPG)

[08:11] Testasin serverin ja sivun tavoittamista Windowsin Firefoxilla. Sivu näkyi onnistuneesti.

![13 oletussivu näkyi globaalisti](https://user-images.githubusercontent.com/105177604/217739026-290c44f7-f42e-4a97-85c9-c0435348c973.JPG)


<h3>d) Forensiikka</h3>

[08:15] Tutkin kansiossa <code>/var/log</code> ollutta lokitiedostoa <code>auth.log</code>.

[08:18] Löysin lokista sellaisen mukavan hepun kuin "firefart". :D Pikaisen googlettelun[4] perusteella hänen modus operadinsa on brute-force -hyökkäys SSH:n yli, hänen rekisterissään on yli 6000 hyökkäystä.

![14 firefart](https://user-images.githubusercontent.com/105177604/217741061-80fd12c5-c0d9-4fdc-9e77-9dd1a93cce08.JPG)

[08:20] Myös herra "nobody" oli käynyt kolkuttelemassa ovella. Kuten Lenin-setä, hänkin on kotoisin Venäjältä[5].

![15 nobody](https://user-images.githubusercontent.com/105177604/217741077-78de3943-67d0-4fb0-9461-9810192f4f77.JPG)

Herää kysymys, tutkisiko KRP yhtä innokkaasti minun joutumistani epätoivottujen lähentely-yritysten kohteeksi kuin jos minä porttiskannaisin Osuuspankin? :|


<h3>Lähteet</h3>

<ol>
<li>Karvinen, Tero. Linux Palvelimet 2023 alkukevät. Luettavissa: https://terokarvinen.com/2023/linux-palvelimet-2023-alkukevat/. Luettu: 9.2.2023.</li>
<li>Karvinen, Tero. First Steps on a New Virtual Private Server – an Example on DigitalOcean and Ubuntu 16.04 LT. 2017. Luettavissa: https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/. Luettu: 9.2.2023. </li>
<li>W3Schools. Luettavissa: https://www.w3schools.com/html/tryit.asp?filename=tryhtml_basic_document. Luettu: 9.2.2023.</li>
<li>AbuseIPDB. 20.228.150.123. Luettavissa: https://www.abuseipdb.com/check/20.228.150.123. Luettu: 9.2.2023.</li>
<li>IPThreat.net. IP Address: 179.60.147.157. Luettavissa: https://ipthreat.net/ip/179.60.147.157?page=0. Luettu: 9.2.2023.</li>

</ol>
