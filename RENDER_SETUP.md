# Nastavení automatického deploymentu na Render.com

Tento návod tě provede nastavením automatického deploymentu přes GitHub Actions.

## 1. Získání Render API klíče

1. Jdi na [dashboard.render.com](https://dashboard.render.com)
2. Klikni na svůj avatar (vpravo nahoře) > **Account Settings**
3. V sekci **API Keys** klikni na **Create API Key**
4. Zkopíruj vygenerovaný klíč

## 2. Získání Service ID

1. V Render dashboardu otevři svůj static site
2. V URL najdeš Service ID (např. `srv-abc123`)
3. Nebo jdi do **Settings** > kopíruj **Service Name**

## 3. Nastavení GitHub Secrets

1. Otevři svůj GitHub repozitář
2. Jdi do **Settings** > **Secrets and variables** > **Actions**
3. Klikni na **New repository secret**
4. Přidej tyto secrets:

### RENDER_API_KEY
- **Name**: `RENDER_API_KEY`
- **Secret**: Tvůj API klíč z kroku 1

### RENDER_SERVICE_ID
- **Name**: `RENDER_SERVICE_ID`
- **Secret**: Tvůj Service ID z kroku 2

## 4. Testování

1. Udělej změnu v kódu
2. Commitni a pushni do `main` větve
3. Jdi do **Actions** tab v GitHub
4. Měl bys vidět běžící workflow
5. Po úspěšném dokončení se aplikace automaticky nasadí na Render

## Manuální deployment

Pokud nechceš používat GitHub Actions:

1. Render automaticky deployuje při pushi do GitHub (pokud je repozitář připojen)
2. Nebo můžeš kliknout na **Manual Deploy** v Render dashboardu

## Řešení problémů

### Workflow selže
- Zkontroluj, že secrets jsou správně nastaveny
- Ověř, že Service ID je správný
- Zkontroluj logy v GitHub Actions

### Aplikace se neaktualizuje
- Zkontroluj, že změny jsou v `main` větvi
- V Render dashboardu zkontroluj **Deploy** logy
- Zkus **Clear Build Cache & Deploy**
