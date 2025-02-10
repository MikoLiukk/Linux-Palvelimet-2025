# H4 Maailma kuulee.

## Johdanto 
Tehtävän ja raportin tavoitteena on virtuaalipalvelimen vuokraaminen.

## X) Teoriasta käytäntöön pilvipalvelimen avulla Susanna Lehto 2024
A) Pilvi palvelimen vuokraus ja asennus
 - Pilvipalvelimen vuokraus.
 - Yhdistys SSH

B) Palvelin suojaan palomuurilta
- `$ sudo apt-get install ufw`
- Avattava portti 22

C) Kotisivut palvelimelle
 - Apache2
 - Määritä asetukset

D) Palvelimien ohjelmien päivitys
- Pakettien säännöllinen päivitus.
- Tarkista turvapäivitykset ja asenna ne mahdollisimman pian.

Lähde: https://susannalehto.fi/2022/teoriasta-kaytantoon-pilvipalvelimen-avulla-h4/

## A) Vuokraa oma virtuaalipalvelin
Vuokrasin virtuaalipalvelimen UpCloudilta. 
Valitsin muuten kaikki standardi asetukset paitsi valitsin serveriksi FI-HEL1 eli Helsingissä olevan serverin ja otin halvimman mahdollisen paketin.
Paketti maksaa 3€/kk, 1GB muistia, 10GB storagea ja OS on Debian GNU/Linux 12 (Bookworm). 
Kirjautuminen toimii ssh avaimilla ja hostname on automaattisesti UpCloudin antama. 

### SSH avaimien luonti.
Asensin ensin OpenSSH:n komennolla `sudo apt-get install openssh-client`
Avainparin sain komennolla `ssh-keygen`

![image](https://github.com/user-attachments/assets/242199d7-9962-4a09-9287-1a1d22896057)

Komennolla `cat ~/.ssh/id_rsa.pub` sain avainparini, jonka laitoin UpCloudin sivulle serveriä varten.

## B) Tulimuuri päälle, root tunnus kiinni ja ohjelmien päivitys

### Tulimuuri ja päivitykset
Palvelimelle pääsin komennolla `ssh root@185.26.49.98`

Asensin ensimmäiseksi tulimuurin ja mahdolliset päivityksen komennoilla `sudo apt-get update`ja `sudo apt-get install ufw`.
Tämän jälkeen avasin portin 22 komennolla `sudo ufw allow 22/tcp` ja käynnistin muurin `sudo ufw enable`.
Tarkistin tämän jälkeen, että pääsenkö rootilla vielä palvelimelle (pääsin).

![image](https://github.com/user-attachments/assets/3570658e-acb4-49f1-8985-5c6f01bc51b0)

### Käyttäjän luominen ja rootin poisto.'

Palvelimella annoin komennot `sudo adduser miko`tämän jälkeen annoin uuden salasanan, lisäsin käyttäjän miko sudo ryhmään ja varmuuden vuoksi admin ryhmään komennoilla:
`sudo adduser miko sudo`ja `sudo adduser miko adm`
![image](https://github.com/user-attachments/assets/334f34d3-77e8-401c-840d-fc507e259805)
Huomio! Epäonnistuin ensimmäisen käyttäjän kanssa, jonka takia komennossa näkyy mikoli käyttäjänä eikä miko.


SSH avaimien asetuksien kopiointi onnistui komennolla `sudo cp -rvn /root/.ssh/ /home/miko/ ja `sudo chown -R miko:miko /home/miko/`
Poistuin ja uudelleen yhdistin palvelimelle `exit` ja `ssh miko@185.26.49.98`. 

Rootin lukitseminen toimi komennoilla `sudo usermod --lock root` ja `sudo mv -nv /root/.ssh /root/DISABLED-ssh/`
Tämän jälkeen poistuin palvelimelta ja kokeilin päästä sisälle root käyttäjällä, ei onnistunut eli tässä vaiheessa kaikki hyvin.
Pääsin palvelimelle miko käyttäjällä.
![image](https://github.com/user-attachments/assets/b5b4515c-97f3-4953-a5cd-8fe2b0dc9daf)

## C) Webbipalvelimen asennus.

Asensin apachen komennolla `sudo apt-get -y install apache2`
Tämän jälkeen vaihdoin testisivun johonkin muuhun komennolla echo "Hei kaikki" | sudo tee /var/www/html/index.html
En tehnyt muita muutoksia.

![image](https://github.com/user-attachments/assets/2b5c197b-39bd-4018-81ab-b762c34507ff)


Sivu näyttää tältä:
![image](https://github.com/user-attachments/assets/96bec3c8-d0b7-4459-b2f4-a74dc780ac77)
Kokeilin sivua fyysisellä koneellani ja mobiililaitteella, kaikissa näyttää samalta.










Lähteet:
https://terokarvinen.com/linux-palvelimet/

https://susannalehto.fi/2022/teoriasta-kaytantoon-pilvipalvelimen-avulla-h4/

https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/
