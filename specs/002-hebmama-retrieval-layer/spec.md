# Feature Specification: HebMama Schicht 2 Retrieval-Layer

**Feature Branch**: `002-hebmama-retrieval-layer`

**Created**: 2026-10-12

**Status**: Draft

**Input**: User description: "Schicht 2 (Retrieval-Layer). Strikte Abfrage- und Synthese-Regeln für die Wissensbasis wissen/. Antworten nur aus den validierten Markdown-Dateien, Einstieg über wissen/README.md, aktive Kinder-Richtlinie Fassung 15.05.2025. Verboten: erfundene Ratschläge, die archivierte Fassung vom 12.05.2023 als aktive Empfehlung, erfundene griechische U-Entsprechungen, U10 als normalen Vergleichseintrag. Jede Antwort enthält Zusammenfassung, Vorbereitung und Fragen, Quellennachweis."

## User Scenarios & Testing *(mandatory)*

### User Story 1 - Modul für die Abfrage anlegen (Priority: P1)

Eine pflegende Person legt die Abrufregeln so ab, dass eine Antwort zu HebMama nur aus `wissen/` kommt und den Einstieg `wissen/README.md` zuerst benutzt.

**Why this priority**: Ohne das Modul gibt es keine verbindliche Schicht zwischen Frage und Wissensbasis.

**Independent Test**: Die Regeldatei `.cursor/rules/hebmama-retrieval.mdc` ist vorhanden, gilt für `wissen/**` und `specs/002-hebmama-retrieval-layer/**`, und nennt Einstieg, aktive Fassung, Verbote und das dreiteilige Antwortformat.

**Acceptance Scenarios**:

1. **Given** das Projekt HebMama, **When** die Regeldatei geöffnet wird, **Then** steht dort die Wissensbasis `wissen/`, der Einstieg `wissen/README.md` und die aktive Kinder-Richtlinie vom 15.05.2025.
2. **Given** eine Frage, **When** der Abruf startet, **Then** wird nicht der ganze Ordner `wissen/` auf einmal gelesen, sondern nur die zur Frage passenden Dateien.
3. **Given** eine Altersangabe oder eine U-Nummer, **When** der Weg gewählt wird, **Then** führt das Alter über den Altersweg und die U-Nummer über den Untersuchungsweg.

---

### User Story 2 - Testfragen für U1 bis U9 (Priority: P1)

Eine prüfende Person stellt für jede Untersuchung von U1 bis U9, einschließlich U7a, je eine Altersfrage und eine Frage mit der U-Nummer und erwartet eine Antwort nur aus den passenden Dateien.

**Why this priority**: Damit ist geprüft, dass beide Wege aus dem Einstieg die richtige Untersuchung treffen.

**Independent Test**: Die Datei `specs/002-hebmama-retrieval-layer/test-prompts.md` enthält für U1, U2, U3, U4, U5, U6, U7, U7a, U8 und U9 je einen Alters-Prompt und einen Nummern-Prompt. Der Alters-Prompt „3–4 Monate“ führt auf U4.

**Acceptance Scenarios**:

1. **Given** die Frage nach einem Kind im 4. Lebensmonat, **When** der Altersweg benutzt wird, **Then** ist die Untersuchung U4 und die Antwort nennt Dateien unter `wissen/vergleich/` und `wissen/vorbereitung/de/u4/`.
2. **Given** die Frage „Was ist die U2?“, **When** der Untersuchungsweg benutzt wird, **Then** ist das Ziel `wissen/vergleich/eintraege/u2.md` und das Paket `wissen/vorbereitung/de/u2/`.
3. **Given** eine Antwort auf einen dieser Prompts, **When** sie geprüft wird, **Then** enthält sie Zusammenfassung, Vorbereitung und Fragen, und einen Quellennachweis mit echten Pfaden unter `wissen/`.

---

### User Story 3 - Griechenland und U10 begrenzen (Priority: P2)

Eine Betreuungsperson fragt nach einer griechischen Entsprechung oder nach U10 und erhält die festgelegte Grenze, keine erfundenen Termine.

**Why this priority**: Das sind die beiden Verbote, die den Vergleich vor stillen Ergänzungen schützen.

**Independent Test**: Ein Prompt zu Griechenland nennt `LUECKE-001` und den Satz „kein Gegenstück im griechischen System“. Ein Prompt zu U10 nennt „U10-Beschluss 20.08.2026 - out of current scope“ und verlinkt nicht `wissen/vergleich/eintraege/u10.md`.

**Acceptance Scenarios**:

1. **Given** die Frage, welche griechische U-Untersuchung der U4 entspricht, **When** geantwortet wird, **Then** wird keine griechische U-Reihe erfunden und `wissen/hinweise/luecken.md` ist im Quellennachweis.
2. **Given** die Frage, ob die U10 jetzt ansteht, **When** geantwortet wird, **Then** gilt der Beschluss vom 20.08.2026 als außerhalb des aktuellen Rahmens.
3. **Given** eine Frage nach der heute geltenden deutschen Untersuchung, **When** eine Fassung zitiert wird, **Then** ist es die Kinder-Richtlinie vom 15.05.2025 und nicht die archivierte Fassung vom 12.05.2023.

---

### User Story 4 - Qualitätsprüfung der Antworten (Priority: P2)

Eine prüfende Person geht die Testfragen durch und hakt die Ausgaberegeln und die Verbote ab.

**Why this priority**: Erst die Prüfung zeigt, dass das Modul im Gebrauch hält, was es vorschreibt.

**Independent Test**: Die Liste `specs/002-hebmama-retrieval-layer/checklists/retrieval.md` ist ausgefüllt. Jeder Prompt hat die drei Ausgabeteile. Kein Prompt zitiert die Fassung vom 12.05.2023 als aktive Empfehlung.

**Acceptance Scenarios**:

1. **Given** alle Prompts aus User Story 2 und 3, **When** die Qualitätsliste geprüft wird, **Then** ist jede Zeile bestand oder mit dem fehlenden Dateipfad markiert.
2. **Given** eine Antwort ohne Quellennachweis, **When** die Liste geprüft wird, **Then** gilt der Prompt als nicht bestanden.

---

### Edge Cases

- Ein Alter liegt zwischen zwei U-Fenstern. Die Antwort nennt die Lücke und erfindet keine Untersuchung.
- Die Frage nennt U7a. U7a gehört zur Reihe zwischen U7 und U8 und hat einen eigenen Prompt.
- Die Frage vermischt Alter und U-Nummer, die nicht zusammenpassen. Die Antwort zeigt beide Wege und erklärt den Unterschied aus den Dateien, ohne eine eigene Regel zu setzen.
- Die Frage verlangt eine Dosierung oder eine persönliche Impffolge. Die Antwort bleibt bei den Dateien in `wissen/` und erfindet keine Dosis.
- Jemand fragt nach der alten Kinder-Richtlinie. Sie darf als archivierte Fassung genannt werden, nicht als aktive Empfehlung.

## Requirements *(mandatory)*

### Functional Requirements

- **FR-001**: HebMama MUSS die Abrufregeln in `.cursor/rules/hebmama-retrieval.mdc` führen. Erfüllt, wenn die Datei den vereinbarten Wortlaut hat, `alwaysApply` falsch ist und die Globs `wissen/**` sowie `specs/002-hebmama-retrieval-layer/**` nennt.
- **FR-002**: Jede Abfrage MUSS bei `wissen/README.md` beginnen und von dort nur die passenden Dateien öffnen. Erfüllt, wenn ein Testprompt den ersten Leseschritt und die danach geöffneten Pfade nennt.
- **FR-003**: Eine Altersfrage MUSS über `wissen/vergleich/nach-alter.md` laufen, eine U-Nummer über `wissen/vergleich/nach-untersuchung.md`. Erfüllt, wenn die Prompts für U1 bis U9 einschließlich U7a beide Wege abdecken und „3–4 Monate“ auf U4 zeigt.
- **FR-004**: Jede Antwort MUSS die drei Teile Zusammenfassung, Vorbereitung und Fragen, und Quellennachweis enthalten. Der Quellennachweis MUSS echte Pfade unter `wissen/` nennen. Erfüllt, wenn die Qualitätsliste das für jeden Prompt prüft.
- **FR-005**: Aktive deutsche Empfehlungen DÜRFEN nur die Kinder-Richtlinie vom 15.05.2025 verwenden. Die Fassung vom 12.05.2023 DARF nur als Archiv genannt werden. Erfüllt, wenn kein bestandener Prompt `wissen/quellen/deutschland/kinder-richtlinie/2023-05-12.md` als Quelle einer heutigen Empfehlung nennt.
- **FR-006**: Eine Frage nach Griechenland MUSS `LUECKE-001` und den Wortlaut „kein Gegenstück im griechischen System“ nennen und MUSS keine griechische U-Reihe anlegen. Erfüllt, wenn der Prompt auf `wissen/hinweise/luecken.md` zeigt.
- **FR-007**: Eine Frage nach U10 MUSS den Wortlaut „U10-Beschluss 20.08.2026 - out of current scope“ verwenden. Erfüllt, wenn kein Prompt eine Datei `wissen/vergleich/eintraege/u10.md` oder ein Paket `wissen/vorbereitung/de/u10/` voraussetzt.
- **FR-008**: Die Testfragen und die Qualitätsliste MÜSSEN unter `specs/002-hebmama-retrieval-layer/` liegen und den Wissensbestand `wissen/` nicht verändern. Erfüllt, wenn nach der Prüfung `git diff -- wissen` leer bleibt.

### Key Entities

- **Abrufregel**: Die Datei `.cursor/rules/hebmama-retrieval.mdc`. Sie legt Einstieg, Verbote und Antwortform fest.
- **Testprompt**: Eine Elternfrage mit erwarteter Untersuchung, erwartetem Weg (Alter oder U-Nummer) und erlaubten Dateipfaden.
- **Antwortnachweis**: Die drei Pflichtteile und die tatsächlich benutzten Pfade unter `wissen/`.
- **Grenzfall**: Griechenland über `LUECKE-001`, U10 als Beschluss außerhalb des Rahmens, Archivfassung vom 12.05.2023.

## Success Criteria *(mandatory)*

### Measurable Outcomes

- **SC-001**: Für alle 10 Untersuchungen U1, U2, U3, U4, U5, U6, U7, U7a, U8 und U9 liegt je ein Alters-Prompt und ein Nummern-Prompt vor. Das sind 20 Prompts.
- **SC-002**: Der Prompt „3–4 Monate“ nennt U4 und mindestens eine Datei unter `wissen/vorbereitung/de/u4/`.
- **SC-003**: 100 % der bestandenen Antworten haben Zusammenfassung, Vorbereitung und Fragen, und mindestens einen Pfad unter `wissen/`.
- **SC-004**: 0 bestandene Antworten nutzen `wissen/quellen/deutschland/kinder-richtlinie/2023-05-12.md` als Quelle einer aktiven Empfehlung.
- **SC-005**: Der Griechenland-Prompt nennt `LUECKE-001` und „kein Gegenstück im griechischen System“. Der U10-Prompt nennt „U10-Beschluss 20.08.2026 - out of current scope“.
- **SC-006**: Nach den Tests ist keine Datei unter `wissen/` geändert.

## Assumptions

- Schicht 1, der Wissensbestand `wissen/`, bleibt die einzige medizinische Quelle. Diese Schicht fügt keine neuen Leitlinien hinzu.
- U7a gehört zu den Testfällen, weil sie im Bestand zwischen U7 und U9 liegt.
- Die Regeldatei wird wortgleich so geführt, wie sie für diese Schicht vorgegeben ist.
- Die Qualitätsprüfung ist eine lesende Prüfung an den Prompts, kein zusätzliches Programm.
- Die Zahl 91 bezieht sich auf den gültigen Bestand der Markdown-Dateien in `wissen/` zum Zeitpunkt dieser Schicht.
