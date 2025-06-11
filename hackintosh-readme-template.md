# macOS Sequoia na PC - Konfiguracja OpenCore

![macOS Version](https://img.shields.io/badge/macOS-Sequoia%2015.x-brightgreen.svg)
![OpenCore Version](https://img.shields.io/badge/OpenCore-1.0.2-blue.svg)
![Build Status](https://img.shields.io/badge/build-stable-green.svg)

## 📋 Spis treści

- [O tym repozytorium](#o-tym-repozytorium)
- [Specyfikacja sprzętowa](#specyfikacja-sprzętowa)
- [Co działa](#co-działa)
- [Co nie działa](#co-nie-działa)
- [Zrzuty ekranu](#zrzuty-ekranu)
- [Wymagania wstępne](#wymagania-wstępne)
- [Instalacja](#instalacja)
- [Konfiguracja BIOS/UEFI](#konfiguracja-biosuefi)
- [Aktualizacja](#aktualizacja)
- [Rozwiązywanie problemów](#rozwiązywanie-problemów)
- [Linki przydatne](#linki-przydatne)
- [Podziękowania](#podziękowania)
- [Disclaimer](#disclaimer)

## 🖥️ O tym repozytorium

Ten config OpenCore został stworzony i przetestowany dla instalacji macOS Sequoia (15.x) na komputerze PC. Konfiguracja jest w pełni funkcjonalna i może służyć jako punkt wyjścia dla podobnych systemów.

**⚠️ WAŻNE**: Ten config został przygotowany dla konkretnej konfiguracji sprzętowej. Nie kopiuj go bezpośrednio - musisz go dostosować do Twojego sprzętu!

## 🔧 Specyfikacja sprzętowa

| Komponent | Model |
|-----------|-------|
| **Motherboard** | [Nazwa płyty głównej] |
| **CPU** | [Procesor] |
| **GPU** | [Karta graficzna] |
| **RAM** | [Ilość i typ pamięci] |
| **Storage** | [Dysk/dyski] |
| **Audio** | [Kodek audio] |
| **Ethernet** | [Kontroler sieci] |
| **WiFi** | [Karta WiFi] |
| **Bluetooth** | [Kontroler Bluetooth] |

## ✅ Co działa

- [x] **Uruchamianie systemu** - Pełne wsparcie dla OpenCore bootloader
- [x] **CPU** - Pełne wsparcie z Power Management
- [x] **iGPU/dGPU** - Akceleracja sprzętowa, Metal, HEVC
- [x] **Audio** - Wszystkie wyjścia audio (wbudowane, HDMI/DP)
- [x] **Ethernet** - Połączenie przewodowe
- [x] **WiFi** - Bezprzewodowa sieć
- [x] **Bluetooth** - Wszystkie funkcje Bluetooth
- [x] **USB** - Wszystkie porty USB (2.0, 3.0, 3.1, USB-C)
- [x] **Sleep/Wake** - Tryb uśpienia i wybudzanie
- [x] **iServices** - iMessage, FaceTime, iCloud, Handoff
- [x] **NVRAM** - Natywne wsparcie NVRAM
- [x] **FileVault 2** - Szyfrowanie dysku

## ❌ Co nie działa

- [ ] **[Przykład]** - AirDrop (wymaga kompatybilnej karty WiFi)

## 📸 Zrzuty ekranu

*[Dodaj tutaj zrzuty ekranu z działającym systemem]*

## 📋 Wymagania wstępne

- Komputer PC z kompatybilnym sprzętem
- Pendrive USB 3.0 (minimum 16GB)
- Dostęp do prawdziwego Maca lub istniejącego Hackintosh do utworzenia installera
- Podstawowa znajomość pracy z terminalem
- Kopia zapasowa ważnych danych

## 🚀 Instalacja

### 1. Przygotowanie bootable USB

```bash
# Ściągnij macOS Sequoia
softwareupdate --fetch-full-installer --full-installer-version 15.0

# Stwórz bootable USB (zastąp MyVolume nazwą swojego pendrive)
sudo /Applications/Install\ macOS\ Sequoia.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume
```

### 2. Przygotowanie EFI

1. Pobierz najnowszą wersję [OpenCore](https://github.com/acidanthera/OpenCorePkg/releases)
2. Skopiuj zawartość folderu `EFI` z tego repozytorium
3. Umieść folder `EFI` na partycji EFI pendrive

### 3. Generowanie SMBIOS

Użyj [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) do wygenerowania unikalnych wartości SMBIOS:

```bash
python GenSMBIOS.py
```

**WAŻNE**: Nie używaj wartości SMBIOS z tego config.plist - wygeneruj własne!

### 4. Instalacja

1. Uruchom komputer z pendrive USB
2. Wybierz "Install macOS Sequoia"
3. Postępuj zgodnie z instrukcjami instalatora
4. Po instalacji skopiuj EFI na dysk twardy

## ⚙️ Konfiguracja BIOS/UEFI

### Wyłącz:
- Secure Boot
- Intel SGX
- Intel Platform Trust Technology (PTT)
- CFG Lock (jeśli dostępne)

### Włącz:
- UEFI Boot Mode
- Above 4G Decoding
- Hyper-Threading
- EHCI/XHCI Hand-off
- OS type: Windows 8.1/10 UEFI Mode

### Ustaw:
- SATA Mode: AHCI
- Boot Priority: USB first

## 🔄 Aktualizacja

### OpenCore
1. Pobierz najnowszą wersję OpenCore
2. Zaktualizuj pliki EFI/BOOT/BOOTx64.efi i EFI/OC/OpenCore.efi
3. Porównaj swój config.plist z nowym sample.plist
4. Zaktualizuj kexty do najnowszych wersji

### macOS
Aktualizacje macOS można instalować normalnie przez System Preferences.

## 🛠️ Rozwiązywanie problemów

### System nie uruchamia się
- Sprawdź czy BIOS jest poprawnie skonfigurowany
- Upewnij się że używasz poprawnych kextów dla swojego sprzętu
- Włącz debug w OpenCore i sprawdź logi

### Brak dźwięku
- Sprawdź czy używasz poprawnego layout-id dla swojego kodeka
- Upewnij się że AppleALC jest poprawnie skonfigurowany

### iServices nie działają
- Wygeneruj nowe wartości SMBIOS
- Sprawdź czy En0 jest poprawnie skonfigurowany

## 🔗 Linki przydatne

- [Oficjalny przewodnik OpenCore](https://dortania.github.io/OpenCore-Install-Guide/)
- [r/hackintosh](https://www.reddit.com/r/hackintosh/)
- [Kext repo](https://kexts.goldfish64.com/)
- [OpenCore Sanity Checker](https://opencore.slowgeek.com/)

## 🙏 Podziękowania

- [Acidanthera](https://github.com/acidanthera) za OpenCore
- [Dortania](https://github.com/dortania) za przewodniki
- Społeczność Hackintosh za ciągłe wsparcie

## ⚖️ Disclaimer

**UWAGA PRAWNA**: Ten projekt służy wyłącznie celom edukacyjnym. Użycie macOS na sprzęcie innych niż Apple może naruszać Umowę Licencyjną Użytkownika Końcowego (EULA) firmy Apple. Użytkowanie na własną odpowiedzialność.

- Autor nie ponosi odpowiedzialności za jakiekolwiek szkody powstałe w wyniku użycia tego config
- To repozytorium nie zawiera żadnych plików zastrzeżonych przez Apple
- Wspieraj Apple kupując oryginalne produkty
- Ten projekt nie służy zyskom komercyjnym

---

**💡 Wskazówka**: Jeśli ten config Ci pomógł, rozważ zostawienie gwiazdki ⭐ na GitHub!

## 📄 Licencja

Ten projekt jest udostępniony na licencji MIT. Zobacz [LICENSE](LICENSE) aby uzyskać więcej informacji.