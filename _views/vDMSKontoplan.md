# DBA.vDMSKontoplan

|Spaltenname|Typ|Kommentar|
|:----------|:--|:--------|
|fibunr|integer||
|jahr|integer||
|kto|integer||
|mwstnr|integer||
|sprcode|integer||
|periodebeginn|date||
|periodeende|date||
|ktobez1|varchar(30)||
|ktobez2|varchar(30)||
|mengezwing|integer|0 = Mengenangabe optional, 1 = Menge zwingend|
|mengeneinh|varchar(25)| NULL = Mengeneingabe nicht möglich, NOT NULL = Mengenangabe grundsätzlich möglich|
|fuerhknk|integer|0 = Abweichendes HKNK Datum nicht erlaubt<br> 1 = Abweichendes HKNK Datum erlaubt <br> Bei Wer 1 gilt: Der Wert in der Importtabelle DMSKontierung.HKNKDAT darf vom Wert DMSKontierung.BUCHUNGDAT abweichen, bei Wert 0 darf das nicht abweichen.|
|standbuchtx1|varchar(50)||
|standbuchtx2|varchar(50)||
|mwst|integer|Wenn 0, darf keine Rechnung mit MWST auf dieses Konto gebucht werden.<br>Wenn 1 darf eine Rechnung mit MWST auf dieses Konto gebucht werden (muss aber nicht)|
|mwstopt|integer|0 = nein (MWSTNR 12,22,32 sind nicht zulässig – MWSTNR siehe Definition Spezialtabellen DMSKontierung.MWSTNR)<br>1 = ja (Alle MWSTNR zulässig)|
|sammelkonto|integer||
