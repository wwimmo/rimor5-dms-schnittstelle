# DBA.dmsremapping

|Spaltenname|Typ|Zwingend|Beispiel|Kommentar|
|:----------|:--|:-------|:-------|:--------|
|remapid|integer||autoincrement|ID wird von Rimo R5 automatisch vergeben|
|dmsnr|varchar(100)|ja|936DA01F-9ABD-4D9D-80C7-02AF85C822A8|Eindeutige Identifikation eines Dokuments aus DMS|
|archiv|integer|ja|500|Die Archivnr wird von Rimo R5 vergeben, kann dort jedoch im Rahmen der E-Dossier Archive frei definiert werden|
|dmslinknr|integer|ja|9803|Eindeutige Rimo R5 interne Identifikation des Dokuments gemäss vDMSExportDokument|
|laufnr|integer|||Ab 5.2.7/bei mehreren DMS-Links: Laufnummer des Dokuments gemäss vDMSExportDokument|
|mapaktion|integer|ja|1|Aktion für Rimo R5:<br>1 = Remapping|
|bezeichnung|varchar(50)||Mietvertrag Hans Muster|Bezeichnung des Dokuments im DMS|
|verarbstatus|integer|ja|0|Verarbeitungsstatus<br>0 = bereit zum Remapping<br>1 = in Arbeit<br>2 = erfolgreiches Remapping<br>-2 = fehlerhaftes Remapping|
|fehlercode|integer|||Wird von Rimo R5 abgefüllt (gemäss [Fehlercodeliste](/_staging%20area/fehlercodes.md))|
|remapdmslinknr|integer|||Wird von Rimo R5 abgefüllt|
|remaplaufnr|integer|||Wird von Rimo R5 abgefüllt|
|erfuser|varchar(20)|||Erfassungsuser|
|erfdat|timestamp|||Erfassungsdatum|
|beauser|varchar(20)|||Letzter Bearbeitungsuser, wird von Rimo R5 abgefüllt|
|beadat|timestamp|||Letztes Bearbeitungsdatum, wird von Rimo R5 abgefüllt|
|satzid|integer|||wird nur von Rimo R5 verwendet|
