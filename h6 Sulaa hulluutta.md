# h6 Sulaa hulluutta

## Tiivistelmä tehtävästä, tehtävänannot ja oman tietokoneen tiedot
Olin poissa viime luennon joten missasin varmasti paljon tärkeää asiaa aiheeseen liittyen. Sain kuitenkin jotain aikaiseksi tähänkin tehtävään. Harmillisesti oma osaamiseni ei ole vielä riittävällä tasolla näin pilkottujen koodien analysointiin.  

### Tehtävänanto:
a) Tutki tiedostoa h1.jpg jo opituilla työkaluilla. Mitä saat selville?

b) Tutki tiedostoa h1.jpg binwalk:lla. Mitä tietoja löydät nyt tiedostosta? Mitä työkalua käyttäisit tiedostojen erottamiseen? (Huomaa, että binwalk versio 2.x ja 3.x toimivat eri tavalla.)

c) FOSS (Free Android OpenSource). Tutustu Android-sovelluksiin Offan (2024) listalta: Android FOSS. Valitse listalla itsellesi mielenkiintoisin applikaatio ja mene sen GitHubiin. Lataa ohjelman APK itsellesi ja käytä seuraavia työkaluja tutustuaksesi, miten APK:n voi avata.

    ZIP
    JADX
    Bytecode-viewer
  
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

## a)
Aloitin käyttämällä `strings` komentoa ja sain vain paljon erilaisia merkkijonoja jotka eivät vaikuttaneet miltään. Testasin myös satunnaista netistä lataamaani kuvaa ja merkkijonot vaikuttivat samantyyppisiltä.

![image](https://github.com/user-attachments/assets/dcff5a8f-8469-4002-95f2-5878e09521ce)

`exiftool`
![image](https://github.com/user-attachments/assets/f0af2598-5dbc-4585-b268-1fccc79b938d)

`file` kertoo sen olevan kuva. 

![image](https://github.com/user-attachments/assets/184ffd1b-f439-4a3f-ba59-6b5fb8a48465)


## b)
Seuraavana ajoin komennon `binwalk h1.jpg` :

![image](https://github.com/user-attachments/assets/df2be75e-d3bd-4e55-90b1-0c422c7d231e)

Ilmeisesti tämä tarkoittaa kuvan sisältävän zip tiedostoja. Kokeilen purkaa tiedoston `binwalk -e h1.jpg` ja saan uuden hakemiston:

![image](https://github.com/user-attachments/assets/1ae5228a-3382-4815-aca1-b526f24db211)

Hakemistosta löytyy `zip` kansio, pari hakemistoa joissa `.xml` tiedostoja. katsoin `494F5.zip` tiedoston `file` komennolla ja se kertoi tiedoston olevan Word 2007+ tiedosto:

![image](https://github.com/user-attachments/assets/77734855-ac08-418f-9f09-daf0b4e1af60)
Kävin läpi tiedostoja joissa oli tyylitietoja, itse dokumentin tekstisisältöä ja tiedoston tekijä:

![image](https://github.com/user-attachments/assets/1c763976-4cb6-4b52-9239-2428e7aa191b)

![image](https://github.com/user-attachments/assets/df10bd52-ce2a-4a87-83c8-854c95a391c2)

En löytänyt tiedostoista mitään mielenkiintoista enkä keksinyt miten saisin tiedoston takaisin oikeaan muoton jotta pystyisin tarkastella sitä. 

Palasin tehtävään myöhemmin koska minua häiritsi kun tiesin kyseessä olevan word tiedosto. Löysin foorumista ohjeen pakata tiedostot uudestaan .zip tiedostoon. Tärkeää oli ettei pakkaa kansiota vaan yksittäiset tiedostot ja hakemistot erikseen.(harrymc 2014) Tämän jälkeen nimesin tiedoston `.docx` ja sain tiedoston auki libreofficella. Ajattelin että tiedosto on turvallista avata virtuaalikoneella netti pois päältä. Luotin että Lari ei ole upottanut haitallista koodia tiedostoon, vaikka ikinä ei voi olla varma.

Itse dokumentista en löytänyt mitään erityisen mielenkiintoista, se on otsikoitu "50 Predictions for the Next 50 Years
A Glimpse into the Future (2025-2075)". Kuvankaappaus ensimmäisestä sivusta:

![image](https://github.com/user-attachments/assets/13798aa7-7db8-40c4-a053-835ef11cc9a5)

Innostuin kuitenkin vielä varmistelemaan ja löysin nopealla googlauksella `oleid` nimisen työkalun. Työkalun avulla pystyy tarkistamaan sisältääkö tiedosto skriptejä ja muuta tietoa. Asensin sen ja ajoin läpi:

![image](https://github.com/user-attachments/assets/fa5bc791-970a-45c3-b1e4-80cb7856e8f4)


### Lähteet
Binwalk man pages: https://manpages.org/binwalk 
Harrymc 2023: How to Convert or repackage a folder back into docx. Luettavissa: https://superuser.com/questions/1784011/how-to-convert-or-repackage-a-folder-back-into-docx Luettu 1.12.2024
deckalage 2019: Oleid: https://github.com/decalage2/oletools/wiki/oleid.


## c) FOSS
Valitsin tehtävään OpenCamera sovelluksen. Latasin SourceForgesta `.apk` paketin ja aloin tutkimaan.

### UNZIP
Purin paketin komennolla `unzip -d opencamera/ OpenCamera.apk`. Siirryin hakemistoon ja aloin selailemaan läpi. Puretun kansion sisällä näyttää tältä: 

![image](https://github.com/user-attachments/assets/9afa7fbe-e204-4e7e-b4e7-7c79347040be)
 Nämä hakemistot taas sisälsivät yli sata tiedostoa yhteensä. Selailin tiedostoja läpi mutta en oikein tiennyt mitä tehdä niiden kanssa. Sieltä löytyi .xml, kotlin tiedostoja, lisenssit ja versionumeroita.

 ### JADX
 Avasin apk paketin JADXilla. Eteeni aukesi selkeä hakemisto. Selailemalla löytyi source koodit ja kaikkea muuta sovelluksesta. 

 ![image](https://github.com/user-attachments/assets/15c17900-3f18-4ae5-9591-053121107a7d)

![image](https://github.com/user-attachments/assets/7cbaa1b4-6875-41f4-bcb4-c8973bba3b79)

Siinä pari esimerkki kuvankaappausta. Ohjelman oikeaan analysointiin en pysty vaikka työkalut siihen on tarjolla. 

### Bytecode-viewer
Avasin ohjelman ja lisäsin `OpenCamera.apk` pyydetysti. Pystyin selailemaan ohjelmaa samaan tyyliin kuin JADX avulla. Jos ymmärsin oikein tässä kuitenkin on mahdollisuus tarkastella ohjelmaa eri tulkkien avulla. Tulkkeja pystyy vaihtelemaan valikoista ja parhaimmillaan saa 3 eri näkymää samanaikaisesti. 

![image](https://github.com/user-attachments/assets/fb0d63ea-b2c1-4fe1-8c16-84ef99765f48)


Kaikenlaista sitä saa näkyviin erilaisten ohjelmien avulla. Täytyy jatkaa opiskelua että ymmärtää näkyvissä olevaa paremmin.


### Lähteet:
https://github.com/skylot/jadx

## Lähteet:
  -  Tehtävät: Iso-Anttila, Karvinen 2024: Sovellusten hakkerointi ja haavoittuvuudet. Luettavissa: https://terokarvinen.com/application-hacking/#h6-sulaa-hulluutta

rvinen 2024: Palvelinten hallinta. Luettavissa: https://terokarvinen.com/palvelinten-hallinta/
