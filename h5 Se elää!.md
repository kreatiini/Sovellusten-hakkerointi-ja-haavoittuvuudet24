# H5 Se elää!

## Tiivistelmä tehtävästä, tehtävänannot ja oman tietokoneen tiedot
Tällä kertaa tehtävät olivat minulle todella vaikeita enkä saanut niitä tehtyä. Tunnilla tuntui selkeältä mutta nyt koodin selaaminen oli todella vaikeaa. En hahmottanut mitä teen ja mitä gdb minulle näyttää. Eli missä kohdassa koodin suoritusta ollaan jotta saisin oikeat tiedot rekistereistä. 

### Tehtävänanto:
  a) Lab1. Tutkiminen mikä on ohjelmassa vialla ja miten se korjataan. lab1.zip
  
  b) Lab2. Selvitä salasana ja lippu + kirjoita raportti siitä miten aukesi. lab2.zip
    
  c) Lab3. Kokeile Nora Crackmes harjoituksia tehtävä 3 ja 4 ja loput vapaaehtoisia. Tindall 2023: NoraCodes / crackmes.
  
  d) Lab4. Vapaaehtoinen: Crackmes.one harjoitus. Saatko salasanan selville? lab4.zip Moodlessa.
  
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

## a) Lab1
##a)Aloitin tutkailemalla koodia. Annoin komennon `list` kaksi kertaa saadakseni koko lähdekoodin näkyviin. Koodia katsoessa näkyy että koodissa on kaksi funktiota `print_scrambled()` sekä `main()`.
Ensimmäisen funktion tehtävänä on tulostaa teksti jossa viestin jokaisesta ASCII merkistä vähennetään kolme. Main funktiossa koodi ajetaan. `bad_message` on arvoltaan NULL. Kun koodin ajaa komennolla `start` loppuun asti,
tulee herja `Program terminated with signal SIGSEGV`. Tämä on jonkinlainen muistiongelma joka johtuu varmaan tästä `NULL` arvosta. Ongelma voidaan korjata esim. Alustamalla teksti jollain kuten `Not good message`. 
Jaoin näytön kahteen `layout split` komennolla ja laitoin breakpointin mainiin `break main`. Ajoin komennolla start ja rullailin läpi `next`. Tämän jälkeen lisäsin watchpointit molempiin muuttujiin
komennoilla `watch bad_message` ja `watch good_message`. Rullailin läpi `start` ja `next`. Selailtuani eteenpäin `good_message` sai arvoksi `Khoor/#zruog1` ja jatkoin. Ongelma tosiaan on kun funktio
yrittää sekoittaa `bad_message` muuttujaa mutta sen arvo on `NULL`. Asetin sille valmiin muuttujan sillä `good_message` muuttujassa oli arvo ja ohjelma ei ottanut syötettä.
Muokkasin koodin:


`g++ gdb_example1.c new` ja `chmod u+x new`. Tämän jälkeen testasin
`./new` ja sain seuraavan tuloksen: 

**KUVA**.

Nyt ohjelma toimii ilman ongelmaa.


## b) lab2
salasanoja toisiinsa. Päätin tutkailla hieman muistissa olevia asioita. En kuitenkaan löytänyt mitään mielenkiintoista. Selattuani pidemmälle löysin `XOR` kohdan. Tutustuin rekistereihin. Aloitin käynnistämällä `passtr2o` `./passtr2o` ja ohjelma kysyi salasanaa. Kokeilin tyhjää ja 1234 syötteitä. Väärä salis. Käynnistin `gdb passtr2o`. Tämän jälkeen `layout split`.

. Kokeilin listata `list` mutta se ei tehnyt mitään.
Seuraavana lisäsin breakpointin mainiin `break main`. Ajoin `start` ja seurailin vain koodin läpi miltä assembly näyttää. En ymmärtänyt juurikaan joten yksityiskohtaisempaa seurantaa vaatii. Selaamalla `step` komennolla löysin salassanan kyselyn jälkeen `TEST` kohdan jossa ehkä verrataan
salasanoja toisiinsa. Päätin tutkailla hieman muistissa olevia asioita. En kuitenkaan löytänyt mitään mielenkiintoista. Selattuani pidemmälle löysin `XOR` kohdan. Tutustuin rekistereihin.

Ehkä ehdin myöhemmin tänään katsomaan uudestaan.


## c)Lab3 Noracrackmes 3 ja 4
Muutin tekstit ajettavaan muotoon ja aloin tutkailemaan. En kuitenkaan päässyt näissäkään mihinkään. Katsotaan saanko muutaman youtube videon jälkeen tehtävän tehtyä myöhemmin.


**EDIT 23.52 25.11.2024** Jatkoin yrittämistä lab2 kanssa. Ei onnistunut mitenkään päin. Sain ulos "RIVATE" Joka ei varmaan liity mitenkään tehtävään vaan itse koodiin. 

## Lähteet:
  -  Tehtävät: Iso-Anttila, Karvinen 2024. Sovellusten hakkerointi ja haavoittuvuudet. Luettavissa: [https://terokarvinen.com/palvelinten-hallinta/](https://terokarvinen.com/application-hacking/)
