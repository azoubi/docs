## Erfassung

- TACO-675 Kompetenzbereich ermittelt (Target < 500k, Target > 500k, AZV)

---

## Ergänzung
- TACO-635 fremde Spesen Landesbank dürfen nur bei Spesenverrechnung OUR erfasst werden

### Fehlerbehebung

- TACO-692 AuditLog Eintrag für das Protokoll der Leitwegeermittlung
- TACO-676 Erkennung von Target Ausgängen in der Kontrahenten Ermittlung
- TACO-695 Korrekturen beim Vorbereiten von Swift-Ausgängen für die Felder 52 und 53
  - MARKDEFF wurde in den Landesbankparametern angelegt

---

## Freigabe

- Überführung nach Camunda wurde diskutiert und ist in der Abstimmung
- TACO-277 FW-Dispo Meldung vorbereiten
- TACO-284 OSPlus Dispo Meldung vorbereiten
- TACO-650 Client Implementierung der Rest-API für die ermittelten Konditionen
- TACO-705 Runden von Beträgen und Kursen auf 2 und 7 Nachkommastellen
- TACO-703 Konditionierung: Repairgründe 57A und SPV implementiert

---

## Storno

TACO-73 Im StornoService wurden die nötigen Service aufrufe aufgenommen
die zur Kompensation bereits erfolgter Meldungen aufgerufen werden müssen.
Neue Status SRST und ENDE eingeführt.

**Implementiert:**

- OSP-Dispo Storno Meldung (TACO-284)
- ZKG-Meldung bei Storno (TACO-480)

**ToDo:**
- Storno Buchungen aufbauen (TACO-58) 
- FW-Dispo Storno Meldung (TACO-279) 
- LDU Storno Meldung (TACO-711)
- MT191 Gebührenanforderung löschen (TACO-712)

Das Senden der Daten wurde noch nicht angegangen.

---

## Entparken

- TACO-654 Kein Rollback bei Fehler 
- TACO-704 Beim manuellen Entparken aus PSTP wird das Feld *cutoffPruefung* nicht mehr gesetzt und *STP* auf *false* gesetzt.

## Datenmodell

- TACO-682 Die Kontonummern im Zahlungseingang wurden von String auf Integer geändert

--- 

## Refactoring add-common

Abgestimmt für Umsetzung in Sprint 19

### Neue Package Struktur: 
- de.nordlb.indzv.commons
- de.nordlb.indzv.add
- de.nordlb.indzv.gc

### Neue Repos
- **common** mit allgemeinen JAVA SE Klassen
- Parent Repos mit den CI Profilen
  - java-parent
  - spring-parent
- sprint-test
- sprint-security
- spring-rest

---

## Microservice Pattern

### Sprint 19 
- Verwendung vom Retry Pattern wird vom DevOps konzipiert
  - Einbau in add-zahlungseingang nach dem Rafactoring von add-common
- Service Discovery wird zentral vom DevOps Teams für alle MS konzipiert

### Sprint 20 / Analyse Vorbereitung weiterer Pattern
- CircuitBreaker
- TimeLimiter
- usw.

---

## Test

- TACO-586 Testfall Datenbank in Microsoft Access aufgebaut
  - CTB0705_TaCo\Hauptdatei\Access-DB aktuell
  - Access Anleitung für Entwickler Notebooks steht im Wiki
- 15 Testfälle aufgebaut
- Messpunkte:
  - Diverse GV-Daten inkl. Gebühren
  - MT191
  - Swift Ausgänge und S-VIA