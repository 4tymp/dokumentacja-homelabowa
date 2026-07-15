**Tagi: [[uczen]] [[Informatyk]] [[Linux]] [[Homelab]]**
**Data: 10-07-2026**

to na start sobie instalujesz ssh wiadomo
```cli
sudo apt install openssh
```

potem odpalasz
```
sudo systemctl enable ssh
```

mozesz se tez sprawdzic
```
systemctl status ssh
```

czy smiga

no i potem z innego kompa mozesz zrobic
```
ssh "user"@"ip0.0.0.0"
```

i wpisujesz haslo.

jezeli chcesz sobie zrobic klucz zeby nie musiec zawsze wrzucac hasla to robisz na kliencie:
```
ssh-keygen -t ed25519 -C "label_nazwij_sobie"
```

no i potem wystarczy przeslac to na serwer
```
ssh-copy-id "user"@"ip"
```

i jeszcze warto sobie zmienic dostep na pliku prywatnym (bo tylko `.pub` leci na serwer, prywatny klucz jest prywatny tylko i wyalcznie!!)
```
chmod 700 $/.ssh/"nazwa_pliku_prywatnego"
```

a jezeli zmieniales nazwe klucza lub port, to
```
ssh -i <lokalizacja/nazwapliku> <user@ip> -p <port>
```


no i warto by bylo oczywiscie w sshd_config pozmieniac rzeczy:
```
sudo nano /etc/ssh/sshd_config
```

najlepiej jak juz masz klucz:
- wylaczyc mozliwosc logowania haslem
- na pewno wylaczyc mozliwosc logowania na roota (zrob sobie uzytkownika z uprawnianimi sudo)
- zmienic port

a zeby zmienic port na ubuntu trzeba jeszcze sie pobawic socketami, wiec wchodzisz w
`sudo systemctl edit ssh.socket`

tam w odpowiednim miejscu pliku wrzucasz
```
[Socket]
ListenStream=
ListenStream=0.0.0.0:41412
```
(to 0.0.0.0 jest wazne, bo bez tego socket czekalby na ipv6)

i potem restartujesz sobie:
```
sudo systemctl daemon-reload
sudo systemctl restart ssh.socket
sudo systemctl restart ssh.service
```

i powinienes miec zmieniony port.


