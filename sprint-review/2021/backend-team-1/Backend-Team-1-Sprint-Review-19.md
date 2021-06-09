# Sprint 19 - Backend Team 1

Detlev, Nico, Tobias

---

## Camunda

- Zwei intensive Workshops mit Frank Oehlschläger durchgeführt
- Ca. 22 Stunden Mob-Programming geleistet
- TACO-729 **spring-camunda** GitHub Projekt erstellt
  - Demo Workflow mit Blocking und Exception Handling erstellt und durchgespielt
  - CamundaService
  - AbstractJavaDelegate
  - AbstractCamundaTest
- **Tenant** Bean aus add-security vom `Request Scope` in den `Singleton Scope` migriert
- LoginClient für die Anmeldung von technischen Usern in add-security umgesetzt
- Freigabeprozess für Zahlungseingänge als BPMN modelliert (TACO-732)
- JavaDelegate Grundgerüste für die einzelnen Aktivitäten im Workflow erstellt

---

## Rückbau add-commons

- Neues base package: `de.nordlb.indzv` eingeführt
- Aufteilung in neue GitHub Projekte:
  - common (TACO-718)
  - spring-test (TACO-717)
  - spring-security (TACO-720)
  - spring-rest (TACO-719)
- add-zahlunsgeingang umgestellt auf das neue **spring-parent** (TACO-728)

---

## Caching TACO-757

- add-security benutzt für das SecurityToken den Default Cachemanager
  - Der Cache `baseoneLogin `muss von nutzenden Projekt konfiguriert werden
- add-zahlungseingang nutzt nur noch den Default Cachemanager
- Caching beim Unit Testing deaktiviert über die Annotation `@AutoConfigureCache`
  - EmbeddedSpringTest und ControllerSpringTest erweitert

---

## Erfassung

### Fehlerbehebung

- TACO-749 - Leerzeichen automatisch aus Eingabedaten entfernen.
  - Beispiel: Feld 50F mit `1/KALITA YULIYA ANATOLEVNA [Blank]`

---

## Ergänzung

---

## Freigabe
 - TACO-714 Umstellung Swiftausgang im Zahlungseingang auf Openapi Modelklassen
   - Bei der Vorbereitung der SWIFT-Ausgangsnachrichten werden die vom OpenAPI-Generator erzeugten Klassen verwendet.

 - TACO-733 FreigabeService durch die Camunda Engine ersetzen

 - TACO-750 AuditLog Überschriften bei Meldungen in Freigabe

---

## Storno

---

## Historie (TACO-541)
- Service für die Abfrage der Historie für Währungspflegeparameter erstellt
- Zahlungseingangs-API um die Historie erweitert
- PoC für die Verwendung der neuen Schnittstelle im Frontend erstellt
- Entwurf für Camunda-Prozess für Freigabe von Parametern im Vieraugenprinzip erstellt
