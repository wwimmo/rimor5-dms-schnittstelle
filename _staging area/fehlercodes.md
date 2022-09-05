# Fehlercodeliste
Die Fehlercodes werden jeweils durch den Rimo R5 Import in die zugehörige Staging Table geschrieben, sobald der Datensatz verarbeitet wurde.

|Fehlercode|Beschreibung|...|
|-|-|-|
|100|Die DMS-Nummer aus der Importtabelle ist bereits im System vorhanden - keine Doppelerfassung möglich||
|110|Nicht korrekt abgefüllte Stagingtabellen (Eintrag in DMSRECHNUNG fehlt)||
|120|Das Fälligkeitsdatum muss grösser oder gleich dem Rechnungsdatum sein||
|130|Zu diesem Beleg ist kein Kreditor angegeben - automatischer Import nicht möglich||
|140|Belegtotal 0 nicht erlaubt||
|200|Keine Kontierungszeilen zum Beleg vorhanden||
|210|Der Totalbetrag der Kontierung (%n) entspricht nicht dem Totalbetrag der Rechnung (%n)||
|220|Wenn kein Fälligkeitsdatum angegeben ist darf der Zahlungscode nicht leer sein||
|225|Die Zahlverbindungsnummer ist für den aktuellen Kreditor ungültig||
|226|Die Zahlverbindungsinformationen fehlen oder können nicht automatisch zugeordnet werden||
|227|Die Rechnung hat keine ESR-Referenz obwohl diese zusammen mit der Teilnehmer-Nr. zwingend ist||
|228|Falsche Länge des ESR-Codes - dieser kann nicht verarbeitet werden||
|229|Falsche Zusammensetzung der Codierzeile - diese kann nicht verarbeitet werden||
|230|Falsche Prüfziffer der ESR-Referenz||
|231|Die aus der Teilnehmernummer ermittelte Clearing-Nummer ist im Clearingstamm nicht vorhanden||
|232|Falsche Prüfziffer der Teilnehmer-Nummer oder der IBAN||
|233|Falsche Prüfziffer des ESR-Betrages oder ESR-Betrag stimmt nicht mit dem Rechnungsbetrag überein||
|234|Falsche/Ungültige Teilnehmer-Nummer oder ESR-Referenz||
|235|Die angegebene IBAN bzw. Teilnehmer-Nummer stimmt nicht mit der im ESR-Code überein||
|236|Die angegebene IBAN bzw. Teilnehmer-Nummer stimmt nicht mit der in der Zahlverbindung überein||
|237|Die angegebene Teilnehmer- bzw. Clearing-Nr. stimmt nicht mit der aus der IBAN ermittelten überein||
|238|Zeilenlänge der ESR Referenz zur DMS Rechnung stimmt nicht mit der Zahlverbindung Kredi überein||
|239|Zur erfassten Zahlverbindung (ESR) muss zwingend eine ESR-Referenz eingegeben werden||
|240|Keine FIBU-Nr. auf der Kontierungszeile erfasst||
|250|Keine Konto-Nr. auf der Kontierungszeile erfasst||
|260|Kein Buchungs-/Valuta-Datum auf der Kontierungszeile erfasst||
|270|Kein Buchungstext auf der Kontierungszeile erfasst||
|280|Die FIBU %d der Kontierung existiert nicht||
|290|Das FIBU-Jahr der FIBU %d zum Buchungsdatum %s ist nicht eröffnet||
|300|Das FIBU-Jahr %d der FIBU %d zum Buchungsdatum %s ist nicht offen für Buchungen||
|310|Zum oder nach dem Buchungsdatum %s wurde im FIBU-Jahr %d der FIBU %d  ein Zwischenabschluss erfasst||
|320|Das Konto %d ist im FIBU-Jahr %d (FIBU %d) nicht vorhanden||
|330|Für das FIBU-Konto %d (FIBU %d) muss zwingend eine Menge angegeben werden||
|340|Für das FIBU-Konto %d (FIBU %d) darf keine Menge erfasst werden||
|350|Das FIBU-Konto %d (FIBU %d) ist nicht für Mehrwertsteuer konfiguriert||
|360|Das Vorsteuerkonto %d für das FIBU-Konto %d (FIBU %d) existiert nicht||
|370|Der erfasste Mehrwertsteuer-Code %d ist ungültig||
|380|Buchungen mit optiertem Anteil dürfen nicht auf das FIBU-Konto %d gebucht werden||
|390|Der eingegebene Mehrwertsteuersatz %n ist ungültig||
|391|Es wurde zu MWST-Nr %d und Buchungsdatum %s kein gültiger MWST-Satz gefunden oder angegeben||
|400|Die Banknummer Kredi ist auf der FIBU %d nicht erfasst||
|410|Die Banknummer Kredi auf unterschiedlichen FIBUs einer Kontierung muss gleich sein||
|420|Unterschiedliche Buchungsdaten auf der Kontierung zum Beleg - automatischer Import nicht möglich||
|431|Fehlerhafter QR-Code - automatischer Import nicht möglich||
|432|Fehlende IBAN- bzw. QRIBAN-Angabe - automatischer Import nicht möglich||
|433|Ungültige QR-IBAN (Länge, Ländercode, Prüfziffer oder QR-IID) - autom. Import nicht möglich||
|434|Zu einer QR-IBAN muss zwingend eine QR-Referenz angegeben werden - autom. Import nicht möglich||
|435|Fehlerhafte QR-Referenz (Länge oder Prüfziffer) - automatischer Import nicht möglich||
|436|Ungültige Kombination QR-IBAN mit Creditor-Referenz - automatischer Import nicht möglich||
|437|Ungültige Creditor-Referenz (Länge, Prüfziffer, Startzeichen) - autom. Import nicht möglich||
|438|Ungültige Kombination IBAN mit QR-Referenz - automatischer Import nicht möglich||
|439|Die angegebene IBAN bzw. QR-IBAN stimmt nicht mit der in der Zahlverbindung überein||
|500|Die Mieter-Nr. %d ist in der Liegenschaft %d nicht vorhanden||
|510|Das Mietersammelkonto %d ist im FIBU-Jahr %d (FIBU %d) nicht vorhanden||
|501|Die Objekt-Nr. %d ist in der Liegenschaft %d nicht vorhanden||
|502|Die Objekt-Nr. %d ist in der Liegenschaft %d annulliert||
|503|Für die Objekt-Nr. %d existiert kein Mietfall mit der Mieter-Nr. %d in der Liegenschaft %d||
|504|Die Angabe der Forderungsart ist nur zulässig für Kontierungen mit erfasster Mieternummer||
|505|Die Kontierung enthält eine nicht zulässige Forderungsart (Miet- oder Steg-Liegenschaft)||
|600|Der Auftrag mit der Nummer %d ist nicht vorhanden||
|610|Das Gerät mit der Nummer %d ist in der Technischen Verwaltung nicht vorhanden||
|620|Die Unterhaltsart-Nr. %d ist ungültig||
|321|Das Kreditoren-Konto %d ist im FIBU-Jahr %d (FIBU %d) nicht vorhanden||
|440|ESR-Code und QR-Code zusammen erfasst - automatischer Import nicht möglich||
|441|Untersch. IBAN/QRIBAN/QRRef/CreditorRef in Feldern und im QRCode - autom. Import nicht möglich||
|442|Untersch. IBAN im Feld und im ESRCode - automatischer Import nicht möglich||
|443|Untersch. Zahlverbindung im Feld und ermittelt aus QRCode - automatischer Import nicht möglich||
|444|Kombination QRR-Code/ESR-Felder nicht erlaubt - automatischer Import nicht möglich||
|445|Kombination ESR-Code/QRR-Felder nicht erlaubt - automatischer Import nicht möglich||
|446|Kombination ESR-Felder/QRR-Felder nicht erlaubt - automatischer Import nicht möglich||
|700|Fehlende Angaben zu %s für Dok./Dossier %s b. DMS-Importlink. DMS-Angaben ergänzen oder man. Import||
|710|Zwingendes Feld %s für den automatischen Import leer. DMS-Angaben ergänzen oder manueller Import||
|720|Der Dokumententyp ist inaktiv gesetzt. DMS-Angaben korrigieren oder manueller Import||
|730|Keine Linkeinträge seitens DMS zu diesem Dokument. DMS-Angaben ergänzen oder manueller Import||
|740|Zu diesem Dokument gibt es keine Entitätenzuweisung. DMS-Angaben ergänzen oder manueller Import||
|750|Die Entität %s existiert in Rimo R5 nicht. DMS-Angaben korrigieren oder manueller Import||
|760|Entitätenzuweisung %s zu Dokument (%s) nicht zulässig. DMS-Angaben korrigieren oder manueller Import||
|705|DMSId %s in Tabelle %s nicht vorhanden. DMS-Angaben korrigieren oder manueller Import||
|800|Die vom DMS angegebene DMSLinkNr existiert in Rimo R5 nicht||
|810|Die DMS-Nr./Archiv-Kombination aus der Remappingtabelle ist bereits in Rimo R5 vorhanden||
|820|Das Dokument mit der angegebenen DMSLinkNr wurde schon exportiert/remapped||
|830|Falscher Dokumentenzustand für diesen Dokumententyp (kleiner 2)||
|840|Falsche Map-Aktion für dieses Remapping erfasst (ungleich 1)||
|999|nicht definierter Fehler / unerwarteter Fehler (z.B. interner Datenbankfehler)||
