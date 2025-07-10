# DBA.DMSImport
|Spaltenname|Typ|Zwingend|Beispiel|Kommentar|
|:----------|:--|:-------|:-------|:--------|
|dmsnr|varchar(100)|ja|936DA01F-9ABD-4D9D-80C7-02AF85C822A8|Eindeutige Identifikation eines Dokuments aus dem DMS|
|archiv|integer|ja|500|Die Archivnummer wird von Rimo R5 vergeben, kann dort jedoch im Rahmen der E-Dossier Archivstammdaten frei definiert werden|
|bezeichnung|varchar(255)||Mietvertrag von Hans Muster|Wird ins gleichnamige Feld im E-Dossier übernommen|
|dmsdokutypnr|integer|ja|1|Dokumententypnummer gemäss separater Dokumentation "Dokumententypen.xlsx"|
|verarbstatus|integer|ja|0|Folgende Status sind definiert:<br>0 = bereit zum Import<br>1 = in Arbeit<br>2 = erfolgreich importiert<br>3 = blockiert im Rimo R5<br>-1 = fehlerhafter Import<br>-2 = fehlerhafte Kontierung (nur Dokumententypen 1 und 2 resp. eingehende Rechnung/Gutschrift)|
|dmslinknr|integer||123|Die Rimo R5 eindeutige interne Nummer jedes Dokumentes. Wird durch Rimo R5 definiert|
|beschreibung|long varchar|||Wird in die Dokumenten-Beschreibung im E-Dossier übernommen|
|dateierfdat|timestamp||16.01.2023 15:00:00|Wird in das Dokumentendatum im E-Dossier übernommen. Wird das Feld nicht abgefüllt, wird ins Dokumentendatum der Zeitpunkt des Imports geschrieben|
|fibunr|integer|||Legacyfeld – wird nicht mehr aktiv verwendet|
|kredinr|integer|||Legacyfeld – wird nicht mehr aktiv verwendet|
|verwaltnr|integer|||Legacyfeld – wird nicht mehr aktiv verwendet|
|invoiceid|varchar(36)|||Wird von Rimo-intern im Zusammenhang mit dem Kredi Flow benötigt - bitte nicht abfüllen|
|fehlercode|integer|||Wird von Rimo R5 gemäss [Fehlercodeliste](/_staging%20area/fehlercodes.md) abgefüllt|
|erfuser|varchar(20)|||Erfassungsuser|
|erfdat|timestamp|||Erfassungsdatum|
|beauser|varchar(20)|||Letzer Bearbeitungsuser|
|beadat|timestamp|||Letztes Bearbeitungsdatum|
|satzid|integer|||Wird nur von Rimo R5 verwendet|
