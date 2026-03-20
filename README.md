# 🎮 Gomoku - Piškvorky Online

Online multiplayer hra piškvorky (Gomoku) postavená na moderních webových technologiích s real-time synchronizací přes Supabase.

![Gomoku Preview](https://img.shields.io/badge/Gomoku-Online%20Multiplayer-green)
![Supabase](https://img.shields.io/badge/Powered%20by-Supabase-3ECF8E)
![Render](https://img.shields.io/badge/Deployed%20on-Render-46E3B7)

## ✨ Funkce

- 🎯 **10x10 herní pole** - klasické piškvorky
- ⚡ **Real-time multiplayer** - okamžitá synchronizace tahů
- 🔗 **Sdílení přes URL** - jednoduché pozvání soupeře
- 📜 **Historie tahů** - přehled všech provedených tahů
- 🏆 **Detekce vítěze** - automatické rozpoznání 5 v řadě
- 🎨 **Moderní design** - dark theme s pěkným UI
- 📱 **Responzivní** - funguje na mobilu i desktopu

## 🚀 Rychlý start

### 1. Vytvoření Supabase projektu

1. Jdi na [supabase.com](https://supabase.com) a vytvoř účet
2. Vytvoř nový projekt
3. V Project Settings > API najdi:
   - **Project URL** (např. `https://abc123.supabase.co`)
   - **anon public** API klíč

### 2. Povolení Realtime

V Supabase dashboardu:
1. Jdi do **Database** > **Replication**
2. Zapni **Realtime** pro všechny tabulky (nebo alespoň pro `broadcast`)

### 3. Nasazení na Render.com

#### Možnost A: Přes GitHub (doporučeno)

1. Forkni tento repozitář na svůj GitHub
2. Jdi na [render.com](https://render.com) a vytvoř účet
3. Klikni na **New** > **Static Site**
4. Připoj svůj GitHub repozitář
5. Klikni na **Create Static Site**
6. Po nasazení otevři URL a nastav Supabase credentials

#### Možnost B: Přes ZIP soubor

1. Stáhni tento repozitář jako ZIP
2. Na Render.com klikni na **New** > **Static Site**
3. Nahraj ZIP soubor
4. Klikni na **Deploy**

### 4. Konfigurace hry

Po prvním otevření aplikace:
1. Zadej svůj **Supabase URL**
2. Zadej svůj **anon public API klíč**
3. Klikni na **Uložit a připojit**
4. Nastavení se uloží do localStorage pro budoucí návštěvy

## 🎯 Jak hrát

1. **Otevři hru** - každý hráč otevře stejnou URL
2. **První hráč** začíná s křížkem (❌)
3. **Klikni na pole** pro provedení tahu
4. **Cíl**: Spoj 5 symbolů v řadě (horizontálně, vertikálně nebo diagonálně)
5. **Sdílej URL** pro pozvání dalšího hráče

## 🏗️ Struktura projektu

```
gomoku-render/
├── index.html          # Hlavní HTML soubor s hrou
├── render.yaml         # Konfigurace pro Render.com
└── README.md          # Tento soubor
```

## 🔧 Technologie

- **Frontend**: Vanilla HTML/CSS/JS
- **Styling**: Tailwind CSS (CDN)
- **Backend**: Supabase Realtime
- **Hosting**: Render.com (Static Site)

## 📝 Poznámky

- **Bez serveru**: Hra používá pouze Supabase Realtime pro synchronizaci
- **URL místnosti**: Každá hra má unikátní room ID v URL (`?room=xyz`)
- **LocalStorage**: Supabase credentials se ukládají lokálně v prohlížeči
- **Zdarma**: Celé řešení lze provozovat zdarma (Supabase free tier + Render free tier)

## 🐛 Řešení problémů

### Hra se nesynchronizuje
- Zkontroluj, že oba hráči mají správné Supabase credentials
- Ověř, že Realtime je povolený v Supabase dashboardu
- Zkus obnovit stránku (F5)

### Nepřipojuje se k Supabase
- Zkontroluj URL (musí začínat `https://`)
- Ověř, že používáš **anon public** klíč, ne service_role
- Zkontroluj browser console pro chybové hlášky

## 📄 Licence

MIT License - volně použitelné a upravitelné.

## 🤝 Příspěvky

Pull requesty vítány! Pro větší změny prosím nejprve otevři issue.

---

**Vytvořeno s ❤️ pro českou komunitu** 🇨🇿
