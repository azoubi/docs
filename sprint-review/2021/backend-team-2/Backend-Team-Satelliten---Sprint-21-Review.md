# Sprint Review für Sprint #21
## Backend Team "Satelliten"

---

# Agenda

1. Vorstellung umgesetzter Jira-Tickets
2. Fragen

---

# Jira-Tickets

| ID	   | Title  	                            |
|:-	       |:-	                                    |
| TACO-523 | SWIFT-Ausgang Erstellung pacs.008 |
| TACO-527 | SWIFT-Ausgang Erstellung MX-Header |
| TACO-735 | Implementierung MappingService |
| TACO-779 | Umstellung add-swift-eingang auf spring-parent |
| TACO-811 | CNY nach CNH bei SWIFT-Eingängen konvertieren |
| TACO-853 | Implementierung dezidierter Delegates  |

---

## TACO-523
### SWIFT-Ausgang Erstellung pacs.008

Es wird mittels der Prowide SWIFT-Bibliothek auf Basis der übergebenen Daten eine pacs.008 Nachricht als Objekt erzeugt. Dieses kann künftig für die
Transformation in eine MT103-Nachricht genutzt werden. Die erzeugten Objekte werden in weiteren Ausbaustufen verwendet, um via MQ die Nachrichten an
die SWIFT-Box abzugeben.

In folgenden Schritten sind fachliche Testcases zu erarbeiten, um die fachlich korrekte Erstellung der Nachrichten zu verifizieren. Weiterhin gibt es
noch eine Anforderung die Mappingregel im Bereich der ClearingCodes zu erweitern. Entsprechende Folgetickets werden erstellt.

---

## TACO-527
### SWIFT-Ausgang Erstellung MX-Header

Im Zuge der Implementierung von TACO-523 wurde ein Mapping zur Erstellung des XML-Headers für die pacs.008 Nachricht realisiert.

---

## TACO-735
### Implementierung MappingService

Gemäß des modellierten Prozesses ist ein Mapping-Service implementiert worden. Dieser Service wandelt Eingangsdaten der unterschiedichen Nachrichtentypen auf die abbildenden Entityklassen um. Dazu werden separate Mapperklassen über eine MapperFactory bereitgestellt, abhängig dazu um welchen Typ es sich handelt (Kundenzahlung, Coverzahlung, etc.).

---

## TACO-779
### Umstellung add-swift-eingang auf spring-parent

Das Projekt "add-swift-eingang" wurde auf "spring-parent" umgestellt und die packages-Struktur auf "indzv" angepasst. Im Rahmen der Umstellung wurden
diverse Funktionlitäten ergänzt, welche vorher in der nicht mehr verwendeten Library "add-common" enthalten waren.

---

## TACO-811
### CNY nach CNH bei SWIFT-Eingängen konvertieren

Bei der Eingangsverarbeitung von SWIFT-Eingängen wird künftig statt des ISO-Währungscodes "CNY" der Code "CNH" verwendet. Dies betrifft die
Felder "waehrung" und "waehrungUrsprung".

---

## TACO-853 
### Implementierung dezidierter Delegates

In der ursprünglichen Umsetzung des Swiftausgang-Prozesses waren Tasks aus dem BPMN-Modell als Service-Klassen implementiert, welche von AbstractJavaDelegate abgeleitet wurden. Um das Prozessmodel und die darunter liegende Businesslogik besser testen zu können, wurde eine 
Aufteilung vorgenommen. Separate Delegate-Klassen wurden implementiert, welche die benötigten Service-Klassen nun injizieren.

---