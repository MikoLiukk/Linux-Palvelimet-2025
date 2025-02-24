# h5 Näkyviin 24.2.2025 klo 12:15

## a) Nimi. Laita julkinen nimi osoittamaan omaan koneeseesi.
Käytin nimen vuokraamiseen "suomalaista" Zoner-palvelua. Nimi maksoi minulle 12€ + alv per vuosi. Vuokrasin nimen mikoliukkonen.com.
Zonerin kanssa oli ongelmia, asiakaspalvelu oli todella hidasta, en päässyt kirjautumaan sisään tilille ja koska minun aikani on rajallista jouduin turvautumaan toiseen palveluntarjoajaan.

Kun etsin muita mahdollisia palvelun tarjoajia, en päässyt sisään millekkään sivustolle. Huomasin, että Linuxin kello oli väärässä ajassa ja korjasin sen komennolla
´sudo apt-get install ntpdate´ Tämä komento päivittäisi kelloni tulevaisuudessa automaattisesti. 
https://askubuntu.com/questions/214246/how-to-fix-wrong-system-time-and-date


Päädyin Namecheapin alle domainilla mikoliukkonen.it.com

Kävin tämän jälkeen muokkaamassa host recordin seuraavaksi. 

![image](https://github.com/user-attachments/assets/17932704-bbef-41d3-9320-6068de3e036a)

Namecheapin kanssa minulla meni aikaa noin 10min.

Testasin sivuston nettiselaimella ja aikaisempi tehty kotisivu löytyi.
## b)  Based. Laita Name Based Virtual Host näkymään uudessa nimessäsi. Kotisvuja pitää pystyä muokkaamaan ilman pääkäyttäjän oikeuksia. 15:00
En ymmärtänyt tai osannut tätä tehtävän antoa. Yritin hakea apua muunmuasta videoilta https://www.youtube.com/watch?v=6Guk-lv7QJQ ja https://www.youtube.com/watch?v=x5fWSWdM4F8

Laitan tehtävät laksuun, koska en pääse itse eteenpäin 17:00

17:10 Tämän ilmeisesti olen jo tehnyt edellisellä kotitehtävällä, kun käytin komentoa echo ´"Hei kaikki" | sudo tee /var/www/html/index.html´

## c)  Kotisivu. Tee vähintään kolmen erillisen alasivun (esim. index.html, blog.html, projects.html) kotisivu ja kopioi se näkymään palvelimellesi.
Sain apua muiden tehtävistä c kohdan tekimiseen. Kiitos linkin Petteri Pinkkilalle 
https://github.com/pinkkila/linux-course/blob/main/tehtava-h5.md

Tässä yiritin kirjottaa koodia index.html dokumenttiin, mutta ilmeisesti minulla ei ole oikeuksia pääkäyttäjänä.
![image](https://github.com/user-attachments/assets/2974047a-2a6c-4e54-aacb-32ea6796b959)

## d)  Alidomain. Tee kaksi uutta alidomainia, jotka osoittava omaan koneeseesi.
![image](https://github.com/user-attachments/assets/fafa90b2-9547-4f38-8429-de2c61e1bdad)


## e) Tutki jonkin nimen DNS-tietoja 'host' ja 'dig' -komennoilla.
Kysyin chatGPT prompilla "mtiä "host" ja "dig" komennot tekevät linuxilla"
Molemia käytetään DNS kyselyihin. Ne auttavat selvittämään verkkkotunnusten ja IP-osoitteiden tietoja.

![image](https://github.com/user-attachments/assets/9210b2db-d36f-42df-8e41-dc5b557aa2bd)

