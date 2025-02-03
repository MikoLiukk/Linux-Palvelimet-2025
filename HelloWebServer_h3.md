# Hello Web Server

## Tiivistelmä
Tehtävässä tehdää Name Based Virtual Host. Tehtävänanto ja lähteet: https://terokarvinen.com/linux-palvelimet/


## X)
### IP-pohjaiset vs. nimiin perustuvat virtuaali-isännät
IP-pohjaiset virtuaali-isännät käyttävät yhteyden IP-osoitetta määrittääkseen, mikä virtuaali-isäntä palvellaan. Tällöin jokaiselle isännälle on oltava oma IP-osoite.
Nimiin perustuvassa virtuaali-isännöinnissä palvelin käyttää asiakkaan lähettämää isäntänimeä HTTP-otsikoissa valitakseen oikean virtuaali-isännän. Näin samaa IP-osoitetta voi käyttää useiden isäntien kanssa. 
Tämä on yleensä yksinkertaisempaa, koska DNS-palvelin konfiguroidaan osoittamaan isäntänimet oikeaan IP-osoitteeseen, ja Apache määritetään tunnistamaan eri isäntänimet.
Nimiin perustuvan virtuaalisen-isäinnöin etuja on yksinkertainen käyttöönotto ja vähentää tarvetta useille IP-osoitteille.

## a) Webbipalvelimen localhost-osoite ja Apachen asennus.
Asensin apachen komennolla `sudo apt install apache2`.
![image](https://github.com/user-attachments/assets/8455d341-de41-4201-8720-c00d0e32f255)

Webbipalvelimen vastaaminen localhost-osoitteesta tarkistin komennolla ´sudo systemctl status apache2` 

Varmistin myös selaimella saman kirjoittamalla selaimeen `http://localhost`
![image](https://github.com/user-attachments/assets/f342c66d-f5a9-462e-943d-8e9c03b8b407)

## b) Lokirivit ja niiden analysointi.
En aluksi päässyt lokeihin käsiksi, mutta StackExchange foorumilta sain apua https://askubuntu.com/questions/421684/cant-access-apache-error-logs.
`sudo usermod -aG amd USERNAME`komennolla annoin itselleni group admin oikeudet ja kun käynnistin koneen uudelleen `/var/log/apache2`avautui.
Tässä logit julkisesti kaikille nähtäväksi:

![image](https://github.com/user-attachments/assets/013cd677-0e8d-443f-9502-7f73c01c66b1)

Osien analyysi:
127.0.0.1
Käyttäjän IP-osoite. Tässä tapauksessa localhost eli palvelimen oma osoite.

-
Ensimmäinen viiva tarkoittaa, että autentikointia ei ole käytetty.

-

Toinen viiva on paikka, jossa normaalisti olisi käyttäjän todellinen tunniste (authenticated username). Tässä sitä ei ole määritelty.
[20/Jan/2025:22:57:02 +0200]
Aikaleima:
Päiväys ja kellonaika: 20. tammikuuta 2025 klo 22:57:02.
+0200 kertoo aikavyöhykkeen: tässä UTC+2.

"GET / HTTP/1.1"
HTTP-pyyntö:
GET: HTTP-metodi. Käyttäjä pyytää verkkosivua.
/: Pyyntö kohdistuu palvelimen juurihakemistoon (esim. index.html).
HTTP/1.1: HTTP-protokollan versio.
200
HTTP-tilakoodi: 200 tarkoittaa, että pyyntö onnistui.
3380
Vastauksen koko tavuina: 3380 tavua.
"-"
Viittaa referrer-otsikkoon, eli osoitteeseen, josta käyttäjä tuli. Tässä kohtaa viiva tarkoittaa, että ei ole referrer-tietoa (käyttäjä tuli suoraan palvelimelle).
"Mozilla/5.0 (X11; Linux x86_64; rv:128.0) Gecko/20100101 Firefox/128.0"
Käyttäjäagentti (User-Agent):
Mozilla/5.0: Käytössä oleva selain on yhteensopiva Mozilla-selaimen kanssa.
X11; Linux x86_64: Käyttöjärjestelmä on Linux 64-bittisellä arkkitehtuurilla.
rv:128.0 ja Firefox/128.0: Selaimen versio on Firefox 128.0.

Lähteet: ChatGPT promppina lokirivi.

## C) Etusivu uusiksi
Tein uuden tiedoston käyttämällä kometoa `sudoedit hattu.example.com.conf`. Konffasin tämän opettajan ohjeiden mukaiseksi:
<VirtualHost *:80>
 ServerName hattu.example.com
 ServerAlias www.hattu.example.com
 DocumentRoot /home/mikol/publicsites/hattu.example.com
 <Directory /home/mikol/publicsites/hattu.example.com>
   Require all granted
 </Directory>
</VirtualHost>
Tämän jälkeen käytin komentoa `sudo a2ensite hattu.example.com`ja käynnistin uudelleen sivuston
komennolla `sudo sustemctl restart apache2`.'

Tämänä jälkeen loin kansion "publicsites" johon tallensin sivoston index.html tiedoston ja conf. tiedoston.

## D) HTML 5
HTML5-koodin tekeminen hattu.example.com tiedostoon onnistui ChatGPT avulla.
![image](https://github.com/user-attachments/assets/c593e827-287c-4c74-b223-f0a1d2a8b88e)
![image](https://github.com/user-attachments/assets/b254ea5b-ffa8-4a8a-9538-1e9dd910f462)

## E) Curl ja Curl-l
![image](https://github.com/user-attachments/assets/56ddbfe8-9c04-4686-aba2-357b4520b055)

Komennoilla `curl -I http://localhost` ja `curl http://localhost`
Näillä komennoilla saa näkyviin HTTP-protokollaversion, statuskoodin, päivämääräm, kontenttityypin ja pituuden, serverin ja sisällön.

Lähteet: https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/
ja https://terokarvinen.com/linux-palvelimet/
