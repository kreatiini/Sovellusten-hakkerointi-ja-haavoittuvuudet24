# TEHTÄVÄ

## Tiivistelmä tehtävästä, tehtävänannot ja oman tietokoneen tiedot
Tähän tulee tiivistelmä 

### Tehtävänanto:
   Tähän tulee tehtävänanto
  
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

## a) Strings
Latasin tehtäväpaketin(Karvinen 2024) ja purin sen. Tämän jälkeen nopealla Googlailulla selvitin mikä on `strings`. Se on ohjelma joka ottaa tulostettavat merkkijonot tiedostoista.(McKay 2019). Päätin aloittaa vain yksinkertaisella `strings passtr` komennolla. Sain  listan:

![image](https://github.com/user-attachments/assets/ab9a7efa-3c39-45a1-9057-4b2b14b8994d)

Tästä voin päätellä että salasana on `sala-hakkeri-321` ja lippu on `FLAG{Tero-d75ee66af0a68663f15539ec0f46e3b1}`. Testasin vielä ajamalla `passtr` ohjelman:

![image](https://github.com/user-attachments/assets/f43da04a-afe2-405b-9b22-fa4fc2af2712)

ja sehän toimii.
### Lähteet:
Mckay 2019: How to Use the strings Command on Linux. Luettavissa: https://www.howtogeek.com/427805/how-to-use-the-strings-command-on-linux/ Luettu: 8.11.2024
Iso-Anttila, Karvinen 2024: Application Hacking. Luettavissa: https://terokarvinen.com/application-hacking/ Luettu: 8.11.2024

## b) You shall not passtr.c (**Rannekello 0833 8.11.2024**)
Seuraavana piti muokata `passtr.c` koodia niin että strings komennolla ei pysty purkamaan suoraan salasanaa. C-kieli on uusi itselleni joten jouduin hieman perehtymään asiaan. Nyt lopetan tältä erää. **0845 8.11.2024**
Palasin asiaan  **2055 09112024**. Olin jo selaillut päivän mitä eri tapoja piilottaa salasana C- kielessä löytyy. Kaikki ohjeet mitä verkosta löytyivät olivat todella vaikeita. Jonkinlainen 
### Lähteet:
Tehtävän lähteet tähän

## c) packd
Aloitin tämän tehtävän ratkomisen samalla tyylillä kuin ensimmäisen. Ajoin `strings packd | less` ja silmäilin tulokset läpi. 
Tulokset näyttävät esim. Tältä joten kokeilen `piilos-An` salasanaa, mutta se ei toiminut. :
![image](https://github.com/user-attachments/assets/d49d504a-928f-4f7f-a4b4-543fcb0e62ba)
Katselin rivejä ja mietin olisiko tehtävässä käytetty jonkinlaista salakirjoitusta. En kuitenkaan keksinyt mitään tapaa lähteä purkamaan sitä. Löysin strings komennolla tiedostoja joihin viitattiin. `.c` ja `.o` loppuisia. Tekstissä mainittiin UPX ja selvitin että sillä on tiivistetty ohjelma. Päätin ladata sen jos saisin purettua ohjelman. Asennettuani `upx` sovelluksen purin paketin komennolla `upx -d packd`. Tämän jälkeen kokeilin ajaa `strings packd` uudestaan. Tällä kertaa löysin rivin:

![image](https://github.com/user-attachments/assets/a68d4665-667f-46eb-b5ff-3e5153a50535)

Kokeilin syöttää sen ja toimii: 

![image](https://github.com/user-attachments/assets/0ce244ea-617f-4bee-aaca-eb25244569dd)

Joten totean tehtävän tehdyksi. Kokonaisuutena luovutin jo heti aluksi, aloin pohtimaan jonkinlaista salakirjoitusta. Palattuani seuraavana päivänä päätin vain purkaa paketin. 

### Lähteet:
Tehtävän lähteet tähän

## tehtävä3

### Lähteet:
Tehtävän lähteet tähän
   
## tehtävä4

### Lähteet:
Tehtävän lähteet tähän

## tehtävä5

### Lähteet:
Tehtävän lähteet tähän

## Lähteet:
   Kaikki lähteet yhteen tähän
