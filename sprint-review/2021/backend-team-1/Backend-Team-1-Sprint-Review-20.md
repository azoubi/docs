# Erfassung

- Swift Gebühren Betrag `0` zulassen (TACO-771)
- Optimierung der Prüfung auf Falschbelastung (TACO-763)
  - Die Prüfung soll zuschlagen wenn Feld 53 **oder** 54 aus der MT103 gefüllt ist

# Freigabe

## Diverse Beträge berechnen (TACO-723)

Am Anfang vom Freigabeprozess werden folgende Beträge berechnet:

**Persistent**
 - Betrag Soll / Haben
 - Kursgewinn bei Sparkassengeschäften   

**Transient** 
  - Betrag Soll / Haben in Euro
  - Gebühren in Währung und Euro

Besonders wichtig ist der `Betrag Haben` der in diversen weiteren Meldungen verwendet wird.

## Buchungstag ermitteln (TACO-508)
  - Der Buchungstag wird für die FW-Dispo Meldung und die Buchungssätze benötigt
  - Janes hat eine CSV Datei mit allen Feiertagen aus der Buchungsdomäne aufgebaut
  - Der FeiertageClient wurde um zwei Funktionen erweitert:
      - `boolean isBookingDay(LocalDate date)`
      - `LocalDate nexBookingDay(LocalDate startDate)`
  - Neue Klasse Buchungskalender für Zahlungseingang spezifische Logik
     - Bei Geschäftsart 1113 muss Valuta Haben speziell berücksichtigt werden  
---

## Freigabe im Fehlerbereich darf keine Fehler ausgeben (TACO-758)
- Bei STP-fähigen Geschäften wird im Anschluss die Ergänzung und Freigabe nach Ergänzung durchgeführt
- In beiden Schritten können Fehler in den fachlichen Prozessen auftreten
- Fehlermeldungen sollen in Warnung konvertiert werden
- Die betroffenen Geschäfte sollen NON-STP werden, aber ihren STP-Preis behalten

## Tracker Informationen an Swift geben (TACO-255)
- Im Zuge der Freigabe wird eine Tracker Information (MT199 Swift Nachricht) ausgegeben.
- Die Nachricht wird zunächst in einer Datenbank gespeichert und wird nicht abgeschickt.

## Automatische Freigabe von manuellen Geschäften (TACO-617)
- Für die Freigabe im 2-Augen-Prinzip nach manueller Ergänzung müssen 2 Voraussetzungen erfüllt sein:
  - Interner Betrag < 10.225,84 EUR
  - Erfassungsbediener <> Ergänzungsbediener

## Setzen der Kundennummer 0 bei der Konditionsermittlung für FIBU-Konten (TACO-812)
- Bei der Konditionsermittlung für FIBU-Konten muss die Kundenummer 0 gesetzt werden.

# Ergänzung

## Fehlerbehebung Valuta Validator (TACO-798)

- Feiertagskalender muss mit Währung Soll- und Haben aufgerufen werden.

## Prüfungen Gebührenkonto (TACO-201)

- Kontoanrufprüfung ohne Kontosperren
- Löschen von abhängigen Feldern wenn das Gebührenkonto durch den Anwender gelöscht wird
- Sicherstellen der Konsistenz von Kontonummer und der dazugehörigen Institutsnummer

## Aufbereitung für UMSATZ / Kontoauszug: Kundeninformationen Haben 1 und 2 (TACO-216)
- Im Rahmen der Leitwegsermittlung werden die Kundeninfomationen  ermittelt.

---

# Storno

## Stornoprozess als Camunda Workflow (TACO-786)
- Stornoworkflow in Cawemo hochgeladen
- Storno auch im Status `SRTS` und `ZRST` möglich
- Stornierte Geschäfte erhalten den Status `ENDE`
- Klärung nötig welche Info-Meldung generiert werden sollen

---

# Test

## Feiertagskalender in den Integrationstests verwenden (TACO-725)

Unsere CI-Build hat an Wochenenden und Feiertagen nicht funktioniert, da die Valuta nicht auf einen Werktag geschoben wurde.
- Bei der Vorgabe von Tagen `+2d` werden jetzt Werktage auf die Datumsfelder addiert.
- Bei allen anderen Einheiten, z.B. Monaten `+1m` wird erst das Datum ausgerechnet und dann der nächste Werktag ermittelt.

## Fail-Fast im IbanCheckService (TACO-755)
- Fehler beim Laden der BBAN Strukturen wurden nicht an das Frontend weitergegeben und nur geloggt
- Wenn keine BBAN Strukturen aus der Base/ONE Komponente geladen werden können funktioniert die IBAN Prüfung nicht
- Wenn die IBAN Prüfung nicht funktioniert wirkt sich das negativ auf die Module der STP Verarbeitung aus
- Lösung: Im IbanCheckService wird geprüft ob BBAN Strukturen vorhanden und ggfs. eine Exception geworfen

---

# Sonstiges

## CheckStyle Findings bereinigen (TACO-761)
- Nach der Umstellung auf **spring-parent** in Sprint 20 sind ca. 80 Findings dazugekommen
- MisingJavaDocType bei Klassen oder Interfaces

## Info/Error Meldungen erweitern (TACO-683)
- Ausgabe vom Modul das die Meldung erzeugt hat
- Beispiel: Kein Soll Kontrahent oder Korrespondent ermittelt! (KontrahentenErfassungsermittlung)

## Min-Betrag in Pflege Währung / Weiterleitung ohne Konvertierung (TACO-797)
- Der Min-Betrag darf 0 sein

## Systeminstitut im Tenant dynamisch ermitteln (TACO-756)
- Property Konfiguration für das Systeminstitut entfällt
- Systeminstitut wird über eine Mapping Tabelle aus dem Institut abgeleitet
- Keine individuellen Kubernetes Pods für NLB und BLB nötig

## Zeitzone UTC+0 in der Azure Cloud umrechnen (TACO-795)
- Wir benötigen die Systemzeit in der Zeitzone `Europe/Berlin`
- Systemzeit wird zentral bereitgestellt: `ZonedDateTime DateUtil.now()`
- Time Warp Feature mit umgesetzt:

```Java
System.setProperty(DateUtil.TIME_WARP_DATE, "2021-04-13");
System.setProperty(DateUtil.TIME_WARP_TIME, "10:00");
```
