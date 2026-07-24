**Tagi: [[uczen]] [[Informatyk]] [[Linux]] [[Homelab]]**
**Data: 10-07-2026**

`w` - sprawdzasz kim jestes
`su <username>` zmienia uzytkownika

`adduser <username>` - dodaje uzytkownika
`deluser <username>` - usuwa uzytkownika

jezeli chcesz na stale zmienic katalog w ktorym powstaja katalogi uzytkownikow z domyslnego `/home`, wchodzisz w `/etc/adduser.conf` i zmieniasz linijke `DHOME=<twoja sciezka>`

mozesz tez zrobic `useradd -m <username>` (-m zeby byl home directory, jezeli chcesz zmienic lokalizacje to robisz `useradd -m -d <sciezka>` a bez `-m` po prostu stworzysz uzytkownika)

jezeli chcesz zmienic folder domowy juz istniejacego uzytkownika, robisz:
`sudo usermod -d <nowasciezka> -m <user>`
`-d` ustawia nowa sciezke katalogu domowego
`-m` przenosi zawartosc starego katalogu do nowej lokalizacji (bez `-m` samo sie nic nei przeniesie, zmieni sie tylko wpis w bazie)

zeby zmieniac zasady dzialania `deluser`, wchodzisz w `/etc/deluser.conf`.
mozesz tam np ustawic, zeby przy uzywaniu deluser usuwany byl tez katalog domowy uzytkownika, albo zeby byl usuwany ale tylko po np. backupie.

`passwd <sername>` - zmienia albo ustawia hasla uzytkownika

za zarzadanie terminow hasel odpowiada plik `/etc/shadow`. jego struktura to : `nazwauzytkownika:haslo_hash:ostatnia_zmiana:min:max:osstrzezenie:niekatywnosc:wygasniecie`

mozesz tez sprawdzic te dane uzywajac `sudo chage -l user`

edycja tego pliku jest niezalecana, lepiej uzyc `chage`.
czyli np `sudo chage -M 365 user` - ustawia max zmiany hasla na 365 uzytkownikowi user. 
po wiecej pamietajmy o `man chage`.

jezeli chcesz zmienic domyslne ustawienia dla nowych kont, uzywasz `/etc/login.defs`.
i suzkasz tam password aging controls.

`sudo passwd -l <user>` - blokuje haslo uzytkownika

`id [username]` - wyswitla id grup i uzytkownikow
`groups [username]` - wyswietla grupy do ktorych nalezy uytkownik

`addgroup <groupname>` - tworzy nowa grupe
`delgroup <groupname>` - usuwa grupe

`usermod -a -G <nazwagrupy> <nazwausera>` - dodaje uzytkownika do grupy. `-a` - append, bez tego jedyna grupa ktora bedzie mial user to ta ktora podasz.