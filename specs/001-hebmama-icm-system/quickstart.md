# Quickstart: HebMama ICM-Wissenssystem

**Feature**: `specs/001-hebmama-icm-system`  
**Date**: 2026-10-12

Dieser Leseweg prüft den Wissensbestand, nachdem `wissen/` aus den Verträgen gefüllt ist. Er setzt keine Installation voraus. Ein Markdown-Editor genügt. Befehle laufen im Projektordner.

Die Verträge und das Datenmodell werden hier nicht wiederholt: [contracts/README.md](contracts/README.md), [data-model.md](data-model.md).

## Voraussetzungen

- Der Ordner `wissen/` ist angelegt und enthält keine Platzhalter `{{`.
- Fünf Quellenwerke haben je genau eine aktuelle Fassung mit Abschnitt `## Tragende Aussagen`.
- Zehn Vergleichseinträge und vierzehn Pakete sind vorhanden.

Solange `wissen/` fehlt, sind die folgenden Prüfungen noch nicht erfüllbar. Das ist der Stand nach diesem Plan.

## Szenario 1: Alter einordnen

Entspricht der ersten Benutzergeschichte und SC-001.

1. `wissen/README.md` öffnen.
2. Dem Link „Vergleich nach Alter“ folgen.
3. Für den 5. Lebenstag, ein Alter im 4. Lebensmonat und ein Alter im U9-Fenster je die Zeile lesen.

Erwartet:

- Der 5. Lebenstag liegt bei U2. Die Zeile nennt das Beziehungswort zu Griechenland, das Beziehungswort zur WHO und den Stand des Postnatalfensters. Der Eintrag verlinkt die Kinder-Richtlinie.
- Der 4. Lebensmonat liegt bei U4. Das Postnatalfenster ist `beendet`.
- Das U9-Alter zeigt U9, Beziehung `kein Gegenstück` oder eine belegte Entsprechung, und das Postnatalfenster `beendet`.
- Ein Alter zwischen zwei äußeren Grenzen zeigt `Zwischenraum` und `keine U-Untersuchung anstehend` sowie Links auf die letzte und die nächste Untersuchung.
- „Vor der Geburt“ und „nach dem Ende der U9-Toleranz“ sind `außerhalb`.

## Szenario 2: Dieselbe Untersuchung über den Namen

1. Vom Einstieg „Vergleich nach Untersuchung“ öffnen.
2. U4 und U7a wählen.

Erwartet: Beide Links enden in `wissen/vergleich/eintraege/u4.md` und `u7a.md`, also in denselben Dateien, die der Altersweg verwendet. U7a steht in der Tabelle zwischen U7 und U8.

## Szenario 3: Termin vorbereiten

Entspricht der zweiten Benutzergeschichte und SC-002, SC-006, SC-008, SC-009.

1. `wissen/vorbereitung/de/u4/index.md` öffnen.
2. Leitfaden, Checkliste und Fragen lesen.

Erwartet:

- Alle drei Dateien sind verlinkt und beginnen mit dem Orientierungshinweis.
- Der Leitfaden nennt den Zweck als `**Leitlinie.**` mit Link auf die aktuelle Kinder-Richtlinie.
- Checkliste: Abschnitte `Vor dem Termin`, `Mitbringen`, `Am Termin`, `Danach`. Unter den ersten beiden zusammen mindestens drei Punkte.
- Mindestens fünf Fragen.
- Jeder Punkt beginnt mit `**Leitlinie.**` oder `**Orientierung.**`.
- Kein Feld für Name, Geburtsdatum oder Impfdaten eines Kindes.
- U4 stellt keine mütterliche Postnatalempfehlung als anstehenden Termin dar.
- U1 und das WHO-Paket `kontakt-24-stunden` sprechen Kind und Mutter an, wo die tragenden Aussagen das tun.

## Szenario 4: Herkunft in drei Schritten

Entspricht der dritten Benutzergeschichte und SC-003, SC-004.

1. In `wissen/vergleich/eintraege/u2.md` einen Absatz `**Leitlinie.**` wählen.
2. Dem Link folgen.

Erwartet: Die Datei ist eine aktuelle Fassung und zeigt Aussteller, amtlichen Titel, Fassung, Abrufdatum und Fundstelle. Vom Einstieg aus sind es höchstens drei Dateiwechsel bis zu dieser Fassung, bis zu einem Eintrag und bis zu einem Paket. Gezählt wird nur das Öffnen einer anderen Datei.

## Szenario 5: Lücke statt erfundener griechischer Reihe

Entspricht SC-005.

1. Einen Eintrag öffnen, dessen Griechenland-Zelle `kein Gegenstück` ist.
2. Dem Link zur Lücke folgen.

Erwartet: `wissen/hinweise/luecken.md` enthält `## LUECKE-001` mit Status, geprüften Quellen und ohne eine selbst festgelegte Termin- oder Impffolge. Es gibt keinen Ordner `wissen/vorbereitung/gr/`.

## Szenario 6: Fassung ersetzen

Entspricht SC-007. Erst ausführbar, wenn eine zweite Fassung abgelegt wird.

1. Eine neue Datei im Werkordner anlegen und im Werkindex als `aktuell` eintragen.
2. Die bisherige Zeile auf `ersetzt` setzen.
3. Vergleich und Pakete prüfen.

Erwartet: Die ersetzte Datei bleibt liegen und ist über den Werkindex erreichbar. Leitlinienlinks in Vergleich und Paketen zeigen auf die neue aktuelle Datei. Je Werk gibt es eine Zeile `aktuell`.

## Suchprüfungen

```bash
test -f wissen/README.md
test -f wissen/vergleich/nach-alter.md
test -f wissen/vergleich/nach-untersuchung.md
test ! -e wissen/vergleich/eintraege/u10.md
test ! -d wissen/vorbereitung/de/u10
test ! -d wissen/vorbereitung/gr
find wissen/vergleich/eintraege -name '*.md' | wc -l
find wissen/vorbereitung -name 'leitfaden.md' | wc -l
rg -n '\{\{' wissen || true
rg -l 'HebMama ist eine Orientierungshilfe' wissen
```

Erwartet:

- Die beiden `test !` Befehle melden keinen Fund.
- `find` für Einträge druckt `10`.
- `find` für Leitfäden druckt `14`.
- `rg '\{\{'` druckt keine Treffer. Der Zusatz `|| true` lässt die Prüfung auch dann weiterlaufen, wenn es keine Treffer gibt; maßgeblich ist die leere Trefferliste.
- Jede Datei unter `wissen/` steht in der Liste des Orientierungshinweises.

Zusätzlich von Hand: Jeder Treffer von `**Leitlinie.**` in `wissen/vergleich` und `wissen/vorbereitung` enthält einen relativen Link auf eine Datei, deren Herkunftstabelle `aktuell` zeigt.
