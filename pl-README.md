# MPT - Modyfikacja umożliwiająca grę wieloosobową dla SPT

<details>
	<summary>Spis treści</summary>
	<ol>
		<li><a href="#what-is-mpt">Czym jest MPT</a></li>
		<li><a href="#license">Licencja</a></li>
		<li>
           	<a href="#prerequisites">Warunki wstępne</a>
            <ul>
                <li><a href="#hosting">Hostowanie</a></li>
                <li><a href="#client">Klient</a></li>
            </ul>
        </li>
        <li><a href="#hardware-requirements">Wymagania Sprzętowe</a></li>
		<li>
	            <a href="#installation">Instalacja</a>
	            <ul>
	                <li><a href="#host-using-port-forwarding">Host - przy użyciu przekierowania portów</a></li>
	                <li><a href="#host-using-a-vpn">Host - przy użyciu VPN</a></li>
	                <li><a href="#client-using-port-forwarding">Klient - Przy użyciu przekierowania portów</a></li>
	                <li><a href="#client-using-a-vpn">Klient - Przy użyciu VPN</a></li>
	            </ul>
	        </li>
		<li><a href="#credits">Uznania autorstwa</a></li>
	</ol>
</details>

## Czym jest MPT

**MPT** jest modyfikacją do **SPT-Aki** która pozwala na grę kooperacyjną (COOP) ze swoimi znajomymi. Modyfikacja wykorzystuje połączenie P2P-UDP, które pozwala na wydajną i nowoczesną rozgrywkę. Główne cele MPT to: wydajność, precyzyjność oraz wsparcie modyfikacji. MPT obecnie jest utrzymywane przez zespół MPT.

## Licencja

<img src="https://mirrors.creativecommons.org/presskit/buttons/88x31/png/by-nc-nd.png" alt="cc by-nc-nd" width="196" height="62" style="float:right">

Ten projekt jest objęty licencją [CC BY-NC-ND 4.0](https://creativecommons.org/licenses/by-nc-nd/4.0/legalcode.en).

- Możesz udostępniać MPT tylko pod warunkiem, że zostaną podane odpowiednie odnośniki dotyczące autorstwa, projekt nie zostanie użyty komercyjnie oraz projekt nie będzie modyfikowany.
- Nie możesz w żaden sposób monetyzować swojego serwera w zakresie płatności czy dotacji.
- Nie możesz hostować ogromnych publicznych serwerów, MPT przeznaczone jest do gry kooperacyjnej (COOP) ze swoimi znajomymi.
- Nie możesz kopiować i/lub replikować kodu wytworzonego przez MPT, nie możesz również wykorzystywać zasobów, które zostały wytworzone przez naszych developerów oraz artystów.

## Warunki wstępne

MPT wymaga ogólnej wiedzy o komputerach, sieciach oraz Aki. Jeżeli nie czujesz się komfortowo w tych aspektach, ten projekt nie jest dla Ciebie. Prosimy o uszanowanie i zrozumienie tego.

### Hostowanie

- Router oraz dostawca internetu (ISP), który wspiera **Przekierowanie Portów** lub **UPnP**
- Router, który wspiera Pętle zwrotną NAT (NAT Loopback) jeżeli będzie to sieć lokalna/wewnętrzna
- Otwarty port 6969 dla serwera AKI
- Port UDP otwarty dla ruchu P2P, domyślnie 25565 (jeżeli użyjesz UPnP nie jest to wymagane)
- Zainstalowane oraz działające SPT, pasujące do wersji MPT, która będzie używana
- Dostęp do Twojej Zapory sieciowej Windows
- Internet o prędkości przynajmniej 20 Mbit/s (Prędkość zalecana w obu kierunkach). Każdy klient wykorzystuje średnio 400 kbit/s.

### Klient

- Router oraz dostawca internetu (ISP), który wspiera **Przekierowanie Portów** lub **UPnP** | **UWAGA**: Jest to wymagane tylko jeżeli planujesz hostować sesje w grze.
- Port UDP otwarty dla ruchu P2P, domyślnie 25565 (jeżeli użyjesz UPnP nie jest to wymagane) | **UWAGA**: Tak samo jak powyżej
- Zainstalowane oraz działające SPT, pasujące do wersji MPT, która będzie używana
- Dostęp do Twojej Zapory sieciowej Windows
- Internet o prędkości przynajmniej 20 Mbit/s (Prędkość zalecana w obu kierunkach).

### Wspólne

- Najnowsze pliki modyfikacji MPT

## Wymagania Sprzętowe

Poniżej podane są rekomendowane wymagania sprzętowe dla płynnej rozgrywki:

- **Procesor**: i7 8700k / Ryzen 7 2700x
- **Karta Graficzna**: GTX 1060 / RX 580
- **Pamięć RAM** minimalnie 16 GB, jednak zalecaną ilością jest 32 GB
- **Magazyn**: Dysk SSD jest wymagany, nie oczekuj wsparcia jeżeli MPT będzie uruchamiane na dysku HDD

Największy wzrost w MPT (oraz w SPT ogółem) dają mocniejszy Procesor oraz Pamięć RAM.

## Instalacja

### Host - przy użyciu przekierowania portów

Zanim rozpoczniesz wykonywanie poniższych kroków, upewnij się, że wszystkie porty podane w **Warunkach Wstępnych** zostały przekierowane. Nie otrzymasz od nas wsparcia przy przekierowaniu portów. Jeżeli nie masz dostępu do routera lub nie masz możliwości przekierowania portów, użyj VPN.

**Konfiguracja Zapory sieciowej**

1. Przekierowanie portu 6969 TCP w swoim routerze (w obu kierunkach wejście/wyjście)
2. Przekierowanie portu UDP, który będzie używany, w swoim routerze, domyślnie 25565 (w obu kierunkach wejście/wyjście)
3. Gdy Windows wyświetli komunikat, zezwól na połączenie w swojej Zaporze sieciowej

**Konfiguracja Ogólna**

1. Pobierz oraz zainstaluj najnowszą wersję MPT
2. Przejdź do katalogu, w którym znajduje się zainstalowany SPT i wypakuj zawartość pliku skompresowanego do tego katalogu
3. Uruchom jednorazowo `Aki.Server.exe` aby pozwolić mu wygenerować pliki konfiguracyjne dla MPT, a następnie go wyłącz.
4. Znajdź swój publiczny adres IP (WAN), możesz użyć przykładowo: [ipv4.icanhazip.com](https://ipv4.icanhazip.com/)
5. Przejdź do `user\mods\MPTCoop\config` i otwórz `coopConfig.json`
6. Zamień wartość `externalIP` na Twój adres IP WAN (lub adres serwera VPN jeżeli go używasz), który znaleziony został w kroku 4, a następnie zapisz oraz zamknij plik.

Przykład ze sztucznym publicznym adresem IP (WAN) (**70.50.130.200**):
```json
{
	"protocol": "http",
	"externalIP": "70.50.130.200"
}
```
7. Znajdź jaki jest Twój lokalny adres IP (LAN). Otwórz `Wiersz poleceń` (Naciśnij start i wyszukaj `cmd` lub `wiersz polecenia` i naciśnij klawisz Enter)

Powinno to wyglądać następująco:
![image](https://github.com/mpt-coop/Documentation/assets/20912169/2b089bba-aac2-437e-9a6a-6620a4ba249b)

8. Wewnątrz `Wiersza poleceń` wpisz 'ipconfig' i naciśnij klawisz Enter. Twój lokalny adres IP (LAN) powinien wyświetlać się tak jak poniżej:
```bat
Windows IP Configuration


Ethernet adapter Ethernet:

   Connection-specific DNS Suffix  . : home
   IPv4 Address. . . . . . . . . . . : 192.168.1.120 <------ To jest Twój lokalny adres IP (LAN)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.1.1
```
9. Wróc do głównego katalogu i przejdź do `Aki_Data\Server\configs` a następnie otwórz `http.json`
10. Zmień wartość pola `ip` na Twój lokalny adres IP (LAN), a nastąpnie zapisz i zamknij plik.

Przykład ze sztucznym lokalnym adresem IP (LAN) (**192.168.1.120**):
```json
{
	"ip": "192.168.1.120",
	"port": 6969,
	"webSocketPingDelayMs": 90000,
	"logRequests": true,
	"serverImagePathOverride": {	}
} 
```
11. Uruchom `Aki.Server.exe` i poczekaj chwilę aż skończy się ładować

Po poprawnym uruchomieniu powinno to wyglądać następująco:
![image](https://github.com/mpt-coop/Documentation/assets/20912169/fe46fb2d-4e90-4f54-b159-745a1561772a)

12. Uruchom `Aki.Launcher.exe` i naciśnij 'Settings'
13. Zmień wartośc w polu `URL` tak aby odzwierciedlała Twój publiczny adres IP (WAN). Używając przykładu z kroku 6 wartością byłoby: `http://70.50.130.200:6969` (pamiętaj aby usunąc jakiekolwiek slashe `/` na samym końcu URL)

### Host - przy użyciu VPN

1. Pobierz oraz zainstaluj najnowszą wersję MPT
2. Przejdź do katalogu, w którym znajduje się zainstalowany SPT i wypakuj zawartość pliku skompresowanego do tego katalogu
3. Uruchom jednorazowo `Aki.Server.exe` aby pozwolić mu wygenerować pliki konfiguracyjne dla MPT, a następnie go wyłącz.
4. Przejdź do `user\mods\MPTCoop\config` i otwórz `coopConfig.json`
5. Zmień wartość `externalIP` na adres IP Twojego serwera VPN, a następnie zapisz i zamknij plik

Przykład ze sztuczym adresem IP serwera VPN (**20.20.56.73**):
```json
{
	"protocol": "http",
	"externalIP": "20.20.56.73"
}
```
9. Wróc do głównego katalogu i przejdź do `Aki_Data\Server\configs` a następnie otwórz `http.json`
10. Zmień wartość pola `ip` na Twój adres IP serwera VPN, a nastąpnie zapisz i zamknij plik.

Przykład ze sztuczym adresem IP serwera VPN (**20.20.56.73**):
```json
{
	"ip": "20.20.56.73",
	"port": 6969,
	"webSocketPingDelayMs": 90000,
	"logRequests": true,
	"serverImagePathOverride": {	}
} 
```
11. Uruchom `Aki.Server.exe` i poczekaj chwilę aż skończy się ładować
12. Uruchom `Aki.Launcher.exe` i naciśnij 'Settings'
13. Zmień wartośc w polu `URL` tak aby odzwierciedlała Twój adres IP serwera VPN. Używając przykładu z kroku 5 wartością byłoby: `http://20.20.56.73:6969` (pamiętaj aby usunąc jakiekolwiek slashe `/` na samym końcu URL)

### Klient - Przy użyciu przekierowania portów

1. Pobierz oraz zainstaluj najnowszą wersję MPT
2. Przejdź do katalogu, w którym znajduje się zainstalowany SPT i wypakuj zawartość pliku skompresowanego do tego katalogu
3. Uruchom `Aki.Launcher.exe` i naciśnij 'Settings'
4. Zmień wartośc w polu `URL` tak aby odzwierciedlała Twój publiczny adres IP (WAN). Używając przykładu opisanego w "Host - przy użyciu przekierowania portów" wartością byłoby: `http://70.50.130.200:6969` (pamiętaj aby usunąc jakiekolwiek slashe `/` na samym końcu URL)
5. Jeżeli hostujesz sesję w grze, zezwól na wszystkie połączenie (publiczne oraz prywatne) jeżeli Zapora sieciowa Windows wyświetli takie zapytanie

### Klient - Przy użyciu VPN

1. Pobierz oraz zainstaluj najnowszą wersję MPT
2. Przejdź do katalogu, w którym znajduje się zainstalowany SPT i wypakuj zawartość pliku skompresowanego do tego katalogu
3. Uruchom `Aki.Launcher.exe` i naciśnij 'Settings'
4. In the `URL` field, change it to reflect the hosts VPN IP. Using the example in step 5 it would be: `http://20.20.56.73:6969` (remember to remove any trailing forward slashes `/`)
4. Zmień wartośc w polu `URL` tak aby odzwierciedlała Twój adres IP serwera VPN. Używając przykładu opisanego w "Host - przy użyciu VPN" wartością byłoby: `http://20.20.56.73:6969` (pamiętaj aby usunąc jakiekolwiek slashe `/` na samym końcu URL)
5. Jeżeli hostujesz sesję w grze, zezwól na wszystkie połączenie (publiczne oraz prywatne) jeżeli Zapora sieciowa Windows wyświetli takie zapytanie

## Uznania autorstwa

**Projekt** | **Licencje i uznania**
----------- | -----------------------------------------------------------------------
Aki.Modules | [NCSA](https://dev.sp-tarkov.com/SPT-AKI/Modules/src/branch/master/LICENSE.md) - Za oryginalne łatki, które są nadpisywane dla kompatybilności MPT
SIT         | Nielicencjonowane (MPT bazuje na commicie [9de30d8](https://github.com/stayintarkov/StayInTarkov.Client/blob/9de30d8bab1a4cd5e8bb7bcf5d32539098e97aa6/README.md))
Open.NAT    | [MIT](https://github.com/lontivero/Open.NAT/blob/master/LICENSE) - Za implementacje UPnP
LiteNetLib  | [MIT](https://github.com/RevenantX/LiteNetLib/blob/master/LICENSE.txt) - Za implementacje serwer/klient
