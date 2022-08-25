# Rimo R5 DMS Schnittstelle
Offene DMS Schnittstelle für das Immobilien-ERP Rimo R5

Dieses Dokument richtet sich an DMS Hersteller und Implementationspartner. Es enthält die Dokumentation über den Aufbau und Inhalt der universellen DMS Schnittstelle Rimo R5. Das Dokument dient als Implementationshilfe und Nachschlagewerk für DMS Hersteller und Implementationspartner.

## Rimo R5 Version
[5.3.0 (Vorschau auf zukünftige Rimo Version](https://github.com/wwimmo/rimor5-dms-schnittstelle/tree/5.3.0)<br>

[5.2.6/5.2.7 (aktuelle Rimo Version)](https://github.com/wwimmo/rimor5-dms-schnittstelle/tree/main)<br>


*History:<br>*
*[5.2](https://github.com/wwimmo/rimor5-dms-schnittstelle/tree/5.2)<br>*
*[5.1](https://github.com/wwimmo/rimor5-dms-schnittstelle/tree/5.1)<br>*
*[5.0](https://github.com/wwimmo/rimor5-dms-schnittstelle/tree/5.0)<br>*

## E-Dossier
Als «E-Dossier» wird im Rimo R5 sämtliche Funktionalität im Zusammenhang mit Dokumenten verstanden.

[E-Dossier Konzept](E-Dossier.md)


## Ablageprozesse der DMS Schnittstelle
Es gibt folgende Ablageprozesse, wie ein Dokument über die DMS Schnittstelle archiviert werden kann:<br>
I) DMS --> E-Dossier<br>
II) E-Dossier --> DMS

[Ablageprozesse](Ablageprozesse.md)

## Dokumentenaufruf Rimo R5
Im Rimo R5 kann ein Dokument via URL aufgerufen werden.
Dazu wird eine **Basis-URL** und ein Parameter für die **eindeutige Dokumentenidentifiaktion** verwendet.

Beispiel (Docuware)<br>
[https://DMSsrv04/jsaklsfjdlsfas-dfsjsijop23om&DocID=**12345-45678-abcde-fghij**]()

## Datenbank Zugriff für DMS Systeme
Der Datenbankzugriff kann via ODBC erfolgen. Je nach Datenbank Rimo R5 müssen die entsprechenden ODBC Treiber verwendet werden:
- SAP SQL Anywhere 17,		17.0.9.4913

Der Benutzer DMS hat auf der Datenbank Rimo R5 folgende Rechte: 

- Schreibrechte auf einige Tabellen mit Präfix: "DMS" (siehe [DMS Schema](DMS%20Schema.md)) 
- Leserechte auf Views mit Präfix: "vDMS"

Eine detaillierte Dokumentation der Tabellen und Views ist im Abschnitt [DMS Schema](DMS%20Schema.md) dokumentiert.

## Dokumententypen
Die DMS Schnittstelle verwendet einen definierten Katalog von Dokumententypen. Für eine möglichst automatisierte Verarbeitung der Dokumente ist die Angabe des Dokumententyps zu einem Dokument zwingend. Die Liste der möglichen Dokumententypen wird jeweils mit jeder Schnittstellenversion durch W&W veröffentlicht.

[Dokumententypen und Dossierstruktur](Dokumententypen.md)

## DMS Schema
Dem User DMS stehen in der Rimo R5 Datenbank Tabellen mit Schreibrechten sowie Views mit Leserechten zur Verfügung.

[DMS Schema](DMS%20Schema.md)

## Anwendungsbeispiele

[Automatischer Kreditoren-/ Personenabgleich](eg_krediabgleich.md)

