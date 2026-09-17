# Kabara Vertriebsportal

Eine einzige Datei: `index.html`. Doppelklick öffnet sie im Browser – kein Server, kein Login, keine Internetpflicht (nur Schriften & ZIP-Export laden aus dem Netz).

## Anmeldung & Rollen

Beim ersten Öffnen legst du **beide Zugänge** an: dich als Admin und einen Vertriebler-Zugang.
Passwörter werden nur als SHA-256-Hash mit Zufalls-Salt gespeichert und lassen sich nicht
wieder anzeigen – notiere sie dir. Neu vergeben kannst du sie jederzeit unter ⚙ Einstellungen → Zugänge.

| | Admin (du) | Vertrieb |
|---|---|---|
| Kunden | alle | nur eigene |
| Einstellungen, Preise, Bankdaten | ja | nein |
| Rabatt | frei | bis zum Limit aus den Einstellungen (Standard 100 €) |
| Provision | eigene + Team-Übersicht | eigene |

Angebotsnummern bekommen das Kürzel des Vertrieblers (z. B. `KD-MM-2026-017`), damit
nichts kollidiert, wenn ihr auf zwei Rechnern arbeitet.

**Wichtig, ohne Beschönigung:** Das ist eine Rollentrennung für den Arbeitsalltag, **kein
technischer Zugriffsschutz**. Die Datei liegt lokal – wer sie in einem Texteditor öffnet,
kommt an die Daten. Für echten Schutz bräuchte es eine Server-Lösung mit zentraler Anmeldung.

## Provision

Unten links steht dauerhaft der aktuelle Monatsstand: verdiente Provision, ein Balken mit
allen Stufen und der Satz, wie viel bis zur nächsten Stufe fehlt und was sie zusätzlich bringt.
Klick darauf öffnet das Cockpit mit Monatswahl, Kennzahlen, Team-Tabelle (nur Admin) und
allen Abschlüssen des Monats.

**Modell: fester Betrag je Paket**

| Paket | Preis | Provision Vertrieb |
|---|---|---|
| Starter | 500 € | 100 € |
| Business | 900 € | 300 € |
| Premium | 1.490 € | 500 € |

Der Balken zeigt den Fortschritt zum **Monatsziel** (Standard 1.500 € Provision) und rechnet
vor, was noch fehlt – z. B. „Noch 900 € bis 1.500 € · 2 × Premium".

Beträge, Monatsziel und Rabattlimit änderst du als Admin unter ⚙ Einstellungen → Provision
bzw. bei den Paketen. Alternativ lässt sich auf eine Prozent-Staffel nach Abschlüssen oder
Umsatz umstellen. Ein Kunde zählt, sobald sein Status auf **Gewonnen** steht – das Datum
setzt sich automatisch.

## Bereiche der Website (Sektion 3b)

Per Häkchen schaltest du je Kunde zu:

- **Google-Bewertungen** – Sternewertung im Hero *und* eigener Bewertungsbereich. Ohne
  eigene Einträge erscheinen **als „Beispiel" gekennzeichnete** Rezensionen plus ein
  Hinweistext. Echte Rezensionen trägst du zeilenweise ein: `M. Krause | 5 | Text` –
  dann verschwindet jede Beispiel-Kennzeichnung.
- **Google-Karte** – erscheint im Kontaktbereich, sobald eine Adresse eingetragen ist.
  Die Karte lädt erst auf Klick („Karte anzeigen"), damit ohne Zustimmung nichts an Google geht.
- **Preisliste** – Zeilen als `Leistung | Preis | Zusatz`, `## Titel` bildet eine Gruppe.
- **Team** – Personen mit Name, Funktion und Foto (klicken oder hineinziehen). Ohne Foto
  erscheint ein Initial-Platzhalter.

Navigation und Ankerlinks der Demo passen sich automatisch an.

**Zu den Beispiel-Bewertungen:** Sie sind für den Entwurf gedacht, nicht für den
Live-Betrieb. Erfundene Rezensionen auf einer echten Unternehmensseite können als
irreführende Werbung gelten – vor dem Livegang also echte Google-Rezensionen eintragen
oder den Bereich abschalten.

## Ablauf pro Kunde

1. **+ Neuer Kunde** → Firmenname, Branche, Stadt, Kontakt eintragen.
   Die Branche setzt automatisch Texte, Leistungen, FAQ, Farben und Schriftstil.
2. **Demo-Website** rechts prüfen → `⤓ HTML` → Datei bei
   [Netlify Drop](https://app.netlify.com/drop) reinziehen → Link kopieren →
   im Feld *Link zur Demo-Website* eintragen.
3. **E-Mails**: „Erstkontakt mit Demo" → *In Mail öffnen*. Der Status springt
   automatisch auf „Demo gesendet".
4. Nach dem Gespräch: Paket + Extras wählen → Tab **Angebot** → `⎙ PDF` (drucken)
   oder `⤓ HTML` hochladen und den Link versenden. Der Kunde kann direkt auf der
   Seite verbindlich bestellen – die Bestellung kommt per Web3Forms in dein Postfach,
   danach sieht er sofort deine Bankdaten.
5. `⤓ Alles (ZIP)` packt Demo + Angebot + E-Mail-Texte + Kundendaten in ein Archiv.

## Einstellungen (⚙)

**Logo**: Für Angebote ist dein Kabara-Digital-Logo (dunkle Schrift) bereits hinterlegt,
es steht im Kopf jedes Angebots. Die helle Variante für die Portal-Seitenleiste wird beim
ersten Start automatisch daraus erzeugt – beide lassen sich jederzeit durch eigene
Dateien ersetzen.

Firmendaten, Bankverbindung, Pakete & Preise, Extras, Support-Leistungen,
Angebotsnummern-Zähler, Web3Forms-Key, Kleinunternehmer-Status (§19 UStG an/aus –
bei „aus" wird 19 % USt. ausgewiesen).

In Paket-Leistungen funktionieren Platzhalter: `{stadt}`, `{region}`, `{firma}`.

## Daten & Speicherung

Die Daten liegen auf **diesem Rechner**, kein Cloud-Konto. Gespeichert wird auf drei
Ebenen gleichzeitig, damit nichts verloren geht:

1. **Daten-Datei** (empfohlen, Chrome): Klick auf `💾 Daten-Datei verbinden`, einmal
   einen Ort wählen (z. B. `Dokumente/kabara-portal-daten.json`). Ab dann schreibt das
   Portal jede Änderung automatisch in diese Datei. Sie überlebt gelöschte Browserdaten
   und lässt sich sichern oder in die Cloud legen.
2. **IndexedDB** im Browser.
3. **localStorage** im Browser.

Beim Start gewinnt die zuletzt gespeicherte Quelle – wird eine Ebene geleert, füllt sie
sich aus einer anderen wieder auf.

**Statusanzeige**: oben im Kundenkopf und unten links in der Seitenleiste steht immer,
wohin gerade gespeichert wird. Steht dort rot „KEIN Speicher", öffnet der Browser die
Datei ohne Speicherrechte – das passiert z. B. in Vorschau-Fenstern. Dann die Datei
direkt in Chrome per Doppelklick öffnen.

Nach einem Chrome-Neustart fragt Chrome **einmal pro Sitzung** nach Zugriff auf die
Daten-Datei – dafür erscheint oben ein Hinweis mit `Zugriff erlauben`.

- `⤓ Backup` exportiert zusätzlich alles als JSON.
- `⤒ Backup laden` führt eine Datei wieder zusammen (nichts wird überschrieben,
  gleiche Kunden-IDs werden aktualisiert).

## Hinweise

- Bewertungen: Trage nur die **echte** Google-Bewertung des Kunden ein. Die Demo zeigt
  Zahl + Sternschnitt und den Hinweis, dass echte Rezensionen später live eingebunden werden.
- Bilder: Titelbild und Logo per Klick auf das Feld, per Drag & Drop oder mit Cmd+V
  einfügen – alternativ eine Bild-URL eintragen. Hochgeladene Bilder werden automatisch
  verkleinert (Titelbild max. 1500 px als JPEG, Logo max. 600 px) und **direkt in die
  HTML-Datei eingebettet**: die Demo funktioniert dadurch auch offline und ohne fremden
  Bildserver. Ohne Bild rendert die Demo einen Farbverlauf – sieht ebenfalls fertig aus.
- Beim Titelbild lassen sich **Bildausschnitt** (oben/Mitte/unten) und **Abdunklung**
  einstellen. Bei hellen Fotos die Abdunklung erhöhen, damit die Überschrift lesbar bleibt.
- Eingebettete Bilder brauchen Platz im Browser-Speicher (ca. 100–250 KB pro Kunde).
  Bei sehr vielen Kunden lieber alte Projekte per Backup sichern und löschen.
- Die Demo trägt unten links den Badge „Demo-Entwurf von Kabara Digital" (im Druck/Mobil ausgeblendet).
