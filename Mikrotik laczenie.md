**Tagi: [[uczen]] [[Informatyk]] [[Homelab]] [[Sieci]]**
**Data: 09-09-2026**

po wlaczeniu nowego lub zresetowanego urzadzenia wchodzisz w przegladarce na domyslny adres RouterOS, czyli **192.168.88.1**

jezeli wchodzisz przez **CHR**, to musisz najpierw w terminalu zrobic 
```
/ip address print
```
zeby zobacyzc jaki adres dostal twoj router z dhcp.

jezeli nie dostal, sprawdz najpierw
```
/interface print
```

zeby sprawdzic jak wygladaja twoje interfejsy.

jezeli chcesz dostac adres z dhcp, robisz
```
/ip dhcp-client add interface=<interfejs> disabled=no
```
i wtedy po wyprintowaniu adresow router powinien dostal adres

i to go mozesz wpisac do Winboxa, jednak poleca sie i tak wchodzic przez mac
