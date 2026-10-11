# Vertrag: Navigation und Kennungen

Ein Schritt ist das Öffnen einer anderen Markdown-Datei über einen relativen Link. Ein Sprung auf eine Überschrift in derselben Datei ist kein Schritt. Der Einstieg ist Schritt 0.

## Direkte Links aus `wissen/README.md`

- `hinweise/orientierung.md`
- `hinweise/geltungsrahmen.md`
- `hinweise/glossar.md`
- `hinweise/luecken.md`
- `quellen/index.md`
- `vergleich/index.md`
- `vergleich/nach-alter.md`
- `vergleich/nach-untersuchung.md`
- `vorbereitung/index.md`

## Pflichtwege

| Ziel | Weg | Schritte |
| --- | --- | --- |
| Aktuelle Fassung | Einstieg → `quellen/index.md` → Fassungsdatei | 2 |
| Ersetzte Fassung | Einstieg → `quellen/index.md` → Werk-`index.md` → Fassungsdatei | 3 |
| Vergleichseintrag | Einstieg → `vergleich/nach-alter.md` oder `nach-untersuchung.md` → `eintraege/<datei>.md` | 2 |
| Paket | Einstieg → `vorbereitung/index.md` → Paket-`index.md` | 2 |
| Leitfaden, Checkliste, Fragen | Einstieg → `vorbereitung/index.md` → Paket-`index.md` → Bestandteil | 3 |

`vergleich/index.md` verlinkt beide Wege und alle zehn Einträge, damit auch dieser Einstieg unter drei Schritten bleibt.

## Linkregeln

- Interne Links sind relativ und zeigen auf eine `.md`-Datei oder auf `#luecke-001` in `hinweise/luecken.md`.
- Sachaussagen vom Typ Leitlinie zeigen auf eine Fassungsdatei mit Status `aktuell`, nicht auf das Werk-`index.md`.
- Übersichtstabellen wiederholen keine Untersuchungsinhalte. Sie nennen Lage, Beziehungswort und den Link zum Eintrag.
- Ein neues Quellenwerk wird nur zusammen mit seinem Link in `quellen/index.md` angelegt.
- Es gibt keine Ordner `wissen/vorbereitung/de/u10/`, `wissen/vergleich/eintraege/u10.md` und `wissen/vorbereitung/gr/`.

## Kennungen

| Art | Muster | Beispiel |
| --- | --- | --- |
| Quellenwerk | fest vergeben | `de-kinder-richtlinie` |
| Deutsche Untersuchung | `de-u1` … `de-u9`, `de-u7a` | `de-u4` |
| WHO-Kontakt | fest vergeben | `who-24h`, `who-48-72h`, `who-d7-14`, `who-w6` |
| Lücke | `LUECKE-` und drei Ziffern | `LUECKE-001` |
| Fassung | Dateiname ohne Endung | `2025-05-15` |

## Tiefe des Orientierungslinks

| Datei liegt in | `{{PFAD_ORIENTIERUNG}}` |
| --- | --- |
| `wissen/` | `hinweise/orientierung.md` |
| `wissen/hinweise/` | `orientierung.md` |
| `wissen/quellen/`, `wissen/vergleich/`, `wissen/vorbereitung/` | `../hinweise/orientierung.md` |
| `wissen/quellen/<bereich>/<werk>/` | `../../../hinweise/orientierung.md` |
| `wissen/vergleich/eintraege/` | `../../hinweise/orientierung.md` |
| `wissen/vorbereitung/de/<kontakt>/` und `wissen/vorbereitung/who/<kontakt>/` | `../../../hinweise/orientierung.md` |

## Gemeinsamer Hinweis

Jedes Leser-Dokument setzt diesen Absatz unmittelbar unter die erste Überschrift. `{{PFAD_ORIENTIERUNG}}` wird aus der Tabelle ersetzt.

```markdown
> **Orientierung.** HebMama ist eine Orientierungshilfe. Sie ersetzt weder den persönlichen ärztlichen Rat noch das Gelbe Heft noch den griechischen Gesundheitsnachweis. Bei akuten Beschwerden wenden Sie sich an eine Ärztin, einen Arzt oder den Notruf. [Ausführlich]({{PFAD_ORIENTIERUNG}})
```
