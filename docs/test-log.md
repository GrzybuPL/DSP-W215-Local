# Dziennik testów
## 2026-10-04 — wstępny odczyt HNAP
- Połączenie: lokalny adres urządzenia (zanonimizowany w repozytorium).
- Metoda: HTTP GET `/HNAP1`.
- Wynik: HTTP 200, `text/xml; charset=utf-8`.
- SOAP: `GetDeviceSettingsResponse`; `GetDeviceSettingsResult=OK`.
- Zebrano: model, wersję firmware/HNAP, moduły i 69 nazw akcji SOAP.
- Zmiany stanu urządzenia: brak.
- MAC i konkretny adres IP usunięte z publicznego zapisu.
## Następne kroki
1. Ustalić format nagłówków i sposób uwierzytelniania HNAP.
2. Pojedynczo wykonać wybrane odczyty SOAP `Get...` i zachować zanonimizowane odpowiedzi.
3. Sprawdzić parowanie i konfigurację Wi-Fi dopiero po poznaniu bezpiecznego formatu żądań.
4. Polecenia `Set...`, reset, restart, czyszczenie logów i firmware wymagają osobnego uzgodnienia.
