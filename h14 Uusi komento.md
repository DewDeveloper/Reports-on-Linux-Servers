<h1>h14 Uusi komento</h1>

<h3>Tehtävänanto a):</h3>

*Tee Linuxiin uusi komento Bashilla. Komennon tulee toimia kaikilla käyttäjillä, työhakemistosta riippumatta. Tee jotain muuta kuin "hei maailma".*

[13.3. 11:14] Tein sudo-oikeuksilla skripti-kansion /usr-hakemistoon komennolla <code>mkdir skripti</code>.

![1](https://user-images.githubusercontent.com/105177604/224974976-5c13a94f-ed36-4033-b362-9cea7f30d512.JPG)

[11:38] Siirryin skripti-kansioon komennolla <code>cd skripti</code>.

[11:38] Loin Microlla <code>alphakomento.sh</code>-nimisen tiedoston. Ohjelma pyytää käyttäjää syöttämään URL:n, lukee syötteen ja sen jälkeen pingaa sitä viidesti. Käytin apuna Phoenixnapin opasta ping-komennon käytöstä[1] ja FreeCodeCampin opasta shellskriptauksesta[2].

![2](https://user-images.githubusercontent.com/105177604/224974992-d955ee90-7aa3-43ca-b530-891f3ed00495.JPG)

![3](https://user-images.githubusercontent.com/105177604/224975008-e6b8ecb1-0246-4b76-b335-18c52e675144.JPG)

[11:58] Testasin skriptiä komennolla <code>bash alphakomento.sh</code> onnistuneesti.

![4](https://user-images.githubusercontent.com/105177604/224975040-4ce29147-cf5b-400e-98f5-72ca711285de.JPG)

[12:28] Muutin <code>alphakomento.sh</code>-tiedoston oikeuksia komennolla <code>sudo chmod u=rwx,g=rwx,o=rwx alphakomento.sh</code> antaen kaikille oikeudet lukea, kirjoittaa ja suorittaa sitä.

![5](https://user-images.githubusercontent.com/105177604/224975056-de7437e5-fd53-4dcf-9516-40adf4ce34d0.JPG)

[12:44] Tarkistin vielä oikeudet komennolla <code>ls -l alphakomento.sh</code>.

![7](https://user-images.githubusercontent.com/105177604/224975071-2bf076bb-d1ce-4db9-9b59-f2efff73d7cc.JPG)

<h3>Tehtävänanto b)</h3> 

*Tee Linuxiin uusi komento Pythonilla. Komennon tulee toimia kaikilla käyttäjillä, työhakemistosta riippumatta.*

[13.3. 13:44] Tein Microlla toiminnallisuudeltaan edellistä tehtävää vastaavan <code>bravokomento.py</code>-tiedoston. Käytin apuna Stackabuse-sivustoa[3]. Kokeilin, että se toimii oikein.

![8](https://user-images.githubusercontent.com/105177604/224975301-d2cc14c1-827b-4933-9da1-93ce7929bf66.JPG)

![10](https://user-images.githubusercontent.com/105177604/224975315-ece919e1-008c-49bf-b423-07edafdb9a81.JPG)

[13:53] Tarkastin oikeudet komennolla <code>ls -l bravokomento.py</code>. Annoin muillekin oikeudet ajamalla jälleen komennon <code>sudo chmod u=rwx,g=rwx,o=rwx bravokomento.py</code>. Tarkastin vielä oikeudet.

![9](https://user-images.githubusercontent.com/105177604/224975399-48d39599-176c-403d-8eed-be2d4da410fa.JPG)

<h3>Tehtävänanto: c) </h3>
  
*Tee Linuxiin komento, joka tekee jotain monelle tiedostolle*

Päätin tehdä skriptin, joka tulostaa kaikkien kansion tiedostojen sisällön. 

[14.3. 12:15] Luin Stackoverflowsta[5], kuinka tehdään kaikki kansion tiedostoja koskeva komento. Tein Microlla <code>tulostakaikki.sh</code>-nimisen tiedoston, johon kirjoitin <code>cat *</code> ja tallensin. Testasin toimivuuden ajamalla tiedoston komennolla <code>bash tulostakaikki.sh</code>, ja se tulosti kaikkien kansiossa olleiden tiedostojen sisällön.

![11](https://user-images.githubusercontent.com/105177604/224975414-dcf3af05-ec3a-428f-b510-083cf567283c.JPG)

[12:25] Muutin tiedoston oikeuksia komennolla <code>sudo chmod u=rwx,g=rwx,o=rwx tulostakaikki.sh</code>

[12:27] Tein uuden kansion komennolla <code>sudo mkdir testi</code> ja siirryin kansioon komennolla <code>cd testi</code>. Tein kansioon kaksi tekstitiedostoa, <code>a.txt</code> ja <code>b.txt</code>.

[12:29] Tein testikäyttäjän komennolla <code>sudo useradd testi</code>. Vaihdoin käyttäjän salasanan komennolla <code>sudo passwd testi</code>.

[12:33] Kirjauduin testikäyttäjään komennolla <code>su testi</code>. Tarkistin komennolla <code>pwd</code>, että olen kansiossa <code>/usr/skripti/testi</code>. Annoin komennon <code>bash /usr/skripti/tulostakaikki.sh</code>. Konsoliin tulostui kahden tekstitiedoston sisältö, eli pystyin ajamaan skriptin toisella käyttäjällä ja toisessa kansiossa kuin missä skripti oli. Toimivuus oli siis varmistettu.

![12](https://user-images.githubusercontent.com/105177604/224975429-412494ad-1600-4e35-be07-9d3bc5dcaf87.JPG)

<h3>Lähteet</h3>

<ol>
<li>Phoenixnap. Linux Ping Command Tutorial with Examples. 2019. Luettavissa: https://phoenixnap.com/kb/linux-ping-command-examples. Luettu: 13.3.2023.</li>
<li>FreeCodeCamp. Shell Scripting for Beginners – How to Write Bash Scripts in Linux. 2022. Luettavissa: https://www.freecodecamp.org/news/shell-scripting-crash-course-how-to-write-bash-scripts-in-linux/. Luettu: 13.3.2023.</li>
<li>Heydari, Sajjad. Executing Shell Commands with Python. Luettavissa: https://stackabuse.com/executing-shell-commands-with-python/. Luettu: 13.3.2023.</li>
<li>Phoenixnap. Linux File Permission Tutorial: How to Check and Change Permissions. Luettavissa: https://phoenixnap.com/kb/linux-file-permissions#ftoc-heading-3. Luettu: 13.3.2023.</li>
<li>Stackoverflow. How to do something to every file in a directory using bash? Luettavissa: https://stackoverflow.com/questions/1310422/how-to-do-something-to-every-file-in-a-directory-using-bash. Luettu: 14.3.2023.</li>
</ol>
