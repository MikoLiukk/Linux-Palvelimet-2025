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

### Pääkäyttäjä ja salasana
Nimesin pääkäyttäjän ja salasanan seuraavasti.

### Virtuaalinentietokone
Base Memoryksi laitoin 4096MB ja 4 prosessoria.
Laitteistolevyn kooksi tuli 62,14GB

### Ongelmia asennuksessa
Kun koitin aloittaa virtuaalikonetta seuraavanlainen virheilmoitus tuli:

Virheen sain korjattua menemällä komentokehotteeseen järjestelmänvalvojana.
Kehoitteeseen kirjoitettiin komento:
### bcdedit /set hypervisorlaunchtype off
Tällä komennolla otettiin hypervision pois käytöstä
Tämän jälkeen käynnistin koneen uudelleen ja avasin Virtual Boxin järjestelmänvalvojana.
Virhe korjaantui.
Linkki YouTube videoon, jonka avulla korjasin virheen.
https://www.youtube.com/watch?v=_aVzQ_qEfhc

### Virtuaalikoneen käynnistäminen ja testaus.
Konetta käynnistäessä tuli virheilmoitus: "mount retry and boot"
Minun piti valita Boot Menusta Live.
Reboottauksen jälkeen kone alkoi toimimaan ja valittiin menusta "Live system (amd64)
Tämän jälkeen tietokone lähti toimimaan.

### Testaus
Testasin Firefoxilla nettiä, joka toimi ja kirjoitin hakuun google.
Tietokone totteli käskyjä, eli internet, hiiri ja näppäimistö toimii.

### Installer
Työpöydällä oli Installer nappi.
Installerin läpi käynnisssä tein seuraavat valinnat:
Kieli: American English
Location/aikavyöhyke: Helsinki, Finland
Keyboard: Finnish Keyboard (Default)
Partitions sivu: Erase Disk, tämän voi valita koska virtuaalikoneella ei ollut tärkeitä tiedostoja minulle.
Users: Käyttäjätunnus ja salasana

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
