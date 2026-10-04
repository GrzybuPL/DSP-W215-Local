# D-Link DSP-W215 Local
Projekt badawczy dla lokalnego API HNAP gniazdka D-Link DSP-W215. Celem jest najpierw udokumentowanie zachowania konkretnego egzemplarza, a później stworzenie aplikacji Android działającej lokalnie (także przez VPN do sieci domowej).
## Stan prac
- Urządzenie odpowiada pod lokalnym adresem `http://<adres-urzadzenia>/HNAP1`.
- Odczyt HTTP GET zwraca SOAP `GetDeviceSettingsResponse` z wynikiem `OK`.
- Urządzenie zgłosiło DSP-W215, hardware B1, firmware 2.02, HNAP 0114 oraz 69 akcji HNAP.
- Inwentaryzacja akcji: [docs/hnap-api.md](docs/hnap-api.md).
- Dane badanego modelu: [docs/device.md](docs/device.md).
- Dziennik testów: [docs/test-log.md](docs/test-log.md).
## Zasady badania
1. Zapisywać każde żądanie i odpowiedź oraz datę, adres urządzenia i wynik.
2. Najpierw wykonywać odczyty `Get...` oraz testy bez wpływu na konfigurację.
3. Nie wywoływać `Set...`, resetu, restartu, czyszczenia logów ani aktualizacji firmware bez osobnego uzgodnienia.
4. Nie umieszczać haseł Wi-Fi, haseł urządzenia ani tokenów w repozytorium.
5. Unikalny MAC urządzenia i lokalny adres IP są redagowane z publicznych materiałów.
## Status
To wczesny etap reverse engineeringu. Lista HNAP pochodzi z odpowiedzi urządzenia i nie stanowi potwierdzenia, że każda akcja działa lub jest bezpieczna. Na razie nie opublikowano kodu aplikacji.
## Licencja
Repozytorium nie ma jeszcze wybranej licencji. Publiczna widoczność pozwala przeglądać materiały, ale nie przyznaje dodatkowych praw do ich ponownego użycia.
