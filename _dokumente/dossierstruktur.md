# Dossierstruktur

#### Die Hauptentitäten zur Dokumentenablage
*Diese Entitäten werden in den meisten Fällen für die Dokumentenablage verwendet. 
Wir empfehlen grundsätzlich nur mit diesen Ablagedossiers zu arbeiten. 
Wenn Sie eine detailliertere Ablagestruktur wünschen, können Sie die Dokumente auch zu den weiter unten aufgeführten Entitäten ablegen.*

|Entität|Entityname|Beschreibung|Dokumententypen|
|:-|:-|:-|:-|
|Liegenschaft|lieg|Dokumente zu einer Liegenschaft|
|Objekt|objekt|Dokumente zu einem Objekt/einer Miet- oder STWEG-Einheit|
|Mieter|mieter|Dokumente zu einem Mieter/STWEG-Eigentümer|
|Fibujahr|fibujahr|Dokumente zu einer Buchhaltungsperiode|
|Buchung (Hauptbuch)|fibubuchung|Dokumente zu einem Buchungsbeleg|

<br>

#### Detailentitäten für Buchhaltungsdokumente
*Zu diesen Entitäten können weitere Dokumente mit Buchhaltungsbezug archiviert werden.*
|Entität|Entityname|Beschreibung|Dokumententypen|
|:-|:-|:-|:-|
|Abrechnung|abrechhknk||
|Finanzbuchhaltung|fibu|Dokumente zur Finanzbuchhaltung. Bei einer Liegenschaftsbuchhaltung entspricht diese Entität immer auch der Entität "lieg"|
|Buchung (Kreditoren)|kredibuchungdms|Kreditorenbeleg Nebenbuch|
|Buchung (Mieter)|mieterbew|Mieterbeleg Nebenbuch|

<br>

#### Entitäten mit Personenbezug
**
|Entität|Entityname|Beschreibung|Dokumententypen|
|:-|:-|:-|:-|
|Eigentümer|eigentuemer||
|Hauswart|hauswart||
|Kreditor|kreditor||
|Person|person||
|Benutzer|produsers||

#### Entitäten zur detaillierten physischen Liegenschaftsstruktur
**
|Entität|Entityname|Beschreibung|Dokumententypen|
|:-|:-|:-|:-|
|Gebäude|gebaeude||
|Haus|haus||
|Etage|etage||

<br>

#### Detailentitäten für Verträge
**
|Entität|Entityname|Beschreibung|Dokumententypen|
|:-|:-|:-|:-|
|Gebäudeversicherung|gebaeudevers||
|Hypothek|hypothek||
|Versicherung|versicherung||
|Verwaltungsvertrag|verwvertrag||

<br>

#### Weitere Entitäten
**
|Entität|Entityname|Beschreibung|Dokumententypen|
|:-|:-|:-|:-|
|Aufgabe|aufgabe||
|Ausgabe (Kommunikationsassistent)|ausgabe||
