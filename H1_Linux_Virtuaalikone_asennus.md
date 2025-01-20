# Kotitehtävä H1

### Tiivistelmä omasta raportista
Raportin tulisi olla toistettava, täsmällinen, helppolukuinen, viittaa lähteisiin, sisältää vakiotekstejä ja viitata mahdollisia pahoja mokia. 
Yksinkertaisuudessaan raportin avulla, jonkun muun pitäisi pystyä toistaa sama minkä olet itse tehnyt.
lähde: https://terokarvinen.com/2006/raportin-kirjoittaminen-4/

### Free software definition/Neljä vapautta.
Freedom 0: Vapaus käyttää ohjelmaa haluamallasi tavalla, mihin tahansa tarkoitukseen.
Freedom 1: Vapaus tutkia ohjelmaa miten se toimii ja muokata sitä niin, että se vastaa tarpeitasi.
Freedom 2: Vapaus levittää ohjelman kopioita, jotta voit auttaa muita.
Freedom 3: Vapaus jakaa muokattuja versioita muilla, Koko yhteisö voi hyötyä muutoksista mitkä olet tehnyt.
lähde: https://www.gnu.org/philosophy/free-sw.html

## Debian 12 Asennus Oracle Virtual Boxiin.

### Mitä tässä tehdään?
Raportissa käydään läpi miten asennat Debian 12 Virtual Boxiin. Raportissa käydään myös läpi mahdollisia vikatilanteita.
Asennuksen ja raportin päivämäärä on 20.01.2025

#Tietokone
Tietokone: Lenovo IdeaPad 3 16ITL6
Käyttöjärjestelmä: Windows 11
Suoritin: 11th Gen Intel(R) Core(TM) i5-1135G7 @ 2.40GHz   2.42 GHz
Asennettu RAM: 8,00Gt

#### Debian ISO kuvan lataaminen
Latasin ISO kuvan sivustolta https://www.debian.org/CD/live/
Tässä tapauksessa valitsin xfc version.

### Virtual Boxin lataaminen

Virtual boxin latasin alla olevasta linkistä:
https://www.virtualbox.org/wiki/Downloads

### Virtuaali koneen asentaminen, asetukset ja niiden valinta.
Nimesin virtuaalikoneen "DebianMikoLiukkonen" 
Valitsin ladatun ISO kuvan, joka löytyi ladatuista tiedostoista.
Versioksi valitsin Debian (64-bit)
![Näyttökuva 2025-01-20 132810](https://github.com/user-attachments/assets/f1a31b28-adc3-43a5-8e5a-24f8c2c050b5)

### Pääkäyttäjä ja salasana
Nimesin pääkäyttäjän ja salasanan seuraavasti.
![Näyttökuva 2025-01-20 132909](https://github.com/user-attachments/assets/77f2e698-295f-4e95-a024-8bd3bc482eb5)

### Virtuaalinentietokone
Base Memoryksi laitoin 4096MB ja 4 prosessoria.
Laitteistolevyn kooksi tuli 62,14GB
![Näyttökuva 2025-01-20 132928](https://github.com/user-attachments/assets/86b3a09c-df74-44aa-9411-0be655ba407b)
![Näyttökuva 2025-01-20 132959](https://github.com/user-attachments/assets/37bd21d2-151f-4e13-8102-50d4e4026a4a)

### Ongelmia asennuksessa
Kun koitin aloittaa virtuaalikonetta seuraavanlainen virheilmoitus tuli:
![Näyttökuva 2025-01-20 133036](https://github.com/user-attachments/assets/28d18f28-8c6b-4055-8962-653f17022f40)

Virheen sain korjattua menemällä komentokehotteeseen järjestelmänvalvojana.
Kehoitteeseen kirjoitettiin komento:
### bcdedit /set hypervisorlaunchtype off
![Näyttökuva 2025-01-20 133335](https://github.com/user-attachments/assets/da011514-ea10-45de-a8b5-c80d23d68821)

Tällä komennolla otettiin hypervision pois käytöstä
Tämän jälkeen käynnistin koneen uudelleen ja avasin Virtual Boxin järjestelmänvalvojana.
Virhe korjaantui.
Linkki YouTube videoon, jonka avulla korjasin virheen.
https://www.youtube.com/watch?v=_aVzQ_qEfhc

### Virtuaalikoneen käynnistäminen ja testaus.
Konetta käynnistäessä tuli virheilmoitus: "mount retry and boot"
Minun piti valita Boot Menusta Live.
![Näyttökuva 2025-01-20 134040](https://github.com/user-attachments/assets/db334f99-26ea-4375-8bc0-65910de440be)

Reboottauksen jälkeen kone alkoi toimimaan ja valittiin menusta "Live system (amd64)
Tämän jälkeen tietokone lähti toimimaan.

### Testaus
Testasin Firefoxilla nettiä, joka toimi ja kirjoitin hakuun google.
![Näyttökuva 2025-01-20 134317](https://github.com/user-attachments/assets/81ef223c-394b-4bd2-b982-62a12c361801)

Tietokone totteli käskyjä, eli internet, hiiri ja näppäimistö toimii.

### Installer
Työpöydällä oli Installer nappi.
Installerin läpi käynnisssä tein seuraavat valinnat:
Kieli: American English
Location/aikavyöhyke: Helsinki, Finland
Keyboard: Finnish Keyboard (Default)
Partitions sivu: Erase Disk, tämän voi valita koska virtuaalikoneella ei ollut tärkeitä tiedostoja minulle.
Users: Käyttäjätunnus ja salasana
![Näyttökuva 2025-01-20 134541](https://github.com/user-attachments/assets/0cb97ee6-660a-4514-a3d9-df2cb4670fa3)

Asennuksen jälkeen käynnistin koneen uudelleen.
Tarkistin asennuksen jälkeen, että löydän googlen.

Linkki alkuperäisiin ohjeisiin ja lähde:
https://terokarvinen.com/2021/install-debian-on-virtualbox/

### Palomuuri ja sen asennus
Komentokehoitteelle kun kirjoittin komennon 
sudo apt-get -y dist-upgrade
Komento päivittää käyttöjärjestelmän. 
Mitään ei latautunut tai asentunut tällä kertaa, voidaan olettaa että ei ole tällä hetkellä päivityksiä olemassa.

Tämän jälkeen asensin palomuurin käyttäen komentoja:
sudo apt-get -y install ufw
ja
sudo ufw enable

Palomuuri asentui ja käynnistin virtuaalikoneen uudelleen ja testasin toiminnan.
Lähde: https://terokarvinen.com/2021/install-debian-on-virtualbox/
