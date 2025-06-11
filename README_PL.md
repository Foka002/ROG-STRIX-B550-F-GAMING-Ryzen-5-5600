# 💻 Hackintosh: macOS na ASUS ROG Strix B550-F Gaming (Ryzen 5 5600 + RX 470/570)

![macOS Version](https://img.shields.io/badge/macOS-Sequoia%2015.x-brightgreen.svg)
![OpenCore Version](https://img.shields.io/badge/OpenCore-1.0.4-blue.svg)
![Build Status](https://img.shields.io/badge/build-stable-green.svg)

## 🖥️ O tym repozytorium

Ten config OpenCore został stworzony i przetestowany dla instalacji macOS Sequoia (15.x) na komputerze PC. Konfiguracja jest w pełni funkcjonalna i może służyć jako punkt wyjścia dla podobnych systemów.

**⚠️ WAŻNE**: Ten config został przygotowany dla konkretnej konfiguracji sprzętowej. Nie kopiuj go bezpośrednio - musisz go dostosować do Twojego sprzętu!

## 🔧 Specyfikacja sprzętowa

| Komponent | Model |
|-----------|-------|
| **Motherboard** | Asus ROG Strix B550-F GAMING |
| **CPU** | AMD Ryzen 5 5600 |
| **GPU** | ASUS RX 470 Mining 4GB (Flashed RX 570 BIOS)
| **GPU2** | ASUS RTX 3060 Ti 8GB
| **RAM** | 32 GB Kingston Beast 3733Mhz DDR4 |
| **Storage** | Goodram CX-400 1TB GB SSD |
| **Audio** | Integrated ALCS1220A |
| **Ethernet** | 1 x Intel® 2.5Gb Ethernet |
| **Bluetooth** | Baseus BA04 USB Dongle |

## ✅ Co działa

- [x] **Uruchamianie systemu** - Pełne wsparcie dla OpenCore bootloader
- [x] **CPU** 
- [x] **GPU1**  - GPU2 musi być wyłączone
- [x] **Audio** - Internal Speakers - innych wyjść nie testowałem
- [x] **Ethernet** - Połączenie przewodowe
- [x] **Bluetooth** 
- [x] **USB** - Wszystkie porty USB (2.0, 3.0, 3.1, USB-C)
- [x] **Sleep/Wake** - Tryb uśpienia i wybudzanie
- [x] **iServices** - nie testowane


## ❌ Co nie działa

Brak czasu na pełną walidację sprzętu

## 📸 Zrzuty ekranu

## ⚙️ Konfiguracja BIOS/UEFI

### Wyłącz:
- CFG Lock

### Włącz:
- UEFI Boot Mode
- Above 4G Decoding
- Hyper-Threading
- EHCI/XHCI Hand-off
- Resize Bar
### Ustaw:
- SATA Mode: AHCI
- Boot Priority: USB first

## 🛠️ Rozwiązywanie problemów

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
