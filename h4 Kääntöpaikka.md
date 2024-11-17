# h4 Kääntöpaikka

## Tiivistelmä tehtävästä, tehtävänannot ja oman tietokoneen tiedot
Tähän tulee tiivistelmä 

### Tehtävänanto:
  
  x) Lue/katso/kuuntele ja tiivistä. (Tässä x-alakohdassa ei tarvitse tehdä testejä tietokoneella, vain lukeminen tai kuunteleminen ja tiivistelmä riittää. Tiivistämiseen riittää muutama ranskalainen viiva.)
  
   Hammond 2022: Ghidra for Reverse Engineering (PicoCTF 2022 #42 'bbbloat') (Video, noin 20 min)
        
   Vapaaehtoinen: € Eagle and Nancy 2020: The Ghidra Book: 2. Reversing And Disassembly Tools (Usein suositeltu kirja Ghidrasta)
        
  a) Asenna Ghidra.
    
  b) rever-C. Käänteismallinna packd-binääri C-kielelle Ghidralla. Etsi pääohjelma. Anna muuttujielle kuvaavat nimet. Selitä ohjelman toiminta. Ratkaise tehtävä binääristä, ilman alkuperäistä lähdekoodia. ezbin-challenges.zip
    
  c) Jos väärinpäin. Muokkaa passtr-ohjelman binääriä (ilman lähdekoodia) niin, että se hyväksyy kaikki salasanat paitsi oikean. Osoita testein, että ohjelma toimii. ezbin-challenges.zip
    
  d) Nora CrackMe: Käännä binääreiksi Tindall 2023: NoraCodes / crackmes. Lue README.md: älä katso lähdekoodeja, ellet tarvitse niitä apupyöriksi. Näissä tehtävissä binäärejä käänteismallinnetaan. Binäärejä ei muokata, koska muutenhan jokaisen tehtävän ratkaisu olisi vaihtaa palautusarvoksi "return 0".
    
  e) Nora crackme01. Ratkaise binääri.
    
  e) Nora crackme01e. Ratkaise binääri.
    
  f) Nora crackme02. Nimeä pääohjelman muuttujat käänteismallinnetusta binääristä ja selitä ohjelman toiminta. Ratkaise binääri.
    
  g) Vapaaehtoinen: Ja sen yli. Crackme01 on useampia ratkaisuja. Montako löydät? Miksi?
    
  h) Vapaaehtoinen: Pyytämättäkin. Crackme02 on kaksi ratkaisua. Löydätkö molemmat?
    
  i) Vapaaehtoinen, hieman haastavampi: A ray. Nora crackme02e. Ratkaise binääri.
  
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

## a) Asenna Ghidra
Asensin Ghidran jo oppitunnilla:

![image](https://github.com/user-attachments/assets/a9b8b57b-c34a-4efd-a930-f8ca9b5b1701)


### Lähteet:
Tehtävän lähteet tähän

## b) rever-c
Tehtävässä piti käänteismallintaa Ghidra C-kielelle ja selittää ohjelman toimintaa.
Aloitin tekemällä uuden projektin ja siirtämällä `packd` ohjelman Ghidraan. Tämän jälkeen avasin sen ja valitsin "Analyze now". Pääsin seuraavaan näkymään:

![image](https://github.com/user-attachments/assets/0e39c963-680d-49d4-af1c-48441f9ca85f)

Ensin muistelin Ghidran käyttöä, klikkailin valikoita ja yritin hahmotella mitä näkyy. Löysin kohdan jossa luki `main` ja klikkaamalla sitä sain seuraavanlaisen näkymän:

![image](https://github.com/user-attachments/assets/3507b13e-078d-44a9-ae7b-75f690bb74a3)

Tässä siis näkyi `main()` funktio. Aloin purkamaan funktiota osiin ja nimeämään sitä. 
Datatyyppi oli määrittämättä mutta katsomalla funktion loppua ja koska C- kielessä `main()` on datatyyppiä `int` laitoin tyypiksi `int`. En nimennyt `main()` funktiota uudestaan koska mielestäni se on hyvin kuvaava. 
Koodissa oli nimettynä kaksi muuttujaa: `int ivar1` ja `char local_28 [32]`. 

### Koodin toiminta
1. Ohjelma käynnistyy
2. Kysyy syötteen
3. Lukee syötteen
4. Vertaa muuttujaa oikeaan merkkijonoon `piilos-AnAnAs`
5. Mikäli merkkijono täsmää tulostuu `"Yes! That\'s the password. FLAG{Tero-0e3bed0a89d8851da933c64fefad4ff2}"`
6. Muuten: `Sorry, no bonus.`

![image](https://github.com/user-attachments/assets/cd3f8e5a-4e11-4418-af70-8153b78b7db5)


## c) Jos väärinpäin

Aloitin tehtävän kopioimalla passtr ohjelman Ghidraan. `main()` funktio löytyi nopeasti ja päättelemällä selvisi että `ivar1 == 0` tarkoittaa että salasana on oikein. Klikkaamalla if lauseketta näin assembly puolelta missä kohdassa tämä tapahtuu. Sieltä löytyi `JNZ` eli jump if non zero joka hyppää else lausekkeeseen. Vaihdoin tyypiksi `JZ` eli jump if zero joka käänsi lausekkeen ympäri. Valitsin "Export file" ja tiedostomuodoksi "Original file". Tämän jälkeen avasin kohdehakemiston ja tein ajettavan `chmod u+x passtr`. Sen jälkeen testit toimivat näin:

 ![image](https://github.com/user-attachments/assets/410947ab-eb87-46a6-9eeb-4fd07abe7428)

 ![image](https://github.com/user-attachments/assets/4f996eff-b30e-49ce-83d8-4f77452f90c3)


## d) Crackme binääriin
Latasin ensin kaikki tiedostot zippinä ja purin `unzip master.zip`. Tämän jälkeen ohjeen mukaan laitoin `make crackme01` ja sain tiedoston `crackme01.64`. Päätin purkaa kaikki kerralla joten ajoin pelkän `make` komennon:


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
