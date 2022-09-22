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
  Tehtävät 20.9.2022
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
  
  
  
  
  
  
