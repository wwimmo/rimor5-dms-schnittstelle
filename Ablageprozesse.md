# Übersicht

Es gibt folgende Ablageprozesse, wie ein Dokument über die DMS Schnittstelle archiviert werden kann:

![Ablageprozesse](https://github.com/wwimmo/rimor5-dms-schnittstelle/blob/main/_grafiken/ablageprozesse.png)

### I) Das Dokument wird im DMS archiviert.
1. Das DMS transferiert die Dokumentendaten (ohne Datei) an Rimo R5.
2. Rimo R5 verlinkt das Dokument im E-Dossier.

*Bsp:	Alle Dokumente, welche von Papier gescannt werden: Kreditorenrechnung/gutschrift, E-Rechnung*

### II) Das Dokument wird im Rimo R5 E-Dossier abgelegt und in der Dateiablage gespeichert
1. Das DMS holt sich das Dokument aus dem E-Dossier (Metadaten) bzw. aus der Dateiablage (Datei) und 
2. archiviert sie im DMS. Das DMS meldet die Archivierung an Rimo R5 zurück.
3. Das Dokument ist entweder nur noch im DMS oder in der Dateiablage Rimo R5 und dem DMS vorhanden.

*Bsp: 	Buchungsbeleg zu manueller Buchung, welcher im DMS gespeichert werden soll: Mahnbriefe, welche aus dem Mahnlauf Rimo R5 generiert wurden und ebenfalls im DMS gespeichert werden sollen*		werden sollen.


# Ablageprozess I
Dokumente vom DMS werden an Rimo R5 transferiert und im E-Dossier abgelegt.

![Ablageprozess I](https://github.com/wwimmo/rimor5-dms-schnittstelle/blob/main/_grafiken/ablageprozessI.png)

1. Ein Dokument wird im DMS archiviert (Scan, Import, usw.). Im DMS wird je nachdem das Dokument mit Daten angereichert. Das DMS verwendet hierfür u.a. den Datenzugriff auf die Rimo R5 Stammdaten. Zum Zeitpunkt X wird das Dokument bzw. die Daten des Dokuments an Rimo R5 übermittelt in die Staging Area.
2. Im Rimo R5 verarbeitet ein regelmässiger Job die neuen Dokumente in der Staging Area. Je nach Dokumenten-typ legt Rimo R5 neue Datensätze (z.B. Kreditorenrechnung mit Buchung) an oder verlinkt das Dokument mit bestehenden Entitäten (z.B. Mietervertrag zu Mieter). Das Dokument aus dem DMS ist nun im E-Dossier ver-linkt.


# Ablageprozess II
Dokumente werden im E-Dossier in der Dateiablage Rimo R5 abgelegt und vom DMS abgeholt und archiviert.

![Ablageprozess I](https://github.com/wwimmo/rimor5-dms-schnittstelle/blob/main/_grafiken/ablageprozessII.png)

1. Das DMS liest in einem regelmässigen Job die View vDMSExportdokument aus. In dieser View sind alle Doku-mente vorhanden, welche noch nicht im DMS gespeichert und im Rimo remapped wurden. Die View enthält ebenfalls die Information, an welchem Pfad/Folder die Datei zum Dokument gespeichert ist. Das DMS liest die Metadaten der View und holt sich die zugehörigen Dateien ab und speichert die Dokument in seiner Daten-bank. Das DMS meldet an Rimo R5 zurück, welche DMSNR für das Dokument im DMS vergeben wurde.
2. Rimo R5 verarbeitet in einem regelmässigen Job die offenen Remapping Einträge. Die Dokumente im E-Dossier werden neu mit dem DMS Eintrag verlinkt. Je nach Einstellung werden ebenfalls die Dateien in der Dateiablage Rimo R5 gelöscht.
