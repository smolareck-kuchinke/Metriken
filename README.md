# Metriken

Für diese Aufgabe habe ich erneut mein Projekt SpieltagPLUS verwendet, das bereits in den vorherigen Einsendeaufgaben zum Einsatz kam. Dadurch konnten die Metrik-Werkzeuge direkt auf dem bestehenden Java-/Maven-Projekt angewendet und die Ergebnisse nachvollziehbar ausgewertet werden.

Verwendet: Checkstyle, PMD und SpotBug

---

# 1. Checkstyle

## Beschreibung

Checkstyle überprüft Java-Quellcode anhand von definierten Programmierregeln. Dabei werden z.B. Verstöße gegen Namenskonventionen, fehlende JavaDoc-Kommentare oder Formatierungsprobleme erkannt.

## Durchführung

Die Analyse wurde mit Maven durchgeführt:

```bash
mvn checkstyle:checkstyle
```

Die Auswertung verlief erfolgreich.

### Screenshot

![Checkstyle](images/checkstyle_report.png)

## Ergebnis

Checkstyle hat verschiedene Hinweise ausgegeben, unter anderem:

- fehlende JavaDoc-Kommentare
- fehlende `final`-Deklarationen
- Tabulatoren im Quellcode
- fehlende package-info.java

Es wurden keine Compilerfehler gefunden. Hinweise dienen der Verbesserung der Codequalität.

---

# 2. PMD

## Beschreibung

PMD analysiert den Quellcode auf typische Qualitätsprobleme. Dazu gehören unter anderem unnötig komplizierter Code, schlechte Programmierpraktiken oder mögliche Wartungsprobleme.

## Durchführung

Die Analyse wurde mit folgendem Maven-Befehl gestartet:

```bash
mvn pmd:pmd
```

Die Ausführung war erfolgreich abgeschlossen.

### Screenshot

![PMD](images/pmd_report.png)

## Ergebnis

PMD hat einen Analysebericht (`target/pmd.xml`) erstellt.

![PMD](images/pmd_xml.png)

Der Bericht enthält keine Beanstandungen, Analysee hat keine Verstöße festgestellt.

---

# 3. Spotbugs

## Beschreibung

SpotBugs analysiert Java-Programme auf mögliche Fehler und Bug-Muster. Im Gegensatz zu Checkstyle liegt der Schwerpunkt nicht auf dem Programmierstil, sondern auf potenziellen Laufzeitfehlern und problematischen Konstruktionen im Quellcode.

## Durchführung

Die Analyse wurde wieder mit Maven durchgeführt:

```bash
mvn spotbugs:spotbugs
```

Die Ausführung lief erfolgreich.

### Screenshot

![SpotBugs](spotbugs_report.png)

## Ergebnis

SpotBugs hat einen Analysebericht (`target/spotbugsXml.xml`) erstellt.

Insgesamt wurden fünf Klassen analysiert. Dabei wurden keine potenziellen Fehler oder Bug-Muster erkannt (`total_bugs="0"`).

### Analysebericht

![SpotBugs-Bericht](spotbugs_xml.png)



# Fazit

Drei Werkzeuge eingesetzt: Checkstyle, PMD und SpotBugs.

Checkstyle identifizierte mehrere Verstöße gegen Programmier- und Stilrichtlinien, beispielsweise fehlende JavaDoc-Kommentare, fehlende `final`-Deklarationen sowie kleinere Formatierungsprobleme.

PMD erzeugte erfolgreich einen Analysebericht, erkannte in diesem Projekt jedoch keine Beanstandungen.

Auch SpotBugs analysierte den Quellcode erfolgreich und untersuchte insgesamt fünf Klassen. Dabei wurden keine potenziellen Fehler oder Bug-Muster gefunden.

Die drei Werkzeuge ergänzen sich sinnvoll, da sie unterschiedliche Aspekte der Softwarequalität untersuchen. Während Checkstyle den Fokus auf Programmierstil und Konventionen legt, analysieren PMD und SpotBugs den Quellcode auf mögliche Qualitätsprobleme und Fehler.
