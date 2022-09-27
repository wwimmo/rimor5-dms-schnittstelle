# DBA.DMSrechnung

|Spaltenname|Typ|Zwingend|Beispiel|Kommentar|
|:----------|:--|:-------|:-------|:--------|
dmsnr|varchar(100)|ja|936DA01F-9ABD-4D9D-80C7-02AF85C822A8|Eindeutige Identifikation eines Dokuments aus DMS
|archiv|integer|ja|500|Die Archivnr wird von Rimo R5 vergeben, kann dort jedoch im Rahmen der E-Dossier Archive frei defineirt werden
|rechnr|varchar(25)||Rechnr, 159X630|Rechnungsnummer
|rechnungdat|date|bedingt|03.11.2020|Rechnungsdatum<br>zwingend für automatischen Import
|betrag|numeric(11, 2)|bedingt|500|Rechnungsbetrag oder Gutschriftsbetrag<br>Betrag immer > 0.00 und inkl. MWST (brutto) erwartet<br>zwingend für automatischen Import
|faelligdat|date|bedingt|04.12.2020|Fälligkeitsdatum der Rechnung<br>faelligdat hat Priorität vor zlgcode wenn beides geliefert wird.<br>zwingend für automatischen Import, wenn zlgcode leer ist
|zlgcode|integer|bedingt|1|Zahlungscode (Codeliste gemäss vDMSZahlungscode). faelligdat hat Priorität vor zlgcode.<br>zwingend für automatischen Import, wenn faelligdat leer ist
|zahlgrund1|varchar(28)||Grund Zeile 1|Detailangaben zum Zahlungsauftrag.<br>nur für DMSDokutypnr = 1 Rechnung sinnvoll
|zahlgrund2|varchar(28)||Grund Zeile 2|Detailangaben zum Zahlungsauftrag.<br>nur für DMSDokutypnr = 1 Rechnung sinnvoll
|zahlgrund3|varchar(28)||Grund Zeile 3|Detailangaben zum Zahlungsauftrag.<br>nur für DMSDokutypnr = 1 Rechnung sinnvoll
|zahlgrund4|varchar(28)||Grund Zeile 4|Detailangaben zum Zahlungsauftrag.<br>nur für DMSDokutypnr = 1 Rechnung sinnvoll
|iban|varchar(34)|bedingt|CH35 0023 0230 5042 2318 T|Zahlungstypen: roter Einzahlungsschein, QR Rechnung mit IBAN, QR Rechnung mit Creditor Reference<br>zwingend für automatischen Import, wenn zahlverbindnr leer ist<br>oder bei QR Rechnung, wenn qrcodetext und zahlverbindnr leer ist
|teilnehmernr|varchar(11)|bedingt|01-2654-5|Zahlungstypen: oranger Einzahlungsschein (ESR)<br>Alternativ zu zahlverbindnr oder esrcode<br>zwingend für automatischen Import, wenn zahlverbindnr und esrcode leer sind
|esrref|varchar(27)|bedingt|00 0000 02009 00050 05260 83538|Zahlungstypen: oranger Einzahlungsschein (ESR)<br>Alternativ zu esrcode<br>zwingend für automatischen Import, wenn esrcode leer ist
|esrcode|varchar(100)|bedingt||Zahlungstypen: oranger Einzahlungsschein (ESR)<br>Prioritär gegenüber zahlverbindnr und teilnehmernr/esrref<br>zwingend für automatischen Import, wenn zahlverbindnr und teilnehmernr/esrref leer sind/td>
|qriban|varchar(34)|bedingt|CH44 3199 9123 0008 8901 2|Zahlungstypen: QR Rechnung mit QRR<br>Alternativ zu zahlverbindnr oder qrtext<br>zwingend für automatischen Import, wenn zahlverbindnr und qrtext leer
|qrreferenz|varchar(27)|bedingt|00 0000 02009 00050 05260 83538|Zahlungstypen: QR Rechnung mit QR<br>Alternativ zu qrtext<br>zwingend für automatischen Import, wenn qrtext leer
|creditorref|varchar(25)||RF48 5000 0567 8901 2345|Alternativ zu qrcodetext<br>SCOR (Structured Creditor Reference) nach ISO 11649<br>Unstrukturierte Mitteilung gemäss QR Code Feld:<br>QRCH<br>+RmtInf<br>++AddInf<br>+++Ustrd
|kundenreferenz|varchar(35)|||Alternativ zu qrcodetext<br>Kundenreferenz gemäss Rechnungsinformationen im QR-Code Feld:<br>QRCH<br>+RmtInf<br>++AddInf<br>+++StrdBkgInf<br>gemäss Kundenrefernz = Swico Tag /20/
|alternverf1|varchar(100)|||Alternativ zu qrcodetext<br>String für alternatives Verfahren gemäss Rechnungsinformationen im QR-Code Feld Zeile 1:<br>QRCH<br>+AltPmtInf<br>++AltPmt
|alternverf2|varchar(100)|||Alternativ zu qrcodetext<br>String für alternatives Verfahren gemäss Rechnungsinformationen im QR-Code Feld Zeile 2:<br>QRCH<br>+AltPmtInf
|qrcodetext|varchar(1000)|bedingt||Gesamter QR Code als String (wird beim Import als Daten ausgelesen)<br>Alternativ zu allen Detailfeldern<br>zwingend für automatischen Import, wenn iban oder qriban/qrreferenz leer
|kredinr|integer|bedingt|51|Kreditorennummer aus Rimo R5 Kreditorenstamm.<br>zwingend für automatischen Import
|zahlverbindnr|integer|bedingt|1|Zahlverbindungsnummer aus Rimo R5 Zahlverbindungsstamm (View vDMSKreditorZahlverb)<br>zwingend für automatischen Import, wenn iban oder teilnehmernr oder
|rspid|varchar(17)|bedingt|4.10108E+16|RS-PID für E-Rechnungssteller<br>zwingend für automatischen Import einer E-Rechnung
|auftragsnr|integer||21|Auftragsnummer gemäss View vDMSAuftrag. Der Auftrag wird im Rimo R5 bei Rechnungsimport erledigt.
|ohnezahlung|char(1)||Y|Die Rechnung direkt nach dem Import auf Status "nicht zahlen" setzen (bei "Y", Default = "N"). Funktionalität aktuell noch nicht immplementiert
|fehlercode|integer|||Wird von Rimo R5 abgefüllt. Gemäss  [Fehlercodeliste](/_staging%20area/fehlercodes.md).
|erfuser|varchar(20)|||Erfassungsuser
|erfdat|timestamp|||Erfassungsdatum
|beauser|varchar(20)|||Letzer Bearbeitungsuser
|beadat|timestamp|||Letztes Bearbeitungsdatum
|satzid|integer|||wird nur von Rimo R5 verwendet


*alle folgenden Personendaten sind nur zu liefern, wenn die Schnittstelle für automatischen Kreditorenabgleich aktiviert ist*

|Spaltenname|Typ|Zwingend|Beispiel|Kommentar|
|:----------|:--|:-------|:-------|:--------|
|extkredinr|integer||9647|Kreditorennummer gemäss Drittsystem
|persartnr|integer||1|Art der Person gemäss vDMSPersart
|anredenr|integer||2|Anrede der Person gemäss vDMSAnrede. Funktionalität aktuell noch nicht immplementiert
|vorname|varchar(30)||Hans|zwingend für automatischen Import einer neuen Person, wenn natürliche Person
|name|varchar(40)||Muster|zwingend für automatischen Import einer neuen Person, wenn natürliche Person
|nambezeichnung|varchar(40)|bedingt|Muster AG|Wenn PERSART = jur. Person<br>zwingend für automatischen Import einer neuen Person, wenn juristische Person
|namzusatz2|varchar(30)||Filiale Zürich|nur wenn juristische Person
|namzusatz3|varchar(30)||Hauswartung|
|strasse|varchar(30)|bedingt|Müsterliweg 1|Strasse und Nr.<br>zwingend für automatischen Import einer neuen Person, wenn postfach leer
|postfach|varchar(30)|bedingt|Postfach 1|Postfach, zwingend für automatischen Import einer neuen Person, wenn strasse leer ist
|plz|varchar(10)|bedingt|8000|Postleitzahl, zwingend für automatischen Import einer neuen Person
|ort|varchar(30)|bedingt|Zürich|Ortschaft, zwingend für automatischen Import einer neuen Person
|kanton|varchar(5)||ZH|Kanton (Kürzel)
|landkbez|varchar(2)|bedingt|CH|zwingend für automatischen Import einer neuen Person
|telefon|varchar(60)||044 812 25 68|
|mobile|varchar(60)||079 868 41 35|
|email|varchar(254)||in-fo@musterag.ch|
|fax|varchar(60)||044 812 25 99|
|regnrmwst|varchar(20)||CHE-123.456.789 MWST|
|unternehmensid|varchar(15)||CHE-123.456.789|

