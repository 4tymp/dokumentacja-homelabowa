**Tagi: [[uczen]] [[Informatyk]] [[Homelab]] [[WinServer]]**
**Data: 22-07-2026**

Server Manager > Add roles and features > 

w Server Selection wybierasz serwer na ktorym chcesz zainstalowac usluge

w Server Roles wybierasz AD DS

i potem next next az nie zainstalujesz (kochamy windowsa)


po zainstalowaniu w prawym gornym rogu poiwnien pojawic ci sie zolty znak z wykrzyknikiem przy fladze, kliknij go bo musisz zrobic Post-deployment Configuration.
kliknij Promote this server to a domain controller.

stad, zakladam ze tworzysz to na nowym serwerze, wiec tworzysz nowy las. 
klikasz wiec ad a new forest, nazwij sobie wtedy domene.

potem musisz ustawic haslo do DSRM

i lecisz windowsowo next next next az do install

po restarcie powinienes widziec, ze w koncu jestes w domenie ktora stworzyles. 

teraz powinienes stworzyc konto ktore jest tylko od zarzadzania ADDS, zebys nie siedzial caly czas na glownym Administratorze.

Start > Windows Administrative Tools > Active Directory Users and Computers

w `<nazwadomeny>`po lewej klikasz lewym, New > Organizational Unit

nazwij jak chcesz, jezeli bedzie to katalog trzymajacy adminow, wiec ja nazwalem `ADMINS`.

w srodku nowego folderu tworzysz New > User
i wpisujesz tam co chcesz razem z logon name (czesto uzywa sie formatu `a-nazwa` zeby bylo wiadomo ze to admin)

wtedy wchdzisz w properties tego usera, Member Of > Add > Domain Admins > Check Names
ok, apply, ok i masz to!

mozesz sie zalogowac na niego klikajac other users na ekranie logowania.
