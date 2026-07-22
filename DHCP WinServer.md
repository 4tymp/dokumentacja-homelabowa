**Tagi: [[uczen]] [[Informatyk]] [[Homelab]] [[WinServer]]**
**Data: 22-07-2026**

Add roles and features > w Server Roles wybierasz "DHCP Server" >next next next install

wtedy Tools > DHCP > `<nazwadomeny>`> IPv4 prawy przycisk > New Scope

wtedy nazywasz sobie scope
i dalej podajesz start i end ip address do rozdania przez dhcp.

potem mozesz dodac exclusions czyli adresy kotyrch NIE chcesz rozdawac.

dalej ustaiwiasz lease duration, czyli na ile komputer dostaje swoj adres.


w naszym dzisiejszym przypadku chcemy dodawac dodatkowe opcje, iwec na nastepnym ekranie zacznamy yes.

chcemy uzyc naszego rasa ktorego konfigurowalisy wczesniej, wiec podajemy adres ip naszego domain controllera

dajlej uzywamy naszego DC jako dns wiec nie zmieniamy Parent domain

o WINS sie nie martw

i tak, chcesz aktywowac scope.

ma koniec czesto musisz jeszcze authorisowac twoj serwer, klikasz wiec prawym i Authorise, a potem mozesz jeszcze zrobic Refresh jezeli ci sie nie zaladowal dhcp.