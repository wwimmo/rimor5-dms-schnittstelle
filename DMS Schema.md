# Staging Area
Das Datenmodell Rimo R5 für den Dokumentenimport sieht aktuell folgende Tabellen vor.
Sämtliche Tabellen sind dem Owner DBA zugewiesen.

|Tabelle|Beschreibung|
|-|-|
|[DMSImport](https://github.com/wwimmo/rimor5-dms-schnittstelle/blob/main/_staging%20area/DMSImport.md)|Jedes Dokument, welches im Rimo R5 verlinkt werden soll, erhält vorerst einen Eintrag in diese Tabelle.|
|[DMSImportLink](https://github.com/wwimmo/rimor5-dms-schnittstelle/blob/main/_staging%20area/DMSImportLink.md)|Zu jedem Dokument soll das DMS so viele Daten wie möglich bereits an Rimo R5 übermitteln, damit Rimo R5 das Dokument möglichst automatisiert im E-Dossier verlinken kann.|
|[DMSRechnung](https://github.com/wwimmo/rimor5-dms-schnittstelle/blob/main/_staging%20area/DMSRechnung.md)|Nur für Dokumententypen 1 und 2 (Kreditorenrechnung/ -gutschrift): Wenn zu einer Kreditorenrechnung/ -gutschrift zusätzliche Daten (Rechnungsdaten wie z.B. Rech-nungsnummer, Zahlungsinformationen, Betrag, usw.) ins Rimo R5 importiert werden sollen, so werden diese Daten zum Import hier gespeichert.|
|[DMSKontierung](https://github.com/wwimmo/rimor5-dms-schnittstelle/blob/main/_staging%20area/DMSKontierung.md)|Nur für Dokumententypen 1 und 2 (Kreditorenrechnung/ -gutschrift): Wenn zu einer Kreditorenrechnung oder Kreditorengutschrift eine Kontierung im DMS Workflow er-folgte, so wird diese Kontierung in der Tabelle DMSKontierung gespeichert.|
|[DMSRemapping](https://github.com/wwimmo/rimor5-dms-schnittstelle/blob/main/_staging%20area/DMSRemapping.md)|Diese Tabelle wird wie folgt verwendet: Wenn das DMS Dokument aus der lokalen Dateiab-lage im Datenspeicher archiviert hat, erfolgt über diese Tabelle die Meldung der neuen DMS-ID. Rimo R5 bearbeitet diese Einträge regelmässig und synchronisiert die Dokumentent-links.|

![Staging Schema](https://github.com/wwimmo/rimor5-dms-schnittstelle/blob/main/_grafiken/dmsstagingschema.png)

# Views
Die Views dienen dem DMS dazu im Workflow oder beim Scanning die Dokumente mit Rimo R5 spezifischen Daten zu versehen. Je mehr Daten den Dokumenten im DMS bereits zugeordnet sind, desto automatisierter kann seitens Rimo R5 das Dokument im E-Dossier verlinkt werden. Sämtliche Views sind dem Owner DBA zugewiesen.

|View|Beschreibung|
|-|-|
|[vDMSAbrechnungLieg]()|Diese View enthält sämtliche Adressen als String mit der jeweiligen Verwendung im Rimo R5. Hiermit können z.B. eingehende Dokumente den Absendern im Rimo R5 zugewiesen werden| 
|[vDMSAdresseZuEntity]()|Diese View enthält sämtliche Adressen als String mit der jeweiligen Verwendung im Rimo R5Hiermit können z.B. eingehende Dokumente den Absendern im Rimo R5 zugewiesen werden|
|[vDMSAuftrag]()|Diese View enthält eine Liste mit sämtlichen Aufträgen. Die Auftragsnummer gemäss dieser View kann zu einer Rechnung in der Tabelle dmsrechnung.auftragsnr mitgeleifert werden, damit Rimo R5 den offenen Auftrag erledigen kann|
|[vDMSBelegIDzuEntity]()|Diese View enthält alle bereits verbuchten Belege mit manueller Belegnummer im Rimo R5. mit diesen Daten können z.B. nachträglich gescannte Belegdokumente, welche eine Belegnummer enthalten den korrekten Buchungen zugewiesen werden|
|[vDMSBuchungsHistory]()|Diese View enthält die Buchungshistory der letzten drei Jahre. Hiermit können z.B. bereits verwendete Buchungstexte auf bestimmten Konti ermittelt und dem Benutzer zur Kontierung vorgeschlagen werden|
|[vDMSDokument]()|Diese View enthält eine Liste sämtlicher ursprünglich von Rimo R5 erstellten und vom DMS zurückgemeldeten Dokumente, die erfolgreich via Remapping (dmsremapping) von Rimo R5 verarbeitet wurden|
|[vDMSDokumententLinks]()|Diese View enthält eine Liste von Verlinkungen sämtlicher ursprünglich von Rimo R5 erstellten und vom DMS zurückgemeldeten Dokumente, die erfolgreich via Remapping (dmsremapping) von Rimo R5 verarbeitet wurden. Die View korrespondiert mit allen Dokumenten gemäss vDMSDokument|
|[vDMSDokuTyp]()|Diese View enthält eine Liste aller Dokumententypen, welche im Rimo R5 verfügbar sind. Jeder Dokumententyp wird je möglicher Zuordnung zu einer Rimo R5 Entität (entityname) in einer separaten Zeile nochmals aufgeführt|
|[vDMSEigentuemer]()|Eine Liste aller Liegenschaftseigentümern im Rimo R5 zur Ablage von Dokumenten zu deren Dossier|
|[vDMSEmailZuEntity]()|Eine Liste sämtlicher im Rimo R5 vorhandenen E-Mail Adressen und deren Zuordnung zu Entitäten und Stammdaten. Mittels dieser View können z.B. erhaltene E-Mails automatisch den Rimo R5 Daten zugewiesen werden|
|[vDMSExportDokument]()|n dieser View werden sämtliche Dokumente angezeigt, welche von Rimo R5 erstellt und dem DMS zur Archivierung bereit stehen.Der physische Dokumentelink setzt sich aus den Spalten pfad und dateiname zusammen. Dokumente, welche aus dieser View erfolgreich im DMS archiviert wurden, müssen via dmsremapping an Rimo R5 zurückgemeldet werden, damit Rimo R5 diese Dokumente korrekt neu verlinken kann|
|[vDMSFibubuchung]()|Eine Liste sämtlicher Fibubuchungen aus Rimo R5. Aufgrung der hohen möglichen Datenmenge sollte diese View bei der Abfrage wenn möglich stark eingegrenzt werden|
|[vDMSFibujahr]()|Eine Liste sämtlicher Buchhaltungsperioden zur Ablage von z.B. Abschlussdokumenten|
|[vDMSFinanzbuchhaltung]()|Diese View enthält eine Liste sämtlicher Finanzbuchhaltungen (Fibus) gemäss Rimo R5 Stammdaten|
|[vDMSGenossenschaft]()|Eine Liste aller Genossenschaften mit Zuordnung zur Finanzbuchhaltung|
|[vDMSGenossenschafter]()|Eine Liste aller Genossenschafter|
|[vDMSGeraet]()|Diese View zeigt sämtliche Geräte gemäss der technischen Verwaltung im Rimo R5. Die Geräte können anhand der Angaben in der Spalte subgearetvon in eine Hierarchische Struktur gebracht werden|
|[vDMSHauswart]()|Eine Liste aller Hauswarte inkl. deren Adresse|
|[vDMSHypothek]()|Diese View zeigt alle Hypotheken mit der Zuordnung zur Liegenschaft. die Angaben zum Kreditor sowie einer Zahlverbindung sind im Datenmodell berücksichtigt, aber aktuell im Rimo R5 noch nicht in Gebrauch|
|[vDMSIBANZuEntity]()|Diese Liste zeigt alle im Rimo R5 vorhandenen IBAN und deren Zuordnung zu den Daten. In dieser Liste kann nach einer IBAN gesucht und die zugeordneten Daten ermitteln, um z.B. Dokumente mit IBAN zu den richtigen Daten im Rimo R4 abgelegt werden|
|[vDMSKontierungsregel]()|In dieser View sind alle definierten Kontierungsregeln mit Referenz-IDs (referenzid) aufgelistet. Die Kontierungsregeln können im Rimo R5 für definierte Geschäftsfälle konfiguriert werden und können im Kontierungsprozess als Vorlage wiederverwendet werden|
|[vDMSKontoplan]()|In dieser View sind alle im Rimo R5 zu bebuchenden Konti aufgeführt. Die verfügbarkeit der Konti wird gemäss Periode Beginn/Ende (periodebeginn/periodeende) definiert. Es dürfen nur Kontierungen via dmskontierung mitgegeben werden, welche gemäss Buchungsdatum (buchungdat) in die hier aufgeführte Periode passen|
|[vDMSKredibuchung]()|Liste aller Kreditorenrechnngen gemäss Buchhaltung im Rimo R5|
|[vDMSKreditor]()|Liste aller Kreditoren/Lieferanten|
|[vDMSKreditorenrechnung]()|In dieser View werden sämtliche im Rimo R5 verbuchten Kreditorenrechnungen aufgeführt, zu welchen Dokumente existieren. Hier erscheint z.B. auch das Zahlngsdatum (buchdatzlg), sobald die Rechnung via Rimo R5 bezahlt wurde|
|[vDMSKreditorZahlverb]()|Eine Liste sämtlicher Zahlverbindungen der Kreditoren mit erweiterten Personendaten der Kreditoren. Diese View eignet sich zur Identifikation eines Kreditore gemäss Rechnungssangaben|
|[vDMSLiegenschaft]()|Liste aller Liegenschaften|
|[vDMSMieter]()|Liste aller Mieter/STEG Eigentümer|
|[vDMSMieterbuchung]()|In dieser Ansicht werden alle Debitorbuchungen aufgelistet|
|[vDMSMieterZuObjekt]()|In dieser View werden alle Zuordnungen von Mietern zu Objekten aufgelistet. Die Zuweisung eines Mieters zu einem Objekt entspricht einem Mietverhältnis und ist zeitlich über Mietbeginn und Mietende eingegrenzt|
|[vDMSMWSTCodes]()|Liste aller möglichen MWST Codes im Rimo R5. Ein MWST Code muss bei einer Buchung inkl. MWST mit der dmskontierung angegeben werden|
|[vDMSObjekt]()|Liste sämtlicher Objekte / Mieteinheiten / STEG-Einheiten|
|[vDMSPersart]()|Liste aller möglichen Personenarten. Die Personenart muss für den automatischen Kreditorenabgleich zur Neuerfassung einer Person im Kreditorenstamm zur dmsrechnung mitgegeben werden|
|[vDMSRGVisumUser]()|In dieser View werden alle Benutzer von Rimo R5 dargestellt. Die Benutzer könen in Workflows (vDMSWorkflow) hinterlegt werden|
|[vDMSRolleZuLieg]()|In dieser View werden je Liegenschaft Benutzer in deren Rolle aufgeführt. Alternativ zu den Daten gemäss vDMSWorkflow können auch diese Rollendaten als Basis für Workflows verwendet werden|
|[vDMSUnterhaltsart]()|Liste aller Unterhaltsarten. Die Unterhaltsart kann zur dmskontierung im Rahmen der technischen Verwaltung eingetragen werden|
|[vDMSVerwaltung]()|Liste aller Verwaltungen|
|[vDMSWorkflow]()|Liste aller Fibus mit Info des Workflows für Kreditorenrechnungen (Visum1-3)|
|[vDMSZahlungscode]()|Liste aller möglichen Zahlungscode. Ein Zahlungscode kann alternativ zum Fälligkeitsdatum zur dmsrechnung angegeben werden|
|[vDMSZahlverbKredi]()|Liste aller Zahlverbindungen zu Kreditoren|
