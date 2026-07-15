**Tagi: [[uczen]] [[Informatyk]] [[Linux]] [[Homelab]]**
**Data: 10-07-2026**

wiec tak, dziala on na zasadzie whitelisty.
mozesz go klasycznie sprawdzic systemctl status

najpierw, sprawdzamy status UFW:
```
sudo ufw status verbose
```

jak dodawac nowe porty?
```
sudo ufw allow [NUMER_PORTU]/[PROTOKÓŁ]
```
wlasnie tak

jak usuwac reguly?

najpierw sprawdz reguly z numareami
```
sudo ufw status numbered
```

i zeby usunac regule (np. 1)
```
sudo ufw delete 1
```