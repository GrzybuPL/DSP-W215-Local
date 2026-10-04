# Badane urządzenie
| Pole | Wartość |
|---|---|
| Producent | D-Link |
| Model | DSP-W215 |
| Wersja sprzętowa | B1 |
| Firmware zgłoszony przez HNAP | 2.02 |
| HNAP | 0114 |
| MAC | zanonimizowany w publicznej kopii |
| URL HNAP | `http://<adres-urzadzenia>/HNAP1` |
| URL prezentacyjny | `http://dsp.local` |
| Tryb dostępu | lokalny awaryjny AP; planowany również VPN do LAN |
## Odpowiedź urządzenia
Odczyt HTTP GET `/HNAP1` zwrócił HTTP 200 i SOAP `GetDeviceSettingsResponse` z `GetDeviceSettingsResult=OK`. Urządzenie zgłosiło trzy moduły: `Smart Plug` i dwa wpisy `Electrical Sensor`, oraz 69 nazw akcji SOAP/HNAP. Sama obecność akcji na liście nie potwierdza, że jest aktywna lub bezpieczna do wywołania.
Dokładny adres LAN i unikalny MAC zostały pominięte z publicznej dokumentacji. Próbka odpowiedzi została zanonimizowana przed publikacją.
## Dane do uzupełnienia
- dokładny wariant firmware (pełny numer kompilacji z panelu),
- sposób przejścia do trybu awaryjnego i warunki Wi-Fi AP,
- metoda uwierzytelnienia HNAP i jej ograniczenia,
- zachowanie po przejściu gniazdka do domowej sieci Wi-Fi.
Nie zapisywać tu kodów parowania, haseł ani sekretów.
