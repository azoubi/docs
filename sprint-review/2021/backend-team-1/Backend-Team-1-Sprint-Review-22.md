# Sprint 22 - Backend Team 1

Detlev, Nico, Tobias

---

# Agenda

- Mob Programming
- Storypoints 
- Erfassungsprozess
- Ergänzungsprozess
- Freigabeprozess
- Sonstiges / ZE-TV
- Work in progress

---

#  Mob Programming

- Fixing Workflow in Camunda

# Punkteverteilung

---

|                   | JIRAs  | Story Points |
| ----------------- | ------ | ------------ |
| Erfassung         | 0      | 0            |
| Ergänzung         | 4      | 10           |
| Freigabe          | 4      | 22           |
| Storno            | 0      | 0            |
| Sonstiges / ZE-TV | 2      | 15           |
|                   | **10** | **47**       |

---

# Erfassung

---

# Ergänzung

## Cut-Off-Prüfung bei NON-STP Geschäften (taco-855)
NON-STP Geschäfte sollen nicht geparkt werden, stattdessen soll ein Fehler geworfen werden:   
`Funktion für GV unzulässig. Cut-Off XXXX < Systemzeit`

---

## Buchungsdatum in der LDU Meldung (taco-836)
Sylvia hat mit Jörg Schimmel abgestimmt, das echte Buchungsdatum im Feld Buchungsdatum an LDU zu
übertragen. In Alt wurde bisher der AZV Geschäftstag übertragen.

---

## Übernahme der Standing Daten bei der Kontrahentenermittlung (taco-639)
- KT + Kontonummer oder IBAN
- Clearing System
- Adresszeile

---

## Geschäftsart Validator bei GA/1113 (taco-839)
Geschäftsart 1113 ist für Target Eingänge nicht zulässig.

---

# Freigabe

---

## Leistungsartenschlüssel bestimmen (taco-183)
Der LA_KEY wird in den nächsten Sprints für den Aufbau der Buchungssätze benötigt.
Die Funktion wurde als einfaches Util ohne Abhängigkeiten umgesetzt. 

---

## Freigabe beim Kunde/Konto Abgleich (taco-852)
- Bei Fehlern im Freigabeprozess soll das Geschäft im Status ZKKA stehen bleiben
- Freigabefehler sollen in der Maske Kunde/Konto Abgleich angezeigt werden
- Lösung: Zwischenstatus ZFRE wird nicht mehr gesetzt: `ZKKA --> ZRST`

---

## Konten ohne Abrechnung/Druckoutput (taco-251)
- Landesbank Parameter um eine weitere Kontenliste erweitert
- In 909 sind es nur die Konten: 9000480363, 9000900856

---

## Dynamischen Fixing im Währungsverfahren (taco-864)

- Neue Tabelle TIZDFIX für Vier-Augen-Prinzip angelegt
- Fixing Button um Aufruf der Zahlungseingang Fixing API erweitert
- Fixing kann beliebig oft neu freigegeben werden

---

## Erweiterung der API im Währungsverfahren (taco-845)
- Neuer Endpunkt `/add/api/fixing-date`
- Liefert das Datum vom letzten freigegebenen Fixing Event zurück

## FW-Disporeferenz auf 24 Zeichen kürzen (TACO-822)

- Die Disporeferenz war zu lang für die FWV-DB.
- Statt der GV-Nummer wird jetzt die Short-Id verwendet, sodass die Referenz jetzt aus 12 Zeichen
für die Short-Id und 12 Zeichen für Datum und Uhrzeit besteht.

---

# Storno

---

# Sonstiges / ZE-TV

---

## Short-Id und Trace-Id speichern (TACO-819, TACO-820)

- Bei Erfassung wird eine Short-Id generiert und es wird die aktuelle Trace-Id gespeichert. 
- Mit beiden Ids kann über das REST-API nach Zahlungseingängen gesucht werden.

## Umstellung auf Camunda Enterprise / Camunda-Cockpit (TACO-842)

- Es wird jetzt die Camunda-Enterprise-Version verwendet.
- Auf dem Testsystem steht jetzt das Camunda-Cockpit (ebenfalls in der Enterprise-Version) zur 
  Verfügung.
  
## Retry bei REST-Service-Aufrufen überall eingebaut (TACO-796)

- Bei allen REST-Service-Aufrufen im Zahlungseingang wird jetzt ein Retry bei Fehlern gemacht.
- Das Retry lässt sich über Spring-Properties pro Klasse und Methode konfigurieren.

## Service-übergreifendes Tracing (TACO-824)

- Alle Logeinträge erhalten jetzt eine serviceübergreifende Trace-Id, nach der später in Grafana
gesucht werden kann.

---

# Work in progress

---

## Camunda Fixing Workflow (taco-83)

### Erledigt

- BPMN Workflow wurde auf CallActivity umgestellt
- Fixing API bezüglich Style Guide überarbeitet
- Monitoring API um FFIX und ZFIX erweitert
- Unit Testing

### Offene Baustellen

- Fixingdatum aus Währungsverfahren abfragen
- Job-Priorisierung untersuchen und pilotieren
- Integration-Tests vervollständigen

---
