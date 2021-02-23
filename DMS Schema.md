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
|vDMSAdresseZuEntity|Diese View enthält sämtliche Adressen als String mit der jeweiligen Verwendung im Rimo R5Hiermit können z.B. eingehende Dokumente den Absendern im Rimo R5 zugewiesen werden|
|vDMSAuftrag|Diese View enthält eine Liste mit sämtlichen Aufträgen. Die Auftragsnummer gemäss dieser View kann zu einer Rechnung in der Tabelle dmsrechnung.auftragsnr mitgeleifert werden, damit Rimo R5 den offenen Auftrag erledigen kann|
|vDMSBelegIDzuEntity|Diese View enthält alle bereits verbuchten Belege mit manueller Belegnummer im Rimo R5. mit diesen Daten können z.B. nachträglich gescannte Belegdokumente, welche eine Belegnummer enthalten den korrekten Buchungen zugewiesen werden|
|vDMSBuchungsHistory|Diese View enthält die Buchungshistory der letzten drei Jahre. Hiermit können z.B. bereits verwendete Buchungstexte auf bestimmten Konti ermittelt und dem Benutzer zur Kontierung vorgeschlagen werden|
|vDMSDokument|Diese View enthält eine Liste sämtlicher ursprünglich von Rimo R5 erstellten und vom DMS zurückgemeldeten Dokumente, die erfolgreich via Remapping (dmsremapping) von Rimo R5 verarbeitet wurden|
|vDMSDokumententLinks|Diese View enthält eine Liste von Verlinkungen sämtlicher ursprünglich von Rimo R5 erstellten und vom DMS zurückgemeldeten Dokumente, die erfolgreich via Remapping (dmsremapping) von Rimo R5 verarbeitet wurden. Die View korrespondiert mit allen Dokumenten gemäss vDMSDokument|
|vDMSDokuTyp||
|vDMSEigentuemer||
|vDMSEmailZuEntity||
|vDMSExport||
|vDMSExportDokument||
|vDMSFibubuchung||
|vDMSFibujahr||
|vDMSFinanzbuchhaltung||
|vDMSGenossenschaft||
|vDMSGenossenschafter||
|vDMSGeraet||
|vDMSHauswart||
|vDMSHypothek||
|vDMSIBANZuEntity||
|vDMSKontierungsregel||
|vDMSKontoplan||
|vDMSKredibuchung||
|vDMSKreditor||
|vDMSKreditorenrechnung||
|vDMSKreditorZahlverb||
|vDMSLiegenschaft||
|vDMSMieter||
|vDMSMieterbuchung||
|vDMSMieterZuObjekt||
|vDMSMWSTCodes||
|vDMSObjekt||
|vDMSPersart||
|vDMSRGVisumUser||
|vDMSRolleZuLieg||
|vDMSUnterhaltsart||
|vDMSVerwaltung||
|vDMSWorkflow||
|vDMSZahlungscode||
|vDMSZahlverbKredi||
 


