# DBA.DMSKontierung

|Spaltenname|Typ|Zwingend|Beispiel|Kommentar|
|:----------|:--|:-------|:-------|:--------|
|dmsnr|varchar(100)|ja|936DA01F-9ABD-4D9D-80C7-02AF85C822A8|Eindeutige Identifikation eines Dokuments aus DMS|
|archiv|integer|ja|500|Die Archivnr wird von Rimo R5 vergeben, kann dort jedoch im Rahmen der E-Dossier Archive frei definiert werden|
|laufnr|integer|ja||Fortlaufende Nummerierung pro dmsnr beginnend mit 1 |
|fibunr|integer|bedingt|81100|Nummer der Finanzbuchhaltung <br>zwingend für automatischen Import|
|liegnr|integer|bedingt|11001|Liegenschaftsnummer gemäss vDMSObjekt<br>zwingend, wenn Objekt (objnr) angegeben wird|
|objnr|integer||10001|Objektnummer gemäss vDMSObjekt|
|:information_source:mieternr[^1]|integer|bedingt|1000101|Mieternummer. Prioritär gegenüber Kontierung (kto)<br>zwingend für automatischen Import, wenn kto leer|
|forderungsart|integer||2|Forderungsart gemäss vDMSForderungsart nur möglich wenn Mieter bzw. STEG-Eigentümer (mieternr) angegeben wird|
|:information_source:kto[^1]|integer|bedingt|4100|Kontonummer. Alternativ zu Mieternummer (mieternr)<br>zwingend für automatischen Import, wenn mieternr leer|
|buchtxt1|varchar(50)|bedingt|Hauswartung|Buchungstext 1<br>zwingend für automatischen Import<br>Wichtig: keine Zeilenumbrüche|
|buchtxt2|varchar(50)||Laub zusam-mennehmen|Buchungstext 2<br>Wichtig: keine Zeilenumbrüche|
|menge|numeric(13, 2)|bedingt|500|Menge ist nur zwingend, wenn Menge auf Konto als zwingend definiert (vDMSFibukonto.MENGEZWING = 1)|
|buchungdat|date|bedingt|03.11.2020|Buchungsdatum muss pro dmsnr immer gleich sein<br>zwingend für automatischen Import|
|hknkdat|date||03.11.2020|Datum zur Abgrenzung der Nebenkostenabrechnung. Wenn dieser Wert leer (NULL) geliefert wird, so überträgt Rimo R5 den Wert = BUCHUNGDAT beim Import in die Systemtabellen. Ansonsten wird das HKNKDAT in die Rimo R5 Buchung übernommen.|
|betrag|numeric(11, 2)|bedingt|500.00|Betrag der Kontierung<br>zwingend für automatischen Import|
|belegnr|integer||532|manuelle Belegnummer|
|mwstnr|integer|bedingt|10|MWST Code. <br>zwingend für automatischen Import, wenn Betrag mit MWST gebucht werden soll|
|mwstsatz|numeric(5, 2)||8.00|Mehrwertsteuersatz<br>Ist nur nötig, wenn der %-Satz ein anderer ist, als derjenige, welcher zum Buchungsdatum gültig ist. <br>Bsp: per 23.01.2018 ist 7.7% gültig. Bei einer Rechnung per Buchungsdatum 23.01.2018, welche aber das Jahr 2017 betrifft, muss hier 8.00% eingetragen werden. Hinweis: Ab Rimo R5 5.4.2.1008 diese Spalte nur zusammen mit "mwstnr" abfüllen, sonst kann der Beleg nicht importiert werden - es wird Import-Fehler 392 ausgegeben.|
|netto|char(1)||N|‚N‘ oder NULL = BRUTTO<br>‚Y‘ = NETTO<br>NETTO bezieht sich auf den Betrag bezüglich MWST.<br>Wenn Betrag inkl. MWST, so kann Feld NETTO leer sein,<br>wenn Betrag exkl. MWST, so muss NETTO = ‚Y‘ sein.|
|geraetenr|integer||698|Gerätenummer gemäss vDMSGeraet.<br>Wenn ein automatischer Unterhalt erfasst werden soll, so muss ein Gerät definiert werden.|
|unterhaltsartnr|integer||1||Unterhaltsart gemäss vDMSUnterhaltsart|
|kurzbez|varchar(40)||Hauswartung||Kurzbezeichnung des Unterhalts|
|auftragsnr|integer||21|Auftragsnummer gemäss View vDMSAuftrag. Der Auftrag wird im Rimo R5 bei Rechnungsimport erledigt. Falls leer gelassen (NULL) wird ein eventuell erfasster Wert aus DMSRechnung.auftragsnr übernommen.
|fehlercode|integer|||Wird von Rimo R5 abgefüllt.  [Fehlercodeliste](/_staging%20area/fehlercodes.md)|
|erfuser|varchar(20)|||Erfassungsuser|
|erfdat|timestamp|||Erfassungsdatum|
|beauser|varchar(20)|||Letzer Bearbeitungsuser|
|beadat|timestamp|||Letztes Bearbeitungsdatum|
|satzid|integer|||wird nur von Rimo R5 verwendet|

[^1]: Neuer Konfigurationeintrag `INIT, DMS, 5, DMS-Links auf Mieter anlegen` *0 = deaktiviert (Standard), 1 = aktiviert* (ab 5.4.2.564)<br>
  Wenn dieser aktiv ist (Typ 1), wird<br>
  a) der Kreditoren-Beleg mit dem auf der Kontierung angegebenen Mieter verlinkt – bei der Aufwandverbuchung wird jedoch nur eine Mieterbewegung angelegt, wenn das FIBU-Konto auf der 
  Kontierung leer ist oder dem Mietersammel-Konto entspricht (bei Konfig-Typ 0 wird bei angegebener Mieter-Nr. immer eine Mieterbewegung angelegt, die angebebene Kontonummer wird dabei 
  ignoriert und durch das Mietersammelkonto ersetzt)<br>
  b) wenn auf der Kontierung ein Auftrag erfasst ist, wird der Kreditoren-Beleg mit dem Mieter aus der Auftragskontierung verlinkt, dabei werden jedoch keine mehrfachen Links auf den 
  gleichen Mieter erstellt (sollte der gleiche Mieter in der DMS-Kontierung und in der Auftrags-Kontierung erfasst sein)<br>

