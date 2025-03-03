# H6 Salataampa

## X) x) Lue ja tiivistä. Tiivistelmäksi riittää muutama ranskalainen viiva per artikkeli. (Tässä alakohdassa ei tarvitse tehdä testejä tietokoneella)
Tiivistetty ChatGPT, promptina sivut.

https://letsencrypt.org/how-it-works/

Let's Encrypt ja ACME-protokolla mahdollistavat HTTPS-sertifikaattien automaattisen hankinnan ja hallinnan ilman ihmisen väliintuloa.
Prosessi koostuu kahdesta vaiheesta: verkkotunnuksen validointi ja sertifikaatin hallinta (myöntäminen, uusiminen, peruminen).
Validointi tapahtuu joko DNS-tietueen tai HTTP-resurssin avulla, ja sen jälkeen CA (varmentaja) myöntää sertifikaatin.
Sertifikaatin uusinta ja peruutus tehdään allekirjoitetuilla pyynnöillä, ja peruutetut sertifikaatit lisätään OCSP-rekisteriin.

https://go-acme.github.io/lego/usage/cli/obtain-a-certificate/index.html#using-an-existing-running-web-server

Sertifikaatin hankkiminen Let’s Encryptiltä onnistuu eri tavoilla, kuten sisäänrakennetulla verkkopalvelimella, DNS-tarjoajalla tai olemassa olevan palvelimen kautta.
lego-komentorivityökalu mahdollistaa sertifikaatin hakemisen ja hallinnan eri menetelmillä, kuten HTTP- tai DNS-pohjaisella todennuksella.
Sertifikaatit tallennetaan .lego-kansioon, ja ne sisältävät palvelimen sertifikaatin (.crt), yksityisen avaimen (.key) ja CA:n varmenteen (.issuer.crt).
Sertifikaatin käyttöönottoa voi automatisoida ajamalla komentosarjoja (esim. palvelimen uudelleenkäynnistys uuden varmenteen asentamisen jälkeen).

https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html#configexample

Peruskonfiguraatio vaatii SSL-moduulin lataamisen (mod_ssl.so), portin 443 kuuntelun ja sertifikaattitiedostojen määrittämisen.
Salausasetukset määritetään SSLCipherSuite-direktiivillä, jolla voidaan pakottaa vahvat salausalgoritmit käyttöön.
OCSP Stapling parantaa suorituskykyä ja yksityisyyttä sertifikaattien tarkistuksessa (SSLUseStapling On).
Asiakasautentikointi voi pakottaa käyttäjät tunnistautumaan sertifikaateilla tietyille alueille palvelimella (SSLVerifyClient require).
Lokitus voidaan säätää eri tarkkuustasoille (LogLevel).

## A) Let's. Hanki ja asenna palvelimellesi ilmainen TLS-sertifikaatti Let's Encryptilta. Osoita, että se toimii.
TLS-sertifikaatin otin Certbotilta.
Asennsin ja käynnistin Certbotin seuraavilla komennoilla `sudo apt update`, `sudo apt install certbot python3-certbot-apache -y`ja `sudo certbot --apache -d mikoliukkonen.it.com -d www.mikoliukkonen.it.com`

![Näyttökuva 2025-03-03 145701](https://github.com/user-attachments/assets/f96d9750-97ab-44a0-8c04-268867516e67)
![Näyttökuva 2025-03-03 145540](https://github.com/user-attachments/assets/70cff441-ff57-436f-aac4-c8178c5773ed)
![Näyttökuva 2025-03-03 145712](https://github.com/user-attachments/assets/4d2d6cf4-052b-40dd-a189-710372d23e75)

Tämän jälkeen tarkistin, ssl tiedoston ja käynnistin Apachen uudelleen.
![image](https://github.com/user-attachments/assets/67c61c43-b482-43fd-9310-977a77a590d2)

Tämän jälkeen otin sites-enabled kansiosta ylimääräset kansiot pois ´a2dissite´ komennolla.
![image](https://github.com/user-attachments/assets/42c0d7b5-26c1-411b-9587-3081af1011fd)



## b) A-rating. Testaa oma sivusi TLS jollain yleisellä laadunvarmistustyökalulla, esim. SSLLabs (Käytä vain tavanomaisia tarkistustyökaluja, ei tunkeutumistestausta eikä siihen liittyviä työkaluja)
![image](https://github.com/user-attachments/assets/c34e98e1-8d05-44a8-acaf-4d83f7e12100)


