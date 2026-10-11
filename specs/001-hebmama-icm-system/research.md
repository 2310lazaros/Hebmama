# Research: HebMama ICM-Wissenssystem

**Feature**: `specs/001-hebmama-icm-system`  
**Date**: 2026-10-12

Alle offenen Punkte aus dem technischen Rahmen sind hier entschieden. Kein `NEEDS CLARIFICATION` bleibt im Plan.

## Decision: Der Wissensbestand ist ein Markdown-Korpus ohne Anwendung

**Rationale**: Die Spezifikation beschreibt HebMama als lesbaren Wissensbestand. Eine Anwendung, eine Datenbank oder eine Anbindung an myHealth würde personenbezogene Gesundheitsdaten und einen technischen Betrieb ins erste Vorhaben ziehen.

**Alternatives considered**: Web-App mit Suche; persönliches Vorsorgeheft. Verworfen, weil die Spezifikation beides ausschließt.

## Decision: Ablage unter `wissen/`, Vorlagen nur in den Verträgen

**Rationale**: `wissen/` ist der Leserbestand. Die Kopiervorlagen stehen in `specs/001-hebmama-icm-system/contracts/` und werden beim Anlegen eines Dokuments kopiert. So erscheinen Platzhalter nicht im Leseweg.

**Alternatives considered**: Ordner `wissen/vorlagen/` neben den Lesertexten. Verworfen, weil eine Betreuungsperson die ungefüllten Vorlagen für Inhalte halten könnte.

## Decision: GitHub-Flavored Markdown, sichtbare Abschnitte, keine versteckte Metadaten

**Rationale**: Vergleichstabellen brauchen Tabellen. GitHub-Flavored Markdown ist dafür die übliche lesbare Form. Herkunft, Status und Kennungen stehen im sichtbaren Text. Versteckte Kopfinformationen wären ohne Werkzeug nicht prüfbar und widersprechen der Interpretable Context Methodology.

**Alternatives considered**: Nur CommonMark ohne Tabellen; YAML-Kopfzeilen für eine spätere Prüfung. Verworfen als primäre Form. Eine maschinelle Prüfung darf nur sichtbare Überschriften und Tabellen lesen.

## Decision: Pfade in ASCII, Überschriften auf Deutsch

**Rationale**: Ordner- und Dateinamen nutzen Kleinbuchstaben, Ziffern und Bindestriche ohne Umlaute (`luecken`, `u7a`). Die Überschrift jedes Dokuments ist Deutsch. Amtliche griechische und englische Titel bleiben im Herkunftsblock stehen.

**Alternatives considered**: Deutsche Ordnernamen mit Umlauten. Verworfen wegen brüchiger Links zwischen Werkzeugen.

## Decision: Einstieg ist `wissen/README.md`, alle anderen Sammlungen nutzen `index.md`

**Rationale**: Genau eine Datei ist der Einstieg. Weitere `README.md` würden diesen Einstieg verwischen.

**Alternatives considered**: `wissen/einstieg.md`. Verworfen, weil der Ordner dann ohne erkennbare erste Seite geöffnet wird.

## Decision: Fassungen sind unveränderliche Dateien

**Rationale**: Je Quellenwerk gibt es einen Ordner mit `index.md` und einer Datei je Fassung. Der Dateiname ist die Kennung der Fassung (`YYYY-MM-DD.md` oder, wenn die Ausgabe keine Datumskennung trägt, eine stabile Ausgabenkennung wie `isbn-978-92-4-004598-9.md`). `index.md` führt eine Tabelle mit dem Status `aktuell` oder `ersetzt`. Es gibt je Werk genau eine aktuelle Fassung. Ersetzte Dateien bleiben liegen. Andere Dokumente verlinken für Sachaussagen nur die aktuelle Fassung.

**Alternatives considered**: Eine Datei `aktuell.md`, die überschrieben wird. Verworfen, weil die vorherige Fassung dann nicht erhalten bleibt.

## Decision: Feste erste Quellenwerke, griechische U-Ordner werden nicht angelegt

**Rationale**: Der erste Bestand legt nur Werke an, die der Auftrag und die amtlichen Veröffentlichungen hergeben.

| ID | Ordner | Amtlicher Bezug | Fundstelle für die spätere Ablage |
| --- | --- | --- | --- |
| `de-kinder-richtlinie` | `wissen/quellen/deutschland/kinder-richtlinie/` | Richtlinie des Gemeinsamen Bundesausschusses zur Früherkennung von Krankheiten bei Kindern, Fassung vom 15. Mai 2025, in Kraft 1. Januar 2026 | https://www.g-ba.de/downloads/62-492-3998/Kinder-RL_2025-05-15_iK-2026-01-01.pdf |
| `gr-myhealth` | `wissen/quellen/griechenland/myhealth/` | myHealth als Zugang zum nationalen elektronischen Gesundheitsdossier | https://ehealthrecord.gov.gr/ehfy-overview-details |
| `gr-vivliario-ygeias-paidiou` | `wissen/quellen/griechenland/vivliario-ygeias-paidiou/` | Ηλεκτρονικό Βιβλιάριο Υγείας Παιδιού | https://www.idika.gr/deltio-typou-diathesima-gia-olous-to-psifiako-vivliario-ygeias-paidiou-kai-to-ethniko-mitroo-emvoliasmon-paidion-kai-efivon/ |
| `gr-mitroo-emvoliasmon` | `wissen/quellen/griechenland/mitroo-emvoliasmon/` | Εθνικό Μητρώο Εμβολιασμών Παιδιών και Εφήβων | https://diadikasies.gov.gr/drasi/61cec97b-cbd9-4f0a-bcce-b1f0acf23a5e |
| `who-postnatal-2022` | `wissen/quellen/who/postnatalversorgung-2022/` | WHO recommendations on maternal and newborn care for a positive postnatal experience, 2022, ISBN 978-92-4-004598-9 | https://www.who.int/publications/i/item/9789240045989 |

`mychildren.gr` ist ein Angebot eines privaten Anbieters und wird nicht als HebMama-Quelle verwendet.

Weitere Werke, etwa ein nationaler Impfkalender oder ein Wochenbett-Text, bekommen erst einen Ordner, wenn sie wirklich abgelegt werden. Dieselbe Änderung verlinkt sie in `wissen/quellen/index.md`.

**Alternatives considered**: Zehn griechische Ordner als Spiegel der U-Untersuchungen. Verworfen. Eine solche Reihe ist in den genannten griechischen Instrumenten nicht belegt. Der Vergleich nutzt dafür `kein Gegenstück` oder eine Inhaltslücke.

## Decision: Zehn Vergleichseinträge, vier WHO-Pakete, keine U10

**Rationale**: Die Kinder-Richtlinie in der Fassung vom 15. Mai 2025 umfasst zehn Untersuchungen: U1, U2, U3, U4, U5, U6, U7, U7a, U8, U9. U7a bleibt im Bestand. Der Gemeinsame Bundesausschuss hat am 20. August 2026 eine U10 für das Alter von 9 bis 10 Jahren beschlossen; sie ist noch nicht der Rahmen dieser Spezifikation und erhält keinen Ordner und keinen Vergleichseintrag. Erwähnt die abgelegte Fassung die U10, verweist die Zusammenfassung auf den Geltungsrahmen.

Die WHO-Leitlinie von 2022 empfiehlt mindestens vier Postnatalkontakte für gesunde Mütter und Neugeborene: die ersten 24 Stunden (in einer Einrichtung mindestens 24 Stunden; bei Hausgeburt so früh wie möglich innerhalb von 24 Stunden), 48 bis 72 Stunden, Tag 7 bis 14 und Woche 6. Dafür werden vier Vorbereitungspakete angelegt. Weicht die beim Ablegen gelesene Fassung davon ab, folgen die Ordner der Fassung, und die Abweichung wird im Quellenwerk festgehalten.

Beim Ablegen zu prüfende Zeitangaben der Kinder-Richtlinie, nicht als vorab geschriebene Lesertexte:

| Untersuchung | Zeitraum | Toleranzgrenze |
| --- | --- | --- |
| U1 | Unmittelbar nach der Geburt | keine eigene Toleranz in der Tabelle |
| U2 | 3.–10. Lebenstag | 3.–14. Lebenstag |
| U3 | 4.–5. Lebenswoche | 3.–8. Lebenswoche |
| U4 | 3.–4. Lebensmonat | 2.–4 ½ Lebensmonat |
| U5 | 6.–7. Lebensmonat | 5.–8. Lebensmonat |
| U6 | 10.–12. Lebensmonat | 9.–14. Lebensmonat |
| U7 | 21.–24. Lebensmonat | 20.–27. Lebensmonat |
| U7a | 34.–36. Lebensmonat | 33.–38. Lebensmonat |
| U8 | 46.–48. Lebensmonat | 43.–50. Lebensmonat |
| U9 | 60.–64. Lebensmonat | 58.–66. Lebensmonat |

Dieselbe Fassung sagt, dass die Untersuchungszeiträume auch bei Frühgeborenen einzuhalten sind und die Frühgeburtlichkeit bei der Beurteilung der Ergebnisse berücksichtigt wird. Der Leserbestand gibt diese Regel mit Herkunft wieder und rechnet kein zweites Alter.

**Alternatives considered**: U10 bereits als Ordner anlegen. Verworfen, weil die Spezifikation U10, U11 und J1 außerhalb des Rahmens lässt.

## Decision: Beziehungswörter und Postnatalfenster sind getrennt

**Rationale**: Die Beziehung zu Griechenland und zur WHO ist genau eines von `Entsprechung`, `teilweise Entsprechung`, `kein Gegenstück`. Das Postnatalfenster ist zusätzlich `läuft`, `beendet` oder `nicht betroffen`. So bleibt U9 bei „kein Gegenstück“ und „beendet“, ohne ein viertes Beziehungswort zu erfinden.

Eine vorläufige Lesehilfe für die Umsetzung, die erst nach dem Lesen der abgelegten WHO-Fassung in den Vergleich darf:

- U1 liegt in den ersten 24 Stunden.
- U2 liegt nahe an 48 bis 72 Stunden und kann den Kontakt von Tag 7 bis 14 berühren.
- U3 liegt nahe an Woche 6.
- Ab U4 ist das sechswöchige Postnatalfenster beendet.

Diese Lesehilfe ist keine Sachaussage des Wissensbestands. Für Griechenland ist der Ausgangswert `kein Gegenstück`, bis eine abgelegte Quelle einen benannten Kontakt belegt.

**Alternatives considered**: Eine freie Textbeziehung je Zelle. Verworfen, weil leere und ausgedachte Zuordnungen dann nicht prüfbar sind.

## Decision: Übersichtstabellen verlinken, Einzeldokumente tragen die Sachaussage

**Rationale**: `nach-alter.md` und `nach-untersuchung.md` sind Wege. Ihre Zellen enthalten Spanne, Lage, Beziehungswort und Links. Die begründetete Aussage steht nur im Vergleichseintrag und verlinkt eine tragende Aussage der aktuellen Quellfassung. So bleibt jede Zeit- und Inhaltsaussage zurückverfolgbar, und die Übersicht wird nicht zur zweiten, unbelegten Leitlinie.

**Alternatives considered**: Eine einzige große Tabelle mit dem vollen Untersuchungsinhalt. Verworfen, weil Herkunft und Widersprüche dort nicht mehr satzweise prüfbar sind.

## Decision: Kennzeichnung `Leitlinie` und `Orientierung`

**Rationale**: Jeder Sachabsatz und jeder Listenpunkt in Vergleich und Vorbereitung beginnt mit `**Leitlinie.**` oder `**Orientierung.**`. Auf `**Leitlinie.**` folgt im selben Absatz ein relativer Link auf die aktuelle Fassungsdatei. Orientierung trägt keinen solchen Anspruch.

**Alternatives considered**: Farben oder Fußnoten. Verworfen, weil sie in reinem Markdown leicht verloren gehen.

## Decision: Navigation in höchstens drei Linkschritten

**Rationale**: Ein Schritt ist das Folgen eines Markdown-Links in eine andere Datei. Der Sprung zu einer Überschrift in derselben Datei zählt nicht. `wissen/README.md` verlinkt die Übersichten, beide Vergleichswege, den Quellenindex, den Vorbereitungsindex und die vier Hinweisdokumente direkt.

- Aktuelle Fassung: Einstieg → `quellen/index.md` → Fassungsdatei (2 Schritte). Die Werk-Indexdatei verlinkt zusätzlich jede ersetzte Fassung (3 Schritte).
- Vergleichseintrag: Einstieg → `vergleich/nach-alter.md` oder `vergleich/nach-untersuchung.md` → Eintrag (2 Schritte).
- Paket: Einstieg → `vorbereitung/index.md` → `index.md` des Pakets (2 Schritte) → Leitfaden, Checkliste oder Fragen (3 Schritte).

**Alternatives considered**: Eine Suche als Zugang. Verworfen. Die Spezifikation verlangt den Weg ohne Suche und ohne weitere Anwendung.

## Decision: Inhaltslücken haben stabile Kennungen

**Rationale**: Jede Lücke ist ein Abschnitt `## LUECKE-001` in `wissen/hinweise/luecken.md`. Der Link lautet `#luecke-001`. Status ist `offen` oder `geschlossen`. Eine geschlossene Lücke bleibt stehen. Vergleichseinträge mit fehlender amtlicher Angabe verlinken die Lücke. Sie füllen die Zelle nicht mit einer eigenen Termin- oder Impffolge.

**Alternatives considered**: Lücken nur als leere Tabellenzellen. Verworfen, weil eine leere Zelle die Spezifikation verfehlt.

## Decision: Prüfung ohne Testframework

**Rationale**: Der Beweis, dass der Bestand trägt, ist der Leseweg in `quickstart.md`: Dateien vorhanden, Pflichtüberschriften vorhanden, Orientierungshinweis vorhanden, zehn Einträge, vierzehn Pakete, keine U10, Herkunftslinks relativ. Dafür reichen Ansehen und die dort genannten Suchbefehle. Ein Anwendungsframework ist keine Abhängigkeit.

**Alternatives considered**: Eine Website mit automatisierten Browserprüfungen. Verworfen für diese Fassung.
