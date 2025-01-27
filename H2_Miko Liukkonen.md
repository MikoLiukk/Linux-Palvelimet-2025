# H2 Komentaja Pingviini 27.01.2025

## Johdanto 
Tämän raportin tarkoituksena on opetella Linuxin komentopäätteen peruskomennot. Raportti perustuu Linux-palvelimien kurssin H2 kotitehtävää.
Linkki: https://terokarvinen.com/linux-palvelimet/

## X Lue ja tiivistä Karvinen 2020: Command line basics revisited

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

###
