# Staging Area
Das Datenmodell Rimo R5 für den Dokumentenimport sieht aktuell folgende Tabellen vor.
Sämtliche Tabellen sind dem Owner DBA zugewiesen.

|Tabelle|Beschreibung|
|-|-|
|[DMSImport](/_staging%20area/DMSImport.md)|Jedes Dokument, welches im Rimo R5 verlinkt werden soll, erhält vorerst einen Eintrag in diese Tabelle.|
|[DMSImportLink](/_staging%20area/DMSImportLink.md)|Zu jedem Dokument soll das DMS so viele Daten wie möglich bereits an Rimo R5 übermitteln, damit Rimo R5 das Dokument möglichst automatisiert im E-Dossier verlinken kann.|
|[DMSRechnung](/_staging%20area/DMSRechnung.md)|Nur für Dokumententypen 1 und 2 (Kreditorenrechnung/ -gutschrift): Wenn zu einer Kreditorenrechnung/ -gutschrift zusätzliche Daten (Rechnungsdaten wie z.B. Rechnungsnummer, Zahlungsinformationen, Betrag, usw.) ins Rimo R5 importiert werden sollen, so werden diese Daten zum Import hier gespeichert.|
|[DMSKontierung](/_staging%20area/DMSKontierung.md)|Nur für Dokumententypen 1 und 2 (Kreditorenrechnung/ -gutschrift): Wenn zu einer Kreditorenrechnung oder Kreditorengutschrift eine Kontierung im DMS Workflow erfolgte, so wird diese Kontierung in der Tabelle DMSKontierung gespeichert.|
|[DMSRemapping](/_staging%20area/DMSRemapping.md)|Diese Tabelle wird wie folgt verwendet: Wenn das DMS Dokument aus der lokalen Dateiablage im Datenspeicher archiviert hat, erfolgt über diese Tabelle die Meldung der neuen DMS-ID. Rimo R5 bearbeitet diese Einträge regelmässig und synchronisiert die Dokumentenlinks.|

![Staging Schema](/_grafiken/dmsstagingschema.png)

Die Datensätze der Staging Tabellen werden durch Rimo R5 verarbeitet. Im Fehlerfall wird ein [Fehlercode](/_staging%20area/fehlercodes.md) in das Feld .fehlercode der jeweiligen Staging Tabelle geschrieben.

# Views
Die Views dienen dem DMS dazu im Workflow oder beim Scanning die Dokumente mit Rimo R5 spezifischen Daten zu versehen. Je mehr Daten den Dokumenten im DMS bereits zugeordnet sind, desto automatisierter kann seitens Rimo R5 das Dokument im E-Dossier verlinkt werden. Sämtliche Views sind dem Owner DBA zugewiesen.

|View|Beschreibung|
|-|-|
|[vDMSAbrechnungLieg](/_views/vDMSAbrechnungLieg.md)|Diese View enthält die Zuweisungen der Heiz- und Nebenkostenabrechnungen zu den Liegenschaften| 
|[vDMSAdresseZuEntity](/_views/vDMSAdresseZuEntity.md)|Diese View enthält sämtliche Adressen als String mit der jeweiligen Verwendung im Rimo R5. Hiermit können z.B. eingehende Dokumente den Absendern im Rimo R5 zugewiesen werden|
|[vDMSAnrede](/_views/vDMSAnrede.md)|Liste aller in Rimo R5 erfassten Anreden. Wird benötigt wenn die Schnittstelle für automatischen Kreditorenabgleich aktiviert ist|
|[vDMSAuftrag](/_views/vDMSAuftrag.md)|Diese View enthält eine Liste mit sämtlichen Aufträgen inkl. Auftrags-Positionen und -Kontierungen. Die Auftragsnummer gemäss dieser View kann zu einer Rechnung in der Tabelle dmsrechnung.auftragsnr mitgeliefert werden, damit Rimo R5 den offenen Auftrag erledigen kann|
|[vDMSBelegIDzuEntity](/_views/vDMSBelegIDzuEntity.md)|Diese View enthält alle bereits verbuchten Belege mit manueller Belegnummer im Rimo R5. Mit diesen Daten können z.B. nachträglich gescannte Belegdokumente, welche eine Belegnummer enthalten den korrekten Buchungen zugewiesen werden|
|[vDMSBuchungsHistory](/_views/vDMSBuchungsHistory.md)|Diese View enthält die Buchungshistory der letzten drei Jahre. Hiermit können z.B. bereits verwendete Buchungstexte auf bestimmten Konti ermittelt und dem Benutzer zur Kontierung vorgeschlagen werden|
|[vDMSDokument](/_views/vDMSDokument.md)|Diese View enthält eine Liste sämtlicher ursprünglich von Rimo R5 erstellten und vom DMS zurückgemeldeten Dokumente, die erfolgreich via Remapping (dmsremapping) von Rimo R5 verarbeitet wurden|
|[vDMSDokumententLinks](/_views/vDMSDokumentenLinks.md)|Diese View enthält eine Liste von Verlinkungen sämtlicher ursprünglich von Rimo R5 erstellten und vom DMS zurückgemeldeten Dokumente, die erfolgreich via Remapping (dmsremapping) von Rimo R5 verarbeitet wurden. Die View korrespondiert mit allen Dokumenten gemäss vDMSDokument|
|[vDMSDokuTyp](/_views/vDMSDokuTyp.md)|Diese View enthält eine Liste aller Dokumententypen, welche im Rimo R5 verfügbar sind. Jeder Dokumententyp wird je möglicher Zuordnung zu einer Rimo R5 Entität (entityname) in einer separaten Zeile nochmals aufgeführt|
|[vDMSEigentuemer](/_views/vDMSEigentuemer.md)|Eine Liste aller Liegenschaftseigentümern im Rimo R5 zur Ablage von Dokumenten zu deren Dossier|
|[vDMSEmailZuEntity](/_views/vDMSEmailZuEntity.md)|Eine Liste sämtlicher im Rimo R5 vorhandenen E-Mail Adressen und deren Zuordnung zu Entitäten und Stammdaten. Mittels dieser View können z.B. erhaltene E-Mails automatisch den Rimo R5 Daten zugewiesen werden|
|[vDMSExportDokument](/_views/vDMSExportDokument.md)|In dieser View werden sämtliche Dokumente angezeigt, welche von Rimo R5 erstellt und dem DMS zur Archivierung bereit stehen. Der physische Dokumentelink setzt sich aus den Spalten pfad und dateiname zusammen. Dokumente, welche aus dieser View erfolgreich im DMS archiviert wurden, müssen via dmsremapping an Rimo R5 zurückgemeldet werden, damit Rimo R5 diese Dokumente korrekt neu verlinken kann|
|[vDMSFibubuchung](/_views/vDMSFibubuchung.md)|Eine Liste sämtlicher Fibubuchungen aus Rimo R5. Aufgrung der hohen möglichen Datenmenge sollte diese View bei der Abfrage wenn möglich stark eingegrenzt werden|
|[vDMSFibujahr](/_views/vDMSFibujahr.md)|Eine Liste sämtlicher Buchhaltungsperioden zur Ablage von z.B. Abschlussdokumenten|
|[vDMSFinanzbuchhaltung](/_views/vDMSFinanzbuchhaltung.md)|Diese View enthält eine Liste sämtlicher Finanzbuchhaltungen (Fibus) gemäss Rimo R5 Stammdaten|
|[vDMSForderungsart](/_views/vDMSForderungsart.md)|Eine Liste aller Forderungsarten mit der Angabe, ob sie für Mieter und/oder STEG-Eigentümer zulässig ist|
|[vDMSGenossenschaft](/_views/vDMSGenossenschaft.md)|Eine Liste aller Genossenschaften mit Zuordnung zur Finanzbuchhaltung|
|[vDMSGenossenschafter](/_views/vDMSGenossenschafter.md)|Eine Liste aller Genossenschafter|
|[vDMSGeraet](/_views/vDMSGeraet.md)|Diese View zeigt sämtliche Geräte gemäss der technischen Verwaltung im Rimo R5. Die Geräte können anhand der Angaben in der Spalte subgearetvon in eine hierarchische Struktur gebracht werden|
|[vDMSHauswart](/_views/vDMSHauswart.md)|Eine Liste aller Hauswarte inkl. deren Adresse|
|[vDMSHypothek](/_views/vDMSHypothek.md)|Diese View zeigt alle Hypotheken mit der Zuordnung zur Liegenschaft. die Angaben zum Kreditor sowie einer Zahlverbindung sind im Datenmodell berücksichtigt, aber aktuell im Rimo R5 noch nicht in Gebrauch|
|[vDMSIBANZuEntity](/_views/vDMSIBANZuEntity.md)|Diese Liste zeigt alle im Rimo R5 vorhandenen IBAN und deren Zuordnung zu den Daten. In dieser Liste kann nach einer IBAN gesucht und die zugeordneten Daten ermitteln, um z.B. Dokumente mit IBAN zu den richtigen Daten im Rimo R4 abgelegt werden|
|[vDMSKontierungsregel](/_views/vDMSKontierungsregel.md)|In dieser View sind alle definierten Kontierungsregeln mit Referenz-IDs (referenzid) aufgelistet. Die Kontierungsregeln können im Rimo R5 für definierte Geschäftsfälle konfiguriert werden und können im Kontierungsprozess als Vorlage wiederverwendet werden|
|[vDMSKontoplan](/_views/vDMSKontoplan.md)|In dieser View sind alle im Rimo R5 zu bebuchenden Konti aufgeführt. Die verfügbarkeit der Konti wird gemäss Periode Beginn/Ende (periodebeginn/periodeende) definiert. Es dürfen nur Kontierungen via dmskontierung mitgegeben werden, welche gemäss Buchungsdatum (buchungdat) in die hier aufgeführte Periode passen|
|[vDMSKredibuchung](/_views/vDMSKredibuchung.md)|Liste aller Kreditorenrechnngen gemäss Buchhaltung im Rimo R5|
|[vDMSKreditor](/_views/vDMSKreditor.md)|Liste aller Kreditoren/Lieferanten|
|[vDMSKreditorenrechnung](/_views/vDMSKreditorenrechnung.md)|In dieser View werden sämtliche im Rimo R5 verbuchten Kreditorenrechnungen aufgeführt, zu welchen Dokumente existieren. Hier erscheint z.B. auch das Zahlungsdatum (buchdatzlg), sobald die Rechnung via Rimo R5 bezahlt wurde|
|[vDMSKreditorZahlverb](/_views/vDMSKreditorzahlverb.md)|Eine Liste sämtlicher Zahlverbindungen der Kreditoren mit erweiterten Personendaten der Kreditoren. Diese View eignet sich zur Identifikation eines Kreditore gemäss Rechnungssangaben|
|[vDMSLiegenschaft](/_views/vDMSLiegenschaft.md)|Liste aller Liegenschaften|
|[vDMSMieter](/_views/vDMSMieter.md)|Liste aller Mieter/STEG Eigentümer|
|[vDMSMieterbuchung](/_views/vDMSMieterbuchung.md)|In dieser Ansicht werden alle Debitorbuchungen aufgelistet|
|[vDMSMieterZuObjekt](/_views/vDMSMieterZuObjekt.md)|In dieser View werden alle Zuordnungen von Mietern zu Objekten aufgelistet. Die Zuweisung eines Mieters zu einem Objekt entspricht einem Mietverhältnis und ist zeitlich über Mietbeginn und Mietende eingegrenzt|
|[vDMSMWSTCodes](/_views/vDMSMWSTCodes.md)|Liste aller möglichen MWST Codes im Rimo R5. Ein MWST Code muss bei einer Buchung inkl. MWST mit der dmskontierung angegeben werden|
|[vDMSObjekt](/_views/vDMSObjekt.md)|Liste sämtlicher Objekte / Mieteinheiten / STEG-Einheiten|
|[vDMSPersart](/_views/vDMSPersart.md)|Liste aller möglichen Personenarten. Die Personenart muss für den automatischen Kreditorenabgleich zur Neuerfassung einer Person im Kreditorenstamm zur dmsrechnung mitgegeben werden|
|[vDMSRechnung](/_views/vDMSRechnung.md)|Liste aller Kreditorenrechnungen/ -gutschriften (Dokumententypen 1 und 2), welche in den Staging Tabellen DMSImport/DMSRechnung/DMSKontierung erfasst sind|
|[vDMSRGVisumUser](/_views/vDMSRGVisumUser.md)|In dieser View werden alle Benutzer von Rimo R5 dargestellt. Die Benutzer könen in Workflows (vDMSWorkflow) hinterlegt werden|
|[vDMSRolleZuLieg](/_views/vDMSRolleZuLieg.md)|In dieser View werden je Liegenschaft Benutzer in deren Rolle aufgeführt. Alternativ zu den Daten gemäss vDMSWorkflow können auch diese Rollendaten als Basis für Workflows verwendet werden|
|[vDMSUnterhaltsart](/_views/vDMSUnterhaltsart.md)|Liste aller Unterhaltsarten. Die Unterhaltsart kann zur dmskontierung im Rahmen der technischen Verwaltung eingetragen werden|
|[vDMSVerwaltung](/_views/.vDMSVerwaltung.md)|Liste aller Verwaltungen|
|[vDMSWorkflow](/_views/vDMSWorkflow.md)|Liste aller Fibus mit Info des Workflows für Kreditorenrechnungen (Visum1-4)|
|[vDMSZahlungscode](/_views/vDMSZahlungscode.md)|Liste aller möglichen Zahlungscode. Ein Zahlungscode kann alternativ zum Fälligkeitsdatum zur dmsrechnung angegeben werden|
|[vDMSZahlverbKredi](/_views/vDMSZahlverbKredi.md)|Liste aller Zahlverbindungen zu Kreditoren|

# Changelog
|Datum|Tabelle/View|Änderung|Kommentar|
|-|-|-|-|
|23.11.2023|[vDMSDokuTyp](/_views/vDMSDokuTyp.md)|neue Spalte active||
|30.11.2023|[vDMSBuchungsHistory](/_views/vDMSBuchungsHistory.md)|neue Spalte hknkdat||
