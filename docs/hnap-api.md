# HNAP API — inwentaryzacja
Źródło listy: zanonimizowana odpowiedź `GetDeviceSettingsResponse` uzyskana przez HTTP GET `http://<adres-urzadzenia>/HNAP1`. Urządzenie ogłosiło poniższe 69 akcji. To inwentaryzacja, a nie potwierdzenie działania każdej akcji.
W HNAP nazwy `Get...` zwykle oznaczają odczyt, `Set...` zapis. Akcje `Reboot`, `SetFactoryDefault`, `StartFirmwareDownload`, `Clean...`, `Push...` i `Settrigger...` wymagają szczególnej ostrożności. Na razie nie wykonano żadnej z nich.
## Rdzeń / urządzenie
- Reboot
- SetFactoryDefault
- IsDeviceReady
- Login
- GetMultipleHNAPs
- SetMultipleHNAPs
- GetDeviceSettings
- SetDeviceSettings
- GetDeviceSettings2
- SetDeviceSettings2
- GetGroupSettings
- SetGroupSettings
- GetSystemLogs
- CleanSystemLogs
- GetModuleOPStatus
- SetModuleOPStatus
- GetModuleProfile
- SetModuleProfile
- GetModuleSOAPActions
## Czas i harmonogram
- GetTimeSettings
- SetTimeSettings
- GetScheduleSettings
- SetScheduleSettings
- GetRecursiveSchedule
- SetRecursiveSchedule
## DCH / zdarzenia
- GetDCHPolicy
- SetDCHPolicy
- PushDCHEvent
- GetEventSupportList
- GetActionSupportList
## Firmware
- GetFirmwareStatus
- GetFirmwareValidation
- StartFirmwareDownload
- PollingFirmwareDownload
## Internet / Wi-Fi
- SettriggerADIC
- GetInternetSettings
- GetCurrentInternetStatus
- GetWLanRadios
- SetTriggerWirelessSiteSurvey
- GetSiteSurvey
- SetAPClientSettings
- GetAPClientSettings
## Pomiar energii
- GetPowerMeterSettings
- SetPowerMeterSettings
- GetPowerMeterSettings2
- GetCurrentPowerConsumption
- GetPMWarningThreshold
- SetPMWarningThreshold
- GetPURSupportedTypes
- GetPURecords
- GetPowerMeterLogs
- SetPowerMeterLogs
- CleanPowerMeterLogs
## Temperatura
- GetTempMonitorSettings
- SetTempMonitorSettings
- GetTempMonitorSettings2
- GetCurrentTemperature
- GetTempMonitorLogs
- SetTempMonitorLogs
- CleanTempMonitorLogs
## Gniazdko
- GetSocketSettings
- SetSocketSettings
- GetSocketSettings2
- GetSocketLogs
- CleanSocketLogs
## mydlink
- GetmydlinkSupportStatus
- GetmydlinkRegInfo
- SetmydlinkReg
- SetmydlinkUnregistration
## Następny etap odczytów
Pojedynczo pobrać schematy i odpowiedzi dla bezpiecznych akcji `Get...`, zaczynając od gotowości, profili modułów, ustawień gniazdka, pomiaru, temperatury, czasu, harmonogramów i sieci. Przed wysłaniem SOAP POST ustalić wymagane nagłówki HNAP, uwierzytelnianie, nonce/haszowanie i dokładny format XML. Nie odgadywać danych logowania ani nie wysyłać zapisów.
