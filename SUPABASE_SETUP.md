# Nastavení Supabase pro Gomoku Online

Tento návod tě provede kompletním nastavením Supabase pro real-time multiplayer hru.

## 1. Vytvoření účtu a projektu

1. Jdi na [supabase.com](https://supabase.com)
2. Klikni na **Start your project** a vytvoř účet (můžeš použít GitHub)
3. Po přihlášení klikni na **New project**
4. Vyber organizaci a zadej:
   - **Name**: `gomoku-online` (nebo libovolný název)
   - **Database Password**: Vygeneruj silné heslo
   - **Region**: Vyber nejbližší region (pro ČR: `Central Europe (Frankfurt)`)
5. Klikni na **Create new project**
6. Počkej na vytvoření (trvá cca 1-2 minuty)

## 2. Získání API credentials

1. V projektu klikni na ikonu **Settings** (vlevo dole)
2. Jdi do **API** sekce
3. Najdi tyto hodnoty:
   - **Project URL**: `https://xxxx.supabase.co`
   - **anon public**: `eyJhbGciOiJIUzI1NiIs...`

4. Zkopíruj obě hodnoty - budouš je potřebovat v aplikaci

## 3. Povolení Realtime

Realtime je potřeba povolit pro synchronizaci tahů mezi hráči:

### Možnost A: Přes Dashboard (doporučeno)

1. V Supabase dashboardu jdi do **Database** (vlevo)
2. Klikni na **Replication**
3. V sekci **Source** klikni na **Realtime**
4. Zapni **Realtime** přepínač
5. Klikni na **Save**

### Možnost B: Přes SQL Editor

1. Jdi do **SQL Editor** (vlevo)
2. Klikni na **New query**
3. Vlož tento SQL kód:

```sql
-- Povolení realtime pro všechny tabulky
begin;
  -- Povolení realtime extension
  drop publication if exists supabase_realtime;
  create publication supabase_realtime;
commit;

-- Přidání všech tabulek do realtime
alter publication supabase_realtime add table all;
```

4. Klikni na **Run**

## 4. Nastavení Row Level Security (RLS)

Pro bezpečnost doporučujeme nastavit RLS:

1. Jdi do **Authentication** > **Policies**
2. Pokud máš tabulky, nastav pro ně politiky:
   - **INSERT**: `true` (povolit vkládání)
   - **SELECT**: `true` (povolit čtení)
   - **UPDATE**: `true` (povolit úpravy)

## 5. Testování připojení

1. Otevři svou nasazenou aplikaci na Render.com
2. Zadej Supabase URL a API klíč
3. Klikni na **Uložit a připojit**
4. Otevři browser console (F12) a zkontroluj, že není chyba
5. Měl bys vidět "Realtime status: SUBSCRIBED"

## 6. Řešení problémů

### Chyba: "Cannot connect to Supabase"
- Zkontroluj, že URL začíná `https://`
- Ověř, že používáš **anon public** klíč
- Zkontroluj, že projekt je aktivní v Supabase dashboardu

### Realtime nefunguje
- Ověř, že Realtime je povolený v Database > Replication
- Zkontroluj browser console pro chybové hlášky
- Zkus obnovit stránku (F5)

### Pomalé připojení
- Zkontroluj, že jsi vybral nejbližší region
- Ověř rychlost internetového připojení

## 7. Bezplatné limity

Supabase Free tier (zdarma):
- **Database**: 500 MB
- **Realtime**: Neomezené připojení
- **API volání**: 100 000 za den
- **Bandwidth**: 2 GB za měsíc

Pro tuto hru je free tier více než dostačující!

## 8. Užitečné odkazy

- [Supabase dokumentace](https://supabase.com/docs)
- [Realtime dokumentace](https://supabase.com/docs/guides/realtime)
- [JavaScript Client](https://supabase.com/docs/reference/javascript/introduction)

---

**Hotovo!** 🎉 Nyní máš plně funkční backend pro svou Gomoku hru.
