# Stage- & vacaturetracker

Persoonlijke tracker voor stageplekken (jaar 3 + afstudeerstage), bijbanen en vacatures in forensische en biomedische labs. Statische web-app: één `index.html`, geen server of build nodig.

## Functies
- **Overzicht** – organisatie, functie, soort, sector, locatie, reistijd (rood boven je maximum), deadline, contact, link; zoeken, filteren, sorteren.
- **Status** – bord met kolommen Geïnteresseerd → Gesolliciteerd → Gesprek → Aangenomen / Afgewezen (slepen). Statushistorie per plek. Bij *Gesolliciteerd* wordt automatisch een follow-up over 10 dagen gezet.
- **Herinneringen** – lijst van deadlines en follow-ups; export als `.ics` (met meldingen 3 en 1 dag vooraf) om in Google Agenda te importeren.
- **Nieuwe vondsten** – inbox die `data/gevonden.json` leest (gevuld door de wekelijkse scan). Toevoegen of negeren.
- **Bronnen** – lijst van sites/instellingen die gescand worden.
- **Documenten** – per sollicitatie welke cv- en motivatiebriefversie is gebruikt.
- **Data** – opgeslagen in de browser (localStorage). Export/import als JSON (back-up, ander apparaat) en export als CSV (Excel/Sheets).

## Gebruiken
1. Zet de bestanden in een GitHub-repo.
2. *Settings → Pages → Deploy from branch* → `main` / root.
3. Open `https://<gebruikersnaam>.github.io/<repo>/`.

Lokaal openen (`index.html` dubbelklikken) werkt ook, alleen laadt de inbox dan niet automatisch — gebruik *Scanbestand handmatig laden…*.

> Let op: als de repo publiek is, is `data/gevonden.json` ook publiek. Je eigen sollicitaties staan alleen in je browser, niet in de repo.

## Formaat `data/gevonden.json`
```json
{
  "bijgewerkt": "2026-11-21",
  "vondsten": [
    {
      "organisatie": "Voorbeeldlab",
      "functie": "Stagiair DNA-analyse",
      "soort": "Stage jaar 3",
      "sector": "Forensisch",
      "locatie": "Den Haag",
      "reistijd": 85,
      "deadline": "2026-12-15",
      "link": "https://...",
      "notities": "Korte samenvatting",
      "gevondenOp": "2026-11-21"
    }
  ]
}
```
`soort`: `Stage jaar 3`, `Afstudeerstage`, `Bijbaan`, `Vacature (na afstuderen)`, `Open sollicitatie`.
`sector`: `Forensisch`, `Ziekenhuislab`, `Onderzoeksinstituut`, `Universiteit`, `Industrie / farma`, `Overheid`, `Overig`.
