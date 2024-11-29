# h6 Sulaa hulluutta

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

## tehtävä1
Aloitin käyttämällä `strings` komentoa ja sain vain paljon erilaisia merkkijonoja jotka eivät vaikuttaneet miltään. Testasin myös satunnaista netistä lataamaani kuvaa ja merkkijonot vaikuttivat samantyyppisiltä.

![image](https://github.com/user-attachments/assets/dcff5a8f-8469-4002-95f2-5878e09521ce)

`exiftool`
![image](https://github.com/user-attachments/assets/f0af2598-5dbc-4585-b268-1fccc79b938d)

`file` kertoo sen olevan kuva. 

![image](https://github.com/user-attachments/assets/184ffd1b-f439-4a3f-ba59-6b5fb8a48465)


# h2
Seuraavana ajoin komennon `binwalk h1.jpg` :

![image](https://github.com/user-attachments/assets/df2be75e-d3bd-4e55-90b1-0c422c7d231e)

Ilmeisesti tämä tarkoittaa kuvan sisältävän zip tiedostoja. Kokeilen purkaa tiedoston `binwalk -e h1.jpg` ja saan uuden hakemiston:

![image](https://github.com/user-attachments/assets/1ae5228a-3382-4815-aca1-b526f24db211)

Hakemistosta löytyy `zip` kansio, pari hakemistoa joissa `.xml` tiedostoja. katsoin `494F5.zip` tiedoston `file` komennolla ja se kertoi tiedoston olevan Word 2007+ tiedosto:

![image](https://github.com/user-attachments/assets/77734855-ac08-418f-9f09-daf0b4e1af60)
Kävin läpi tiedostoja joissa oli tyylitietoja, itse dokumentin tekstisisältöä ja tiedoston tekijä:

![image](https://github.com/user-attachments/assets/1c763976-4cb6-4b52-9239-2428e7aa191b)

![image](https://github.com/user-attachments/assets/df10bd52-ce2a-4a87-83c8-854c95a391c2)

En löytänyt tiedostoista mitään mielenkiintoista enkä keksinyt miten saisin tiedostosta word tiedoston avattavaan muotoon. 

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

## tehtävä1

### Lähteet:
- Tehtävän lähteet tähän

## tehtävä2

### Lähteet:
- Tehtävän lähteet tähän

## tehtävä3

### Lähteet:
- Tehtävän lähteet tähän

## tehtävä3

### Lähteet:
- Tehtävän lähteet tähän
   
## tehtävä4

### Lähteet:
- Tehtävän lähteet tähän

## tehtävä5

### Lähteet:
- Tehtävän lähteet tähän

## Lähteet:
  -  Tehtävät: Karvinen 2024: Palvelinten hallinta. Luettavissa: https://terokarvinen.com/palvelinten-hallinta/

### Lähteet:
- Tehtävän lähteet tähän

## tehtävä2

### Lähteet:
- Tehtävän lähteet tähän

## tehtävä3

### Lähteet:
- Tehtävän lähteet tähän

## tehtävä3

### Lähteet:
- Tehtävän lähteet tähän
   
## tehtävä4

### Lähteet:
- Tehtävän lähteet tähän

## tehtävä5

### Lähteet:
- Tehtävän lähteet tähän

## Lähteet:
  -  Tehtävät: Karvinen 2024: Palvelinten hallinta. Luettavissa: https://terokarvinen.com/palvelinten-hallinta/
