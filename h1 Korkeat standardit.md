# h1 Korkeat standardit
## Tiivistelmä ja tehtävänanto:
Tehtävässä piti tutustua standardeissa oleviin käsitteisiin sekä pohtia erään podcastin väittämiä. Lopuksi tuli asentaa Debian-virtuaalikone. Tehtävät sujuivat ongelmitta. 
### Tehtävänanto:
- a) Tutustu kurssin sanastoon, joka on määritelty SFS-EN ISO/IEC 27000:2020:en standardissa, kappaleessa 3. Terms and Definitions. Selvitä seuraavien kappaleiden määritteet ja selitä omin sanoin mitä ne tarkoittavat: 3.2, 3.31, 3.56, 3.58, 3.77. (Ei edellytä teknisiä testejä tietokoneella)
- b) Tutustu standardiin ISO 27034-1 - 5. Selvitä mistä standardi kokonaisuudesta on kyse. (Ei edellytä teknisiä testejä tietokoneella)
- c) Kuuntele podcast: Meurman 2021: Laatulöpinät 30: Tietoturvallisuus ohjelmistokehityksessä (jakson mp3, Laatolöpinät RSS-syöte). Mitä mieltä olet podcastin väittämistä? (Ei edellytä teknisiä testejä tietokoneella) [podcast](https://www.arter.fi/podcast/laatulopinat-podcast-tietoturvallisuus-ohjelmistokehityksessa-tarkastele-kokonaisuutta-ja-hyodynna-viitekehykset/)
- d) Asenna Debian 12-Bookworm virtuaalikoneeseen. Päivitä kaikki ohjelmat. (Poikkeuksellisesti tätä alakohtaa ei tarvitse raportoida, paitsi jos jokin ei toimi. Ympäristö tarvitaan seuraavalle oppitunnille. Joten tämän kohdan vastaukseksi riittää kuittaus, että Linux on asennettu.)
## a) Kurssisanasto
- 3.2: **attack** tarkoittaa yritystä tuhota, paljastaa, muuttaa, sulkea, varastaa tai hankkia luvaton pääsy ja käyttää jotain omaisuutta luvatta.
- 3.31: **information security incident** yksi tai useampi ei toivottu tai odottamaton tietoturvatapahtuma jolla on suuri mahdollisuus vaikuttaa yritystoimintaan ja uhkaamaan tietoturvaa.
- 3.56: **requirement** tarkoittaa tarvetta tai odotettua asiaa joka on ilmoitettu, joko yleiseen hyvään tapaan kuuluvaa tai pakollista(vaatimus)
- 3.58: **review** toimintaa jolla määritetään jonkin asian soveltuvuus ja tehokkuus määritettyjen tavoitteiden saavuttamiseksi
- 3.77: **vulnerability** omaisuuden tai suojaominaisuuden heikkous jota voidaan käyttää hyväksi yhden tai useamman uhan toimesta.
  
**Lähteet**: SFS-EN ISO/IEC27000:2020
## b) iso 27034 kokonaisuus
ISO 27034 kokonaisuus antaa ohjenuorat sovellusten tietoturvaan. Niin suunnittelu, määrittely, ohjelmointi tai käyttöönotto vaiheissa. 

**Lähteet:** https://www.iso27001security.com/html/27034.html Luettu 27.10.24

## c) Laatulöpinät
1. **Mikään ohjelmisto ei ole täysin tietoturvallinen:** Tämä väittämä on mielestäni totta. Kuten podcastissa mainitaan, ihminen on aina heikoin lenkki. Toinen pohdittava asia on milloin kustannukset nousevat liian kalliiksi suhteessa riskiin.
   
2. **Hallinnollinen tietoturva on teknisen tietoturvan edellytys:** Hallinnollinen tietoturva on tärkeä osa tietoturvaa, en osaa kuitenkaan sanoa onko se teknisen tietoturvan edellytys. Ehkä kuitenkin hallinnollisella tietoturvalla myös määritetään mitä teknisiä tietoturvaominaisuuksia tarvitaan.
   
3. **Automaatiotestaus on ohjelmistotietoturvan kannalta erittäin tärkeää:** Uskon tämän olevan tärkeää, vaikkakin se monimutkaistaa työvaiheita. Eikä siihen voi luottaa sokeasti.
   
4. **Ohjelmistoa suunniteltaessa voidaan tehdä paljonkin auttamaan käyttäjää toimimaan tietoturvallisesti. Usein kuitenkin nämä toimenpiteet vaikuttavat negatiivisesti:** Suunniteltaessa voidaan tehdä paljon ominaisuuksia jotka auttavat käyttäjää toimimaan tietoturvallisesti. Sillä voidaan kuitenkin heikentää myös käyttäjän tietoturvaa sillä laiskat käyttäjät eivät jaksa noudattaa näitä ohjeita. 

**Lähteet:** Meurman 2021: Laatulöpinät 30: Tietoturvallisuus ohjelmistokehityksessä. Kuunneltavissa: https://www.arter.fi/podcast/laatulopinat-podcast-tietoturvallisuus-ohjelmistokehityksessa-tarkastele-kokonaisuutta-ja-hyodynna-viitekehykset/ kuunneltu: 27.10.2024

## Debiani 12
Debian asennettu ja kaikki vaiheet tehty.

## Lähteet:
Tehtävät: Iso-Anttila, Karvinen 2024: Sovellusten hakkerointi ja haavoittuvuudet. https://terokarvinen.com/application-hacking/
