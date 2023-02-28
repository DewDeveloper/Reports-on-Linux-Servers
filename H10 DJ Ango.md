<h1>h10 DJ Ango</h1>

<h3>a) Kannattavaa</h3>

Tehtävänanto[1]:

>Tee oma tietokantasovellus. jossa on weppiliittymä. Kirjautuneet käyttäjät saavat lisätä, muokata ja poistaa tietueita. (Voit käyttää Djangon kehityspalvelinta. Tee jotain muuta kuin asiakastietokanta.)

[01:17] Kirjauduin virtuaalikoneelle Windowsin Powershellillä. Käyttäisin apuna tehtävässä Karvisen pikaohjetta asiakasrekisterin luomisesta Djangolla[2].

[01:22] Annoin komennot <code>sudo apt-get -y install virtualenv</code> ja <code>virtualenv --system-site-packages -p python3 env/</code>.

[01:27] Tarkistin <code>which pip</code> -komennolla, mihin asennetaan.

![2](https://user-images.githubusercontent.com/105177604/221804570-c67e347c-ef86-4d9a-b49a-8c3322378d77.JPG)

[01:29] Ajoin komennot <code>sudo apt-get install micro
</code> ja <code>micro requirements.txt</code>. Lisäsin tiedostoon rivin <code>django</code> ja tallensin muutoksen näppäinyhdistelmällä <code>CTRL+S</code>. Suljin tekstieditorin näppäinyhdistelmällä <code>CTRL+Q</code>.

[01:39] Ajoin komennon <code>pip install -r requirements.txt</code>.

[01:41] Tarkistin asentuneen Djangon version komennolla <code>django-admin --version</code>. Versio 4.1.7 oli asennettu.

![4](https://user-images.githubusercontent.com/105177604/221806149-e6dc5021-e1f1-4ff3-9686-5639ed27c44c.JPG)

[11:45] Ajoin komennon <code>django-admin startproject harjoituscompany</code> ja siirryin projektikansioon komennolla <code>cd harjoituscompany</code>.

![5](https://user-images.githubusercontent.com/105177604/221808992-05f94dc6-6a20-4824-94ce-fc7dba7b48b0.JPG)

[11:48] Käynnistin palvelimen komennolla <code>./manage.py runserver</code>.

[11:50] Kohtasin ongelman, koska pilvessä olevalla virtuaalikoneellani ei ole graafista käyttöliittymää. Enkä ylipäätään tiennyt, kuinka pitää serveri auki samalla kun kirjoittaisin muita komentoja. 

[12:37] Päädyin low-tech-ratkaisuun, jossa avasin Windowsin komentokehotteen ja otin siitäkin SSH-yhteyden virtuaalikoneeseen. Sitten käytin komentokehotteesta Curlia nähdäkseni, onko mitään siinä osoitteessa kuin pitäisi. Siellä oli.

![6](https://user-images.githubusercontent.com/105177604/221809185-a42fa635-189e-4d0c-a3f8-7251ed29840a.JPG)

![7](https://user-images.githubusercontent.com/105177604/221809222-113bf60e-7d24-4771-8bde-68828ce3c44d.JPG)

[12:44] Päivitin tietokannat komennoilla <code>./manage.py makemigrations</code> ja <code>./manage.py migrate</code>.

![10](https://user-images.githubusercontent.com/105177604/221809795-0d406af6-5b64-44b7-a3f9-c562eb782925.JPG)

[04:24] Ajoin komennon <code>sudo apt-get install pwgen</code>.

[04:27] Ajoin komennon <code>pwgen -s 20 1</code> luodakseni vahvan salasanan. (Kuinka satunnainen tämä oikeasti on?)

[04:48] Ajoin komennon <code>./manage.py createsuperuser</code>. Jätin käyttäjänimen blankoksi (jolloin käyttäjätunnukseksi tulee "matiask").

[04:59] Käytin W3M-selainta ja kirjauduin sisään adminina saaden näkyviin admin-paneelin.

![ADMIN view näkyy](https://user-images.githubusercontent.com/105177604/221810104-0bb94d63-bd36-453b-83f1-b01ab4d6b5b9.JPG)

[05:00] Tein Toimitusjohtaja-nimisen käyttäjän admin-paneelissa.

![11](https://user-images.githubusercontent.com/105177604/221810247-39ec215e-fab1-4906-a865-4dd52d6f5982.JPG)

[05:07] Selasin alaspäin ja annoin Toimitusjohtajalle superuser- ja staff-oikeudet.

[05:15] Vaihdettuani käyttäjän Toimitusjohtajaksi kokeilin tehdä uuden ryhmän ("group") "Henkilokunta". Se onnistui.

![13 henkilokunta](https://user-images.githubusercontent.com/105177604/221810488-26612383-48b3-48d7-a900-e2396b63de7e.JPG)

[05:25] Ajoin komennon <code>./manage.py startapp register</code>.

[05:34] Avasin asetustiedoston komennolla <code>micro harjoituscompany/settings.py</code>. Lisäsin rivin 'register' ja tallensin tiedoston.

![14](https://user-images.githubusercontent.com/105177604/221811636-9d97e684-2c5a-49d0-b84c-ebab911e7d73.JPG)

[05:42] Ajoin komennon <code>micro register/models.py</code>. Tein kuvanmukaisen taulun.

![15](https://user-images.githubusercontent.com/105177604/221811680-99843e98-d60f-49e3-b077-d44d4e8c941b.JPG)

[06:09] Suoritin migraatiot komennoilla <code>./manage.py makemigrations</code> ja <code>./manage.py migrate</code>.

![16 migraatiot](https://user-images.githubusercontent.com/105177604/221811953-c457b586-94ff-4ed3-8745-30a81c9d75a9.JPG)

[06:11] Avasin tietokannan komennolla <code>micro register/admin.py</code>. Tein alapuolisen kuvan mukaiset lisäykset ja tallensin tiedoston.

![17](https://user-images.githubusercontent.com/105177604/221812070-c1f8c67b-df37-4c9d-a7c6-2e7f6d3bb150.JPG)

[06:55] Käynnistin serverin komennolla <code>./manage.py runserver</code>. Kirjauduin sisään Toimitusjohtajana. Lisäsin ajoneuvoja tietokantaan, muokkasin yhden ajoneuvon tietoja ja poistin sen sitten onnistuneesti.

![18 ajoneuvot tietokannassa](https://user-images.githubusercontent.com/105177604/221812153-d6633d0a-bdd0-4839-a7bb-753f1cdd437f.JPG)
![autoja 19](https://user-images.githubusercontent.com/105177604/221812291-d35070e4-1910-43c4-bee3-e606390d6e8e.JPG)

<h3>Lähteet</h3>

<ol>
<li>Karvinen, Tero. Linux Palvelimet 2023 alkukevät. Luettavissa: https://terokarvinen.com/2023/linux-palvelimet-2023-alkukevat/#laksyt. Luettu: 27.2.2023. </li>
<li>Karvinen, Tero. Django 4 Instant Customer Database Tutorial. Luettavissa: https://terokarvinen.com/2022/django-instant-crm-tutorial/. Luettu: 27.2.2023.</li>
</ol>
