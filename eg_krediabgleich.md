# Automatischer Kreditoren-/ Personenabgleich

Die DMS Schnittstelle ermöglicht optional mit externen Kreditorenstammdaten/Personendaten zu arbeiten. Die Option beinhaltet folgende Fälle:
- neue Kreditoren werden automatisch erfasst
- bestehende Kreditorendaten werden aktualisiert
- Kreditorendaten werden automatisch gematched
 
## Aktivierung der Funktionalität
Wenn man mit der Funktion "Automatischer Kreditoren-/ Personenabgleich" arbeitet, werden immer alle obenstehenden Fälle aktiviert.
Die Option muss im Rimo R5 aktiviert werden. Dazu existiert ein Konfigurationseintrag:<br>

`INIT, DMS, 4, Kreditor autom. aktualisieren` *0 = deaktiviert (Standard), 1 = aktiviert*

Es werden mit dieser Funktionalität folgende Daten zu einem Kreditor automatisch abgeglichen: Kreditor, Person, Adresse, Kommunikation. Daten zur Rechnung und Zahlverbindung werden auch ohne diese Funktionalität automatisch ergänzt und abgeglichen.

## Identifikation eines Kreditors
Es gelten folgende Regeln beim Import:

1. Wenn [dmsechnung](https://github.com/wwimmo/rimor5-dms-schnittstelle/blob/main/_staging%20area/DMSRechnung.md#dbadmsrechnung).kredinr vorhanden ist, so erfolgt die Identifikation des Kreditors immer über diese ID
2. Wenn [dmsechnung](https://github.com/wwimmo/rimor5-dms-schnittstelle/blob/main/_staging%20area/DMSRechnung.md#dbadmsrechnung).extkredinr vorhanden ist und mit einer externen ID im Rimo R5 matched, wird der Kreditor darüber identifiziert
3. Wenn [dmsechnung](https://github.com/wwimmo/rimor5-dms-schnittstelle/blob/main/_staging%20area/DMSRechnung.md#dbadmsrechnung).extkredinr vorhanden ist und mit einer externen ID im Rimo R5 matched, wird ein neuer Kreditor erfasst
4. Wenn weder [dmsechnung](https://github.com/wwimmo/rimor5-dms-schnittstelle/blob/main/_staging%20area/DMSRechnung.md#dbadmsrechnung).kredinr noch extkredinr vorhanden sind, werden Kreditorenstammdaten und Informationen der Rechnung abgeglichen und so ein Kreditor identifiziert

Für die Identifikation eines Kreditors mit Regel 4 gelten folgende Bedingungen (entweder / oder in folgender Reihenfolge):
- i) dmsrechnung.unternehmensid <-> person.unternehmensid
- ii) dmsrechnung.regnrmwst <-> person.regnrmwst
- iii) dmsrechnung.nambezeichnung <-> person.nambezeichnung und dmsrechnung.strasse <-> adresse.strasse und dmsrechnung.plz <-> adresse.plz
- iiii) dmsrechnung.name <-> person.name und dmsrechnung.vorname <-> person.vorname  und dmsrechnung.strasse <-> adresse.strasse und dmsrechnung.plz <-> adresse.plz

Bei einer erfolgreichen Identifikation eines Kreditors, werden im Rimo R5 immer die Stammdaten der Person, Adresse oder Kommunikation gemäss den aktuellen Daten aus [dmsechnung](https://github.com/wwimmo/rimor5-dms-schnittstelle/blob/main/_staging%20area/DMSRechnung.md#dbadmsrechnung) aktualisiert.

## Neuerfassung eines Kreditors 
Wurde kein Kreditor identifiziert, so wird automatisch ein neuer Kreditor erfasst. Dabei sind folgende Daten zur [dmsechnung](https://github.com/wwimmo/rimor5-dms-schnittstelle/blob/main/_staging%20area/DMSRechnung.md#dbadmsrechnung) zwingend:
- vorname, name bei Einzelpersonen
- nambezeichnung bei juristischer Person
- strasse oder postfach
- plz
- ort

Wenn die Daten nicht komplett sind, erfolgt kein automatischer Import und eine Fehlermeldung wird ausgegeben.

## Externe Kreditorennummer
Im Rimo R5 Kreditorenstamm kann die externe Kreditorennummer hier gespeichert werden:
![image](https://user-images.githubusercontent.com/34299234/136810162-906ddc29-7b5e-4eeb-92aa-3ed10c4efd99.png)



