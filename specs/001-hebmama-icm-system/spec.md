# Feature Specification: HebMama ICM-System für Mütter- und Kindergesundheit

**Feature Branch**: `001-hebmama-icm-system`

**Created**: 2026-10-12

**Status**: abgeschlossen / completed

**Input**: User description: "Ich erstelle das Projekt HebMama als strukturiertes System für Mütter- und Kindergesundheit nach der Interpretable Context Methodology (ICM). Inhaltlicher Kern: 1. Pädiatrische Vorsorge und Neugeborenenbegleitung im Vergleich (Deutsche U1-U9 Kinder-Richtlinie vs. griechisches Gesundheitssystem mit myHealth/Digitalem Impfpass sowie WHO-Leitlinien für die Postnatalversorgung). 2. Strukturierte Leitfäden, Checklisten und Vorbereitungsdokumente für Arzt- und Vorsorgetermine. 3. Systematische Ablage aller Richtlinien in einer klaren, menschenlesbaren Markdown-Ordnerstruktur (ICM)."

## User Scenarios & Testing *(mandatory)*



### User Story 1 - Vorsorgekontakt nach Alter einordnen (Priority: P1)

Eine Betreuungsperson (Mutter, Vater oder andere sorgeberechtigte Person) möchte für ein bestimmtes Kindesalter oder eine genannte Untersuchung wissen, welche deutsche U-Untersuchung ansteht, wie sich der griechische Vorsorge- und Impfpassweg über myHealth dazu verhält und ob in diesem Zeitraum noch ein WHO-Kontakt der Postnatalversorgung gilt.

**Why this priority**: Der Vergleich der drei Systeme ist der inhaltliche Kern von HebMama. Ohne diese Einordnung bleiben Leitfäden und Checklisten ohne verlässlichen Bezug.

**Independent Test**: Eine Person, die die amtlichen Leitlinien nicht gelesen hat, kann allein vom Einstiegsdokument aus für drei vorgegebene Alter (5. Lebenstag, 4. Lebensmonat, Alter im U9-Fenster) die deutsche Untersuchung oder die Lücke, die griechische Beziehung und die WHO-Beziehung benennen.

**Acceptance Scenarios**:

1. **Given** der Wissensbestand und ein Kind am 5. Lebenstag, **When** die Betreuungsperson den Vergleich über den Altersweg öffnet, **Then** sieht sie die dafür zuständige deutsche U-Untersuchung mit dem Altersfenster aus der abgelegten Kinder-Richtlinie, die griechische Beziehung (Entsprechung, teilweise Entsprechung oder kein Gegenstück) und den passenden WHO-Postnatalkontakt, jeweils mit Herkunftsangabe.
2. **Given** ein Kind im Altersfenster von U9, **When** die Betreuungsperson den Vergleich öffnet, **Then** sind die WHO-Postnatalkontakte als nicht mehr anstehend gekennzeichnet, und die griechische Beziehung ist ohne erfundene U9-Kopie dargestellt.
3. **Given** ein Alter, das zwischen zwei U-Fenstern liegt, **When** die Betreuungsperson dieses Alter nachschlägt, **Then** nennt der Vergleich die letzte und die nächste Untersuchung und stellt klar, dass im Zwischenraum keine U-Untersuchung ansteht.
4. **Given** zwei Quellen, die zum selben Zeitpunkt Unterschiedliches empfehlen, **When** die Betreuungsperson den Vergleich liest, **Then** stehen die Aussagen nebeneinander mit ihrer jeweiligen Quelle, und HebMama erklärt keine der Aussagen zur allein gültigen Handlungsanweisung.

---



### User Story 2 - Vorsorgetermin vorbereiten (Priority: P2)

Eine Betreuungsperson bereitet einen konkreten Arzt- oder Vorsorgetermin vor und braucht dafür einen Leitfaden, eine Checkliste und eine Fragenliste, ohne die Originalleitlinien selbst durchsuchen zu müssen.

**Why this priority**: Die Vorbereitungspakete sind der alltägliche Nutzen. Sie setzen voraus, dass die Kontakte aus User Story 1 benannt sind, und sind danach eigenständig verwendbar.

**Independent Test**: Anhand allein des Vorbereitungspakets für eine gewählte deutsche U-Untersuchung kann eine Betreuungsperson Zweck des Termins, mitzubringende Unterlagen und Fragen an die Ärztin oder den Arzt wiedergeben und erkennen, welche Aussagen aus einer Leitlinie stammen und welche Orientierungshilfen sind.

**Acceptance Scenarios**:

1. **Given** eine abgelegte deutsche U-Untersuchung, **When** die Betreuungsperson ihr Vorbereitungspaket öffnet, **Then** enthält es einen Leitfaden, eine Checkliste und eine Fragenliste und nennt die verknüpften Quellen.
2. **Given** ein praktischer Hinweis, der nicht in der Leitlinie steht (zum Beispiel was eingepackt werden soll), **When** die Betreuungsperson ihn liest, **Then** ist er als Orientierung gekennzeichnet und nicht als Leitlinienaussage.
3. **Given** ein Vorbereitungspaket für U1, U2 oder U3, **When** die Betreuungsperson es liest, **Then** werden Kind und Mutter dort angesprochen, wo die abgelegten deutschen oder WHO-Quellen das tun, und Themen der Schwangerschaft kommen nicht vor.
4. **Given** ein beliebiges Vorbereitungspaket, **When** die Betreuungsperson es öffnet, **Then** steht am Anfang ein sichtbarer Hinweis, dass HebMama eine Orientierungshilfe ist und weder ärztlichen Rat noch das Gelbe Heft oder den griechischen Gesundheitsnachweis ersetzt.

---



### User Story 3 - Eine Aussage zur Quelle zurückverfolgen (Priority: P2)

Eine Betreuungsperson oder eine pflegende Person will prüfen, woher eine Altersangabe, eine Untersuchungsaussage oder ein Hinweis zur Postnatalversorgung stammt.

**Why this priority**: Medizinische Orientierung ist nur tragfähig, wenn jede Sachaussage auf eine benannte Quelle zurückgeführt werden kann. Das ist der Vertrauenskern der Interpretierbarkeit.

**Independent Test**: Aus einer beliebigen Zeit- oder Inhaltsaussage im Vergleich oder in einem Vorbereitungspaket gelangt die lesende Person in höchstens drei Schritten zu Aussteller, amtlichem Titel, Fassung und Fundstelle der Quelle.

**Acceptance Scenarios**:

1. **Given** eine Aussage zu Zeitpunkt oder Untersuchungsinhalt, **When** die lesende Person der Herkunftsangabe folgt, **Then** erreicht sie ein Quellendokument mit Aussteller, amtlichem Titel, Fassung oder Veröffentlichungsdatum, Abrufdatum und Fundstelle.
2. **Given** zwei Fassungen derselben Leitlinie, **When** die lesende Person den aktuellen Vergleich öffnet, **Then** nennt der Vergleich die verwendete Fassung, und die ältere Fassung bleibt auffindbar und als ersetzt gekennzeichnet.
3. **Given** ein Quellendokument, das nur auf Griechisch oder Englisch vorliegt, **When** die lesende Person es öffnet, **Then** ist der amtliche Titel in der Originalsprache erhalten und eine deutsche Zusammenfassung vorhanden.

---



### User Story 4 - Leitlinie in der ICM-Ablage pflegen (Priority: P3)

Eine pflegende Person legt eine neue oder aktualisierte Leitlinie so ab, dass Menschen sie ohne weiteres Werkzeug lesen, einordnen und mit Vergleich und Vorbereitungspaketen verbinden können.

**Why this priority**: Die Ablage hält den Wissensbestand aktuell. Leserinnen und Leser ziehen ihren Nutzen schon aus dem ersten Bestand; die Pflege sichert, dass spätere Fassungen die Lesbarkeit nicht zerstören.

**Independent Test**: Eine pflegende Person kann ein weiteres Quellendokument mit vollständiger Herkunft ablegen, es vom Einstieg aus in höchstens drei Schritten erreichen und eine ersetzte Fassung als solche stehen lassen.

**Acceptance Scenarios**:

1. **Given** eine neue amtliche Leitlinie aus einem der drei Bereiche, **When** die pflegende Person sie ablegt, **Then** liegt sie im Quellenbereich ihres Geltungsraums, trägt die geforderte Herkunft und ist vom Einstieg in höchstens drei Schritten erreichbar.
2. **Given** eine aktualisierte Fassung, **When** die pflegende Person sie ablegt, **Then** bleibt die vorherige Fassung erhalten, ist als ersetzt markiert und der Vergleich nennt genau eine aktuelle Fassung je Quelle.
3. **Given** ein Thema ohne ausreichende amtliche Angabe (zum Beispiel kein griechisches Gegenstück zu einer U-Untersuchung), **When** die pflegende Person die Lücke vermerkt, **Then** zeigt der Vergleich die Lücke und keine ausgedachte Termin- oder Impffolge.

---



### Edge Cases

- **Alter außerhalb des Rahmens**: Liegt das Alter vor der Geburt oder nach dem Ende des U9-Fensters, nennt HebMama den Rahmen und erfindet keine weitere Untersuchung.
- **Frühgeborenes Kind**: HebMama verwendet die Altersdefinition der abgelegten Quelle und weist Fragen zur korrigierten Altersberechnung an die behandelnde Fachperson. Eine zweite, eigene Terminrechnung gibt es nur, wenn eine abgelegte Quelle sie ausdrücklich vorgibt.
- **Versäumtes Untersuchungsfenster**: Sieht die Quelle eine Nachholregel vor, wird sie mit Herkunft wiedergegeben. Fehlt eine solche Regel, stellt HebMama klar, dass es keine eigene Nachholregel festlegt.
- **Geburt außerhalb einer Klinik**: Hängt der erste WHO-Kontakt vom Geburtsort ab, gibt HebMama beide in der Quelle beschriebenen Wege wieder und wählt nicht stillschweigend einen aus.
- **Widerspruch zwischen Deutschland, Griechenland und WHO**: Unterschiede bleiben nebeneinander stehen. HebMama löst sie nicht zu einer einzigen klinischen Empfehlung auf.
- **Kein griechisches Gegenstück**: Eine deutsche Untersuchung ohne amtliches griechisches Gegenstück wird als „kein Gegenstück“ geführt, nicht als Lücke im Text und nicht als erzwungene Paarung.
- **Quelle nur auf Griechisch oder Englisch**: Originaltitel und nötige Originalbegriffe bleiben stehen; die deutsche Zusammenfassung macht den Inhalt lesbar, ohne die Quelle umzudeuten.
- **Quelle nicht mehr abrufbar**: Die abgelegte Zusammenfassung, Fassung und das Abrufdatum bleiben lesbar. Eine tote Fundstelle wird als solche kenntlich gemacht.
- **Mehrkind oder Zwillinge**: Vorbereitungspakete beschreiben den Termintyp, nicht die Akte eines bestimmten Kindes.
- **Kein Zugang zu myHealth**: HebMama beschreibt den digitalen Impfpass und myHealth. Es setzt keine Anmeldung und keinen Abruf personenbezogener Daten voraus.
- **Impffrage zu einem bestimmten Kind**: HebMama gibt keine individuelle Impffolge aus. Es verweist auf die abgelegten amtlichen Kalender und auf die behandelnde Fachperson.
- **Akute Beschwerden**: HebMama bietet keine Symptomanalyse. Enthält eine Quelle Warnzeichen, werden sie nur mit der dort genannten Aufforderung wiedergegeben, Hilfe zu holen.
- **Postnatalzeit endet, Kindervorsorge läuft weiter**: Ab dem in der WHO-Quelle genannten Ende der Postnatalzeit erscheinen mütterliche Postnatalempfehlungen nicht mehr als anstehend. Die weiteren U-Untersuchungen bleiben sichtbar.
- **U7a**: Die Untersuchung liegt zwischen U7 und U8 in der Kinder-Richtlinie und gehört zum Bestand, auch wenn die Anfrage „U1–U9“ sagt.
- **Dokument einzeln gelesen**: Jedes Quellendokument, jeder Vergleich und jedes Vorbereitungspaket nennt seinen Zweck, seinen Rahmen und den Orientierungshinweis, damit es ohne die übrigen Dokumente verständlich bleibt.



## Requirements *(mandatory)*



### Functional Requirements

- **FR-001**: HebMama MUSS einen menschenlesbaren Wissensbestand zu drei Quellenbereichen bereitstellen: die deutsche Kinder-Richtlinie für die Untersuchungen U1, U2, U3, U4, U5, U6, U7, U7a, U8 und U9; den griechischen Weg der kindlichen Vorsorge und des digitalen Impfpasses über myHealth; die WHO-Leitlinien der Postnatalversorgung von Mutter und Neugeborenem. Ergänzende Texte, etwa zum Wochenbett, gehören in einen dieser drei Bereiche und eröffnen keinen vierten Vergleich. Erfüllt, wenn zu jedem Bereich mindestens ein Quellendokument vom Einstieg aus erreichbar ist.
- **FR-002**: Jedes Quellendokument MUSS Aussteller, amtlichen Titel, Geltungsraum, Fassung oder Veröffentlichungsdatum, Abrufdatum, Sprache und Fundstelle nennen sowie in deutscher Sprache zusammenfassen, was Vergleiche und Vorbereitungspakete daraus verwenden dürfen. Erfüllt, wenn keines dieser Felder fehlt und die Zusammenfassung keine Aussagen enthält, die in der Quelle nicht stehen.
- **FR-003**: Der Vergleich MUSS für jede Untersuchung von U1 bis U9 einschließlich U7a das Altersfenster, den Zweck laut abgelegter Kinder-Richtlinie, die griechische Beziehung und die WHO-Beziehung zeigen. Die Beziehung ist „Entsprechung“, „teilweise Entsprechung“ oder „kein Gegenstück“. Erfüllt, wenn alle zehn Untersuchungen diese vier Angaben tragen und jede Angabe auf eine abgelegte Quelle zeigt.
- **FR-004**: Derselbe Vergleich MUSS über zwei Wege lesbar sein: nach Kindesalter und nach Untersuchungsnamen. Erfüllt, wenn ein Alter im Rahmen und ein Untersuchungsname jeweils zum selben Vergleichseintrag führen.
- **FR-005**: HebMama MUSS widersprüchliche Aussagen der drei Bereiche nebeneinander mit ihrer Quelle zeigen und MUSS sie nicht zu einer einzigen klinischen Handlungsanweisung zusammenziehen. Erfüllt, wenn ein dokumentierter Widerspruch im Vergleich beide Fassungen und keine HebMama-eigene Entscheidung enthält.
- **FR-006**: Fehlt ein amtliches Gegenstück oder eine ausreichende amtliche Angabe, MUSS HebMama die Lücke ausdrücklich benennen. Erfüllt, wenn keine Vergleichszelle leer ist und keine Termin-, Untersuchungs- oder Impffolge ohne abgelegte Quelle erscheint.
- **FR-007**: HebMama MUSS für jede der zehn deutschen Untersuchungen und für jeden in der abgelegten WHO-Leitlinie genannten Postnatalkontakt ein Vorbereitungspaket bereitstellen. Für einen abgelegten griechischen Vorsorgekontakt MUSS ebenfalls ein Paket bestehen; fehlt der amtliche Kontakt, tritt an die Stelle des Pakets die benannte Lücke. Erfüllt, wenn Leitfaden, Checkliste und Fragenliste in jedem vorhandenen Paket enthalten sind und auf die Quellen des Kontakts verweisen.
- **FR-008**: HebMama MUSS in Leitfäden, Checklisten und Fragenlisten Leitlinienaussagen und praktische Orientierung äußerlich unterscheidbar kennzeichnen. Erfüllt, wenn eine stichprobenartig gewählte Orientierungshilfe nicht als Leitlinienfakt gelesen werden kann.
- **FR-009**: Jede Sachaussage zu Zeitpunkt, Untersuchungsinhalt, Impfung oder Postnatalversorgung in Vergleich und Vorbereitungspaketen MUSS auf ein abgelegtes Quellendokument verweisen. Erfüllt, wenn in einer vollständigen Durchsicht jede solche Aussage eine Herkunftsangabe hat.
- **FR-010**: HebMama MUSS die Ablage nach der Interpretable Context Methodology führen: ein Einstiegsdokument, Quellendokumente getrennt nach Deutschland, Griechenland und WHO, ein Vergleich, Vorbereitungspakete und ein Hinweisbereich mit Geltungsrahmen, Orientierungshinweis, Glossar und bekannten Lücken. Die Form sind menschenlesbare Markdown-Dokumente in Ordnern. Erfüllt, wenn diese fünf Bereiche vorhanden sind und jedes Dokument Zweck und Rahmen in sich trägt.
- **FR-011**: Vom Einstiegsdokument MUSS jede Quelle, jeder Vergleichseintrag und jedes Vorbereitungspaket in höchstens drei Schritten erreichbar sein, ohne Suche und ohne zusätzliche Anwendung. Erfüllt, wenn ein Stichprobenweg zu je einem Dokument jeder Art diese Schrittzahl nicht überschreitet.
- **FR-012**: Die Lesesprache MUSS Deutsch sein. Amtliche Begriffe auf Griechisch oder Englisch MUSS HebMama beim ersten Vorkommen in einem Dokument in der Originalsprache und mit deutscher Erläuterung nennen. Erfüllt, wenn Originalbegriff und deutsche Erläuterung gemeinsam stehen.
- **FR-013**: Einstieg, Vergleich und jedes Vorbereitungspaket MÜSSEN zu Beginn den Hinweis tragen, dass HebMama eine Orientierungshilfe ist und ärztlichen Rat, das Gelbe Heft und den griechischen Gesundheitsnachweis nicht ersetzt. Erfüllt, wenn der Hinweis in jedem dieser Dokumente sichtbar ist.
- **FR-014**: Mütterliche Inhalte MUSS HebMama auf das Postnatalfenster der abgelegten WHO-Leitlinie und auf ausdrücklich abgelegte deutsche oder griechische Wochenbettquellen begrenzen. Schwangerschaft und Versorgung nach diesem Fenster sind außerhalb des Rahmens und werden als solche genannt. Erfüllt, wenn ein Paket ab U4 keine mütterliche Postnatalempfehlung als anstehenden Termin darstellt.
- **FR-015**: HebMama MUSS keine personenbezogenen Gesundheitsdaten eines bestimmten Kindes speichern, keine individuelle Impffolge erzeugen, keine Symptomanalyse, keine Diagnose und keine Dosierung anbieten. Erfüllt, wenn keines der Dokumente einen Platz für Namen, Geburtsdatum oder Impfdaten eines realen Kindes vorsieht und keine dieser Leistungen beschrieben wird.
- **FR-016**: Bei einer neuen Fassung MUSS die bisherige Fassung erhalten und als ersetzt gekennzeichnet bleiben. Der Vergleich MUSS die verwendete aktuelle Fassung benennen. Erfüllt, wenn nach einer Aktualisierung beide Fassungen auffindbar sind und der Vergleich nur die neue als aktuell verwendet.
- **FR-017**: HebMama MUSS bei Frühgeburt und bei versäumtem Fenster die Regel der abgelegten Quelle wiedergeben und offene Fragen an die behandelnde Fachperson verweisen. Erfüllt, wenn keine zweite, quellenlose Altersrechnung oder Nachholregel im Bestand steht.
- **FR-018**: HebMama MUSS ein Glossar führen, das jeden fachlichen Begriff der drei Bereiche auf Deutsch erklärt und den amtlichen Begriff der Originalsprache nennt. Erfüllt, wenn U-Untersuchung, Gelbes Heft, myHealth, digitaler Impfpass und Postnatalversorgung im Glossar stehen.
- **FR-019**: Das Einstiegsdokument MUSS die Zielgruppe (Betreuungspersonen, die sich zwischen dem deutschen und dem griechischen System sowie der WHO-Postnatalversorgung orientieren) und die drei Inhaltssäulen nennen. Erfüllt, wenn eine erstlesende Person daraus Zielgruppe und die drei Säulen wiedergeben kann.
- **FR-020**: HebMama MUSS Leitlinien zusammenfassen und kurz zitieren, nicht vollständig abschreiben. Jedes Zitat MUSS der Quelle zugeordnet sein. Erfüllt, wenn Quellendokumente eine deutsche Zusammenfassung und die Fundstelle enthalten und nicht aus der vollständigen Leitlinie bestehen.



### Key Entities *(include if feature involves data)*

- **Quelle**: Eine abgelegte Leitlinie oder ein amtlicher Begleittext. Attribute: Aussteller, amtlicher Titel, Geltungsraum (Deutschland, Griechenland oder WHO), Fassung, Abrufdatum, Sprache, Fundstelle, deutsche Zusammenfassung, Status (aktuell oder ersetzt), ausdrücklich ausgeschlossener Rahmen.
- **Vorsorgekontakt**: Ein benannter Kontakt in einem der drei Bereiche, etwa eine U-Untersuchung, ein griechischer Vorsorge- oder Impfkontakt oder ein WHO-Postnatalkontakt. Attribute: Name, Bereich, Altersfenster laut Quelle, betroffene Personen (Kind, Mutter oder beide), Zweck, verknüpfte Quelle.
- **Vergleichseintrag**: Die Beziehung zwischen einem deutschen Kontakt und dem griechischen sowie dem WHO-Kontakt. Attribute: Art der Beziehung (Entsprechung, teilweise Entsprechung, kein Gegenstück), Unterschied in eigenen Worten, verwendete Fassungen, Verweis auf das Vorbereitungspaket oder auf eine benannte Lücke.
- **Vorbereitungspaket**: Die lesbare Vorbereitung auf einen Kontakt. Bestandteile: Leitfaden (wozu der Termin da ist), Checkliste (was vorher zu klären und mitzubringen ist), Fragenliste (was die Betreuungsperson ansprechen kann), Kennzeichnung von Leitlinienaussage und Orientierung, verknüpfte Kontakte und Quellen.
- **Inhaltslücke**: Ein Thema im Rahmen, zu dem keine ausreichende amtliche Quelle abgelegt ist. Attribute: Thema, betroffener Bereich, was fehlt, Datum des Vermerks. Eine Lücke ist kein Freiraum für eine eigene medizinische Festlegung.
- **Glossareintrag**: Ein Fachbegriff mit deutscher Erklärung, Originalbegriff und Verweis auf die Quelle, die den Begriff trägt.
- **Orientierungshinweis**: Der feste Hinweis, dass HebMama keine Behandlung, keinen Nachweis und keine persönliche Akte ersetzt.



## Success Criteria *(mandatory)*



### Measurable Outcomes

- **SC-001**: Eine erstlesende Betreuungsperson kann für ein Alter zwischen Geburt und dem Ende des U9-Fensters in höchstens 3 Minuten, allein vom Einstieg aus, die zuständige deutsche Untersuchung oder die Zwischenraum-Lücke sowie die griechische und die WHO-Beziehung benennen.
- **SC-002**: Für alle 10 deutschen Untersuchungen (U1 bis U9 einschließlich U7a) und für jeden Postnatalkontakt der abgelegten WHO-Leitlinie liegt ein vollständiges Vorbereitungspaket vor (Leitfaden, Checkliste, Fragenliste).
- **SC-003**: In einer vollständigen Durchsicht von Vergleich und Vorbereitungspaketen haben 100 % der Aussagen zu Zeitpunkt, Untersuchungsinhalt, Impfung und Postnatalversorgung eine Herkunftsangabe auf ein abgelegtes Quellendokument.
- **SC-004**: 100 % dieser Herkunftsangaben sind vom Satz aus in höchstens 3 Schritten bis zu Aussteller, Titel, Fassung und Fundstelle verfolgbar.
- **SC-005**: Im veröffentlichten Vergleich ist jede deutsche Untersuchung ohne griechisches oder ohne WHO-Gegenstück ausdrücklich als „kein Gegenstück“ markiert. Ziel: 0 leere oder stillschweigend gefüllte Vergleichsfelder.
- **SC-006**: Eine Betreuungsperson, die die Originalleitlinien nicht gelesen hat, kann anhand eines einzigen Vorbereitungspakets in höchstens 10 Minuten den Zweck des Termins, mindestens 3 Vorbereitungs- oder Mitbringpunkte und mindestens 5 Fragen an die Fachperson nennen.
- **SC-007**: Nach dem Ablegen einer neuen Fassung bleiben 100 % der ersetzten Fassungen auffindbar und als ersetzt gekennzeichnet, und der Vergleich nennt je Quelle genau eine aktuelle Fassung.
- **SC-008**: 100 % der Einstiegsdokumente, Vergleichsdokumente und Vorbereitungspakete zeigen den Orientierungshinweis, dass HebMama ärztlichen Rat und amtliche Nachweise nicht ersetzt.
- **SC-009**: In einer Prüfung der Pakete ab U4 wird keine mütterliche Postnatalempfehlung als noch anstehender Termin dargestellt. Ziel: 0 solche Fehldarstellungen.
- **SC-010**: Eine erstlesende Person kann nach dem Einstieg die drei Inhaltssäulen und die Zielgruppe in eigenen Worten wiedergeben. Ziel: gelingt in einem Leseversuch ohne Rückfrage an eine pflegende Person.



## Assumptions

- HebMama ist in dieser Fassung ein lesbarer Wissensbestand und keine Software, keine Akte und keine Anbindung an myHealth, das Gelbe Heft oder eine Krankenkasse.
- Die Interpretable Context Methodology bedeutet hier: jedes Thema steht in einem eigenen menschenlesbaren Markdown-Dokument, die Ordner folgen der fachlichen Gliederung (Einstieg, Quellen, Vergleich, Vorbereitung, Hinweise), Herkunft und Rahmen stehen im Dokument selbst, und der Text bleibt ohne zusätzliches Werkzeug verständlich. Diese Arbeitsdefinition folgt aus der Projektbeschreibung.
- Primäre Leserschaft sind Betreuungspersonen, die sich zwischen dem deutschen U-Untersuchungen-Weg, dem griechischen Weg über myHealth und den digitalen Impfpass sowie der WHO-Postnatalversorgung orientieren. Fachpersonen sind nicht die Hauptzielgruppe, können die Quellen aber mitprüfen.
- Die Lesesprache ist Deutsch. Griechische und englische Amtsbegriffe bleiben erhalten und werden erklärt.
- U7a gehört zum Rahmen, weil sie Teil der Kinder-Richtlinie zwischen U7 und U9 ist. U10, U11, J1 und die Schuleingangsuntersuchung liegen außerhalb.
- Mütterliche Gesundheit ist auf die Postnatal- und Wochenbettzeit begrenzt, wie sie die abgelegten WHO-, deutschen oder griechischen Quellen beschreiben. Schwangerschaftsvorsorge liegt außerhalb.
- Die deutsche Bezugsquelle ist die Kinder-Richtlinie des Gemeinsamen Bundesausschusses in der abgelegten Fassung. Altersfenster werden aus dieser Fassung übernommen und nicht aus dem Gedächtnis festgeschrieben.
- Die WHO-Bezugsquelle ist die abgelegte WHO-Leitlinie zur Postnatalversorgung von Mutter und Neugeborenem. Kontakte und das Ende des Postnatalfensters folgen dieser Fassung.
- Der griechische Bereich beschreibt myHealth und den digitalen Impfpass sowie die amtlich belegbare Kindervorsorge. Wo Griechenland keine der deutschen U-Untersuchung entsprechende Reihe veröffentlicht, bleibt das ein „kein Gegenstück“ oder eine Inhaltslücke.
- Impfinhalte erscheinen nur so weit, wie sie in den abgelegten Quellen der drei Bereiche oder in einem von dort bezeichneten und ebenfalls abgelegten amtlichen Impfkalender stehen. HebMama erstellt daraus keinen persönlichen Impfplan.
- Hebammenhilfe im Wochenbett wird nur dort erwähnt, wo eine abgelegte Quelle sie mit den frühen Kontakten (U1–U3 oder WHO-Postnatalversorgung) verbindet. Ein eigenes Hebammen-Lehrwerk ist nicht Teil dieser Fassung.
- Amtliche Volltexte werden nicht vollständig in den Bestand kopiert. Aufgenommen werden deutsche Zusammenfassungen, knappe zugeordnete Zitate und die Fundstelle.
- Personenbezogene Daten eines realen Kindes werden nicht erhoben und nicht abgelegt. Eine Betreuungsperson kann Checklisten für den eigenen Gebrauch abschreiben; der Bestand selbst bleibt allgemein.
- Akute Krankheit, Diagnose, Medikamentendosis und Notfallentscheidungen liegen außerhalb. Warnzeichen werden nur wiedergegeben, wenn die Quelle sie nennt, und stets mit dem Hinweis, sich an eine Fachperson oder den Notruf zu wenden.
- Die Verfassung des Projekts enthält noch keine beschlossenen Grundsätze. Diese Spezifikation setzt deshalb keine zusätzlichen Verfassungsregeln voraus.

