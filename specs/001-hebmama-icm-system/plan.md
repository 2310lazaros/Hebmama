# Implementation Plan: HebMama ICM-Wissenssystem

**Branch**: `001-hebmama-icm-system` | **Date**: 2026-10-12 | **Status**: abgeschlossen / completed | **Spec**: [spec.md](spec.md)

**Input**: Feature specification from `/specs/001-hebmama-icm-system/spec.md`

**Note**: This template is filled in by the `/speckit-plan` command; its definition describes the execution workflow.

## Summary

HebMama wird ein offline lesbarer Wissensbestand in GitHub-Flavored Markdown. Betreuungspersonen ordnen darüber die deutschen Untersuchungen U1 bis U9 einschließlich U7a gegenüber dem griechischen Weg (myHealth, elektronisches Kindergesundheitsheft, nationales Impfregister) und gegenüber vier WHO-Postnatalkontakten ein und öffnen je Kontakt ein Vorbereitungspaket aus Leitfaden, Checkliste und Fragenliste.

Der Leserbestand liegt unter `wissen/`. Kopiervorlagen und Linkregeln liegen unter `specs/001-hebmama-icm-system/contracts/`. Herkunft, Beziehungswörter und der Orientierungshinweis stehen sichtbar im Dokument. Es gibt keine Anwendung, keine Datenbank und keine persönliche Kinderakte.

## Technical Context

**Language/Version**: GitHub-Flavored Markdown, lesbar in einer Markdown-Vorschau

**Primary Dependencies**: Amtliche Veröffentlichungen, keine Programmbibliotheken. Erste Werke und Fundstellen stehen in [research.md](research.md).

**Storage**: Markdown-Dateien im Ordner `wissen/`

**Testing**: Leseweg und Suchprüfungen aus [quickstart.md](quickstart.md). Kein Testframework.

**Target Platform**: Lokales Lesen, offline, in Editor oder Dateiansicht

**Project Type**: Wissenskorpus

**Performance Goals**: Eine Altersfrage in höchstens 3 Minuten vom Einstieg aus. Ein Paket in höchstens 10 Minuten. Jede Quelle, jeder Vergleichseintrag und jedes Paket in höchstens 3 Linkschritten.

**Constraints**: Deutsch mit erhaltenen Amtsbegriffen. Jede Sachaussage verlinkt die aktuelle Quellfassung. Beziehung nur als `Entsprechung`, `teilweise Entsprechung` oder `kein Gegenstück`. Keine personenbezogenen Kinddaten, keine Diagnose, keine Dosierung, kein persönlicher Impfplan. Zusammenfassungen statt Vollabschrift. U10 bleibt außerhalb.

**Scale/Scope**: 1 Einstieg, 4 Hinweisdokumente, 5 Quellenwerke, 10 Vergleichseinträge, 2 Vergleichswege, 14 Vorbereitungspakete mit je 4 Dateien. Griechische Pakete nur, wenn später ein benannter Kontakt abgelegt wird.

## Constitution Check

*GATE: Must pass before Phase 0 research. Re-check after Phase 1 design.*

Die Verfassung unter `.specify/memory/constitution.md` ist weiterhin die unausgefüllte Vorlage. Es sind keine Grundsätze verabschiedet. Die Spezifikation hält das fest. Deshalb gibt es keine verletzten Gates.

**Vor Phase 0**: Bestanden. Keine Grundsätze, gegen die der Markdown-Korpus verstoßen könnte.

**Nach Phase 1**: Bestanden. Datenmodell, Verträge und Leseweg bleiben bei den drei Säulen der Spezifikation. Sie führen keine Anwendung, keine Akte und keine U10 ein. Die griechischen Werke sind die amtlichen Teile des beauftragten Weges über myHealth und den digitalen Impfpass, kein vierter Vergleich.

## Project Structure

### Documentation (this feature)

```text
specs/001-hebmama-icm-system/
├── plan.md
├── research.md
├── data-model.md
├── quickstart.md
├── contracts/
│   ├── README.md
│   ├── navigationsregeln.md
│   ├── vorlage-einstieg.md
│   ├── vorlage-geltungsrahmen.md
│   ├── vorlage-orientierung.md
│   ├── vorlage-glossar.md
│   ├── vorlage-luecken.md
│   ├── vorlage-quellen-index.md
│   ├── vorlage-quellenwerk-index.md
│   ├── vorlage-quelle.md
│   ├── vorlage-vergleich-index.md
│   ├── vorlage-nach-alter.md
│   ├── vorlage-nach-untersuchung.md
│   ├── vorlage-vergleichseintrag.md
│   ├── vorlage-vorbereitung-index.md
│   ├── vorlage-paket-index.md
│   ├── vorlage-leitfaden.md
│   ├── vorlage-checkliste.md
│   └── vorlage-fragen.md
├── spec.md
├── checklists/
│   └── requirements.md
└── tasks.md             # erst durch /speckit-tasks
```

### Source Code (repository root)

```text
wissen/
├── README.md
├── hinweise/
│   ├── geltungsrahmen.md
│   ├── orientierung.md
│   ├── glossar.md
│   └── luecken.md
├── quellen/
│   ├── index.md
│   ├── deutschland/
│   │   └── kinder-richtlinie/
│   │       ├── index.md
│   │       └── <fassung>.md
│   ├── griechenland/
│   │   ├── myhealth/
│   │   │   ├── index.md
│   │   │   └── <fassung>.md
│   │   ├── vivliario-ygeias-paidiou/
│   │   │   ├── index.md
│   │   │   └── <fassung>.md
│   │   └── mitroo-emvoliasmon/
│   │       ├── index.md
│   │       └── <fassung>.md
│   └── who/
│       └── postnatalversorgung-2022/
│           ├── index.md
│           └── <fassung>.md
├── vergleich/
│   ├── index.md
│   ├── nach-alter.md
│   ├── nach-untersuchung.md
│   └── eintraege/
│       ├── u1.md
│       ├── u2.md
│       ├── u3.md
│       ├── u4.md
│       ├── u5.md
│       ├── u6.md
│       ├── u7.md
│       ├── u7a.md
│       ├── u8.md
│       └── u9.md
└── vorbereitung/
    ├── index.md
    ├── de/
    │   ├── u1/
    │   ├── u2/
    │   ├── u3/
    │   ├── u4/
    │   ├── u5/
    │   ├── u6/
    │   ├── u7/
    │   ├── u7a/
    │   ├── u8/
    │   └── u9/
    └── who/
        ├── kontakt-24-stunden/
        ├── kontakt-48-72-stunden/
        ├── kontakt-tag-7-14/
        └── kontakt-woche-6/
```

Jeder Ordner unter `vorbereitung/de/` und `vorbereitung/who/` enthält `index.md`, `leitfaden.md`, `checkliste.md` und `fragen.md`.

**Structure Decision**: Der Leserbestand ist `wissen/` und folgt den fünf Bereichen der Spezifikation: Einstieg, Hinweise, Quellen, Vergleich, Vorbereitung. Vorlagen liegen bei den Verträgen, damit ungefüllte Platzhalter nicht neben den Lesertexten stehen. Es gibt keinen Anwendungscode.

## Implementation Sequence

Die Reihenfolge hält die Links gültig und verhindert, dass Sachaussagen vor den Quellen entstehen.

1. Hinweisdokumente aus den Vorlagen anlegen: Orientierung, Geltungsrahmen, leeres Glossar, Lückenregister mit `LUECKE-001`.
2. Die fünf Quellenwerke anlegen. Je Werk `index.md` und genau eine aktuelle Fassung mit Herkunft, Zusammenfassung und tragenden Aussagen. Keine Vollabschrift.
3. Glossar mit den fünf Pflichtbegriffen aus diesen Fassungen füllen.
4. Vergleichswege und zehn Einträge füllen. Zeitfenster nur aus der abgelegten Kinder-Richtlinie. Griechenland bleibt `kein Gegenstück`, bis eine Fassung einen benannten Kontakt hergibt. WHO-Beziehung und Postnatalfenster erst nach dem Lesen der WHO-Fassung eintragen.
5. Vierzehn Pakete aus den Paketvorlagen füllen. Leitlinienpunkte nur aus tragenden Aussagen.
6. `wissen/README.md` zuletzt auf die dann vorhandenen Ziele verlinken.
7. Den Leseweg in [quickstart.md](quickstart.md) durchgehen.

Eine spätere Fassung wird als neue Datei abgelegt. Die bisherige Zeile im Werkindex wechselt auf `ersetzt`. Vergleich und Pakete zeigen weiter nur auf `aktuell`.

## Complexity Tracking

Keine Verstöße. Die Verfassung enthält keine beschlossenen Grundsätze, die eine einfachere Form verlangen oder diese Form verbieten.
