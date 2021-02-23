# DBA.vDMSAbrechnungLieg 
Diese View enthält eine Liste aller Nebenkostenabrechnungen mit Zuordnung zur Liegenschaft. Dokumente für Entität abrechhknk können zur Nebenkostenabrechnung abgelegt werden.

|Spaltenname|Typ|Kommentar|
|:----------|:--|:--------|
|abrechnr|integer||
|liegnr|integer||
|bezeichnung|varchar(30)||
|fibunr|integer||
|fibujahr|integer||
|beginn|date||
|ende|date||
|status|char(1)||
|verwaltnr|integer||
|verwaltbezeichnung|varchar(30)||
|beschreibung|long varchar||
|entityname|varchar(50)||
|dmsid|integer||
