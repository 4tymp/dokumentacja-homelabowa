**Tagi: [[uczen]] [[Informatyk]] [[Homelab]] [[WinServer]]**
**Data: 26-08-2026**

wchodzisz sobie w `wf.msc`
i tam od razu widzisz inbound i outbound rules.

jak klikniesz na jedno z tych to od razu widzisz co tam mamy i co jest wlaczone (zielony ptaszek).

jezeli chcesz np. wlaczyc sobie pingi (ICMP) szukasz tam `File and Printer Sharing (Echo Request - ICMPv4-In` i klikasz prawy > Enable Rule

jezeli checsz stworzyc wlasna zasade (np zeby wpuscic specyficzny port) to klikasz prawym na Inbound Rules > New Rule...
i tam wybierasz sobie Rule Type jak chcesz, Potem protokol, Akcje i Profile, po czym nazywasz ta zasade i tyle - smiga.