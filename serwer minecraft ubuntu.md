**Tagi: [[uczen]] [[Informatyk]] [[Homelab]]**
**Data: 28-10-2026**

na start pobierasz jave, w zaleznosci od wersji na jaka tworzysz serwer
- Dla Minecrafta **1.20.5 i nowszych** (w tym 1.21+): Pobierz i zainstaluj **Java 21**.
- Dla Minecrafta **1.17 do 1.20.4**: Pobierz **Java 17**.
- Dla starszych wersji (1.16 i niżej): Pobierz **Java 8**.

```
sudo apt install openjdk-21-jre-headless -y
```
fajnie tez jakbys mial tmuxa zeby moglo sobie latac w tle

tworzysz potem katalog gdzie ma sie znalezc serwer i wchodzisz na niego

nastepnie musisz pobrac silnik kotry ma prowadzic twoj serwer (ja tu bede bral PaperMC), wiec wchodzisz na strone silnika i pobierasz go (odpowiadajaca swojej wersji mc)

dla ulatwienia zycia zmien nazwe pobranego pliku na `server.jar`

no i przez ftp teraz wrzuc sobie to do katalogu ktory stworzyles

nastepnie tworzysz skrypt `start.sh` w naszym katalogu.

w srodku niego wrzucasz
```
#!/bin/bash
java -Xmx4G -Xms4G -jar server.jar nogui
```
(mozesz zmienic wartosci 4GB na wlasne)

i pamietaj zeby dac mu prawa do uruchamiania!

musisz jeszcze zaakceptowac aule, najlatwiej:
```
echo "eula=true" > eula.txt
```

no i odpal skrypt, po czym go zamknij i pobaw sie `server.properties` ziom

a jak chcesz zamknac serwer, wpisujesz `stop`
