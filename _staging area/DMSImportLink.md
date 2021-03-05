# DBA.DMSimportlink

|Spaltenname|Typ|Zwingend|Beispiel|Kommentar|
|:----------|:--|:-------|:-------|:--------|
|![](pkey16.gif)dmsnr|varchar(100)|ja|936DA01F-9ABD-4D9D-80C7-02AF85C822A8|Eindeutige Identifikation eines Dokuments aus DMS|
|![](pkey16.gif)archiv|integer|ja|500|Die Archivnr wird von Rimo R5 vergeben, kann dort jedoch im Rahmen der E-Dossier Archive frei defineirt werden|
|![](pkey16.gif)laufnr|integer|ja|1|Fortlaufende Nummer pro DMSNR beginnend mit 1|
|entityname|varchar(50)|ja|mieter|Entität gemäss Rimo R5 Entitätenliste ("Dokumententypen.xlsx") mit welcher das Dokument verlinkt werden soll|
|dmsid|integer|||Eine Rimo R5 interne eindeutige ID des Datensatzes pro Entität (nur mit entityname eindeutig). Die dmsid zu einem Datensatz kann aus jeder View (z.B. vDMSMieter) ausgelesen werden und anstelle des kombinierten Primärschlüssels (z.B. liegnr, mieternr) zur Identifikation des Datensatzes verwendet werden|
|liegnr|integer|||Liegenschaftsnummer<br>Für Entitäten: lieg, mieter, objekt, gebaeude, haus, etage, hypothek,mieterbew|
|objnr|integer|||Objektnummer<br>Für Entitäten: objekt|
|mieternr|integer|||Mieternummer<br>Für Entitäten: mieter, mieterbew|
|mbuchungnr|integer|||Buchungsnummer einer Mieterbuchung<br>Für Entitäten: mieterbew|
|gebaeudenr|integer|||Gebäudenummer<br>Für Entitäten: gebaeude|
|hausnr|integer|||Hausnummer<br>Für Entitäten: haus, etage|
|etagenr|integer|||Etagennummer<br>Für Entitäten: etage|
|eigentuemernr|integer|||Eigentümernummer<br>Für Entitäten: eigentuemer|
|verwvertragsnr|integer|||Verwaltungsvertragsnummer<br>Für Entitäten: verwvertrag|
|hauswartnr|integer|||Hauswartnummer<br>Für Entitäten: hauswart|
|hyponr|integer|||Hypothekennummer<br>Für Entitäten: hypothek|
|fibunr|integer|||Fibunummer<br>Für Entitäten: fibu, fibujahr1, fibubuchung|
|jahr|integer|||Jahr (Buchhaltungsjahr)<br>Für Entitäten: fibujahr1|
|fbuchungnr|integer|||Buchungsnummer einer Fibubuchung<br>Für Entitäten: fibubuchung|
|kredinr|integer|||Kreditorennummer<br>Für Entitäten: kreditor,kredibuchungdms|
|flaufnr|integer|||fortlaufende Nummer einer Kreditorenrechnung<br>Für Entitäten: kredibuchungdms|
|geraetenr|integer|||Gerätenummer<br>Für Entitäten: geraet,gunterhalt|
|gabolaufnr|integer|||Geräteabonummer (Serviceabo)<br>Für Entitäten: gabo|
|gunterhaltlaufnr|integer|||Unterhaltslaufnummer<br>Für Entitäten: gunterhalt|
|auftragsnr|integer|||Auftragsnummer<br>Für Entitäten: auftrag|
|abrechnr|integer|||Abrechnungsnummer<br>Für Entitäten: abrechhknk|
|genonr|integer|||Genosssenschaftsnummer<br>Für Entitäten: akgenossenschaft, akgenomitglied, akmitglkonto, akmitglkontobeweg|
|mitglnr|integer|||Genossenschafternummer<br>Für Entitäten: akgenomitglied, akmitglkonto, akmitglkontobeweg|
|genokontoartnr|integer|||Genossenschaft-Kontoart<br>Für Entitäten: akmitglkonto, akmitglkontobeweg|
|mitglktonr|integer|||Genossenschafter Kontonummer<br>Für Entitäten: akmitglkonto, akmitglkontobeweg|
|gbuchungnr|integer|||Genosssenschafter Buchungsnummer<br>Für Entitäten: akmitglkontobeweg|
|gebaeudeversnr|integer|||Gebäudeversicherungsnummer<br>Für Entitäten: gebaeudevers|
|versicherungnr|integer|||Versicherungsnummer<br>Für Entitäten: versicherung|
|aufgabenr|integer|||Nummer einer Aufgabe<br>Für Entitäten: aufgabe|
|jobnr|integer|||Nummer eines Jobs<br>Für Entitäten: jobkonfig|
|ausgabenr|integer|||Ausgabenumme<br>\>Für Entitäten: ausgabe|
|persnr|integer|||Personennummer<br>Für Entitäten: person|
|prodreportid|integer|||ReportID<br>Für Entitäten: archivreport|
|produserid|varchar(20)|||BenutzerID<br>Für Entitäten: produsers|
|fehlercode|integer|||Fehler gemäss [Fehlercodeliste](/_staging%20area/fehlercodes.md)|
|lnkvstatus|integer|||Linkstatusnummer|
|erfuser|varchar(20)|||Erfassungsuser|
|erfdat|timestamp|||Erfassungsdatum|
|beauser|varchar(20)|||Letzer Bearbeitungsuser|
|beadat|timestamp|||Letztes Bearbeitungsdatum|
|satzid|integer|||wird nur von Rimo R5 verwendet|
