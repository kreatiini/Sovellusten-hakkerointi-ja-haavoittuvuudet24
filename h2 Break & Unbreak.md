# h2 Break & Unbreak

## Tiivistelmä tehtävästä, tehtävänanto ja oman tietokoneen tiedot
Tähän tulee tiivistelmä 

### Tehtävänanto:
**x)** Lue/katso/kuuntele ja tiivistä. (Tässä x-alakohdassa ei tarvitse tehdä testejä tietokoneella, vain lukeminen tai kuunteleminen ja tiivistelmä riittää. Tiivistämiseen riittää muutama ranskalainen viiva.)

   OWASP: OWASP Top 10: A01 Broken Access Control
   
   Karvinen 2023: Find Hidden Web Directories - Fuzz URLs with ffuf
   
   PortSwigger: Access control vulnerabilities and privilege escalation
   
   Karvinen 2006: Raportin kirjoittaminen
   
   Vapaaehtoinen: PortSwigger 2020: What is SQL injection? - Web Security Academy (noin 10 min video)
   
   **a)** Murtaudu 010-staff-only. Ks. Karvinen 2024: Hack'n Fix
   
   **b)** Korjaa 010-staff-only haavoittuvuus lähdekoodista. Osoita testillä, että ratkaisusi toimii.
   
   **c)** Ratkaise dirfuzt-1 artikkelista Karvinen 2023: Find Hidden Web Directories - Fuzz URLs with ffuf. Tämä auttaa 020-your-eyes-only ratkaisemisessa.
   
   **d)** Murtaudu 020-your-eyes-only. Ks. Karvinen 2024: Hack'n Fix
   
   **e)** Korjaa 020-your-eyes-only haavoittuvuus. Osoita testillä, että ratkaisusi toimii.
   
   **g)** Vapaaehtoinen. Johdantotehtävä, joka auttaa 010-staff-only ratkaisemisessa. Ratkaise Portswigger Academyn "Lab: SQL injection vulnerability in WHERE clause allowing retrieval of hidden data".
   
   **h)** Vapaaehtoinen. Johdantotehtävä, joka auttaa 010-staff-only ratkaisemisessa. Ratkaise Portswigger Academyn "Lab: SQL injection vulnerability allowing login bypass"
   
  
### Tietokoneen tiedot: 
- Näytönohjain: Asus GeForce RTX 3070 Ti ROG Strix - OC Edition
- Virtalähde: Corsair 750W SF Series SF750, modulaarinen SFX-virtalähde
- Emolevy: Asus ROG STRIX B550-I GAMING, Mini-ITX -emolevy
- Prosessori: AMD 5800x3D
- RAM: Corsair 32GB (2 x 16GB) Vengeance LPX, DDR4 3600MHz, CL18,
- SSD: Samsung 1TB 980 SSD-levy, M.2 2280, PCIe 3.0 x4, NVMe 1.4, sekä Kingston 1TB A2000 NVMe PCIe SSD-levy, M.2 2280, 2200/2000
- Käyttöjärjestelmä: Edition	Windows 10 Pro Version	22H2
- Virtuaaliympäristö: VirtualBox Version 7.0.14 r161095 (Qt5.15.2)
- Operating System: Debian GNU/Linux 12 (bookworm)  
- Kernel: Linux 6.1.0-25-amd64

## x) Lue ja tiivistä

### Lähteet:
Tehtävän lähteet tähän

## a) 010-staff-only
Tämän tehtävän ehdin jo ratkaisemaan ennen tehtävänantoa kotitehtäväksi. Tehtävä oli kuitenkin looginen SQL-injektio kuten harjoitustehtävät ennen tätä. Jouduin perehtymään vähän paremmin SQL-injektion maailmaan mutta onnistuin ratkaisemaan tehtävän. Kokeilin ensin kaikenlaisia muotoja kunnes osuin oikeaan. Laitan tähän kuvankaappauksen muistiinpanoista jotka tein tehtävää tehdessä:

![image](https://github.com/user-attachments/assets/ae513954-00f4-4527-a256-612c8d65752e)

Eli tutkailin erilaisilla injektioilla. Päättelin 1. ja 2. Salasanan näiden SQL-komentojen avulla. Ajattelin siis että selvitän seuraavan salasanan saadakseni mahdollisen admin salasanan jonka sainkin. Sain sen komennolla `' OR 1=1 LIMIT 2,1 --` ja vastaus oli ` SUPERADMIN%%rootALL-FLAG{Tero-e45f8764675e4463db969473b6d0fcdd}`

### Lähteet:
Karvinen 2023: Hack'n Fix Luettavissa: https://terokarvinen.com/hack-n-fix/ Luettu 1.11.2024
Portswigger: What is SQL Injection. Luettavissa: https://portswigger.net/web-security/sql-injection#examining-the-database Luettu 30.10.2024
W3Schools: SQL Comments. Luettavissa: https://www.w3schools.com/sql/sql_comments.asp Luettu 30.10.2024

## b) 010-staff-only, this time for real
En juurikaan muista mitä tein tälle tehtävälle. Olin jotain kirjoittanut itselleni muistiin. Riviltä 19 eteenpäin muutin niin että pin ei ole suora syöte.

![image](https://github.com/user-attachments/assets/349e7d29-50a7-4bed-91fb-4851d668f449)

Testatessa se toimii nyt oikein. Ainakaan aiemmin toiminut SQL-Lause ei toimi. Oma pin-koodi kuitenkin antaa oikean vastauksen. Myös Adminin pin-koodi antaa oikean vastauksen.

![image](https://github.com/user-attachments/assets/47ab9b32-854b-448a-8ded-d6a0eb9dba8e)

![image](https://github.com/user-attachments/assets/30529c15-b76f-42bc-a3d7-2743b629f29e)

![image](https://github.com/user-attachments/assets/9e35a3e0-569a-4b89-b7ac-e301743e66de)


### Lähteet:
Karvinen 2023: Hack'n Fix Luettavissa: https://terokarvinen.com/hack-n-fix/ Luettu 1.11.2024
Benita: Preventing SQL Injection Attacks With Python. Luettavissa: https://realpython.com/prevent-python-sql-injection/ Luettu 29.11.2024
## c) dirfuzt-1
Olin jo aiemmin asentanut ffufin valmiiksi [Teron ohjeiden](https://terokarvinen.com/2023/fuzz-urls-find-hidden-directories/) mukaan. Olin myös jo tehnyt valmiiksi ensimmäisen dirfutz-0 tehtävän. Tämä tehtävä oli siis helppo ratkaista. Latasin paketin ja laitoin sen käyttöön. Etusivu näytti tältä:

![image](https://github.com/user-attachments/assets/6caa37b9-5036-4384-a63f-5433f5a85867)

Otin virtuaalikoneeni irti verkosta. Tämän jälkeen käynnistin ffufin ensin normaalisti komennolla `./ffuf -w common.txt -u http://127.0.0.2:8000/FUZZ`. Havaitsin että tuloksissa oli paljon paketteja joiden koko oli 154, joten päätin filtteröidä ne pois komennolla `/ffuf -w common.txt -u http://127.0.0.2:8000/FUZZ -fs 154`. Nyt sain seuraavan listan:

![image](https://github.com/user-attachments/assets/ceb89c71-7d24-46bc-881a-db739788ec57)

Listalta päätin valita ensin suurimman ja nimeltään loogisimman tähän tarkoitukseen eli `wp-admin`.
Siirryin selaimella tähän sivuun ja tuloksena oli:
![image](https://github.com/user-attachments/assets/a6b174cb-ca26-4133-a674-387c56ca5a2c)

Kokeilin myös muut tulokset ja myös `.git` tuloksilla lippu tuli näkyviin. Erona oli lipun tunnus:

![image](https://github.com/user-attachments/assets/71a786d1-5b24-4bdc-a2ad-b070c99a6154)


### Lähteet:

Karvinen 2023: Find Hidden Web Directories - Fuzz URLs with ffuf. Luettavissa: https://terokarvinen.com/2023/fuzz-urls-find-hidden-directories/. Luettu 1.11.2024

   
## d) 020-your-eyes-only
Olin jo asentanut Djangon ja tehnyt valmistelut tehtävää varten oppitunnilla. Käynnistin siis palvelimen `./manage.py runserver` komennolla. Etusivu näytti tältä:

![image](https://github.com/user-attachments/assets/61a7f8d9-a50b-467d-9bd5-a5c1ed81664c)

Ehdin jo tunnilla hieman tutustua sivun toimintaan. Loin myös tunnuksen sivulle oppitunnin aikana. En kuitenkaan pystynyt kirjautumaan enää ulos. Ajattelin nyt aloittaa siis sivun tutkimisen ensin kirjautumatta. 
Tunnilla koitin jo klikkailla ja selata kaikenlaista. Koska nyt oli jo valmisteleva tehtävä vinkkinä, ajattelin käynnistää ffufin ensimmäisenä. Ajoin ffufin ensin ilman rajoituksia: `./ffuf -w common.txt -u http://127.0.0.1:8000/FUZZ`
Ainoa tulos oli `admin-console` Status `301`. Koitin avata sivun mutta ei tapahtunut mitään. Päätin muuttaa hakuehtoja myös seuraavanlaisiksi:
- `./ffuf -w common.txt -u http://127.0.0.1:8000/admin-console/FUZZ` ei tuloksia
-  `./ffuf -w common.txt -u http://127.0.0.1:8000/admin-dashboard/FUZZ` ei tuloksia
-  `./ffuf -w common.txt -u http://127.0.0.1:8000/accounts/FUZZ` tulokset: login, logout ja register. Status 301. Linkit johtivat oikeille sivuille.
Kokeilin tehdä samat haut hitaammin laittamalla loppuun parametrin `-rate 50`. Tulokset pysyivät samana. Olin jo alkamassa kaivamaan salasanalistoja esiin kun päätin kirjautua sisään ja siirtyä sivulle `http://127.0.0.1:8000/admin-console/`
Kirjautuneena sisään sain seuraavanlaisen sivun auki:

![image](https://github.com/user-attachments/assets/ed955716-b00d-433f-840d-ff9abfaeb0f8)


### Lähteet:
Loami Barbosa Dos Santos: ffuf Luettavissa: https://linuxcommandlibrary.com/man/ffuf Luettu: 1.11.2024
Karvinen 2023: Find Hidden Web Directories - Fuzz URLs with ffuf. Luettavissa: https://terokarvinen.com/2023/fuzz-urls-find-hidden-directories/. Luettu 1.11.2024
Karvinen 2023: Hack'n Fix Luettavissa: https://terokarvinen.com/hack-n-fix/ Luettu 1.11.2024

## 020-your-eyes-only, hopefully
Seuraavana lähdin tutustumaan ohjelman koodiin. Nämä tehtävät ovat minulle haasteellisempia. Ymmärrän ohjelmoinnin perusasiat. Nämä tehtävät tuntuvat hieman edistyneemmiltä. Selailin koodia ja löysin tämän:

![image](https://github.com/user-attachments/assets/b00224d1-a557-4d53-af53-465138ffbea7)

Löysin myös kyseisen sivun html tiedoston. Aina tietysti sivun voisi poistaa, mutta tarkoitus varmaan on näyttää se ainoastaan admin luvilla. 

Onnistuin löytämään oikean tiedoston jossa määritellään luvat. Koska AdminShowAllViewissä ei ollut `self.request.user.is_staff` osaa. Lisäsin sen sinne:

![image](https://github.com/user-attachments/assets/29fe415d-9f0d-4c5b-a205-f8cbc0b94551)

Tallensin ja tein migraatiot. Tämän jälkeen käynnistin tuotantopalvelimen uusiksi:
Kuten näkyy olen kirjautuneena käyttäjälleni: 
![image](https://github.com/user-attachments/assets/ab14c6f8-d199-4efc-80f8-a66076cdd6df)

ja siirtyessäni admin-console osoitteeseen:

![image](https://github.com/user-attachments/assets/39190119-ced0-4f3c-8015-076c72c49898)

Eli ainakaan sivulle ei pysty nyt siirtymään. Sivu kuitenkin löytyy ffufin avulla. En tiedä onko sillä merkitystä.


### Lähteet:
Django documentation. Luettavissa: https://docs.djangoproject.com/en/5.1/topics/auth/default/ Luettu: 1.11.2024
Karvinen 2023: Hack'n Fix Luettavissa: https://terokarvinen.com/hack-n-fix/ Luettu 1.11.2024

## Lähteet:
   Kaikki lähteet yhteen tähän
