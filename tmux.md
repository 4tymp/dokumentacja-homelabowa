**Tagi: [[uczen]] [[Informatyk]] [[Homelab]] [[Linux]]**
**Data: 14-09-2026**

tmux (terminal multiplexer) pozwala uruchamiac wiele terminali w jednymi oknie, odlaczac sesje i wracac do niej pozniej (nawet po zerwaniu polaczenia ssh proces dalej dziala)

instalacja
```
sudo apt install tmux
```

podstawowe pojecia:
- sesja - kontener na cala twoja prace, mozna ja odlaczyc i podlaczyc ponownie (jak przegladarka)
- okno (window) - jak okno w przegladarce, wewnatrz sesji
- panel (pane) - podzial okna na czesci (gora dol lewo prawo)

zeby uruchomic sesje:
```
tmux
```
jezeli chcesz nowa sesje bez nazwy, lub
`tmux new -s praca` (nowa sesja z nazwa praca)

prefix!
prawie kazda komenda tmuxa zaczyna sie od nacisniecia prefixa, a potem nacisniecia kolejnego przycisku.

domyslny prefix to `ctrl + b`

a np. `ctrl + b`, potem `d` odlaczy sesje.

najwazniejsze skroty:
`ctrl+b d` - odlacz sie od sesji (praca dalej dziala w tle)

`tmux ls` - lista sesji

`tmux attach -t praca` - podlacz sie z powrotem (lub po prostu attach jezeli nie ma nazwy)

`tmux kill-session -t praca` - usun sesje

okna:
- `Ctrl+b c` — nowe okno
- `Ctrl+b n` / `Ctrl+b p` — następne/poprzednie okno
- `Ctrl+b 0-9` — przejdz do okna o numerze
- `Ctrl+b ,` — zmien nazwe okna
- `Ctrl+b &` — zamknij okno


czyli typowy sceniariusz:
1. laczysz sie z ssh
2. `tmux new -s nazwa`
3. uruchamiasz proces ktory troche potrwa
4. `ctrl+b d` - odlaczasz sie i mozesz wyjsc z ssh
5. wracasz pozniej: ssh na serwer, potem `tmux attach -t nazwa` - wszystko dalej dziala jakbys nigdy nie wyszedl