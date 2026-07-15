**Tagi: [[uczen]] [[Informatyk]] [[Linux]] [[Homelab]]**
**Data: 10-07-2026**

1. sprawdzasz swoj interfejs `ip a`
2. szukasz swojego interfejsu w netplanie `ls /etc/netplan/`
3. wbijasz sie w plik ktory tam masz z sudo
4. zmodyfikuj plik zeby i zmien co chcesz
przyklad:
```
network:
  version: 2
  ethernets:
    nazwa_twojej_karty:
      dhcp4: no
      addresses:
        - 192.168.1.100/24
      routes:
        - to: default
          via: 192.168.1.1
      nameservers:
        addresses:
```
5. zapisz zmiany `sudo netplan apply`