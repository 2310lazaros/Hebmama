# Data Model: HebMama ICM-Wissenssystem

**Feature**: `specs/001-hebmama-icm-system`  
**Date**: 2026-10-12

Die „Daten“ sind Markdown-Dokumente. Felder stehen in sichtbaren Abschnitten oder Tabellen. Beziehungen sind relative Links.

Verträge: `specs/001-hebmama-icm-system/contracts/`

## Gemeinsame Regeln

Jedes lesende Dokument beginnt mit einer Überschrift der ersten Ebene und unmittelbar danach diesem Hinweis:

> **Orientierung.** HebMama ist eine Orientierungshilfe. Sie ersetzt weder den persönlichen ärztlichen Rat noch das Gelbe Heft noch den griechischen Gesundheitsnachweis. Bei akuten Beschwerden wenden Sie sich an eine Ärztin, einen Arzt oder den Notruf. [Ausführlich]({{PFAD_ORIENTIERUNG}})

Pflichtabschnitte jedes Dokuments: `Zweck`, `Rahmen`, `Verweise`.

Beziehungswort, genau eines je Seite: `Entsprechung` | `teilweise Entsprechung` | `kein Gegenstück`.

Postnatalfenster: `läuft` | `beendet` | `nicht betroffen`.

Aussageart: `Leitlinie` | `Orientierung`. Ein Leitlinienabsatz verlinkt die aktuelle Fassungsdatei. Ein Orientierungsabsatz tut das nicht.

Lage in der Alterstabelle: `Zeitraum` | `frühe Toleranz` | `späte Toleranz` | `Zwischenraum` | `außerhalb`.

Verboten in allen Dokumenten: Eingabefelder oder Abschnitte für den Namen eines Kindes, ein individuelles Geburtsdatum, individuelle Impfdaten, einen Befund, eine Dosierung, eine Diagnose oder eine persönliche Impffolge.

## Quelle

Ein Quellenwerk ist ein Ordner. Eine Fassung ist eine Datei in diesem Ordner.

| Feld | Pflicht | Regel |
| --- | --- | --- |
| ID | ja | Stabil, siehe Liste unten |
| Aussteller | ja | Amtlicher Name |
| Amtlicher Titel | ja | Originalsprache, dazu deutsche Bezeichnung |
| Geltungsraum | ja | `Deutschland`, `Griechenland` oder `WHO` |
| Fassung | ja | Kennung, zugleich Dateiname ohne `.md` |
| Veröffentlichung | ja | Datum oder `nicht angegeben` |
| Inkrafttreten | ja | Datum oder `nicht angegeben` |
| Abrufdatum | ja | Datum des Lesens |
| Sprache | ja | Sprachen der gelesenen Ausgabe |
| Fundstelle | ja | Amtliche Adresse |
| Status | ja | `aktuell` oder `ersetzt` |
| Zusammenfassung | ja | Deutsch, keine Vollabschrift |
| Tragende Aussagen | ja | Aufzählung, auf die Vergleich und Pakete sich stützen dürfen |
| Nicht abgedeckt | ja | Was diese Fassung nicht hergibt |

**Beziehungen**: Das Werk-`index.md` listet alle Fassungen. Genau eine davon ist `aktuell`. Vergleich, Pakete und Glossar verlinken für Sachaussagen nur diese Datei.

**Zustände**: Eine neue Fassung wird als `aktuell` eingetragen. Die bisher aktuelle Fassung wechselt in derselben Änderung auf `ersetzt`. Dateien werden nicht gelöscht. Es gibt keinen Leserstatus `Entwurf`: Unfertiges wird nicht verlinkt.

**Erste Werke**:

| ID | Pfad |
| --- | --- |
| `de-kinder-richtlinie` | `wissen/quellen/deutschland/kinder-richtlinie/` |
| `gr-myhealth` | `wissen/quellen/griechenland/myhealth/` |
| `gr-vivliario-ygeias-paidiou` | `wissen/quellen/griechenland/vivliario-ygeias-paidiou/` |
| `gr-mitroo-emvoliasmon` | `wissen/quellen/griechenland/mitroo-emvoliasmon/` |
| `who-postnatal-2022` | `wissen/quellen/who/postnatalversorgung-2022/` |

## Vorsorgekontakt

| Feld | Pflicht | Regel |
| --- | --- | --- |
| ID | ja | `de-u1` … `de-u9`, `de-u7a`, `who-24h`, `who-48-72h`, `who-d7-14`, `who-w6` |
| Name | ja | Lesename, zum Beispiel `U4` oder `WHO-Kontakt 48–72 Stunden` |
| Bereich | ja | `Deutschland` oder `WHO`. Griechenland erhält eine ID erst mit einem belegten Kontakt |
| Altersfenster | ja | Wortlaut aus der aktuellen Quelle |
| Toleranz | bei deutschen U-Untersuchungen | Wortlaut oder `keine eigene Toleranz angegeben` |
| Betrifft | ja | `Kind`, `Mutter` oder `beide` |
| Zweck | ja | Als Leitlinie mit Link |
| Quelle | ja | Aktuelle Fassung |

Deutsche Kontakte haben einen Vergleichseintrag und ein Vorbereitungspaket. WHO-Kontakte haben ein Vorbereitungspaket und erscheinen in den deutschen Einträgen, deren Altersfenster sie berühren. Griechische Kontakte werden nicht gespiegelt angelegt.

## Vergleichseintrag

Eine Datei je deutscher Untersuchung unter `wissen/vergleich/eintraege/`.

| Datei | ID |
| --- | --- |
| `u1.md` | `de-u1` |
| `u2.md` | `de-u2` |
| `u3.md` | `de-u3` |
| `u4.md` | `de-u4` |
| `u5.md` | `de-u5` |
| `u6.md` | `de-u6` |
| `u7.md` | `de-u7` |
| `u7a.md` | `de-u7a` |
| `u8.md` | `de-u8` |
| `u9.md` | `de-u9` |

| Feld | Pflicht | Regel |
| --- | --- | --- |
| Altersfenster | ja | Leitlinie, Link auf `de-kinder-richtlinie` |
| Toleranzgrenze | ja | Leitlinie oder der Satz, dass die Quelle keine nennt |
| Zweck | ja | Leitlinie |
| Beziehung Griechenland | ja | Eines der drei Beziehungswörter, plus geprüfte griechische Quellen |
| Beziehung WHO | ja | Eines der drei Beziehungswörter |
| Postnatalfenster | ja | `läuft`, `beendet` oder `nicht betroffen` |
| Unterschiede | ja | Beide Seiten mit Link, oder der Satz, dass kein Widerspruch in den tragenden Aussagen steht |
| Frühgeburt | ja | Nur die Regel der Quelle, dazu der Verweis an die Fachperson |
| Versäumtes Fenster | ja | Toleranz der Quelle oder der Satz, dass HebMama keine Nachholregel festlegt |
| Verwendete Fassungen | ja | Genau die aktuellen Fassungen, die der Eintrag nutzt |
| Weiter | ja | Link auf das deutsche Paket oder auf eine Lücke |

**Beziehungen**: Beide Übersichten verlinken diesen Eintrag. Der Eintrag verlinkt Quellen und genau ein Paket.

**Deckung der Altersspanne**: `nach-alter.md` enthält für die Spanne von vor der Geburt bis nach dem Ende der U9-Toleranz nur die fünf Lagewerte. Jeder Tag in dieser Spanne fällt in genau eine Zeile. Zwischenräume sind eigene Zeilen mit dem deutschen Kontakt `keine U-Untersuchung anstehend`. Die Spalte WHO nutzt nur die drei Beziehungswörter. Das Postnatalfenster steht in einer eigenen Spalte.

## Vorbereitungspaket

Ordner mit vier Dateien: `index.md`, `leitfaden.md`, `checkliste.md`, `fragen.md`.

Deutsche Pakete: `wissen/vorbereitung/de/u1/` bis `u9/` einschließlich `u7a/`.

WHO-Pakete:

| Ordner | ID |
| --- | --- |
| `wissen/vorbereitung/who/kontakt-24-stunden/` | `who-24h` |
| `wissen/vorbereitung/who/kontakt-48-72-stunden/` | `who-48-72h` |
| `wissen/vorbereitung/who/kontakt-tag-7-14/` | `who-d7-14` |
| `wissen/vorbereitung/who/kontakt-woche-6/` | `who-w6` |

| Bestandteil | Pflichtinhalt |
| --- | --- |
| `index.md` | Zweck, betroffene Personen, Links auf die drei Teile und auf die aktuellen Quellen, Link auf den Vergleichseintrag bei deutschen Paketen |
| `leitfaden.md` | Wozu der Termin da ist, als Leitlinie; was HebMama nicht festlegt, als Orientierung |
| `checkliste.md` | Abschnitte `Vor dem Termin`, `Mitbringen`, `Am Termin`, `Danach`. Zusammen mindestens drei Punkte unter `Vor dem Termin` und `Mitbringen` |
| `fragen.md` | Mindestens fünf Fragen. Jede Frage ist Orientierung, sofern sie nicht eine Leitlinienaussage wiedergibt. Leitlinienfragen tragen den Quelllink |

Pakete ab U4 stellen keine mütterliche Postnatalempfehlung als anstehenden Termin dar. Pakete für U1 bis U3 und die WHO-Pakete nennen Mutter und Kind, wo die tragenden Aussagen das tun.

Es gibt keinen Ordner `wissen/vorbereitung/gr/`, solange kein griechischer Vorsorgekontakt mit eigener ID abgelegt ist.

## Inhaltslücke

Abschnitt in `wissen/hinweise/luecken.md`.

| Feld | Pflicht | Regel |
| --- | --- | --- |
| Kennung | ja | `LUECKE-001` aufwärts, Überschrift genau `## LUECKE-001` |
| Thema | ja | |
| Bereich | ja | `Deutschland`, `Griechenland` oder `WHO` |
| Was fehlt | ja | |
| Geprüfte Quellen | ja | Links auf Fassungen |
| Status | ja | `offen` oder `geschlossen` |
| Datum | ja | |

Eine offene Lücke ist das Ziel eines Vergleichslinks. Beim Schließen bleiben Abschnitt und Kennung stehen, der Status wechselt, und der Vergleich nennt die neue Quelle.

Die erste erwartete Lücke ist die fehlende griechische Entsprechung der deutschen U-Reihe, sofern die drei griechischen Werke keine benannten Vorsorgekontakte mit Altersfenster enthalten. Kennung: `LUECKE-001`.

## Glossareintrag

Abschnitt zweiter Ebene in `wissen/hinweise/glossar.md`.

| Feld | Pflicht |
| --- | --- |
| Deutscher Begriff | ja, als Überschrift |
| Originalbegriff | ja, oder `kein abweichender Amtsbegriff` |
| Erklärung | ja, gestützt auf eine verlinkte aktuelle Fassung |
| Quelle | ja |

Pflichtbegriffe: `U-Untersuchung`, `Gelbes Heft`, `myHealth`, `Digitaler Impfpass`, `Postnatalversorgung`.

`Digitaler Impfpass` erklärt den vom Auftrag verwendeten deutschen Namen und nennt daneben `Εθνικό Μητρώο Εμβολιασμών Παιδιών και Εφήβων`. `myHealth` bleibt der Name des Zugangs und wird nicht mit dem Impfregister gleichgesetzt.

## Orientierungshinweis und Geltungsrahmen

`wissen/hinweise/orientierung.md` enthält den kurzen Hinweis und die längere Fassung: keine Akte, keine Diagnose, keine Dosierung, keine Symptomanalyse, kein persönlicher Impfplan, Warnzeichen nur aus einer Quelle und mit dem dort genannten Hilfeweg.

`wissen/hinweise/geltungsrahmen.md` nennt die drei Säulen und die Ausschlüsse: Schwangerschaft, Zeit nach dem Postnatalfenster für mütterliche Inhalte, U10, U11, J1, Schuleingangsuntersuchung, individuelle Kinddaten, Anmeldung bei myHealth.

## Zustandsübergänge

```text
Fassung:    (neu) → aktuell → ersetzt
Lücke:      (neu) → offen → geschlossen
```

`ersetzt` und `geschlossen` sind Enden. Ein zurückgenommener Text bleibt als `ersetzt` lesbar. Die Fundstelle darf zusätzlich als nicht mehr abrufbar gekennzeichnet werden, wenn die Adresse nicht mehr antwortet.
