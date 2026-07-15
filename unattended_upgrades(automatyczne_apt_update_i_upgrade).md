**Tagi: [[uczen]] [[Informatyk]] [[Linux]] [[Homelab]]**
**Data: 10-07-2026**

```
sudo apt install unattended-upgrades
sudo dpkg-reconfigure --priority=low unattended-upgrades
```

na ekranie, który się pojawi, wybierz `<Yes>` i kliknij enter. Od teraz system raz na dobę sam po cichu pobierze i zainstaluje krytyczne poprawki bezpieczeństwa systemu.

a jezeli bys chcial wylaczyc auto updaty to znowu odpalasz druga komende i tam zaznaczasz 
`<no>`.

