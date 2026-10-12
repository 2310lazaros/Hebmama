---

description: "Task list for HebMama Schicht 2 Retrieval-Layer"
---

# Tasks: HebMama Schicht 2 Retrieval-Layer

**Input**: Design documents from `/specs/002-hebmama-retrieval-layer/`

**Prerequisites**: plan.md, spec.md, bestehender Bestand `wissen/`

**Tests**: Die Prüfung ist die Qualitätsliste in Phase 4. Es gibt kein Testframework.

**Organization**: Vier Phasen, passend zu Modulanlage, Test-Prompts U1–U9, LUECKE-001 und Qualitätsprüfung.

## Format: `[ID] [P?] [Story] Description`

- **[P]**: Kann parallel laufen (andere Dateien, keine Abhängigkeit zu unfertigen Geschwisteraufgaben)
- **[Story]**: `[US1]` Modulanlage, `[US2]` Test-Prompts, `[US3]` LUECKE-001 und U10, `[US4]` Qualitätsprüfung
- Jede Aufgabe nennt einen konkreten Dateipfad

## Path Conventions

- Regel: `.cursor/rules/hebmama-retrieval.mdc`
- Prompts und Prüfung: `specs/002-hebmama-retrieval-layer/`
- Gelesene Quelle: `wissen/`. Diese Schicht verändert dort keine Datei.

## Phase 1: Modulanlage (User Story 1)

**Goal**: Die Abrufregel liegt wortgleich vor und gilt nur für die Wissensbasis und diese Spezifikation.

**Independent Test**: `.cursor/rules/hebmama-retrieval.mdc` enthält Einstieg `wissen/README.md`, aktive Fassung 15.05.2025, die vier Verbote und die drei Ausgabeteile. `alwaysApply` ist false.

- [ ] T001 [US1] Prüfe `.cursor/rules/hebmama-retrieval.mdc` gegen den vorgegebenen Wortlaut. Globs bleiben `wissen/**, specs/002-hebmama-retrieval-layer/**`. Die Datei nennt 91 Wissensdateien, verbietet das Lesen des gesamten Ordners `wissen/` und verlangt den ersten Blick in `wissen/README.md`. Keinen zweiten Regelsatz daneben anlegen.

**Checkpoint**: Das Modul ist die einzige Abrufregel dieser Schicht.

---

## Phase 2: Test-Prompts U1–U9 (User Story 2)

**Goal**: Für jede Untersuchung gibt es einen Alters-Prompt und einen Nummern-Prompt. „3–4 Monate“ führt auf U4.

**Independent Test**: `specs/002-hebmama-retrieval-layer/test-prompts.md` hat 20 Prompts für U1, U2, U3, U4, U5, U6, U7, U7a, U8 und U9. Jeder Prompt nennt den Weg `Alter` oder `U-Nummer`, die erwartete Untersuchung und mindestens einen erlaubten Pfad unter `wissen/`.

- [ ] T002 [US2] Lege `specs/002-hebmama-retrieval-layer/test-prompts.md` an. Schreibe für U1, U2, U3, U4, U5, U6, U7, U7a, U8 und U9 je einen Prompt mit expliziter U-Nummer. Erlaubte Pfade je Prompt: `wissen/vergleich/nach-untersuchung.md`, `wissen/vergleich/eintraege/<slug>.md` und `wissen/vorbereitung/de/<slug>/`. Slugs sind `u1`, `u2`, `u3`, `u4`, `u5`, `u6`, `u7`, `u7a`, `u8`, `u9`. Der erste Leseschritt jedes Prompts ist `wissen/README.md`.
- [ ] T003 [P] [US2] Ergänze in `specs/002-hebmama-retrieval-layer/test-prompts.md` je einen Alters-Prompt für dieselben zehn Untersuchungen. Der Weg ist `Alter`, der erste Leseschritt bleibt `wissen/README.md`, danach `wissen/vergleich/nach-alter.md`. Der Prompt für den 4. Lebensmonat erwartet U4 und eine Datei unter `wissen/vorbereitung/de/u4/`. Altersfenster nur so verwenden, wie sie in `wissen/quellen/deutschland/kinder-richtlinie/2025-05-15.md` stehen. Für Zwischenräume einen eigenen Prompt „zwischen U6 und U7“ aufnehmen, der keine neue Untersuchung erwartet.

**Checkpoint**: 20 Untersuchungs-Prompts und ein Zwischenraum-Prompt sind ohne Änderung an `wissen/` lesbar.

---

## Phase 3: LUECKE-001 (User Story 3)

**Goal**: Griechenland bleibt ohne erfundene U-Reihe. U10 bleibt außerhalb des Vergleichs. Die Archivfassung ist keine aktive Empfehlung.

**Independent Test**: Dieselben Prompts nennen `LUECKE-001` mit dem Wortlaut „kein Gegenstück im griechischen System“ und für U10 den Wortlaut „U10-Beschluss 20.08.2026 - out of current scope“.

- [ ] T004 [US3] Ergänze in `specs/002-hebmama-retrieval-layer/test-prompts.md` drei Grenz-Prompts. Griechenland: erwarteter Nachweis `wissen/hinweise/luecken.md` und der Satz „kein Gegenstück im griechischen System“, kein Ordner `wissen/vorbereitung/gr/`. U10: erwarteter Wortlaut „U10-Beschluss 20.08.2026 - out of current scope“, erlaubte Datei nur `wissen/quellen/deutschland/u10-beschluss-2026-08-20/2026-08-20.md` und `wissen/hinweise/geltungsrahmen.md`, keine Datei `wissen/vergleich/eintraege/u10.md`. Archiv: eine Frage nach der Fassung vom 12.05.2023 darf `wissen/quellen/deutschland/kinder-richtlinie/2023-05-12.md` nur als Archiv nennen; die aktive Empfehlung bleibt `wissen/quellen/deutschland/kinder-richtlinie/2025-05-15.md`.

**Checkpoint**: Die drei Grenzen stehen in der Prompt-Datei und erfinden keine Untersuchung.

---

## Phase 4: Qualitätsprüfung (User Story 4)

**Goal**: Jeder Prompt wird gegen Antwortform und Verbote geprüft.

**Independent Test**: `specs/002-hebmama-retrieval-layer/checklists/retrieval.md` hat für jeden Prompt eine Zeile. Bestanden ist nur, wer Zusammenfassung, Vorbereitung und Fragen, und einen existierenden Pfad unter `wissen/` hat.

- [ ] T005 [US4] Lege `specs/002-hebmama-retrieval-layer/checklists/retrieval.md` an. Eine Zeile je Prompt aus `specs/002-hebmama-retrieval-layer/test-prompts.md` mit den Spalten Prompt, erwartete Untersuchung, gelesene Pfade, drei Ausgabeteile vorhanden, Verbot eingehalten, bestand. Prüfe dabei: kein Lesen des gesamten Ordners `wissen/`, keine aktive Empfehlung aus `wissen/quellen/deutschland/kinder-richtlinie/2023-05-12.md`, Griechenland nur über `LUECKE-001`, U10 nur mit „U10-Beschluss 20.08.2026 - out of current scope“.
- [ ] T006 [US4] Kontrolliere nach T005, dass unter `wissen/` keine Datei geändert wurde. Wenn ein Prompt einen Pfad nennt, der nicht existiert, markiere die Zeile in `specs/002-hebmama-retrieval-layer/checklists/retrieval.md` als nicht bestanden und korrigiere den Prompt, nicht den Wissensbestand.

---

## Dependencies & Execution Order

### Phase Dependencies

- **Phase 1**: sofort. T001 blockiert nichts Inhaltliches in `wissen/`, aber die Prompts sollen die Regel nicht umschreiben.
- **Phase 2**: nach T001. T002 vor oder zusammen mit T003, beide schreiben dieselbe Datei und laufen nacheinander.
- **Phase 3**: nach T003, weil T004 dieselbe Prompt-Datei ergänzt.
- **Phase 4**: nach T004.

### Parallel Opportunities

- T003 ist erst parallel zu T002, wenn die Prompt-Datei aufgeteilt würde. Sie bleibt eine Datei, deshalb T002 dann T003.
- T005 und T006 betreffen Prüfung und Bestand und laufen nacheinander.

## Implementation Strategy

1. Modul wortgleich lassen.
2. Prompts für alle zehn Untersuchungen auf beiden Wegen schreiben.
3. Grenzen für Griechenland, U10 und die Archivfassung ergänzen.
4. Qualitätsliste ausfüllen und `wissen/` unangetastet lassen.

## Notes

- Die medizinische Quelle bleibt Schicht 1. Diese Aufgaben erzeugen keine neue Leitlinie.
- U7a ist ein eigener Prompt, auch wenn die Reihe „U1 bis U9“ heißt.
