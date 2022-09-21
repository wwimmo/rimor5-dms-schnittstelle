# DBA.DMSImport
|Spaltenname|Typ|Zwingend|Beispiel|Kommentar|
|:----------|:--|:-------|:-------|:--------|
|dmsnr|varchar(100)|ja|936DA01F-9ABD-4D9D-80C7-02AF85C822A8|Eindeutige Identifikation eines Dokuments aus DMS|
|archiv|integer|ja|500|Die Archivnr wird von Rimo R5 vergeben, kann dort jedoch<br>im Rahmen der E-Dossier Archive frei defineirt werden|
|bezeichnung|varchar(50)|bedingt|Mietvertrag von Hans Muster|zwingend nur für automatischen Import bei allen<br> Dokumenten ausser 1 Rechnung und 2 Gutschrift|
|dmsdokutypnr|integer|ja|1|Dokumententypnummer gemäss separater Dokumentation "Dokumententypen.xlsx"|
|verarbstatus|integer|ja|0|Es gibt folgende Status:<br>0 = bereit zum Import<br>1 = in Arbeit<br>2 = erfolgreich importiert<br>3 = blockiert im Rimo R5<br>-1 = fehlerhafter Import<br>-2 = fehlerhafte Lieferung|
|dmslinknr|integer||123|Die Rimo R5 interne eindeutige Nummer eines jeden Dokuments<br>Wird durch Rimo R5 definiert|
|beschreibung|long varchar|||Wird ins E-Dossier übernommen beim Dokumentenimport vom DMS bei allen Dokumententypen ausser 1 und 2 Rechnung/Gutschrift (eingehend)|
|fibunr|integer|||Legacyfeld – wird nicht mehr aktiv verwendet.|
|kredinr|integer|||Legacyfeld – wird nicht mehr aktiv verwendet.|
|verwaltnr|integer|||Legacyfeld – wird nicht mehr aktiv verwendet.|
|fehlercode|integer|||Wird von Rimo R5 abgefüllt. Gemäss [Fehlercodeliste](/_staging%20area/fehlercodes.md).|
|erfuser|varchar(20)|||Erfassungsuser|
|erfdat|timestamp|||Erfassungsdatum|
|beauser|varchar(20)|||Letzer Bearbeitungsuser|
|beadat|timestamp|||Letztes Bearbeitungsdatum|
|satzid|integer|||wird nur von Rimo R5 verwendet|
