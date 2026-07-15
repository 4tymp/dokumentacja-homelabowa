
Tagi: [[uczen]] [[Informatyk]] [[Linux] [[Homelab]]**
**Data: 11-07-2026**

1. instalujesz `sudo apt install samba`
2. tworzysz katalog ktory chcesz zeby byl sharowany normalnie mkdirem (najlepiej w `/srv/`).
3. wchodzisz w confa samby `sudo nano /etc/samba/smb.conf`
4. na dole pliku dodajesz:
```
[sambaubuntu]
    comment = Samba na Ubuntu
    path = <lokalizacja>
    read only = no
    browsable = yes
```
5. restartujesz sambe
```plaintext
sudo service smbd restart
```
6. dodajesz sambe do ufw `sudo ufw allow samba`

i dalej

tworzysz uzytkownika dla samby
```
sudo adduser --system --no-create-home --group sambauser
```

i wpychasz go do samby
`sudo smbpasswd -a sambauser`
i musisz mu wrzucic haslo

wtedy jeszcze upewniasz sie ze folder nalezy do niego:
```
sudo chown -R nasuser:nasuser /srv/nas
sudo chmod -R 770 /srv/nas
```

i wpisujesz folder do konfiguracji samby:
```
[sambaubuntu]
   path = /srv/nas
   browsable = yes
   read only = no
   guest ok = no
   valid users = sambauser
```

no i od razu resetujesz znowu sambe
`sudo systemctl restart smbd`

i potem gdziekolwiek chcesz sie polaczyc dajesz (nazwa na koniec ta sama ktora podales w `[]` w conf)
```
smb://<ip>/sambaubuntu
```

i wpisujesz usera ktorego stworzyles

lub na windowsie:
```
\\<ip>\sambaubuntu
```