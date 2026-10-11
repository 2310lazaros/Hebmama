<!-- Vorlage: wissen/vergleich/nach-alter.md — diese Zeile nicht mitkopieren -->

# Vergleich nach Alter

> **Orientierung.** HebMama ist eine Orientierungshilfe. Sie ersetzt weder den persönlichen ärztlichen Rat noch das Gelbe Heft noch den griechischen Gesundheitsnachweis. Bei akuten Beschwerden wenden Sie sich an eine Ärztin, einen Arzt oder den Notruf. [Ausführlich](../hinweise/orientierung.md)

## Zweck

Dieser Weg beantwortet: Welche deutsche Untersuchung, welche griechische Beziehung und welche WHO-Beziehung gelten für ein gegebenes Alter?

## Rahmen

Die Tabelle deckt die Spanne von vor der Geburt bis nach dem Ende der U9-Toleranz. Jeder Zeitpunkt fällt in genau eine Zeile. Zeitangaben sind Leitlinienaussagen und verlinken die aktuelle Kinder-Richtlinie. Beziehungswörter werden nicht zu Untersuchungsinhalten ausgebaut; die Begründung steht im Eintrag.

Zulässige Werte in der Spalte Lage: `Zeitraum`, `frühe Toleranz`, `späte Toleranz`, `Zwischenraum`, `außerhalb`.

Je Untersuchung gibt es eine Zeile `Zeitraum`. Eine Zeile `frühe Toleranz` oder `späte Toleranz` gibt es nur, wenn die Quelle die Toleranz über den Zeitraum hinauszieht. Zwischen dem Ende der äußeren Grenze einer Untersuchung und dem Beginn der nächsten äußeren Grenze steht eine Zeile `Zwischenraum`, wenn dort Tage liegen. `außerhalb` gibt es für die Zeit vor der Geburt und für die Zeit nach dem Ende der U9-Toleranz.

## Alterstabelle

Die Zeilen mit Platzhaltern sind das Muster und werden je reale Spanne ersetzt. Im Leserbestand bleibt kein `{{…}}` stehen.

| Spanne | Lage | Deutscher Kontakt | Griechenland | WHO | Postnatalfenster | Weiter |
| --- | --- | --- | --- | --- | --- | --- |
| vor der Geburt | außerhalb | keine U-Untersuchung anstehend | kein Gegenstück | kein Gegenstück | nicht betroffen | [Geltungsrahmen](../hinweise/geltungsrahmen.md) |
| {{SPANNE}} | Zeitraum | {{U_NAME}} | {{BEZIEHUNG_GR}} | {{BEZIEHUNG_WHO}} | {{POSTNATALFENSTER}} | [Eintrag](eintraege/{{DATEI}}.md) |
| {{SPANNE}} | frühe Toleranz | {{U_NAME}} | {{BEZIEHUNG_GR}} | {{BEZIEHUNG_WHO}} | {{POSTNATALFENSTER}} | [Eintrag](eintraege/{{DATEI}}.md) |
| {{SPANNE}} | späte Toleranz | {{U_NAME}} | {{BEZIEHUNG_GR}} | {{BEZIEHUNG_WHO}} | {{POSTNATALFENSTER}} | [Eintrag](eintraege/{{DATEI}}.md) |
| {{SPANNE}} | Zwischenraum | keine U-Untersuchung anstehend | {{BEZIEHUNG_GR}} | {{BEZIEHUNG_WHO}} | {{POSTNATALFENSTER}} | [letzte](eintraege/{{VORHER}}.md), [nächste](eintraege/{{NAECHSTE}}.md) |
| nach dem Ende der U9-Toleranz | außerhalb | keine U-Untersuchung anstehend | kein Gegenstück | kein Gegenstück | beendet | [U9](eintraege/u9.md) |

Zeilen mit `frühe Toleranz` oder `späte Toleranz` entfallen, wenn die Quelle diese Spanne nicht ausweist. WHO-Pakete der frühen Kontakte werden aus dem passenden Eintrag U1, U2 oder U3 verlinkt, nicht aus einer eigenen Altersrechnung.

**Leitlinie.** Die Spannen stammen aus der aktuellen Kinder-Richtlinie. ([Kinder-Richtlinie]({{PFAD_KINDER_RICHTLINIE}}))

## Verweise

- [Nach Untersuchung](nach-untersuchung.md)
- [Vergleich](index.md)
- [Einstieg](../README.md)
