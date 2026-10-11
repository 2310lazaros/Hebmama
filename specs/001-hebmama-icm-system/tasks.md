---

description: "Task list for HebMama ICM-Wissenssystem"
---

# Tasks: HebMama ICM-Wissenssystem

**Input**: Design documents from `/specs/001-hebmama-icm-system/`

**Prerequisites**: plan.md, spec.md, research.md, data-model.md, contracts/, quickstart.md

**Tests**: Keine Testdateien. Die Spezifikation verlangt kein TDD. Die Prüfung ist der Leseweg in `specs/001-hebmama-icm-system/quickstart.md` in der letzten Phase.

**Organization**: Aufgaben folgen den Benutzergeschichten. Jede Geschichte bleibt für sich prüfbar.

## Format: `[ID] [P?] [Story] Description`

- **[P]**: Kann parallel laufen (andere Dateien, keine Abhängigkeit zu unfertigen Geschwisteraufgaben)
- **[Story]**: Nur in den Geschichten-Phasen (`[US1]` … `[US4]`)
- Jede Aufgabe nennt einen konkreten Dateipfad

## Path Conventions

- Leserbestand: `wissen/` im Projektordner
- Vorlagen: `specs/001-hebmama-icm-system/contracts/`
- Die erste HTML-Kommentarzeile einer Vorlage wird nicht mitkopiert
- Keine Anwendung, kein `src/`

## Phase 1: Setup (Shared Infrastructure)

**Purpose**: Leere Ordnerstruktur aus `specs/001-hebmama-icm-system/plan.md` anlegen

- [X] T001 Lege ausschließlich diese Ordner an, ohne Dateien und ohne `wissen/vorbereitung/gr/` oder `u10`: `wissen/hinweise/`, `wissen/quellen/deutschland/kinder-richtlinie/`, `wissen/quellen/griechenland/myhealth/`, `wissen/quellen/griechenland/vivliario-ygeias-paidiou/`, `wissen/quellen/griechenland/mitroo-emvoliasmon/`, `wissen/quellen/who/postnatalversorgung-2022/`, `wissen/vergleich/eintraege/`, `wissen/vorbereitung/de/u1/` bis `wissen/vorbereitung/de/u9/` einschließlich `wissen/vorbereitung/de/u7a/`, `wissen/vorbereitung/who/kontakt-24-stunden/`, `wissen/vorbereitung/who/kontakt-48-72-stunden/`, `wissen/vorbereitung/who/kontakt-tag-7-14/`, `wissen/vorbereitung/who/kontakt-woche-6/`

---

## Phase 2: Foundational (Blocking Prerequisites)

**Purpose**: Orientierung, Geltungsrahmen und die fünf aktuellen Quellenwerke. Ohne diese Phase gibt es keine belegbare Aussage für die Geschichten.

**⚠️ CRITICAL**: Keine Benutzergeschichte beginnt vor dem Abschluss dieser Phase

- [X] T002 [P] Schreibe `wissen/hinweise/orientierung.md` aus `specs/001-hebmama-icm-system/contracts/vorlage-orientierung.md` mit dem Hinweis unmittelbar unter der ersten Überschrift: „HebMama ist eine Orientierungshilfe. Sie ersetzt weder den persönlichen ärztlichen Rat noch das Gelbe Heft noch den griechischen Gesundheitsnachweis. Bei akuten Beschwerden wenden Sie sich an eine Ärztin, einen Arzt oder den Notruf.“
- [X] T003 [P] Schreibe `wissen/hinweise/geltungsrahmen.md` aus `specs/001-hebmama-icm-system/contracts/vorlage-geltungsrahmen.md`. Im Bestand: U1, U2, U3, U4, U5, U6, U7, U7a, U8, U9; myHealth, elektronisches Kindergesundheitsheft, nationales Impfregister; WHO-Postnatalversorgung. Nicht im Bestand: Schwangerschaftsvorsorge, mütterliche Versorgung nach dem Postnatalfenster, U10, U11, J1, Schuleingangsuntersuchung, eine griechische U-Reihe ohne abgelegte Quelle, persönliche Kinderakten, Anmeldung bei myHealth
- [X] T004 [P] Lege `wissen/quellen/deutschland/kinder-richtlinie/index.md` und `wissen/quellen/deutschland/kinder-richtlinie/2025-05-15.md` aus `specs/001-hebmama-icm-system/contracts/vorlage-quellenwerk-index.md` und `specs/001-hebmama-icm-system/contracts/vorlage-quelle.md` an. ID `de-kinder-richtlinie`. Fundstelle https://www.g-ba.de/downloads/62-492-3998/Kinder-RL_2025-05-15_iK-2026-01-01.pdf. Herkunftstabelle vollständig: Aussteller, Amtlicher Titel, Deutsche Bezeichnung, Geltungsraum `Deutschland`, Fassung, Veröffentlichung, Inkrafttreten, Abrufdatum, Sprache, Fundstelle, Status `aktuell`. Genau eine Zeile `aktuell`. Abschnitte `Zusammenfassung`, `Tragende Aussagen`, `Nicht abgedeckt`. Deutsche Zusammenfassung, keine Vollabschrift. Zeitfenster nur im Wortlaut dieser PDF-Fassung; die Prüfliste in `specs/001-hebmama-icm-system/research.md` gilt nur als Kontrolle und verliert, wenn die PDF abweicht. U7a aufnehmen. U10 nicht als Untersuchung dieser Fassung führen
- [X] T005 [P] Lege `wissen/quellen/griechenland/myhealth/index.md` und eine Fassungsdatei `wissen/quellen/griechenland/myhealth/<fassung>.md` aus denselben Quellenvorlagen an. ID `gr-myhealth`. Geltungsraum `Griechenland`. Fundstelle https://ehealthrecord.gov.gr/ehfy-overview-details. Dieselbe vollständige Herkunftstabelle wie in T004, Status `aktuell`, Abschnitte `Zusammenfassung`, `Tragende Aussagen`, `Nicht abgedeckt`. Amtlicher Titel im Original. `mychildren.gr` nicht als Quelle verwenden. Dateiname ist die auf der Seite genannte Fassung; fehlt sie, heißt die Datei `fassung-abgerufen-YYYY-MM-DD.md` und Veröffentlichung ist `nicht angegeben`
- [X] T006 [P] Lege `wissen/quellen/griechenland/vivliario-ygeias-paidiou/index.md` und `wissen/quellen/griechenland/vivliario-ygeias-paidiou/<fassung>.md` an. ID `gr-vivliario-ygeias-paidiou`. Amtlicher Titel `Ηλεκτρονικό Βιβλιάριο Υγείας Παιδιού`. Fundstelle https://www.idika.gr/deltio-typou-diathesima-gia-olous-to-psifiako-vivliario-ygeias-paidiou-kai-to-ethniko-mitroo-emvoliasmon-paidion-kai-efivon/. Dieselbe Herkunftstabelle, Status `aktuell`, `Zusammenfassung`, `Tragende Aussagen`, `Nicht abgedeckt`. Keine erfundene U-Reihe
- [X] T007 [P] Lege `wissen/quellen/griechenland/mitroo-emvoliasmon/index.md` und `wissen/quellen/griechenland/mitroo-emvoliasmon/<fassung>.md` an. ID `gr-mitroo-emvoliasmon`. Amtlicher Titel `Εθνικό Μητρώο Εμβολιασμών Παιδιών και Εφήβων`. Fundstelle https://diadikasies.gov.gr/drasi/61cec97b-cbd9-4f0a-bcce-b1f0acf23a5e. Dieselbe Herkunftstabelle, Status `aktuell`, `Zusammenfassung`, `Tragende Aussagen`, `Nicht abgedeckt`. Keine persönliche Impffolge
- [X] T008 [P] Lege `wissen/quellen/who/postnatalversorgung-2022/index.md` und `wissen/quellen/who/postnatalversorgung-2022/isbn-978-92-4-004598-9.md` an. ID `who-postnatal-2022`. Geltungsraum `WHO`. Fundstelle https://www.who.int/publications/i/item/9789240045989. Dieselbe Herkunftstabelle, Status `aktuell`, `Zusammenfassung`, `Tragende Aussagen`, `Nicht abgedeckt`. Die vier Kontakte (erste 24 Stunden, 48 bis 72 Stunden, Tag 7 bis 14, Woche 6) nur aufnehmen, wenn diese Fassung sie nennt; sonst der Fassung folgen und die Abweichung unter `Nicht abgedeckt` festhalten
- [X] T009 Schreibe `wissen/quellen/index.md` aus `specs/001-hebmama-icm-system/contracts/vorlage-quellen-index.md`, nachdem T004 bis T008 fertig sind. Jede der fünf IDs hat einen direkten Link auf die aktuelle Fassungsdatei und einen Link auf das Werk-`index.md`. Orientierungslink `../hinweise/orientierung.md`
- [X] T010 [P] Schreibe `wissen/hinweise/glossar.md` aus `specs/001-hebmama-icm-system/contracts/vorlage-glossar.md` mit den Pflichtüberschriften `U-Untersuchung`, `Gelbes Heft`, `myHealth`, `Digitaler Impfpass`, `Postnatalversorgung`. Jede Erklärung verlinkt eine aktuelle Fassungsdatei. `Digitaler Impfpass` nennt `Εθνικό Μητρώο Εμβολιασμών Παιδιών και Εφήβων` und setzt den Namen nicht mit myHealth gleich. `myHealth` bleibt der Zugangsname
- [X] T011 [P] Schreibe `wissen/hinweise/luecken.md` aus `specs/001-hebmama-icm-system/contracts/vorlage-luecken.md` mit der Überschrift `## LUECKE-001`. Felder Thema, Bereich `Griechenland`, Was fehlt, Geprüfte Quellen, Status `offen` oder `geschlossen`, Datum. Status `offen`, wenn die drei griechischen Fassungen keine benannten Vorsorgekontakte mit Altersfenster enthalten; sonst `geschlossen` und den belegten Kontakt nennen. Keine selbst festgelegte Termin- oder Impffolge

**Checkpoint**: Fünf aktuelle Quellen, Glossar und Lückenregister sind lesbar. Geschichten können beginnen.

---

## Phase 3: User Story 1 - Vorsorgekontakt nach Alter einordnen (Priority: P1) 🎯 MVP

**Goal**: Vom Einstieg aus ist für ein Alter die deutsche Untersuchung oder der Zwischenraum, die griechische Beziehung und die WHO-Beziehung mit Herkunft sichtbar.

**Independent Test**: `wissen/README.md` öffnen, „Vergleich nach Alter“ folgen und für den 5. Lebenstag, ein Alter im 4. Lebensmonat und ein Alter im U9-Fenster die Zeile benennen. Ein Alter zwischen zwei äußeren Grenzen zeigt `Zwischenraum`.

### Implementation for User Story 1

- [X] T012 [P] [US1] Schreibe `wissen/vergleich/eintraege/u1.md` aus `specs/001-hebmama-icm-system/contracts/vorlage-vergleichseintrag.md`. ID `de-u1`. Altersfenster und Toleranz im Wortlaut von `wissen/quellen/deutschland/kinder-richtlinie/2025-05-15.md`. Beziehung Griechenland und Beziehung WHO je genau eines von `Entsprechung`, `teilweise Entsprechung`, `kein Gegenstück`. Postnatalfenster genau eines von `läuft`, `beendet`, `nicht betroffen`. Jeder Leitlinienabsatz beginnt mit `**Leitlinie.**` und verlinkt die aktuelle Fassungsdatei, nicht das Werk-`index.md`. Orientierungsabsätze beginnen mit `**Orientierung.**` und tragen keinen Quellenanspruch. Frühgeburt nur als Regel der Kinder-Richtlinie, ohne zweite Altersrechnung. Bei `kein Gegenstück` auf `wissen/hinweise/luecken.md#luecke-001` verlinken. Paketlink `../../vorbereitung/de/u1/index.md`. Keine Platzhalter `{{ }}`
- [X] T013 [P] [US1] Schreibe `wissen/vergleich/eintraege/u2.md` mit denselben Feldregeln wie T012. ID `de-u2`. Paketlink `../../vorbereitung/de/u2/index.md`
- [X] T014 [P] [US1] Schreibe `wissen/vergleich/eintraege/u3.md` mit denselben Feldregeln wie T012. ID `de-u3`. Paketlink `../../vorbereitung/de/u3/index.md`
- [X] T015 [P] [US1] Schreibe `wissen/vergleich/eintraege/u4.md` mit denselben Feldregeln wie T012. ID `de-u4`. Paketlink `../../vorbereitung/de/u4/index.md`. Postnatalfenster `beendet`, sobald das abgelegte WHO-Fenster vor diesem Alter endet
- [X] T016 [P] [US1] Schreibe `wissen/vergleich/eintraege/u5.md` mit denselben Feldregeln wie T012. ID `de-u5`. Paketlink `../../vorbereitung/de/u5/index.md`. Postnatalfenster `beendet`, wenn das WHO-Fenster vor diesem Alter endet
- [X] T017 [P] [US1] Schreibe `wissen/vergleich/eintraege/u6.md` mit denselben Feldregeln wie T012. ID `de-u6`. Paketlink `../../vorbereitung/de/u6/index.md`. Postnatalfenster `beendet`, wenn das WHO-Fenster vor diesem Alter endet
- [X] T018 [P] [US1] Schreibe `wissen/vergleich/eintraege/u7.md` mit denselben Feldregeln wie T012. ID `de-u7`. Paketlink `../../vorbereitung/de/u7/index.md`. Postnatalfenster `beendet`, wenn das WHO-Fenster vor diesem Alter endet
- [X] T019 [P] [US1] Schreibe `wissen/vergleich/eintraege/u7a.md` mit denselben Feldregeln wie T012. ID `de-u7a`. Paketlink `../../vorbereitung/de/u7a/index.md`. Postnatalfenster `beendet`, wenn das WHO-Fenster vor diesem Alter endet
- [X] T020 [P] [US1] Schreibe `wissen/vergleich/eintraege/u8.md` mit denselben Feldregeln wie T012. ID `de-u8`. Paketlink `../../vorbereitung/de/u8/index.md`. Postnatalfenster `beendet`, wenn das WHO-Fenster vor diesem Alter endet
- [X] T021 [P] [US1] Schreibe `wissen/vergleich/eintraege/u9.md` mit denselben Feldregeln wie T012. ID `de-u9`. Paketlink `../../vorbereitung/de/u9/index.md`. WHO-Beziehung `kein Gegenstück`, sofern die Fassung keinen U9-Kontakt nennt, und Postnatalfenster `beendet`
- [X] T022 [P] [US1] Schreibe `wissen/vergleich/nach-alter.md` aus `specs/001-hebmama-icm-system/contracts/vorlage-nach-alter.md`, nachdem T012 bis T021 fertig sind. Lage nur `Zeitraum`, `frühe Toleranz`, `späte Toleranz`, `Zwischenraum` oder `außerhalb`. Jeder Zeitpunkt von vor der Geburt bis nach dem Ende der U9-Toleranz fällt in genau eine Zeile. Zwischenräume heißen `keine U-Untersuchung anstehend` und verlinken letzte und nächste Untersuchung. Die Spalte WHO nutzt nur `Entsprechung`, `teilweise Entsprechung` oder `kein Gegenstück`. Das Postnatalfenster steht in einer eigenen Spalte mit `läuft`, `beendet` oder `nicht betroffen`. Keine leere Zelle, keine Platzhalter
- [X] T023 [P] [US1] Schreibe `wissen/vergleich/nach-untersuchung.md` aus `specs/001-hebmama-icm-system/contracts/vorlage-nach-untersuchung.md`, nachdem T012 bis T021 fertig sind. Zehn Zeilen in der Reihenfolge U1, U2, U3, U4, U5, U6, U7, U7a, U8, U9. Zeitraum und Toleranz im Wortlaut der Kinder-Richtlinie; ohne eigene Toleranz der Satz `keine eigene Toleranz angegeben`. Dieselben Beziehungswörter und dasselbe Postnatalfenster wie in T022. Jede Zeile verlinkt dieselbe Datei unter `wissen/vergleich/eintraege/` wie der Altersweg
- [X] T024 [US1] Schreibe `wissen/vergleich/index.md` aus `specs/001-hebmama-icm-system/contracts/vorlage-vergleich-index.md` mit Links auf `nach-alter.md`, `nach-untersuchung.md` und alle zehn Einträge samt Paketpfaden. Keine leere Beziehungszelle
- [X] T025 [US1] Schreibe `wissen/README.md` aus `specs/001-hebmama-icm-system/contracts/vorlage-einstieg.md` mit Zielgruppe, den drei Säulen und direkten Links auf `hinweise/orientierung.md`, `hinweise/geltungsrahmen.md`, `hinweise/glossar.md`, `hinweise/luecken.md`, `quellen/index.md`, `vergleich/index.md`, `vergleich/nach-alter.md`, `vergleich/nach-untersuchung.md`. Den Link auf `vorbereitung/index.md` erst in T041 setzen

**Checkpoint**: Szenario 1 und 2 aus `specs/001-hebmama-icm-system/quickstart.md` sind ohne Vorbereitungspakete prüfbar.

---

## Phase 4: User Story 2 - Vorsorgetermin vorbereiten (Priority: P2)

**Goal**: Jeder deutsche Kontakt und jeder abgelegte WHO-Postnatalkontakt hat Leitfaden, Checkliste und Fragenliste.

**Independent Test**: Allein `wissen/vorbereitung/de/u4/index.md` öffnen und Zweck, mindestens drei Vorbereitungs- oder Mitbringpunkte und mindestens fünf Fragen nennen. Leitlinie und Orientierung sind unterscheidbar.

### Implementation for User Story 2

- [X] T026 [P] [US2] Lege das Paket U1 in `wissen/vorbereitung/de/u1/index.md`, `wissen/vorbereitung/de/u1/leitfaden.md`, `wissen/vorbereitung/de/u1/checkliste.md` und `wissen/vorbereitung/de/u1/fragen.md` aus `specs/001-hebmama-icm-system/contracts/vorlage-paket-index.md`, `specs/001-hebmama-icm-system/contracts/vorlage-leitfaden.md`, `specs/001-hebmama-icm-system/contracts/vorlage-checkliste.md` und `specs/001-hebmama-icm-system/contracts/vorlage-fragen.md` an. ID `de-u1`. Betrifft Kind und Mutter, wo `Tragende Aussagen` das tun. Checkliste mit den Abschnitten `Vor dem Termin`, `Mitbringen`, `Am Termin`, `Danach`; die ersten beiden zusammen mindestens drei Punkte. Mindestens fünf Fragen. Jeder Punkt beginnt mit `**Leitlinie.**` oder `**Orientierung.**`. Leitlinie verlinkt `wissen/quellen/deutschland/kinder-richtlinie/2025-05-15.md`. Keine Eingabefelder für den Namen eines Kindes, ein individuelles Geburtsdatum, individuelle Impfdaten, einen Befund, eine Dosierung, eine Diagnose oder eine persönliche Impffolge. Orientierungslink `../../../hinweise/orientierung.md`
- [X] T027 [P] [US2] Lege das Paket U2 unter `wissen/vorbereitung/de/u2/` mit denselben vier Dateien und denselben Regeln wie T026 an. ID `de-u2`. Betrifft Kind und Mutter, wo die tragenden Aussagen das tun
- [X] T028 [P] [US2] Lege das Paket U3 unter `wissen/vorbereitung/de/u3/` mit denselben vier Dateien und denselben Regeln wie T026 an. ID `de-u3`. Betrifft Kind und Mutter, wo die tragenden Aussagen das tun
- [X] T029 [P] [US2] Lege das Paket U4 unter `wissen/vorbereitung/de/u4/` mit denselben vier Dateien und denselben Regeln wie T026 an. ID `de-u4`. Keine mütterliche Postnatalempfehlung als anstehenden Termin. Keine Schwangerschaftsthemen
- [X] T030 [P] [US2] Lege das Paket U5 unter `wissen/vorbereitung/de/u5/` mit denselben vier Dateien und denselben Regeln wie T026 an. ID `de-u5`. Keine mütterliche Postnatalempfehlung als anstehenden Termin
- [X] T031 [P] [US2] Lege das Paket U6 unter `wissen/vorbereitung/de/u6/` mit denselben vier Dateien und denselben Regeln wie T026 an. ID `de-u6`. Keine mütterliche Postnatalempfehlung als anstehenden Termin
- [X] T032 [P] [US2] Lege das Paket U7 unter `wissen/vorbereitung/de/u7/` mit denselben vier Dateien und denselben Regeln wie T026 an. ID `de-u7`. Keine mütterliche Postnatalempfehlung als anstehenden Termin
- [X] T033 [P] [US2] Lege das Paket U7a unter `wissen/vorbereitung/de/u7a/` mit denselben vier Dateien und denselben Regeln wie T026 an. ID `de-u7a`. Keine mütterliche Postnatalempfehlung als anstehenden Termin
- [X] T034 [P] [US2] Lege das Paket U8 unter `wissen/vorbereitung/de/u8/` mit denselben vier Dateien und denselben Regeln wie T026 an. ID `de-u8`. Keine mütterliche Postnatalempfehlung als anstehenden Termin
- [X] T035 [P] [US2] Lege das Paket U9 unter `wissen/vorbereitung/de/u9/` mit denselben vier Dateien und denselben Regeln wie T026 an. ID `de-u9`. Keine mütterliche Postnatalempfehlung als anstehenden Termin
- [X] T036 [P] [US2] Lege das WHO-Paket erste 24 Stunden unter `wissen/vorbereitung/who/kontakt-24-stunden/` mit `index.md`, `leitfaden.md`, `checkliste.md`, `fragen.md` an. ID `who-24h`. Dieselben Listenregeln wie T026. Betrifft `beide`, wo die WHO-Fassung das tut. Vergleichslinks auf die deutschen Einträge, deren Altersfenster diesen Kontakt berühren. Quelle `wissen/quellen/who/postnatalversorgung-2022/isbn-978-92-4-004598-9.md`
- [X] T037 [P] [US2] Lege das WHO-Paket 48 bis 72 Stunden unter `wissen/vorbereitung/who/kontakt-48-72-stunden/` mit denselben vier Dateien und denselben Regeln wie T036 an. ID `who-48-72h`
- [X] T038 [P] [US2] Lege das WHO-Paket Tag 7 bis 14 unter `wissen/vorbereitung/who/kontakt-tag-7-14/` mit denselben vier Dateien und denselben Regeln wie T036 an. ID `who-d7-14`
- [X] T039 [P] [US2] Lege das WHO-Paket Woche 6 unter `wissen/vorbereitung/who/kontakt-woche-6/` mit denselben vier Dateien und denselben Regeln wie T036 an. ID `who-w6`
- [X] T040 [US2] Schreibe `wissen/vorbereitung/index.md` aus `specs/001-hebmama-icm-system/contracts/vorlage-vorbereitung-index.md` mit den zehn deutschen Paketen und den vier WHO-Paketen. Keinen Ordner `wissen/vorbereitung/gr/` anlegen; stattdessen auf `wissen/hinweise/luecken.md` verweisen
- [X] T041 [US2] Ergänze in `wissen/README.md` den direkten Link auf `vorbereitung/index.md`, ohne die Links aus T025 zu entfernen

**Checkpoint**: Szenario 3 aus `specs/001-hebmama-icm-system/quickstart.md` ist an U4 und am Paket `kontakt-24-stunden` prüfbar.

---

## Phase 5: User Story 3 - Eine Aussage zur Quelle zurückverfolgen (Priority: P2)

**Goal**: Jede Zeit- und Inhaltsaussage in Vergleich und Paketen endet bei Aussteller, amtlichem Titel, Fassung und Fundstelle.

**Independent Test**: In `wissen/vergleich/eintraege/u2.md` einen Absatz `**Leitlinie.**` wählen und in höchstens drei Dateiwechseln vom Einstieg aus bei der Herkunftstabelle der aktuellen Fassung ankommen.

### Implementation for User Story 3

- [X] T042 [P] [US3] Prüfe jeden Absatz und Listenpunkt mit `**Leitlinie.**` in `wissen/vergleich/` und `wissen/vorbereitung/` und ergänze fehlende relative Links auf die aktuelle Fassungsdatei. Kein Leitlinienlink zeigt auf ein Werk-`index.md`. Jeder Eintrag unter `wissen/vergleich/eintraege/` behält die Tabelle `Verwendete Fassungen` mit genau einer Zeile `aktuell` je genutztem Werk
- [X] T043 [P] [US3] Prüfe jede Fassungsdatei unter `wissen/quellen/` auf die Herkunftsfelder Aussteller, Amtlicher Titel, Geltungsraum, Fassung, Veröffentlichung, Inkrafttreten, Abrufdatum, Sprache, Fundstelle und Status. Griechische und englische Amtstitel bleiben in der Originalsprache, mit deutscher Bezeichnung daneben. Dieselbe Regel gilt für die Originalbegriffe in `wissen/hinweise/glossar.md`
- [X] T044 [US3] Richte die Wege aus `specs/001-hebmama-icm-system/contracts/navigationsregeln.md` in `wissen/README.md`, `wissen/quellen/index.md`, `wissen/vergleich/nach-alter.md`, `wissen/vergleich/nach-untersuchung.md` und `wissen/vorbereitung/index.md`: aktuelle Fassung in 2 Schritten, ersetzte Fassung in 3 Schritten, Vergleichseintrag in 2 Schritten, Paket in 2 Schritten, Leitfaden in 3 Schritten. Ein Schritt ist nur das Öffnen einer anderen Datei

**Checkpoint**: Szenario 4 aus `specs/001-hebmama-icm-system/quickstart.md` gelingt für U2.

---

## Phase 6: User Story 4 - Leitlinie in der ICM-Ablage pflegen (Priority: P3)

**Goal**: Eine weitere Quelle lässt sich ablegen, eine alte Fassung bleibt als `ersetzt` stehen, und eine Lücke wird nicht mit einer eigenen Terminfolge gefüllt.

**Independent Test**: Vom Einstieg in höchstens drei Schritten eine neu abgelegte Quelle öffnen. Im Ordner der Kinder-Richtlinie ist genau eine Fassung `aktuell`, eine ältere bleibt auffindbar und `ersetzt`, sofern sie amtlich abrufbar war. Es gibt weiterhin keine Datei `wissen/vergleich/eintraege/u10.md`.

### Implementation for User Story 4

- [X] T045 [P] [US4] Lege das Quellenwerk Kinderuntersuchungsheft unter `wissen/quellen/deutschland/kinderuntersuchungsheft/index.md` und `wissen/quellen/deutschland/kinderuntersuchungsheft/<fassung>.md` an. Fundstelle https://www.g-ba.de/downloads/83-691-1068/2025-05-15_G-BA_Kinderuntersuchungsheft_WEB_WZ_PW.pdf. Dieselbe Herkunftstabelle wie in T004, Geltungsraum `Deutschland`, Status `aktuell`, `Zusammenfassung`, `Tragende Aussagen`, `Nicht abgedeckt`. Keinen neuen Vergleichseintrag anlegen
- [X] T046 [P] [US4] Ermittle auf https://www.g-ba.de/ die Kinder-Richtlinie, die der Fassung vom 15. Mai 2025 unmittelbar vorausgeht. Lege sie als `wissen/quellen/deutschland/kinder-richtlinie/<datum>.md` mit Status `ersetzt` ab und setze in `wissen/quellen/deutschland/kinder-richtlinie/index.md` genau eine Zeile auf `aktuell` für `2025-05-15.md`. Leitlinienlinks in `wissen/vergleich/` und `wissen/vorbereitung/` bleiben auf `2025-05-15.md`. Ist keine Vorfassung abrufbar, keine Datei erfinden; im Werkindex Abrufdatum und die erfolglose Suche vermerken
- [X] T047 [P] [US4] Lege den Beschluss vom 20. August 2026 als eigenes Werk `wissen/quellen/deutschland/u10-beschluss-2026-08-20/index.md` und `wissen/quellen/deutschland/u10-beschluss-2026-08-20/2026-08-20.md` an. Fundstelle https://www.g-ba.de/downloads/39-261-7982/2026-08-20_Kinder-RL_Einfuehrung-U10-Dokumentation-J1-WZ.pdf. Status `aktuell` für diesen Beschluss. Die Zusammenfassung verweist auf `wissen/hinweise/geltungsrahmen.md` und legt keine Datei `wissen/vergleich/eintraege/u10.md` und kein Paket `wissen/vorbereitung/de/u10/` an
- [X] T048 [US4] Ergänze in `wissen/quellen/index.md` die Werke aus T045 und T047 mit direktem Link auf die aktuelle Fassung und auf das Werk-`index.md`. Prüfe `wissen/hinweise/luecken.md`: `## LUECKE-001` bleibt stehen. Status nur auf `geschlossen` setzen, wenn eine abgelegte griechische Fassung den fehlenden U-Kontakt belegt; sonst `offen` lassen. Keine griechische Terminfolge ergänzen

**Checkpoint**: Szenario 5 und 6 aus `specs/001-hebmama-icm-system/quickstart.md` sind prüfbar. Szenario 6 entfällt nur in dem dokumentierten Fall, dass keine Vorfassung abrufbar war.

---

## Phase 7: Polish & Cross-Cutting Concerns

**Purpose**: Der ganze Bestand besteht den Leseweg

- [X] T049 [P] Entferne in `wissen/` jeden verbliebenen Platzhalter `{{` und jede mitkopierte Zeile `<!-- Vorlage:`
- [X] T050 [P] Prüfe jede Markdown-Datei unter `wissen/` und setze den Orientierungshinweis aus T002 unmittelbar unter die erste Überschrift, mit der Linktiefe aus `specs/001-hebmama-icm-system/contracts/navigationsregeln.md`
- [X] T051 [P] Prüfe, dass `wissen/vergleich/eintraege/u10.md`, `wissen/vorbereitung/de/u10/` und `wissen/vorbereitung/gr/` fehlen und dass kein Dokument Eingabefelder für den Namen eines Kindes, ein individuelles Geburtsdatum, individuelle Impfdaten, einen Befund, eine Dosierung, eine Diagnose oder eine persönliche Impffolge enthält
- [X] T052 Führe die Szenarien 1 bis 6 und die Suchprüfungen in `specs/001-hebmama-icm-system/quickstart.md` aus und behebe Abweichungen in den dort genannten Dateien unter `wissen/`

---

## Dependencies & Execution Order

### Phase Dependencies

- **Setup (Phase 1)**: sofort
- **Foundational (Phase 2)**: nach T001, blockiert alle Geschichten
- **User Story 1 (Phase 3)**: nach Phase 2
- **User Story 2 (Phase 4)**: nach Phase 2. Paketlinks in den Einträgen aus Phase 3 werden erst hier zu echten Dateien. Die Altersprüfung von US1 braucht die Pakete nicht
- **User Story 3 (Phase 5)**: nach US1 und US2, weil sie deren Leitlinienabsätze prüft
- **User Story 4 (Phase 6)**: nach Phase 2. Sie bearbeitet andere Werkordner als US1 und kann nach den Quellen starten; die Linkkontrolle auf `2025-05-15.md` setzt voraus, dass US1 und US2 ihre Links schon gesetzt haben
- **Polish (Phase 7)**: nach den gewünschten Geschichten

### User Story Dependencies

- **US1 (P1)**: nur Phase 2. Kein Bedarf an US2, US3 oder US4
- **US2 (P2)**: nur Phase 2 für die Quellen. Die Einträge aus US1 liefern die Paketziele, die Prüfung eines einzelnen U4-Pakets gelingt auch ohne den Altersweg
- **US3 (P2)**: nutzt die Aussagen aus US1 und US2
- **US4 (P3)**: nutzt die Ablageregeln aus Phase 2 und lässt die zehn Einträge unverändert

### Within Each User Story

- T004 bis T008 vor T009; T009 vor T010 und T011
- T012 bis T021 vor T022 und T023; beide vor T024; T024 vor T025
- T026 bis T039 vor T040; T040 vor T041
- T042 und T043 vor T044
- T045, T046 und T047 vor T048
- T049, T050 und T051 vor T052

### Parallel Opportunities

- T002 bis T008 parallel nach T001
- T010 und T011 parallel nach T009
- T012 bis T021 parallel
- T022 und T023 parallel nach T021
- T026 bis T039 parallel
- T042 und T043 parallel
- T045, T046 und T047 parallel
- T049, T050 und T051 parallel

---

## Parallel Example: User Story 1

```bash
# Nach Phase 2, zehn Einträge gleichzeitig:
Task: "T012 wissen/vergleich/eintraege/u1.md"
Task: "T013 wissen/vergleich/eintraege/u2.md"
Task: "T014 wissen/vergleich/eintraege/u3.md"
Task: "T015 wissen/vergleich/eintraege/u4.md"
Task: "T016 wissen/vergleich/eintraege/u5.md"
Task: "T017 wissen/vergleich/eintraege/u6.md"
Task: "T018 wissen/vergleich/eintraege/u7.md"
Task: "T019 wissen/vergleich/eintraege/u7a.md"
Task: "T020 wissen/vergleich/eintraege/u8.md"
Task: "T021 wissen/vergleich/eintraege/u9.md"

# Danach die beiden Wege gleichzeitig:
Task: "T022 wissen/vergleich/nach-alter.md"
Task: "T023 wissen/vergleich/nach-untersuchung.md"
```

---

## Parallel Example: User Story 2

```bash
# Vierzehn Pakete gleichzeitig, je vier Dateien im eigenen Ordner:
Task: "T026 wissen/vorbereitung/de/u1/"
Task: "T027 wissen/vorbereitung/de/u2/"
Task: "T028 wissen/vorbereitung/de/u3/"
Task: "T029 wissen/vorbereitung/de/u4/"
Task: "T030 wissen/vorbereitung/de/u5/"
Task: "T031 wissen/vorbereitung/de/u6/"
Task: "T032 wissen/vorbereitung/de/u7/"
Task: "T033 wissen/vorbereitung/de/u7a/"
Task: "T034 wissen/vorbereitung/de/u8/"
Task: "T035 wissen/vorbereitung/de/u9/"
Task: "T036 wissen/vorbereitung/who/kontakt-24-stunden/"
Task: "T037 wissen/vorbereitung/who/kontakt-48-72-stunden/"
Task: "T038 wissen/vorbereitung/who/kontakt-tag-7-14/"
Task: "T039 wissen/vorbereitung/who/kontakt-woche-6/"
```

---

## Implementation Strategy

### MVP First (User Story 1 Only)

1. Phase 1 abschließen
2. Phase 2 abschließen
3. Phase 3 abschließen
4. **STOP and VALIDATE**: Szenario 1 und 2 in `specs/001-hebmama-icm-system/quickstart.md`
5. Erst danach Pakete, Herkunftsgang und weitere Quellen

### Incremental Delivery

1. Setup und Grundlagen liefern die belegten Quellen
2. US1 liefert den Vergleich nach Alter und nach Untersuchung
3. US2 liefert die vierzehn Vorbereitungspakete
4. US3 zieht jede Leitlinienaussage auf die Herkunftstabelle
5. US4 legt weitere Werke ab und behält ersetzte Fassungen

### Parallel Team Strategy

1. Gemeinsam T001, dann T002 bis T008 verteilt auf die fünf Quellenwerke
2. Nach T009 eine Person US1 (Einträge), eine andere kann die Quelltexte gegenlesen
3. Nach US1 die vierzehn Pakete von US2 verteilen
4. US3 und US4 folgen, weil sie dieselben Links und `wissen/quellen/index.md` nachziehen

---

## Notes

- `[P]` bedeutet andere Dateien und keine Abhängigkeit zu unfertigen Geschwisteraufgaben
- Die Verfassung unter `.specify/memory/constitution.md` ist nicht verabschiedet und erzeugt keine zusätzlichen Aufgaben
- Keine Vollabschrift amtlicher Leitlinien
- Zeitfenster, WHO-Kontakte und griechische Gegenstücke kommen aus den abgelegten Fassungen, nicht aus der Prüfliste in `research.md`
