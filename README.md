# Markus sin Julekalender – README

Velkommen! Dette repoet inneholder en ferdig julekalender bygget som én enkel HTML-side med en separat JSON-fil for innhold. Kalenderen kan brukes år etter år og enkelt tilpasses til nye personer.

Denne README er fullversjonen av bruksveiledningen. Øverst i `index.html` finner du en kortversjon.

---

## 📁 Filstruktur

De viktigste filene/mappene:

- **index.html** – Hele kalenderen (stil, logikk, modalvinduer, testmodus)
- **data/days.json** – Tekstinnhold + musikklenker for alle 24 luker

> Kalenderen bruker **ingen bildefiler**, så det behøves ingen `assets`-mappe.

---

## ✏️ Endre innhold i lukene

Alt innhold som vises når du åpner en luke, ligger i:

```
data/days.json
```

Dette er en liste med 24 objekter, ett per dag:

```json
[
  {
    "title": "1. desember",
    "text": "Tekst for denne luken...",
    "apple": "https://music.apple.com/...",
    "spotify": "https://open.spotify.com/..."
  }
]
```

**Forklaring:**
- `title`: vises i den røde toppen i modalvinduet
- `text`: innholdet i luken.
  - Du kan bruke **vanlig linjeskift** i teksten
  - Tom linje = nytt avsnitt
- `apple` og `spotify`:
  - Legg inn direktelenker
  - La stå tom (`""`) hvis du ikke ønsker å vise knappen

---

## ℹ️ Endre info-teksten

Teksten som vises når man trykker på info-knappen styres av konstanten:

```js
const INFO_TEXT = ` ... `;
```

Du finner den i `index.html`. Her kan du skrive:
- Vanlig tekst
- Linjeskift
- Avsnitt (tom linje)

Alt formateres automatisk i modalen.

---

## 🧪 Testmodus (åpne alle luker)

Øverst i `<script>`-delen av `index.html` ligger:

```js
const DEBUG_ALWAYS_OPEN = true;
```

- **true** = alle luker åpne, uansett dato
  - En liten oransje tekst vises: *TESTMODUS – alle luker er åpne nå*
- **false** = ekte datostyring (se under)

Bruk **true** mens du jobber – sett til **false** før kalenderen skal tas i bruk.

---

## 📅 Datostyring (live-modus)

Når `DEBUG_ALWAYS_OPEN = false` styres åpne/låste luker automatisk etter systemdatoen på brukerens enhet.

Reglene er:

- Før desember → all luker lukket
- I desember → luke *n* åpnes når datoen ≥ *n*
- Etter desember → alle luker åpne igjen

Merk:
- Kalenderen bruker **ikke årstall**, så den fungerer år etter år uten endringer.
- Du kan teste dette manuelt ved å endre datoen på enheten og refreshe siden.

---

## 🔁 Lage ny kalender (for nytt år eller ny person)

For å lage en ny variant:

1. Lag et nytt repo på GitHub
2. Kopier inn:
   - `index.html`
   - mappen `data`
3. Endre:
   - Tittel i HTML (`<title>` og `<h1>`)
   - Innhold i `data/days.json`
   - Info-tekst i `INFO_TEXT`
4. Sett opp GitHub Pages for det nye repoet (se egen seksjon)

Dette gjør kalenderen ekstremt lett å gjenbruke.

---

## 💻 Arbeidsflyt med GitHub Desktop (Mac)

Dette er den enkleste måten å jobbe på.

### 📥 1. Klone repoet
- Åpne **GitHub Desktop**
- ``File → Clone Repository...``
- Velg repoet (f.eks. `julekalender`)

### 📝 2. Redigere filer
- Åpne mappen i **VS Code**
- Endre `days.json` eller `index.html`
- Lagre

### 📤 3. Publisere endringer
- Gå til GitHub Desktop
- Skriv en commit-melding
- Klikk *Commit to main*
- Klikk *Push origin*

Endringene vil være live på nettsiden etter noen sekunder.

---

## 🌐 Publisering med GitHub Pages

1. Gå til repoet på GitHub i nettleseren
2. Åpne **Settings → Pages**
3. Under *Build and Deployment* velger du:
   - Source: *Deploy from a branch*
   - Branch: `main` (root)
4. GitHub gir deg en nettadresse, typisk:
   
   `https://brukernavn.github.io/julekalender`

Kalenderen er nå live og delt klar.

---

## ❗ Feilsøking

Du kan møte en vennlig feilmelding:

> "Oisann, det er noe feil her…"

Det betyr at kalenderen ikke fant `data/days.json`.

Sjekk:
- Finnes mappen `data`?
- Ligger `days.json` inni der?
- Heter filen *nøyaktig* `days.json`?
- Er repoet pushet til GitHub?

Kalenderen vil fortsatt virke (med tomme luker), men du bør rette opp filplasseringen.

---

## 💡 Mulige forbedringer for neste år

Dette repoet er fullt funksjonelt. Men hvis du vil bygge videre:

- Valgfritt: la kalenderen være åpen hele januar
- Støtte for flere musikktjenester (YouTube Music, Tidal, osv.)
- Egne illustrasjoner eller bilder for hver luke (ikke nødvendig, men mulig)
- Flere designvarianter

---

God jul – og kos deg med kalenderen! 🎄✨

