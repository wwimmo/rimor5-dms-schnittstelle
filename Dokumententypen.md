# Dokumententypen und Dossierstruktur

Jedes im E-Dossier Rimo R5 verlinkte oder abgelegte Dokument ist einem eindeutigen Dokumententyp zuzuweisen. 
Im DMS müssen zwingend die Dokumententypen gemäss Rimo R5 Struktur verwendet, 
oder aber die DMS eignen Dokumententypen auf die Rimo R5 Struktur gemappt werden. 
Im Rimo R5 ist kein Mapping von Dokumententypen möglich.<br><br>

Die Dokumententypen sind den möglichen Ablagentitäten zugeordnet. 
Die Zuordnung zu den Entitäten folgt aufgrund deren fachlichen verwendung - 
d.h. ein Dokument des Typs "Mietvertrag" kann nur zur Entität "mieter" zugewiesen werden.

## Dokumententypen
Die ID der Dokumententypen sind wie folgt aufgebaut:

|Nummernkreis|Beschreibung|Liste|
|:-|:-|:-|
|1-999|allgemeine Dokumententypen. Diese Dokumententypen sind auf allen Rimo R5 Datenbanken identisch.|[allgemeine Dokumententypen](/_dokumente/dokutypen.md#allgemeine-dokumententypen)|
|1000-9999|individuelle Dokumententypen. Diese können von individuell pro Kunde vorkommen.|[individuelle Dokumententypen](/_dokumente/dokutypen.md#individuelle-dokumententypen)|
|99999+|Rimo R5 Reports. In der Regel werden diese also mit Ablageprozess B) archiviert.|[Report Dokumententypen](/_dokumente/dokutypen.md#dokumententypen-der-reports-rimo-r5)|

## Dossierstruktur

Dokumententypen können nur zu ausgewählten Entitäten zugewiesen werden.

#### Hauptentitäten
*Diese Entitäten werden in den meisten Fällen für die Dokumentenablage verwendet. 
Wir empfehlen grundsätzlich nur mit diesen Ablagedossiers zu arbeiten. 
Wenn Sie eine detailliertere Ablagestruktur wünschen, können Sie die Dokumente auch zu den weiter unten aufgeführten Entitäten ablegen.*
|Entität|entityname|Beschreibung|
|-|-|-|
|[Liegenschaft](_dokumente/dossierstruktur.md#liegenschaft-lieg)|lieg|Dokumente zu einer Liegenschaft|
|[Objekt](_dokumente/dossierstruktur.md#objekt-objekt)|objekt|Dokumente zu einer Miet- / STWEG-Einheit|
|[Mieter](_dokumente/dossierstruktur.md#mieter-mieter)|mieter|Dokumente zu einem Mieter / STWEG Eigentümer|
|[Buchung (Hauptbuch)](_dokumente/dossierstruktur.md#buchung-hauptbuch-fibubuchung)|fibubuchung|Dokument zu einem Beleg/einer Buchung|
|[Fibujahr](_dokumente/dossierstruktur.mdfibujahr-fibujahr)|fibujahr1|Dokumente zu einer Buchhaltungsperiode/-abschluss|

#### Detailentitäten für Buchhaltungsdokumente
|Entität|entityname|Beschreibung|
|-|-|-|
|Abrechnung|abrechhknk||
|Buchung (Kreditoren)|kredibuchungdms||
|Buchung (Mieter)|mieterbew||
|Finanzbuchhaltung|fibu||


#### Entitäten mit Personenbezug
|Entität|entityname|Beschreibung|
|-|-|-|
|Person|person||
|Kreditor|kreditor||
|Hauswart|hauswart||
|Eigentümer|eigentuemer||
|Benutzer|produsers||

#### Entitäten zur detaillierten physischen Liegenschaftsstruktur
|Entität|entityname|Beschreibung|
|-|-|-|
|Gebäude|gebaeude||
|Haus|haus||
|Etage|etage||

#### Detailentitäten für Verträge
|Entität|entityname|Beschreibung|
|-|-|-|
|Hypothek|hypothek||
|Versicherung|versicherung||
|Verwaltungsvertrag|verwvertr||
|Gebäudeversicherung|gebaeudevers||

#### Weitere Entitäten
|Entität|entityname|Beschreibung|
|-|-|-|
|Aufgabe|aufgabe||
|Ausgabe](Kommunikationsassistent)|ausgabe||




