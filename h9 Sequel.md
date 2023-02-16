<h3>h9 Sequel</h3>

<h3>x) Yrityssoftaa </h3>

Tehtävänannossa pyydetään keksimään esimerkki palvelusta, jota käytetään nettiselaimella, jossa koodia ajetaan palvelimelle ja jossa taustalla on tietokanta. Esimerkkinä tällaisesta palvelusta voisi käyttää ehkäpä Facebookia.

On ilmeistä, että tämä ratkaisu säästää levytilaa. Vaikka periaatteessa jokainen Facebookin sivu voisi olla oma palvelimelle tallennettu verkkosivunsa kaikkine kuvine ja linkkeineen, niin on turha tallentaa esimerkiksi samaa profiilikuvaa/avataria jopa kymmeniä tuhansia kertoja eri paikkaan aina käyttäjän kommentoidessa jotakin postausta.

Tietokantapohjainen ratkaisu on myös näppärämpi ja notkeampi, jos ja kun tietoja halutaan yhdistää muihin palveluihin. Facebookia pyörittävän Metan kaltaiselle yritykselle tämä on luonnollisesti tärkeää, koska Facebook ei ole ainoa sen palveluista.

Myös markkinointimielessä tietokanta on verraton. Yhteen käyttäjätiliin yhdistyy tietoja, joihin yhdistyy tietoja. Näiden tietojen järkevä käsittely suorastaan vaatii tietokantapohjaista ratkaisua, kun halutaan tietää, mikä käyttäjää kiinnostaa ja näyttää hänelle kohdistettuja mainoksia.

<h3>a) Postgre</h3>

[00:53] Käyttäen apuna Karvisen vanhempaa kirjoitusta[1] tein uuden käyttäjän ("postuser"), koska olin jo asentanut "matiask"-käyttäjälleni Postgresql:n.

![1](https://user-images.githubusercontent.com/105177604/219267982-32b08dc1-fb5d-443f-90ff-98872744a87c.JPG)

[00:57] Vaihdoin käyttäjän postuseriksi.

[00:58] Yritin käynnistää PostgreSQL:n tarkistaakseni, ettei matiask-käyttäjälle tehty asennus näy. Se näkyi olevan olemassa ja kertasin tehtävänantoa[2].

![2](https://user-images.githubusercontent.com/105177604/219267989-47814daf-50df-405d-9036-ca148aa99cbe.JPG)

[00:59] Tein sitten tehtävänannon[2] mukaisesti uuden tietokannan ja tietokantakäyttäjän postuserille.

![3](https://user-images.githubusercontent.com/105177604/219267999-a397d8ab-cbca-46c8-a977-267ad0cfeba9.JPG)

[01:04] Testasin uuden tietokannan SQL-komennolla. Se toimi.

![4](https://user-images.githubusercontent.com/105177604/219268007-227aef16-a754-43f1-a56b-42e9c167bc18.JPG)

<h3>b) Crud</h3>

[04:53] Avasin PostgreSQL:n komennolla <code>psql</code>.

[04:53] Kertasin ohjeita[3], koska edellisistä SQL-opinnoistani oli jo kulunut aikaa. 

[04:58] Tein uuden taulun "items" komennolla <code>CREATE TABLE items (id SERIAL PRIMARY KEY, name VARCHAR(100));</code>. Katsoin tauluja komennolla <code>/d</code>.

![5](https://user-images.githubusercontent.com/105177604/219268057-2a38a66f-ddb4-4895-b644-347096f54231.JPG)

[05:02] Lisäsin tauluun esineet "milk", "bread" ja "apple". Tulostin kaiken taulusta "items".

![6](https://user-images.githubusercontent.com/105177604/219268072-a6bb8538-8487-4713-93a4-59ce14368c44.JPG)

[05:06] Muutin tietueen "apple" muotoon "apple, granny smith". Tulostin kaiken taulusta "items".

![7](https://user-images.githubusercontent.com/105177604/219268086-877bdd95-6a8e-4219-8ac5-6dfb4cdc0bed.JPG)

[05:08] Poistin tietueen "milk". Tulostin kaiken taulusta "items".

![8](https://user-images.githubusercontent.com/105177604/219268099-902ca7a2-21cd-412c-a513-fd6990339d22.JPG)

<h3>Lähteet</h3>

<ol>
<li>Karvinen, Tero. First Steps on a New Virtual Private Server – an Example on DigitalOcean and Ubuntu 16.04 LTS. 2017. Luettavissa: https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/. Luettu: 16.2.2023.</li>
<li>Karvinen, Tero. Linux Palvelimet 2023 alkukevät. Luettavissa: https://terokarvinen.com/2023/linux-palvelimet-2023-alkukevat/. Luettu: 16.2.2023.</li>
<li>Karvinen, Tero. PostgreSQL Install and One Table Database – SQL CRUD tutorial for Ubuntu. 2016. Luettavissa: https://terokarvinen.com/2016/postgresql-install-and-one-table-database-sql-crud-tutorial-for-ubuntu/. Luettu: 16.2.2023.</li>
</ol>
