# rimor5-dms-schnittstelle
Offene DMS Schnittstelle für das Immobilien-ERP Rimo R5

Dieses Dokument richtet sich an DMS Hersteller und Implementationspartner. Es enthält die Dokumentation über den Aufbau und Inhalt der universellen DMS Schnittstelle Rimo R5. Das Dokument dient als Implementationshilfe und Nachschlagewerk für DMS Hersteller und Implementationspartner.

## Rimo R5 Version

[Rimo R5 Version 5.2 [dev]](https://github.com/wwimmo/rimor5-dms-schnittstelle/tree/main)

## E-Dossier
Als «E-Dossier» wird im Rimo R5 sämtliche Funktionalität im Zusammenhang mit Dokumenten verstanden.

[E-Dossier Konzept](https://github.com/wwimmo/rimor5-dms-schnittstelle/blob/main/E-Dossier.md)


## Ablageprozesse der DMS Schnittstelle
Es gibt folgende Ablageprozesse, wie ein Dokument über die DMS Schnittstelle archiviert werden kann:<br>
I) DMS --> E-Dossier<br>
II) E-Dossier --> DMS

[Ablageprozesse](https://github.com/wwimmo/rimor5-dms-schnittstelle/blob/main/Ablageprozesse.md)

## Dokumentenaufruf Rimo R5
Im Rimo R5 kann ein Dokument via URL aufgerufen werden.
Dazu wird eine **Basis-URL** und ein Parameter für die **eindeutige Dokumentenidentifiaktion** verwendet.

Beispiel<br>
[https://DMSsrv04/dokumentenspeicher/jsaklsfjdlsfas-dfsjsijop23om&p=v/DMSnr=**12345-45678-abcde-fghij**]()

## Datenbank Zugriff für DMS Systeme
Der Datenbankzugriff kann via ODBC erfolgen. Je nach Datenbank Rimo R5 müssen die entsprechenden ODBC Treiber verwendet werden:
- SAP SQL Anywhere 17,		17.0.7.3382

Dieser Benutzer hat auf der Datenbank Rimo R5 folgende Rechte: 

- Schreibrechte auf Tabellen mit Präfix: "DMS"
- Leserechte auf Views mit Präfix: "vDMS"

Eine detaillierte Dokumentation der Tabellen und Views ist im Abschnitt [DMS Schema](https://github.com/wwimmo/rimor5-dms-schnittstelle/blob/main/DMS%20Schema.md) dokumentiert.

## Dokumententypen
Die DMS Schnittstelle verwendet einen definierten Katalog von Dokumententypen. Für eine möglichst automatisierte Verarbeitung der Dokumente ist die Angabe des Dokumententyps zu einem Dokument zwingend. Die Liste der möglichen Dokumententypen wird jeweils mit jeder Schnittstellenversion durch W&W veröffentlicht.

[DMS Dokutypen.xlsx](https://github.com/wwimmo/rimor5-dms-schnittstelle/blob/main/_dokumente/DMS%20Dokutypen.xlsx)

## DMS Schema
Dem User DMS stehen in der Rimo R5 Datenbank Tabellen mit Schreibrechten sowie Views mit Leserechten zur Verfügung.

[DMS Schema](https://github.com/wwimmo/rimor5-dms-schnittstelle/blob/main/DMS%20Schema.md)

## Anwendungsbeispiele
t.b.d

