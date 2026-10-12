# Implementation Plan: HebMama Schicht 2 Retrieval-Layer

**Branch**: `002-hebmama-retrieval-layer` | **Date**: 2026-10-12 | **Status**: Draft | **Spec**: [spec.md](spec.md)

**Input**: Feature specification from `/specs/002-hebmama-retrieval-layer/spec.md`

## Summary

Schicht 2 ist die Abrufschicht über dem bestehenden Wissensbestand. Sie besteht aus der Regeldatei `.cursor/rules/hebmama-retrieval.mdc`, einer Prompt-Liste für U1 bis U9 einschließlich U7a und einer Qualitätsliste für Antwortform, `LUECKE-001` und den U10-Beschluss. Es kommt keine Anwendung und keine neue medizinische Quelle hinzu. `wissen/` wird nur gelesen.

Die Regeldatei ist mit dem vorgegebenen Wortlaut angelegt. Die Prompts und die Qualitätsliste entstehen in den Aufgaben.

## Technical Context

**Language/Version**: Markdown für Prompts und Prüfung, Cursor-Regel als `.mdc`

**Primary Dependencies**: Der Bestand `wissen/` und der Einstieg `wissen/README.md`. Aktive deutsche Fassung: `wissen/quellen/deutschland/kinder-richtlinie/2025-05-15.md`. Archiv: `wissen/quellen/deutschland/kinder-richtlinie/2023-05-12.md`.

**Storage**: Keine neue Ablage für medizinische Inhalte. Testdateien nur unter `specs/002-hebmama-retrieval-layer/`.

**Testing**: Lesende Prüfung der Prompts gegen die Regeldatei. Kein Testframework.

**Target Platform**: Antworten im Editor, wenn Dateien unter `wissen/` oder dieser Spezifikation betroffen sind.

**Project Type**: Abrufregeln über einem Markdown-Wissensbestand

**Performance Goals**: Eine Frage öffnet den Einstieg und danach nur die zur Untersuchung gehörenden Dateien, nicht den ganzen Ordner `wissen/`.

**Constraints**: Keine erfundene Empfehlung. Keine aktive Nutzung der Fassung vom 12.05.2023. Keine griechische U-Reihe. U10 nur als „U10-Beschluss 20.08.2026 - out of current scope“. Jede Antwort hat Zusammenfassung, Vorbereitung und Fragen, und einen Quellennachweis.

**Scale/Scope**: 1 Regeldatei, 20 Untersuchungs-Prompts, 2 Grenz-Prompts (Griechenland, U10), 1 Qualitätsliste.

## Constitution Check

*GATE: Must pass before research. Re-check after design.*

Die Verfassung unter `.specify/memory/constitution.md` ist nicht verabschiedet. Es gibt keine verletzten Gates.

**Vor der Ausarbeitung**: Bestanden.

**Nach der Ausarbeitung**: Bestanden. Die Schicht liest `wissen/` und schreibt nur Regel, Prompts und Prüfliste.

## Project Structure

### Documentation (this feature)

```text
specs/002-hebmama-retrieval-layer/
├── plan.md
├── spec.md
├── tasks.md
├── test-prompts.md          # Aufgabe T002 und T003
└── checklists/
    └── retrieval.md         # Aufgabe T004
```

### Retrieval module

```text
.cursor/rules/hebmama-retrieval.mdc
```

**Structure Decision**: Die Regel liegt bei den Cursor-Regeln und gilt für `wissen/**` und `specs/002-hebmama-retrieval-layer/**`. Die Prüfungen liegen neben der Spezifikation, damit `wissen/` unverändert bleibt.

## Implementation Sequence

1. Regeldatei auf den vorgegebenen Wortlaut prüfen.
2. `test-prompts.md` mit 20 Prompts für U1 bis U9 einschließlich U7a schreiben. Jeder Prompt nennt Weg, erwartete Untersuchung und erlaubte Pfade.
3. Dieselbe Datei um den Griechenland-Prompt mit `LUECKE-001` und den U10-Prompt ergänzen.
4. `checklists/retrieval.md` anlegen und die Prompts gegen Antwortform und Verbote prüfen.
5. Sicherstellen, dass unter `wissen/` keine Datei geändert wurde.

## Complexity Tracking

Keine Verstöße. Die Schicht fügt keine zweite Wissensbasis und kein Programm hinzu.
