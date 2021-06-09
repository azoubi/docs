# Sprint 23 - Backend Team 1

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

- Fixing Workflow in Camunda (taco-841)
   - Fixingdatum abfragen
   - Freigabefehler im AuditLog speichern
   - Job Priorisierung und Rückmeldung an WOFL
   - Massentest

# Punkteverteilung

---

|                   | JIRAs  | Story Points |
| ----------------- | ------ | ------------ |
| Erfassung         | 0      | 0            |
| Ergänzung         | 0      | 0            |
| Freigabe          | 0      | 0            |
| Storno            | 0      | 0            |
| Sonstiges / ZE-TV | 0      | 0            |
|                   | **0**  | **0**        |

---

# Ergänzung

---

## Cut-Off-Prüfung bei NON-STP Geschäften (taco-889)

- Cut-Off-Prüfung nicht ausführen wenn die Leitwegermittlung STP/N ermittelt hat

---

## LDU Meldung nur nach erfolgreicher Ergänzung durchführen (taco-911)
- Die LDU Verarbeitung benötigt die ermittelte Haben-Seite im Geschäft
- Meldung nur für Geschäfte im Status ZFRE oder ZKKA durchführen

---

## Fehlerhandling beim maschinellen Entparken (taco-912)
- Bei Fehlern in der maschinellen Ergänzung muss wie bei Freigabefehlern reagiert werden
- Geschäft wird NON-STP und die Fehlermeldung wird im AuditLog abgespeichert

---

# Freigabe

---

## AuditLog im Fehlerfall erweitern (taco-904)
- Neben den Fehlermeldungen sollen auch die Info-Meldungen aus der ZRST Verarbeitung gespeichert werden

---

## Fix Gebührenanforderung (taco-905)
- Im JSON Request Objekt hat die GV-Nummer gefehlt

---

## Erweiterung der Valuta-Haben Ermittlung (taco-906)
- Valuta-Haben darf am Ende der Ermittlung nicht vor der Valuta-Soll liegen
- Valuta Haben wird in dem Fall auf Valuta-Soll verschoben

---

# Sonstiges / ZE-TV

---

## AuditLog Bediener im Freigabe Workflow (taco-823)

- Header Parameter `X-On-Behalf-Of` mit dem UserInfo aus Camunda aufbauen

---

# Work in progress

---

