**Tagi: [[uczen]] [[Informatyk]] [[Homelab]] [[Linux]]**
**Data: 14-09-2026**

najpierw upewnij sie, jak nazywa sie twoj naped. uzyj
```
lsblk
```
powinno tam byc cos w stylu `/dev/sr0` < to jest wlasnie twoj naped

wtedy mozesz sobie sprawdzic mozliwosci napedu, pobierasz wiec
```
sudo apt install wodim
```

i mozesz sprawdzic
```
sudo wodim -prcap dev=/dev/srv0
```

# ripowanie CD
bedziemy uzywac cdparanoia (silnik czytajacy dane z plyty), flac (enkoder na  flaci), abcde (skrypt spinajacy to w calosc), pobierz wiec 
```
sudo apt install abcde flac cdparanoia
```

abcde ciagnie ze soba postfix, wiec daj tam local-only zeby nic ci nie wychodzilo poza serwer ziomek

dalej, chcemy zeby abcde ripowalo do FLAC z dobra struktura folderow pod naszego jellyfina (`wykonawca/album/01 - tytul.flac`)

utworz/otworz plik `~/.abcde.conf`
i wklej do niego:
```
OUTPUTTYPE=flac
FLACOPTS='--best'
OUTPUTFORMAT='${ARTISTFILE}/${ALBUMFILE} (${YEAR})/${TRACKNUM} - ${TRACKFILE}'
VAOUTPUTFORMAT='Various Artists/${ALBUMFILE} (${YEAR})/${TRACKNUM} - ${ARTISTFILE} - ${TRACKFILE}'
OUTPUTDIR="/sciezka/do/muzyki"
CDDBMETHOD=musicbrainz
CDCOVERARTPROVIDER="musicbrainz"
MAXPROCS=2
PADTRACKS=y
COMMENT=''
mungefilename ()
{
  echo "$@" | sed s/:/-/g | tr -d \"\'
}
```

ofc zmien OUTPUTDIR na realna sciezke gdzie chcesz zeby to lecialo

co co robi:
- `OUTPUTTYPE=flac` — kodowanie do FLAC (bezstratne)
- `FLACOPTS='--best'` — najlepsza kompresja (nie wpływa na jakość dźwięku, tylko na rozmiar pliku)
- `OUTPUTFORMAT` — struktura folderów `Wykonawca/Album/01 - Tytuł.flac`, dokładnie to, co lubi Jellyfin
- `CDDBMETHOD=musicbrainz` — źródło metadanych (tytuły, wykonawca, rok, numer ścieżki)
- `CDCOVERARTPROVIDER="musicbrainz"` - zrodlo okladek
- `PADTRACKS=y` — numery ścieżek z zerem wiodącym (01, 02 zamiast 1, 2), żeby się dobrze sortowały

no i zapisz, powinienes bys gotowy do ripowania!

wsadz plyte do napedu, poczekaj kilka sekund a potem sprawdz czy cdparanoia widzi plyte i ile ma sciezek:
```
cdparanoia -Q
```

jezeli pokazuja sie sciezki i czas, to znaczy ze plyta jest ladnie czytana.

taeaz czas na uzycie naszego skryptu. odpal abcde:
```
abcde
```

i skrypt sam powinien wykryc plyte w napedzie, sprobuje pobrac metadane z musicBrainz (mozesz byc zapytany jezeli bedzie wiecej niz jeden) a potem zripuje i zakoduje wszystko do FLAC zgodnie z configiem ktory wyzej ustawilismy.

moze to chwile potrwac, szczegolnie jak ripujemy w --best jakosci