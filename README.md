# Stage- & vacaturetracker

Persoonlijke tracker voor stageplekken (jaar 3 + afstudeerstage), bijbanen en vacatures in forensische en biomedische labs. Statische web-app: één `index.html`, geen server of build nodig.

## Functies
Indeling als een mailprogramma: mappen links, lijst in het midden, leesvenster rechts.

- **Mappen per status**: Nieuw (scanvondsten, vet = ongelezen), Interesse, Verstuurd, Gesprek, Resultaat, Genegeerd, Alles. Sleep een plek op een map om de status te wijzigen.
- **Labels** per soort: Stage jaar 3, Afstudeerstage, Bijbaan, Vacature, Open sollicitatie.
- **Lijst of pijplijn**: compacte lijst (triage) of kolommen Interesse → Verstuurd → Gesprek → Resultaat (slepen).
- **Leesvenster**: alle gegevens direct bewerkbaar, contactpersoon, cv-/briefversie, notities en tijdlijn.
- **Volgende actie** per plek met datum, *Gedaan* en *+3 dagen*. Smart-mappen *Te laat* en *Deze week*. Bij *Verstuurd* komt automatisch een follow-up over 10 dagen.
- **Zoeken met filters**: `label:afstuderen status:gesprek plaats:breda sector:forensisch deadline:<30d reistijd:<60`.
- **Bulkacties**: selecteer meerdere plekken → gelezen, status, label of negeren.
- **Sneltoetsen**: `J`/`K` navigeren, `X` selecteren, `E` negeren, `1`–`5` status, `U` ongelezen, `N` nieuw, `V` lijst/pijplijn, `/` zoeken, `?` overzicht.
- **Agenda**: export van deadlines en volgende acties als `.ics` (meldingen 3 en 1 dag vooraf) voor Google Agenda.
- **Data** in de browser (localStorage). Export/import JSON en export CSV via Instellingen. Data uit v1 wordt automatisch omgezet.

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
