# Dziennik testów

## 2026-10-04 — wstępny odczyt HNAP

- Połączenie: lokalny adres urządzenia (zanonimizowany w repozytorium).
- Metoda: HTTP GET `/HNAP1`.
- Wynik: HTTP 200, `text/xml; charset=utf-8`.
- SOAP: `GetDeviceSettingsResponse`; `GetDeviceSettingsResult=OK`.
- Zebrano: model, wersję firmware/HNAP, moduły i 69 nazw akcji SOAP.
- Zmiany stanu urządzenia: brak.
- MAC i konkretny adres IP usunięte z publicznego zapisu.

## 2026-10-04 — uwierzytelnienie i odczyt stanu

- Logowanie HNAP dwuetapowe: PASS. Wyzwanie zwróciło `LoginResult=OK`; drugi krok zwrócił `LoginResult=success`.
- Cookie `uid` musi być dodane do sesji HTTP i zachowane dla kolejnych żądań.
- `HNAP_AUTH` dla logowania i akcji: HMAC-MD5 kluczem `PrivateKey`, z timestampem Unix w sekundach i cytowanym adresem SOAPAction.
- `GetDeviceSettings`: PASS, HTTP 200; zawiera model, wersje i listę akcji. Surowej odpowiedzi nie zapisano, bo zawiera MAC urządzenia.
- `GetSocketSettings`: PASS, HTTP 200; `GetSocketSettingsResult=OK`, `ModuleID=1`, `OPStatus=false` w chwili testu.
- Zanonimizowana odpowiedź: [captures/get-socket-settings.xml](captures/get-socket-settings.xml).
- Szczegóły uwierzytelnienia: [authentication.md](authentication.md).
- Wykonano wyłącznie odczyty; nie zmieniano stanu ani konfiguracji urządzenia.

## Następne kroki

1. Testować pojedynczo kolejne odczyty SOAP `Get...` i zachowywać zanonimizowane odpowiedzi.
2. Opracować interfejs i zapis sparowanego urządzenia w aplikacji Android.
3. Polecenia `Set...`, reset, restart, czyszczenie logów i firmware wymagają osobnego uzgodnienia.
