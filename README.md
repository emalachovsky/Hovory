# Hovory - CRM EnergyPartners PWA

Moderná web aplikácia na správu hovorov a kontaktov priamo z Google Sheets.

## 📋 Obsah

Aplikácia automaticky načítava dáta z vášho Google Sheets dokumentu a zobrazuje ich v prehľadnom formáte.

**Používané stĺpce:**
- **A** - Názov firmy
- **B** - Meno kontaktnej osoby
- **C** - Telefón
- **D** - Telefón 2
- **E** - Stav (status)
- **G** - Poznámka
- **H** - Zaradenie (sort)
- **I** - Ďalší krok (next action)

## 🚀 Ako nasadiť

### 1. Na GitHub Pages

1. Vytvor nový repozitár (alebo použij existujúci) s názvom `Hovory`
2. Skopíruj tieto súbory do koreňa repozitára:
   - `index.html`
   - `manifest.json`
   - `sw.js`
   - `README.md` (voliteľne)

3. V nastaveniach GitHub repozitára aktivuj **GitHub Pages** s vetvou `main` (alebo ktorú máš)

4. Aplikácia bude dostupná na: `https://tvoje-uzivatelske-meno.github.io/Hovory/`

### 2. Lokálne testovanie

Aplikáciu môžeš testovať lokálne:

```bash
# Spusti lokálny server (Python 3)
python -m http.server 8000

# Potom otvor v prehliadači
# http://localhost:8000/index.html
```

## ⚙️ Konfigurácia

Hlavné konfiguračné parametre v `index.html` (riadky 210-213):

```javascript
const SHEET_ID = '1yjOl0-yYSOI2lTCxflBfZWiohGkQmJkMVJLIlxGBUdU';
const SHEET_GID = '356854980';  // Skrytý (hidden sheet ID)
const API_KEY = 'AIzaSyDRccaAkI4j_NCHTxw3LbJpl2j1IBpSAN8';
```

**Ako získať vlastné ID:**
1. Google Sheet ID: `https://docs.google.com/spreadsheets/d/**SHEET_ID**/edit`
2. GID (sheet ID): Na spodku tabuľky skrytá ID
3. API key: [Google Cloud Console](https://console.cloud.google.com/)

## 🎨 Funkčnosti

### Všeobecne
- ✅ Automatické načítanie dát z Google Sheets
- ✅ Live aktualizácia každých 5 minút
- ✅ Tlačidlo Refresh na manuálnu obnovitu
- ✅ Hľadanie podľa názvu firmy alebo osoby
- ✅ Offline funkčnosť (cached data)
- ✅ PWA - inštalácia ako aplikácia

### Detaily karty
- Názov spoločnosti
- Kontaktná osoba
- Telefón (klikacia ikona na volanie)
- Status
- Poznámky
- Ďalší krok

### Detailný pohľad
- Klikni na kartu na zobrazenie úplných detailov
- Všetky telefónne čísla sú klikacia na volanie
- Rozklinutí detaily sa zobrazujú v paneli od spodu

## 📱 Ako používať

### Hľadanie
- Napíš názov spoločnosti alebo osoby do poľa hľadania
- Aplikácia filtruje výsledky v reálnom čase

### Volanie
- Klikni na 📱 ikonku na karte - otvorí sa volanie (na iPhonu)
- V detailovom pohľade klikni na telefónne číslo

### Refresh
- Klikni na ⟳ v pravom hornom rohu na obnovení dát
- Aplikácia si vyberá nové dáta z Google Sheets

### Inštalácia ako aplikácia
- **iOS**: Klikni na "Zdieľať" → "Pridať na domovskú obrazovku"
- **Android**: Klikni na "Možnosti" (3 bodky) → "Inštalovať aplikáciu"

## 🔐 Bezpečnosť API

Tvoj API kľúč je viditeľný v `index.html`. Ak chceš zvýšiť bezpečnosť:

1. Vytvor nový API kľúč v Google Cloud Console
2. Obmedz ho iba na Google Sheets API
3. Postav backend proxy server, ktorý bude API kľúč ukrývať

## 🔄 Dátová synchronizácia

- Aplikácia načítava dáta pri spustení
- Dáta sa automaticky obnovia každých **5 minút**
- Kliknutí na "Refresh" okamžite načíta nové dáta
- Offline režim zobrazuje posledné vyčítané dáta

## 📊 Formát dát v Google Sheets

Tabuľka by mala mať strukúru:

| A | B | C | D | E | F | G | H | I |
|---|---|---|---|---|---|---|---|---|
| Názov firmy | Meno | Tel | Tel 2 | Stav | - | Poznámka | Zaradenie | Ďalší krok |
| Crown House | František | 0911 727 220 | 0907 108 829 | Analýza | | ... | | ... |

## ⚠️ Problémy

### "Chyba pri načítaní - API Error"
- Skontroluj, či je API kľúč správny
- Skontroluj, či je SHEET_ID správny
- Skontroluj, či má API kľúč prístup k Google Sheets

### Aplikácia sa nenačítava
- Otvri Developer Tools (F12)
- Pozri si "Console" tab na chyby
- Skontroluj internetové pripojenie

### Offline režim nefunguje
- Prvýkrát aplikáciu otvori s internetom
- Service Worker si tak vyčíta súbory do cache-u
- Potom bude fungovať offline (len s posledným cache-om)

## 📝 Licencia

Voľne dostupné na použitie a úpravu.

## 💡 Tipy

1. Môžeš si aplikáciu inštalovať ako natívnu aplikáciu na mobile
2. Aplikácia funguje offline s posledným vyčítaným obsahom
3. Dáta sa synchronizujú automaticky každých 5 minút
4. Všetky telefónne čísla sú klikacia na volanie

---

**Vytvorenosť:** 2026
**Kompatibilita:** iOS, Android, Windows, macOS (akýkoľvek moderný prehliadač)
