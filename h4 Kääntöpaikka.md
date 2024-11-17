# h4 Kääntöpaikka

## Tiivistelmä tehtävästä, tehtävänannot ja oman tietokoneen tiedot
Tehtävissä tuli ratkaista Crackme haasteita. Ensimmäiset pari olivat helppoja. Viimeinen ei niinkään. Käytin todella paljon aikaa koodin tutkimiseen enkä meinannut keksiä mitä koodissa tapahtuu tärkeimmässä kohdassa. En koe ymmärtäväni koko koodia siltikään kaikilta osin. Pitkän pohdinnan jälkeen sain oikean tuloksen joten olen tyytyväinen tämän viikon tehtäviin.  

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

## x) Tiivistelmä John Hammondin videosta GHIDRA for Reverse Engineering (PicoCTF 2022 #42 'bbbloat')
- Videolla käänteismallinnetaan PicoCTF `Bbbbloat` haastetta
- Käänteismallintamiseen käytetään Ghidraa
- Videolla tutkitaan miten ohjelma liikkuu kohdasta kohtaan ja mitä se tekee eri kohdissa
- `main` funktiossa on kohta joka vertaa syötettä heksadesimaaliin
- Videolla John Hammond muuntaa heksadesimaalin desimaaliin ja saa ongelman ratkaistua
- 

### Lähteet:
- Hammond, J. 27.4.2022. GHIDRA for Reverse Engineering (PicoCTF 2022 #42 'bbbloat').  Katsottavissa: https://www.youtube.com/watch?v=oTD_ki86c9I. Katsottu: 17.11.2024.
## a) Asenna Ghidra
Asensin Ghidran jo oppitunnilla:

![image](https://github.com/user-attachments/assets/a9b8b57b-c34a-4efd-a930-f8ca9b5b1701)


### Lähteet:
- https://github.com/NationalSecurityAgency/ghidra

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

![image](https://github.com/user-attachments/assets/b1864981-37e4-43ab-baef-09d692453df5)

### Lähteet:
https://github.com/NoraCodes/crackmes
   
## e) Nora crackme01
Aloitin ajamalla ohjelman tyhjällä syötteellä sekä `0000` syötteellä:

![image](https://github.com/user-attachments/assets/d05c97fd-d5a9-4030-a5da-a88d99e3e992)

Tämän jälkeen kokeilin tuttua turvallista `strings` komentoa ja löysin tämän:
![image](https://github.com/user-attachments/assets/9515b8dc-035f-4fcc-855e-86549f8b0c32)

Kokeilin ajaa sitä ja sain tuloksen:

![image](https://github.com/user-attachments/assets/7c70d400-d15c-44de-b7fe-e40ae9d108bb)

Toimii.

## e) Nora crackme01e
Aloitin samalla taktiikalla ja löysin `strings` komennolla seuraavan:
![image](https://github.com/user-attachments/assets/93dbb068-22c9-4f30-9462-40e20b87d69c)

Lähdin kokeilemaan sitä:

![image](https://github.com/user-attachments/assets/681f9487-f938-4a3a-95ac-c212542f5e1c)

Avasin ohjelman Ghidralla. Etsin `main` funktion josta hahmottelin itselleni miten ohjelma toimii. Ohjelma on aika suoraviivainen. Koska syötettä verrataan merkkijonoon `slm!paas.k` oletan että se on oikea salasana. Se pitää vain syöttää tietyllä tavalla. 

Päätin syöttää syötteen `\` avulla joka jättää huutomerkin huomioimatta:

![image](https://github.com/user-attachments/assets/1bd32712-f053-4f24-acff-65e437e8d8d9)

Nythän se siis toimi. 

## e) Nora crackme02
Tällä kertaa skippasin suoraan `strings` komennon sillä on ehkä parempi käyttää aika Ghidran ja koodin tulkintaan. Testasin ensin ohjelman toimintaa normaalisti tyhjällä syötteellä ja `0000` syötteellä:

![image](https://github.com/user-attachments/assets/03b3462f-e522-46e5-af5c-5667316ac667)

Seuraavana avasin ohjelman Ghidrassa ja aloin tutkailemaan pääfunktiota. Ensin vastaani tuli merkkijono `password1` jota testasin mutta se ei toiminut. Koodi oli hieman haasteellisemman näköistä kuin aiemmassa tehtävässä. Muokkailin koodia oman ymmärrykseni mukaan eri näköiseksi. En osaa selittää koodin toimintaa kauhean hyvin. Pohdin hävettävän kauan miten merkkijonosta vähennetään numeroita. Muistin että tunnilla puhuttiin aiemmin kirjainten ASCII arvoista. Lähdin siis selvittämään ASCII arvoja sanalle `password1` koska sen osia selvästi verrataan. 
1. Ensin se tarkistaa että syötteitä on yksi
2. Seuraavana se asettaa `expected` arvoksi `p`
3. Otetaan syöte
4. Verrataan sanan password-1 ja syötteen-1 ascii arvoja. 
5. Arvojen täsmätessä tulostaa `Yes, is correct`

Käytin verkosta löytyvää muuntajaa ensin `password1` ascii arvoihin ja vähensin yhden jokaisesta kirjaimesta ja käänsin takaisin. Sain seuraavan o`rrvnqc0 jota kokeilin. Sain kuitenkin vain aikaan tämän:
![image](https://github.com/user-attachments/assets/a885c1f3-c33e-4c77-a2f7-9164c6bd37fc)

Päättelin että erikoismerkki tekee taas temppuja ja käytin \ viivaa:

![image](https://github.com/user-attachments/assets/a7e91c21-9e0e-4b7c-b11d-2859658ce5fe)

Muissa tehtävissä en käyttänyt paljoa aikaa. Otin kuvan puhelimeeni koodista ja tuijottelin sitä metrossa, salilla sarjojen välissä tai ruokapöydässä. Tuotti paljon vaikeuksia tajuta mitä koodissa oikeasti tapahtuu. Mahtava onnistumisen tunne kun keksin ratkaisun vaikka tehtävä olikin yksinkertaisimmasta päästä. 

### Lähteet:
- https://www.unit-conversion.info/texttools/ascii/

## Lähteet:
   Kaikki lähteet yhteen tähän
