**Tagi: [[uczen]] [[Informatyk]] [[Homelab]] [[Linux]]**
**Data: 22-07-2026**

na start sie bawimy przezabawnie, wiec musisz dodac oficjalne repo jellyfina 
```
sudo apt update && sudo apt install -y curl gnupg debian-keyring
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://repo.jellyfin.org/jellyfin_team.gpg.key | sudo gpg --dearmor -o /etc/apt/keyrings/jellyfin.gpg
```

no i tworzymy plik repo (nowszy format .sources, zalecany przez jellyfina)

```
. /etc/os-release
ARCH=$(dpkg --print-architecture)
cat <<EOF | sudo tee /etc/apt/sources.list.d/jellyfin.sources
Types: deb
URIs: https://repo.jellyfin.org/ubuntu
Suites: ${VERSION_CODENAME}
Components: main
Architectures: ${ARCH}
Signed-By: /etc/apt/keyrings/jellyfin.gpg
EOF
```

no i w koncu mozesz instalowac
`sudo apt install jellyfin`

potem dodajesz port do firewalla (specjalnie robimy przez tailscale bo to mam na serwerze)
```
sudo ufw allow in on tailscale0 to any port 8096 proto tcp
```

no i wiadomo tez na lokalny
```
sudo ufw allow from 192.168.1.0/24 to any port 8096 proto tcp
```

no i uruchamiamy i dojemy autostart!
```
sudo systemctl enable --now jellyfin
```

no i teraz pierwsza konfiguracja, wchodzisz na ip serwera z portem 8096 w przegladarce i konfigurujesz sobie pierwsze wlaczenie

zeby dodac filmy do bayz uzytkownik jellyfin musi miec dostep do folderow (u mnie samba), musze go wiec dodac do grupy sambauser
`sudo usermod -aG sambauser(nazwagrupy) jellyfin`

i teraz musisz zrestartowac jellyfina klasycznie `systemctl restart jellyfin`

i tyle! masz jellyfina