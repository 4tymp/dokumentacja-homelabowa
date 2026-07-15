**Tagi: [[uczen]] [[Informatyk]] [[Linux]] [[Homelab]]**
**Data: 10-07-2026**

**Fail2Ban** działa jak automatyczny ochroniarz: jeśli zauważy, że ktoś kilka razy pod rząd odbija się od Twojego SSH, automatycznie i całkowicie blokuje adres IP agresora na poziomie UFW (na godzinę lub na stałe).

`sudo apt install fail2ban` i jazda

teraz powiedzmy mu, gdzie ma pilnować porządku. Stwórz plik konfiguracji:
```
sudo nano /etc/fail2ban/jail.local
```

i wrzucasz co tam potrzebujesz (np ssh)
```
[sshd]
enabled = true
port = <port ssh>
filter = sshd
logpath = /var/log/auth.log
maxretry = 3
bantime = 1h
findtime = 10m
```

no i klasyczny restart
`sudo systemctl restart fail2ban`
