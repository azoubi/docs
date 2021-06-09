# Sprint Review für Sprint #22
## Backend Team "Satelliten"

---

# Jira-Tickets

| ID	   | Title  	                            |
|:-	       |:-	                                    |
| TACO-567 | API für Buchungsgenerierungsserive |
| TACO-734 | Modellierung Datenhaltung für Eingangsdaten |

---

## TACO-567
### API für Buchungsgenerierungsserive

Die API wurde gemäß der Vorgaben im Ticket als YAML-Datei aufgebaut und im OpenAPI-Repository
"account-transactions" bereitgestellt. Die entwickelte Spezifikation wurde vom OpenAPI-Team einem
Review unterzogen und im Projekt "add-buchungsservice" eingebunden.

Offener Punkt: Durch die bisher noch nicht verfügbare Anbindung an das Artifactory ist der
Buchungsservice aktuell nur lokal bzw. mit Github-Packages baubar. Sobald die entsprechende Action
vorhanden ist, wird dies nachgezogen (vermutlich KW22).

---

## TACO-734
### Modellierung Datenhaltung für Eingangsdaten

- Das interne Datenmodell (Entity-model) konzipieren und modellieren. 
- JPA-Annotationen zum Modell hinzufügen und mit der Liquibase-Generierung testen.
- Internes Datenmodell auf deutsch umbenannt.
- JUnit-Tests anpassen und erweitern.

---

## TACO-737
### Implementierung Statusprüfung eingehende Nachricht

Bei bereit vorhandener UUID oder ID,wurde die Nachricht bereits empfangen. Es ging in diesem Ticket zu prüfen, 
in welchem Status die voprherigen Verarbeitung abgeschlossen wurde.

Sollte es keinen Fehler gegeben haben, ist die ursprüngliche Nachricht inklusive Referenz-ID an den Aufrufer zurückzugeben.

Wenn es Fehler gab, ist einen Fehlermeldung zu erzeugen und ein BPMN-Error zu werfen.