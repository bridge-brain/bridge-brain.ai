# bridgebrAIn Website

Quellcode von [bridge-brain.ai](https://bridge-brain.ai), gebaut mit [Astro](https://astro.build/) und [Tailwind CSS](https://tailwindcss.com/), gehostet auf GitHub Pages.

**Jeder Push auf `main` geht automatisch live** (nach ca. 1–2 Minuten). Schlägt der Build fehl, bleibt die bisherige Version online.

## ✏️ Texte ändern

Die einfachste Variante: direkt auf GitHub im Browser.

1. Datei auf GitHub öffnen (siehe Tabelle unten) und oben rechts auf das Stift-Symbol klicken.
2. Text ändern. Die Sektionsdateien enthalten Deutsch (`de:`) und Englisch (`en:`) nebeneinander, bitte beide Sprachen pflegen.
3. Auf **Commit changes** klicken und eine kurze Beschreibung eingeben, z. B. „Hero: Untertitel angepasst“.
4. Unter dem Reiter **Actions** sieht man den Lauf. Grüner Haken bedeutet: Die Änderung ist live.

Dabei bitte nur den Text **zwischen den Anführungszeichen** ändern. Steht ein Text in einfachen Anführungszeichen (`'…'`) und enthält selbst ein Apostroph, muss davor ein Backslash stehen: `don\'t`. In Überschriften erzeugt `\n` einen Zeilenumbruch.

Bei einem roten Kreuz unter **Actions** ist meist ein Anführungszeichen oder Komma verrutscht. Die Seite bleibt dann einfach auf dem alten Stand; die Datei korrigieren und erneut committen.

| Bereich der Startseite | Datei |
|---|---|
| Kopfbereich (Headline, Untertitel, Button) | `src/components/v2/HeroV2.astro` |
| Umsetzungslücke | `src/components/v2/Problem.astro` |
| Marktbelege | `src/components/v2/Evidence.astro` |
| Zwei Säulen | `src/components/v2/Pillars.astro` |
| Ablauf | `src/components/v2/Process.astro` |
| Virtuelle Kollegen | `src/components/v2/Colleagues.astro` |
| Zielgruppe | `src/components/v2/TargetV2.astro` |
| Team | `src/components/Team.astro` |
| Kontakt | `src/components/Contact.astro` |
| Navigation / Fußzeile | `src/components/Header.astro`, `src/components/Footer.astro` |
| Seitentitel & Beschreibung für Google | `src/pages/de/index.astro`, `src/pages/en/index.astro` |
| Impressum | `src/pages/de/imprint.astro`, `src/pages/en/imprint.astro` |
| Datenschutz | `src/pages/de/privacy.astro`, `src/pages/en/privacy.astro` |

Bilder (Teamfotos, Logos) liegen in `public/`.

Eine Änderung zurücknehmen: die Datei einfach wieder auf den alten Text ändern, oder lokal `git revert <commit>` und pushen.

## 🛠️ Lokal arbeiten

Mehrere Leute pflegen die Seite: **vor jeder Änderung `git pull`**.

```bash
npm install
npm run dev       # http://localhost:4321
npm run build     # Produktions-Build nach dist/
npm run preview   # Produktions-Build lokal ansehen
```

## 📁 Projektstruktur

```
src/
├── components/      # Sektionen (aktuelle Startseite: v2/ + Team, Contact, Header, Footer)
├── layouts/         # Seitenlayout (Meta-Tags, OG-Bild)
├── pages/           # Routing nach Dateistruktur
│   ├── index.astro         # Redirect → /de
│   ├── de/ , en/           # Startseite, Impressum, Datenschutz je Sprache
│   └── archiv-…/           # alte Version, noindex
└── styles/          # globale Styles
public/              # statische Assets (Logos, Favicon, Teamfotos, CNAME)
```

Die Markenfarben stehen in `tailwind.config.mjs` unter `colors.brand`.

## 🌐 Deployment

Das Deployment läuft über GitHub Actions (`.github/workflows/deploy.yml`): Push auf `main` → Build → GitHub Pages. Unter **Actions → Deploy → Run workflow** lässt es sich auch von Hand starten.

Die Domain `bridge-brain.ai` ist unter **Settings → Pages** eingetragen (HTTPS erzwungen). DNS: A-Records der Apex-Domain auf `185.199.108.153`, `185.199.109.153`, `185.199.110.153` und `185.199.111.153`.

---

**Bridgebrain.AI GmbH** – KI-Implementierer für den Mittelstand
