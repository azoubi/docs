# Sprint 21 - Backend Team 1

Detlev, Nico, Tobias

---

# Erfassung
## Text Leitwegsermittlung (TACO-843)
- Bei der manuellen Ergänzung wurde dem User bei der Leitwegermittlung nicht die korrekten Daten angezeigt. Wenn die Leitwegermittlung  ein Eingangsmerkmal findet muss es 5.17 und Eingangsmerkmale heißen, stat 4.17

## fehlender Text Leitwegsermittlung (TACO-849)
-  Bei den Hinweismeldungen aus der Leitwegsermittlung fehlte der Hinweistext für das Zwischenkonto.

---

# Ergänzung

---

## Fehlerbehebung  Ergänzung aus Bereich (TACO-814)
- Update mit dem Query Parameter `giveMeTheNext` war unvollständig umgesetzt

---

## Fehlerbehebung Prüfung auf Falschbelastung (TACO-840)
- darf nicht bei Target Eingängen aufgerufen werden
- ein gelöschtes Soll-Konto darf bei der Ergänzung nicht erneut ermittelt werden

## Zahlungseingang zur Ergänzung nach STP/NONSTP (TACO-851)
- In dem Bereich für die manuelle Ergänzung dürfen mir nur die Eingänge angezeigt werden. die nicht in der STP Verarbeitung stehen. Sondern nur die Eingänge, die entweder manuell erfasst wurden oder STP/N erhalten haben.
- API um STP-Merkmal erweiter
- Filtern der Sucheregebnisse um das STP-Merkmal ergänzt

---

# Freigabe

---

## Fehlerbehebung Freigabe aus Bereich (TACO-814)
- Approve mit dem Query Parameter `giveMeTheNext` war unvollständig umgesetzt

---

## Erweiterung GebuehrenanforderungService (TACO-712)
- Ein DELETE und POST mit den MT191 Daten wird jetzt an die BONE Komponente gesendet

---

## Aufruf der FWV Dispo API im Camunda Workflow
- Health Check verfügbar
- Open API Spec importiert
- Http 409 bei doppelter Disporeferenz wird nicht als Fehler angesehen

---

# Storno

---

## Erweiterung GebuehrenanforderungService (TACO-712)
- Ein DELETE wird jetzt beim Storno an die BONE Komponente gesendet

--- 

## Info Meldung für Swift-Ausgänge (TACO-813)
- Im Stornoprozess werden keine Swift-Ausgänge aufgebaut.
- Allerdings besteht die Anforderung eine INFO Meldung für den Anwender aufzubauen.

---

## Aufruf der FWV Dispo API im Camunda Workflow
- Http 409 bei doppelter Disporeferenz wird nicht als Fehler angesehen

---

# Sonstiges / ZE-TV

---

## Camunda Timer zum Entparken von geparkten Cut-Off Zahlungen (TACO-85)
- Geschäfte werdenam nächsten Werktag am Anfang der AZV Service Zeit entparkt
- Entparkte Geschäfte werden maschinell in die Ergänzung geworfen

---

## Logging von sensiblen Informationen verhindern (TACO-754)
- Im ERROR Logging sollen keine Geschäftsdaten ausgegeben werden
- Vorgezogene Konditionierung
- RestControllerLoggingAspect
- ApplicationExceptionHandler

---

## Zurücksetzen der GV-Nummer (TACO-589)
- Die Sequence der Laufenden Nummer wird durch Camunda zurückgesetzt
- Der Job wird um Mitternacht getriggert

--- 

## Spring Camunda 1.2.0 released
- Update to spring-parent version 1.0.2
- Update to spring-security 1.2.0
- Support for camunda-bpm-junit5
- Support for Start Message Events
- More Assertions
- New Twitter Demo mit Message Start Event und DMN Business Rule

---

## Camunda Testing
- AbstractCamundaTest wurde entfernt
- AbstractCamundaProcessEngineTest für schnellere Tests mit dem Camunda Mock Container.
- AbstractCamundaSpringBootTest für Tests mit dem loC Spring Container.

---

## More Testing
- StartMessageBuilder startMessageBuilder()
- StartProcessBuilder startProcessBuilder() 
- Mit `startAfterActivityId` nur bestimmte Teile des Workflows testen

---

## Camunda Assertions

- assertThatProcessIsStarted(processInstance)
- assertThatProcessIsWaitingAt(processInstance,activityIds)
- assertThatProcessIsEnded(processInstance)
- assertThatProcessIsActive(processInstance)
- assertThatProcessHasPassed(processInstance,activityIds)
- assertThatProcessHasPassedInOrder(processInstance,activityIds)
- assertThatProcessHasNotPassed(processInstance,activityIds)
