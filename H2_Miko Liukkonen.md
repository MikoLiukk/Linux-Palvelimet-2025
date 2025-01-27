# H2 Komentaja Pingviini 27.01.2025

## Johdanto 
Tämän raportin tarkoituksena on opetella Linuxin komentopäätteen peruskomennot. Raportti perustuu Linux-palvelimien kurssin H2 kotitehtävää.
Linkki: https://terokarvinen.com/linux-palvelimet/

## Lue ja tiivistä Karvinen 2020: Command line basics revisited

### Liikkuminen ja tarkastelu
`pwd` näyttää nykyisen työhakemiston.

`ls` listaa tiedostot nykyisessä hakemistossa.

`cd (hakemisto)` vaihtaa hakemistoa.

`cd ..` siirtyy ylöspäin hakemistohierarkiassa.

`less tiedosto.txt` näyttää tiedoston sisällön sivu kerrallaan.

### Tiedostojen käsittely
`nano TIEDOSTO.TXT` avaa tiedoston muokattavaksi nano-editorissa.

`mkdir UUSIHAKEMISTO` luo uuden hakemiston.

`mv VANHANIMI UUSINIMI` siirtää tai nimeää uudelleen tiedoston tai hakemiston.

`cp -r ALKUPERÄINEN KOPIO` kopioi tiedoston tai hakemiston.

`rm TIEDOSTO` poistaa tiedoston.

`rm -r HAKEMISTO` poistaa hakemiston ja sen sisällön.

### Etäyhteys SSH:n avulla:

`ssh käyttäjä@esimerkki.com` avaa suojatun etäyhteyden.

`scp -r HAKEMISTO` käyttäjä@esimerkki.com:public_html/ kopioi hakemiston etäkoneelle.

### Apu ja ohjeet:


`man` komento näyttää komennon manuaalisivun.

komento `--help` tai komento -h antaa lyhyen ohjeen komennosta.


### Historia ja automaattinen täydennys:


`Sarkain-näppäin (Tab)` täydentää komentoja ja tiedostonimiä.

`Nuolinäppäimet` selaavat komentohistoriaa.

Lähde: https://terokarvinen.com/2020/command-line-basics-revisited/?fromSearch=command%20line%20basics%20revisited

### Oma idea
Sivustolla voisi olla esimerkki video tai "Top 10 useinten käytettyä komentoa".

## Lähtötilanne
Fyysinen konen ja virtuaalikone ovat samat kui H1 tehtävässä.

## Asenna micro-editori 27.01.2025
Kun avasin virtuaalikoneeni laitoin komentokehotteeseen komennot "sudo apt-get update", jolla päivitin virtuaalikoneeni. Tämän jälkeen laitoin komennon "sudp apt-get install micro", joka asentaa ja päivittää micro-ohjelman. Komentokehoite myös kysyi että haluanko asentaa micro-ohjelman (y/n) ja tässä kohtaa painoin y.

### Pääte
Laitoin komentokehotteeseen seuraavat komennot järjestyksessä:
´pwd´ --> ´ls´--> ´cd Documents/´--> ´ls´--> ´mkdir h2´ --> ´cd h2´--> `micro tehtava-a-h2`

Tämä komentosarja luo uuden kansion nimeltä h2 ja siihen dokumentin nimeltä tehtava-a-h2

Editoriin kirjoitin_
Tämä on tehtävä A)
Kun haluan tallentaa ja poistua micro editorista painen vasen ctl + s
Tämän jälkeen painan vasen ctrl + q 

## Apt. Asenna kolme itsellesi uutta komentoriviohjelmaa.
Tässä kysyin ChatGPT apua propilla "3 hyödyllistä komentoriviohjelmaa linuxille".

### htop
Asensin htopin komennolla ´sudo apt install htop´ ja käynnistin sen komennolla `htop`
![Näyttökuva 2025-01-27 120422](https://github.com/user-attachments/assets/6958140e-9d90-481f-99fd-43061751ec7c)
htop näyttää järjestelmän prosessit ja resurssien käytön helposti ymmärrettävässä muodossa.
htopilla voin tarkkailla järjestelmän suorituskykyä reaaliajassa ja tappaa halutessani prosesseja.

### curl 
curl lataa tiedostaja, hakee verkkosivuja ja tekee HTTP-pyyntöjä.
Asensin curlin komennolla ´sudo apt install curl`

![image](https://github.com/user-attachments/assets/07b1d1ec-087d-41e2-9cdf-e19963686b29)

### fzf (Fuzzy Finder)
Asennettu komenolla ´sudo apt install fzf´
fzf tarjoaa nopean ja tehokkaan hakutoiminnon tiedostoille, komennoille ja muulle datalle. 
Toimii komennolla fzf.

![image](https://github.com/user-attachments/assets/dc483c78-47f4-4603-bf01-70fe1982de73)

### Huomioita
Yritin asentaa rsyncin ja tmuxin, mutta en onnistunut, koska ainakin vielä vaikutti minulle liian monimutkasilta, joten vaihdoin ChatGPT prompiksi "3 hyödyllistä komentoriviohjelmaa linuxille ei tmux tai  rsync"

## Command Line Basics Revisited
### /home/mikol
Terminaalin oletusasetuksena on avata aina tämä kansio käynnistettäessä. Jos halusin palata tähän samaan kansioon, pelkkä komento `cd` riittää palauttamaan minut alkutilanteeseen. Esimerkissä siirryn kansioon Documents ja sen sisällä olevaan kansioon h2, jonka jälkeen palaan takaisin /home/mikol/-kansioon.
`pwd` näyttää nykyisen työhakemiston.
`ls` listaa tiedostot nykyisessä hakemistossa.
`cd (hakemisto)` vaihtaa hakemistoa.
![image](https://github.com/user-attachments/assets/376e4cf0-0094-4eb9-b26b-b3e2002882d8)
#### Huomio:
Viikonpäivä ja eläin.txt oli tehty väärin 21.1.2025 tunnilla.

### /home
Kotihakemistoon (/home/mikol) pääsin komennolla ´cd`. Komennolla `pwd` tarkistan, että olen todella siinä kansiossa, jossa tällä kertaa haluan olla.

Seuraavaksi käytin komentoa `cd ..`, joka siirtää minut yhden tason ylemmäs hakemistorakenteessa. Näin päädyin /home-kansioon, joka on rakenteessa edellinen kansio.

/home-hakemistosta löytyvät kaikkien käyttäjien kotikansiot. Koska virtuaalikoneessa on vain oma käyttäjäni, lista on suppea.

![image](https://github.com/user-attachments/assets/cfedcb04-3b06-4881-92c4-7ec038fa4675)

### / (root directory)
Pääsin root directoriin samalla logiikalla aikaisemmin halusin "peruuttaa taakse päin" eli ´cd ..`
Tämän jälkeeen kirjoitin komennon `pwd` joka tässä kohtaa avasi kaikki rootin kansiot. 
Kirjoittamalla komennon `cd etc/` ja tämän jälkeen ´ls´ avasi asetukset.

![image](https://github.com/user-attachments/assets/b94e7939-2478-4989-9c1b-effddb12655f)

Suurin osa näistä kansioista on tyhjiä tai koskemattomia, koska virtuaalikoneelle ei ole tehty paljoa muutoksia.

## The Friendly M. Näytä 2-3 kuvaavaa esimerkkiä grep-komennon käytöstä.
### Esimerkki 1
Käytin komentoa grep -r ".txt" Oletin, että löytäisin aikasemman googlen txt-tiedoston jonka olin tallentanut curlin avulla ja se löytyi. Löytyi myös aikaisemmin mielestäni epäonnistunut rsync varmuuskopio tehtävästä A (positiivinen yllätys).

![image](https://github.com/user-attachments/assets/c019b926-c5f8-4577-a0b8-d354b82dded7)

### Esimerkki 2
Käytin komentoa `ps aux | grep "nginx`. Käytin tätä, koska ChatGPT antoi sen vaihtoehdoksi kun käytti promptia " Näytä 2-3 kuvaavaa esimerkkiä grep-komennon käytöstä"

![image](https://github.com/user-attachments/assets/e9722727-cb61-4e76-99a4-48ee3253862c)

En tiennyt mitä numerot tarkoittavat ja mikä on nginx.
#### 4863
Tämä on PID tai prosessin tunnus.
#### 0.0 (ensimmäinen)
Tämä on prosenttuaalinen luku kuinka paljon prosessiresursseja (CPU) prosessi käyttää.
Tässä tilanteessa 0% koska prosessi ei ole käynnissä vaan "unessa"
#### 0.0 (toinen)
Kuinka paljon muistia (RAM) prosessi käyttää prosentteina kokonaismuistista.
#### 8996
VSZ (Virtual Memory Size): Prosessin käyttämä virtuaalimuisti tavuina.
Huom. Annettu numero on kilotavuina.
#### 2199
RSS (Resident Set Size): Prosessin fyysisesti käyttämän muistin koko tavuina.
Tämäkin on annettu kilotavuina.
#### pts/0
pts/0 tarkoittaa, että prosessi on liitetty nykyiseen terminaali-istuntoon.
#### S+
Prosessin tila, joka on tässä nukkuva (S/sleeping) + tarkoittaa että prosessi on liitettynä nykyiseen terminaaliin.
#### 21:41
Kellon aika kun prosessi käynnistettiin.
#### 0:00
Prosessin CPU-aika.
#### Nginx
Nginx on avoin lähdekoodi jota voi käyttää muunmuassa erillaisina palvelimina.

Nämä sai selville kun kirjoitti numerot samanlailla kuin ylemmässä kuvassa ChatGPT.

#### Huomioitavaa
Linuxin putkitusmerkin (|) saa suomalaisella 80% näppäimistöllä painamalla oikea ALT ja <.

## Esimerkki putkista
"Putkittaminen tarkoittaa toisen ohjelman standarditulosteen ohjaamista toisen ohjelman standardisyötteelle" https://www.linux.fi/wiki/Putki
ChatGPT kun pyysi helppoja linux putkia tuli esimerkki kuinka lasketaan tiedostojen määrän.
Komennolla `ls | grep -c ""` Saadaan vastaukseksi 18, joka tarkoittaa että tällä hakemistolla on 18 tiedostoa.

![image](https://github.com/user-attachments/assets/b6cdcd24-9060-41b0-a1aa-3edad23d0ec2)

## Rauta 
Minun piti ensin asentaa lshw komennolla `sudo apt install lshw`
Tämän jälkeen ajoin komennon `sudo lshw -short`

![image](https://github.com/user-attachments/assets/e6b6e5ac-5ef1-4e1e-b0b7-75a69a3b5535)

Listaus koneen raudasta tuli.

System: VirtualBox (virtuaalikone tietää olevansa virtuaalikone)
Processor: 11th Gen Intel(R) Core(TM) i5-1135G7
Memory: 4Gig (RAM)
Disk: 66GB (Linux swap)

Kysessä on virtuaalikone :D.
