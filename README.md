# IoT
### 12.9.2022 Projektin suunnitelma
### Jarco
![kaava drawio](https://user-images.githubusercontent.com/113332610/189615513-e08b5469-86d4-45cd-aecb-be395c0a7cd5.png)
### Aloitettiin Raspberryn asennus, ladattiin Raspberryn asennus SD kortille, siirrettiin ja aukaistiin se toisella läppärillä. Tehtiin tunnukset raspberryyn ja ladatiin päivitykset. Päivityksen jälkeen rebootattiin kone, ja asennus oli valmis. Asennuksen jälkeen aloitettiin tekemään toista asennusta command promptissa, ja tehtiin seuraavasti.
### 1. Päivitettiin packages.
### 2. Ladattiin apache2.
### 3. Ladattiin php.
### 4. Ladattiin mariadb.
### 5. Ladattiin php-mysql connector.
### 6. Restartattiin apache2.
### 7. Testatiin serveriä.

### 15.9.2022
### 1. Tehtiin tietokanta nimeltä SMarket
### 2. Tehtiin molemmille omat tietokannat ja niihin taulukot

#### 1. sudo mariadb
#### 2. CREATE DATABASE Jerry_SMarket;
#### 3. use SMarket
#### 4. CREATE TABLE Liike (id int AUTO_INCREMENT NOT NULL PRIMARY KEY, arvo boolean, aika datetime);
#### 5. PRAGMA TABLE_INFO(Liike)
#### 6. INSERT INTO Liike (arvo, aika) VALUES (false, now());
#### 7. SELECT * FROM Liike;

 <h3>19.9.2022</h3>
  Tehtiin liikesensori pelkällä Raspberryllä.
  <details>
    <summary>
      Koodi:
    </summary>
  
      import time
      import RPi.GPIO as GPIO // (Lisättiin libraryt jota voi käyttää koodissa)
      
      pin = 4 // (Variable)
      GPIO.setmode(GPIO.BCM)   // (Setuppi)
      GPIO.setup(pin, GPIO.IN)
      
      def getTime():
        result = time.localtime()
        time_string = time.strftime("%m/%d&%y/, %H:%M:%S:", result)
        return time_string  // (Funktiolla haetaan aikaa)
        
      try:
        while True:
          timeResult = getTime()
          if GPIO.input(pin):
            print("Liikettä: "+ str(timeResult))
          else:
            print("Ei liikettä: "+ str(timeResult))
          time.sleep(2.5)  // (Kokeillaan onko virheitä jos ei ole niin toimii)
      except:
        print("-")
        GPIO.cleanup()
  </details>
  
  
  <h3>20.9.2022</h3>
  Tehtävät 20.9.2022
   <details>
    <summary>
     Tehtävät:
 </summary>
 
### 1. EEPROM on haihtumatonta puolijohdemuistia, joka voidaan uudelleenkirjoittaa n. 10 000–100 000 kertaa. EEPROM-muistia käytetään pääasiassa asetustietojen tallentamiseen mikroprosessorin tai mikrokontrollerin sisältävissä laitteissa.
### 2. UART eli sarjaliikennepiiri on laitteisto tai mikropiiri, joka muuntaa rinnakkaismuotoista tietoa sarjamuotoiseksi ja päinvastoin.
### 3. I2C on yksinkertainen kaksisuuntainen ohjaus- ja tiedonsiirtoväylä. Tavallisin käyttö kulutuselektroniikassa on näytön tai television liitännän kyky kertoa nimensä ja tarkkuutensa tietokoneelle VGA-, DVI- tai HDMI-liittimen sisässä olevan I2C-liitynnän kautta. I2C-väylässä on sarjamuotoinen data- ja kellolinja.
### 4. SIP on IP-puhelinyhteyksien luonnista vastaava tietoliikenneprotokolla. SIP on korvaamassa vanhemman videoneuvotteluun käytetyn H.323-protokollan. SIP-protokollan avulla voidaan muodostaa puhelinyhteyksiä.
### 5. Mitä eroa on I2C ja SIP? I2C on half-duplex-viestintä ja SPI on full-duplex-viestintä. I2C on kaksijohtiminen protokolla ja SPI on nelijohdinprotokolla.
</details>

  <h3>20.9.2022</h3>
  Tehtävät
   <details>
    <summary>
     Tehtävät 2:
 </summary>

### 1. Raspberryn lämpötila = $vcgencmd measure_temp
### 2. Kuinka paljon tilaa jäljellä = $df -Bm
### 3. Miten vaihdetaan polusta toiseen = $cd ~
</details>



  <details>
    <summary>
      Lista:
    </summary>
  
      apt-get update = päivittää raspberryn
      clear = pyyhkii kaiken terminaalista
      date = näyttää päivämäärän
      find / -name esimerkki.txt = etsii tiedoston nimellä
      nano example.txt = voi kontrolloida
      poweroff = laittaa virrat kiinni
      raspi-config = aukaisee raspin configurationin
      reboot = käynnistää uudelleen
      shutdown -h now = sulkee heti
      shutdown -h 01:22: = sulkee asettaman ajan päästä
      startx = menee serverille X
      
      cat esimerkki.txt = aukaisee tai tekee tiedoston
      cd/abc/xyz = path directory
      ls -l = listaa sovellukset
      mkdir esimerkki:_polku = tekee directoryn
      mv XXX = ei löydy
      rm esimerkki.txt = poistaa tiedoston
      scp user@10.0.0.32:/some/path/tiedosto.txt = kopioi tiedostoja kahden paikan välillä
      touch example.txt = muuttaa timestamppia
      
      ifconfig = näyttää netin tiedot
      iwconfig = näyttää langattoman netin tiedot
      iwlist wlan0 scan = scannaa langattoman yhteyden
      iwlist wlan0 | grep ESSID = 
      nmap = näyttää mikä service on auki
      ping = näyttää yhteyden nopeude
      wget https://www.website.com/example.txt = näyttää nettisivun tiedot
      
      
      cat /proc/meminfo = memoryn info
      cat /proc/partitions = Näyttää väliseinät
      cat /proc/version = Näyttää versiot
      df -h = Näyttää paljon tilaa on jäljellä
      df / = näyttää tilaa tietyllä systeemillä
      dpkg - -get-selections | grep XXX 
      dpkg - -get-selections
      free = näyttää käytetyn muistin
      hostname -l
      lsusb = näyttää tietoja usb laitteista
      UP key = näyttää aiemmin syötetyt komennot terminaalissa
      vcgencmd measure_temp = näyttää raspberryn lämpötilan
      vcgencmd get_mem arm && vcgencmd get_mem gpu = arm memoryn käyttö ja GPU memoryn käyttö
      
  </details>
  
   <h3>22.9.2022</h3>
  <details>
    <summary>
     Tehtävä 1.
    </summary>
 
 A)
 
    - sudo mariadb (käynnistää mariadb:n)
    - show databases; (näyttää tietokannat)
  
  B)
 
    - use SMarket (menee tietokantaan)
    - SELECT * FROM Liike; (avaa taulukon)
    - desc Liike; (näyttää kaiken tiedon)
 
  
  </details>
  
  
  
  <details>
    <summary>
     Tehtävä 2.
    </summary>
   
   import time
   import datetime
   import mariadb
   import RPi.GPIO as GPIO


   inputPin = 4
   sleepTime = 5


   GPIO.setmode(GPIO.BCM)
   GPIO.setup(inputPin, GPIO.IN)

   conn = mariadb.connect(user="jaje", password="JarcoJerry1", host="localhost", database="SMarket")
   cur = conn.cursor()


   try:

   while True:

   inputType = GPIO.input(inputPin)
   curTime = datetime.datetime.now()

   #sqlStr = "INSERT INTO Liike (arvo, aika) VALUES({boolean}, '{timeCurrently}')".format(boolean = inputType, timeCurrently = curTime)
   #sqlStr = "INSERT INTO Liike (arvo, aika) VALUES(%s, '%s')" % (inputType, curTime)
   sqlStr = f"INSERT INTO Liike (arvo, aika) VALUES({inputType}, '{curTime}')"

   print(sqlStr)
   cur.execute(sqlStr)
   conn.commit()

   time.sleep(sleepTime)

   except:
   print("Ei toimi")

   conn.close()

   </details>
  
  
   
<h3>26.9.2022</h3>
   
  <details>
    <summary>
     DHT11
    </summary>
 
     import time
     import Adafruit_DHT
     import datetime
     import mariadb



     sensor = Adafruit_DHT.DHT11
     pin = 4
     waitTime = 5



     conn = mariadb.connect(user="jaje", password="JarcoJerry1", host="localhost", database="SMarket")
     cur = conn.cursor()



     try:
     while True:

     curTime = datetime.datetime.now()
     humidity, temperature = Adafruit_DHT.read_retry(sensor, pin)

     sqlStr = "INSERT INTO Liike (arvo, aika) VALUES({boolean}, '{timeCurrently}')".format(boolean = temperature, timeCurrently = curTime)
     print(sqlStr)
     cur.execute(sqlStr)
     time.sleep(waitTime)

     except RuntimeError as error:
     print(error.args[0])
     print("Ei Toimi")

</details>

<h3>29.9.2022</h3>
   
  <details>
    <summary>
     Nettisivu
    </summary>
 
     <!-- Documentti tyyppi -->
     <!DOCTYPE html>



     <html>

       <!-- Headeri -->

       <head>
         <title>Hälytin</title>
       </head>

       <body>

         <!-- Siirä data taulukkoon -->

         <div style="
           box-sizing: border-box;
           border: 2px solid #969696;
           border-radius: 5px;
           background: #fffffff;
         ">
           <center>

             <!-- Otsikko -->

             <h1 style="
               align-left: center;
               align-right: center;
               text-align: center;
               color: rgb(255,55,55);
               font-family: Courier New;
             ">HÄLYTIN</h1><br>

             <!-- Ala Otsikko -->

             <img src="images/skul" alt="skull emoj" width=100 height=100><br>
             <h2 style="font-family: Courier New;">Data:</h2>



            <!-- PHP -->



            <?php

               // Laitetaan muuttujat, ja niille arvot.

               $servername = "localhost";
               $username = "jaje";
               $password = "JarcoJerry1";
               $dbname = "SMarket";
               $conn = new mysqli($servername, $username, $password, $dbname); // Yhteys databaseen

               // Katsotaanko toimiiko yhteys vai ei, jos toimii se jatkaa ohjelmaa, jos ei se antaa sivulle viestin.

               if ($conn->connect_error){
                 die("😭😭 Connection failed 😭😭" . $conn->connection_error);
               }

               // Yhteys toimii, joten jatkaa ohjelmaa. Asettaa SQL komennon ja syöttää sen.

               $sql = "SELECT id, arvo FROM Liike ORDER BY -id LIMIT 10";
               $data = $conn->query($sql);

               // Antaa sivulle kaikki tiedot muuttujan "data" sisältä ja syöttää ne sivulle.

               ?>
               <table>
                 <style>

                   table, th, td {
                     border-radius: 5px;
                   }

                   table {
                     border: 1px solid #ccd6dd;
                     font-family: arial, sans-serif;
                     width: 25%;
                   }



                  td, th {
                     border: 1px solid #edf7ff;
                     text-align: left;
                     padding: 10px;
                   }

                   tr:nth-child(even) {
                     border: 1px solid #edf7ff;
                     background-color: #ccd6dd;
                   }



                </style>
                   <tr>
                     <th>id</th>
                     <th>arvo</th>
                   </tr>
               <?php
                 while($row = $data->fetch_assoc()){
                   ?>
                   <tr>
                     <td><?php echo $row["id"]?></td>
                     <td><?php echo $row["arvo"]?></td>
                   </tr>
                   <?php
                 }
               ?>
               </table>
               <?php

               // Sulkee yhteyden.

               $conn->close();



            ?><br>

             <!-- Nappula -->

             <button style="
               box-sizing: border-box;
               border: 2px solid #ccd6dd;
               border-radius: 5px;
               width: 25%;
               height: 50px;
               color: rgb(255,55,55);
               background: #ffffff;
               font: bold 5pt Arial;
               font-family: Courier New;
               font-size: 24px;
             ">FREE DOWNLOAD</button>

             <!-- Linkki -->

             <p style="font-family: bold 10pt, Courier New;">Powered by S-Ketju</p>
             <a href="https://www.s-ryhma.fi">Linkki</a>

           </center><br>
         </div>
       </body>

     </html>

</details>




<h3>6.10.2022</h3>
  <details>
     <summary>
       PHP index
     </summary>

       Tehtiin azure serveri MySQL workbenchillä
       kirjauduttiin admin-tunnuksilla
       
       komennot:
       - cd Tietopolku
       - $php -S localhost:8000
       
      </details>
      
      
      <p align="center">
  <a href="https://www.yushi.dev/" target="_blank" rel="noreferrer"><img src="https://user-images.githubusercontent.com/75753187/123350185-74ce0900-d528-11eb-848d-d92955dbb944.png" alt="my banner"></a>
</p>

<h3 align="center">
Hi there, I'm <a href="https://www.yushi.dev/" target="_blank" rel="noreferrer">Yu</a> 👋
</h3>

<h2 align="center">
I'm a Full-Stack Web Developer 💻, Photographer 📸, and Designer 🎨!
</h2> 

I love the entire process of developing creative websites. I love the challenge of finding caches and spending time to meet new people. Learning how people hide things and where people are likely to look.

### 🤝 Connect with me:

<a href="https://www.linkedin.com/in/yushi95/"><img align="left" src="https://raw.githubusercontent.com/yushi1007/yushi1007/main/images/linkedin.svg" alt="Yu Shi | LinkedIn" width="21px"/></a>
<a href="https://instagram.com/yushi.95"><img align="left" src="https://raw.githubusercontent.com/yushi1007/yushi1007/main/images/instagram.svg" alt="Yu Shi | Instagram" width="21px"/></a>
<a href="https://yushi95.medium.com/"><img align="left" src="https://raw.githubusercontent.com/yushi1007/yushi1007/main/images/medium.svg" alt="Yu Shi | Medium" width="21px"/></a>
</br>
- 💬 If you have any question/feedback, please do not hesitate to reach out to me!

## 🔭 I'm currently working on

- My old projects
- Restaurant Recommendation App (React-Native)
- Mobile + Desktop Spotify Clone (Working on it soon...)
- My next blog
- My CSS skill

## 🌱 I'm currently learning

- 📱 React Native
- Firebase
- React Context API
- Styled Components  

## 💼 Technical Skills

![](https://img.shields.io/badge/Code-React-informational?style=flat&logo=react&color=61DAFB)
![](https://img.shields.io/badge/Code-Redux-informational?style=flat&logo=Redux&color=764ABC)
![](https://img.shields.io/badge/Code-JavaScript-informational?style=flat&logo=JavaScript&color=F7DF1E)
![](https://img.shields.io/badge/Code-Ruby-informational?style=flat&logo=Ruby&color=CC342D)
![](https://img.shields.io/badge/Code-Ruby_on_Rails-informational?style=flat&logo=Ruby-On-Rails&color=CC0000)
![](https://img.shields.io/badge/Code-HTML5-informational?style=flat&logo=HTML5&color=E34F26)
![](https://img.shields.io/badge/Code-PostgreSQL-informational?style=flat&logo=PostgreSQL&color=336791)
![](https://img.shields.io/badge/Code-SQLite-informational?style=flat&logo=SQLite&color=003B57)

</br>

![](https://img.shields.io/badge/Style-Bootstrap-informational?style=flat&logo=Bootstrap&color=7952B3)
![](https://img.shields.io/badge/Style-CSS3-informational?style=flat&logo=CSS3&color=1572B6)
![](https://img.shields.io/badge/Style-styled--components-informational?style=flat&logo=styled-components&color=DB7093)


</br>

![](https://img.shields.io/badge/Tools-Figma-informational?style=flat&logo=Figma&color=F24E1E)
![](https://img.shields.io/badge/Tools-NPM-informational?style=flat&logo=NPM&color=CB3837)
![](https://img.shields.io/badge/Tools-Heroku-informational?style=flat&logo=Heroku&color=430098)
![](https://img.shields.io/badge/Tools-Netlify-informational?style=flat&logo=netlify&color=00C7B7)
![](https://img.shields.io/badge/Tools-Git-informational?style=flat&logo=Git&color=F05032)
![](https://img.shields.io/badge/Tools-GitHub-informational?style=flat&logo=GitHub&color=181717)

## 📝 Latest Blog Posts

- [Deploy Rails API Backend to Heroku and React Frontend to Netlify](https://yushi95.medium.com/deploy-rails-api-backend-to-heroku-and-react-frontend-to-netlify-b515239d5022)
- [Animation Login Popup Form by Using React State Hook and CSS](https://medium.com/geekculture/animation-login-popup-form-by-using-react-state-hook-and-css-7ecf803f1fa9)
- [Checklist ✅ for Rails Application](https://yushi95.medium.com/checklist-for-rails-application-30868cb4f48b)
- [Self and Operator in Ruby](https://blog.usejournal.com/self-in-ruby-5e8a91fa4602)

## 📈 GitHub Stats 

[![Anurag's github stats](https://github-readme-stats.vercel.app/api?username=yushi1007)](https://github.com/yushi1007)

[![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=yushi1007&layout=compact)](https://github.com/yushi1007)

[![Visitors](https://visitor-badge.glitch.me/badge?page_id=yushi1007.yushi1007)](https://www.yushi.dev/)
