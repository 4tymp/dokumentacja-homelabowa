**Tagi: [[uczen]] [[Informatyk]] [[Homelab]] [[Sieci]]**
**Data: 28-10-2026**

najpierw tworzysz sobie POOL
*IP > Pool > New*

wtedy 
*IP > DHCP > New*
i ladnie sobie ustawiasz co chcesz XD (pamietaj zeby miec IP na interfejsie!)

jezeli laczysz sie z innym routerem pamietaj zeby na nim zrobic
```
/ip dhcp-client add interface=<interfejs> disabled=no
```
zeby dostal adres!