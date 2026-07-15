**Tagi: [[uczen]] [[Informatyk]] [[Linux]] [[Homelab]]**
**Data: 10-07-2026**

`scp <zrodlo> <user@ip>:<destynacja>` - bezpiecznie kopiuje pliki pomiedzy hostami


laczenie sie poprzez ssh file transfer protocol:
```
sftp <user>@<ip>
```

i wtedy klasycznie `ls` zeby zobacyzc pliki na serwerze

`put <plik_lokalny>` - wrzuca pliki na serwer
`get <plik_zdalny>` - pobiera pliki z serwera

a wychodzisz `exit`.