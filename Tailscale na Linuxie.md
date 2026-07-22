**Tagi: [[uczen]] [[Informatyk]] [[Homelab]] [[Linux]]**
**Data: 22-07-2026**

na poczatku chcialem dzwonic do mojego dostawcy internetu, prosic o publiczne ip i robic VPNa wireguarda, ale potem dowiedzialem sie o tailscale wiec jazda!

robimy subnet router, czyli tak zeby jedno urzadzenie reklamowala cala siec domowa, a ja z zewnatrz po prostu lacze sie do niej tak, jakbym byl w domu.

to dzialamy!
instalujesz:
```
curl -fSL https://tailscale.com/install.sh | sh
```

potem musisz wlaczyc ip forwarding na serwerz(wymagane dla subnet routera), bo bez tego serwer nie bedzie w stanie przepuszczac ruchu z tailnetu do reszty twojej sieci lan.
```
echo 'net.ipv4.ip_forward = 1' | sudo tee -a /etc/sysctl.d/99-tailscale.conf
echo 'net.ipv6.conf.all.forwarding = 1' | sudo tee -a /etc/sysctl.d/99-tailscale.conf
sudo sysctl -p /etc/sysctl.d/99-tailscale.conf
```

teraz musisz uruchowic i zaadvertisowac podsieci
wiec sprawdzasz jaka jest twoja podsiec domowa (najczesciej 198.168.1.0/24) `ip route` < tym mozesz sprawdzic
```
sudo tailscale up --advertise-routes=192.168.1.0/24 --accept-dns=false
```
*pamietaj zeby podmienic adres na swoja rzeczywista podsiec*

`--accept-dns=false` jest dodane, bo planuje niedlugo zrobic pihole i nie potrzebuje nowego resolvera od tailscale.

po wpisaniu tego dostaniesz link na ktorym bedziesz musial sie zalogowac do tailscale.

nastepnie musisz zatwierdzic route w panelu admina.
wejdz na https://login.tailscale.com/admin/machines
znajdz swoj serwer, powinien miec oznaczenie "Subnets"

kliknij menu przy urzadzeniu i edit route settings
zatwierdz podsiec ktora advertisowal

no i tyle, ufw powinno byc samo ogarniete przez tailscale
