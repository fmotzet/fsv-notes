# FSV Vorlesung

## Vorlesung 1

### Motivation  

+ Anforderungen erfüllen
+ Fehler vermeiden
+ Testen, Modelierung, Simulationen
+ Beweisen das Systeme sich verhalten wie man geplant hat
+ Man will möglichst verständliche und präzise Abstarktion

### Spezifikation (des Sollverhaltens, z.B.)

+ keine Abstürze
+ korrekte Ein-/Ausgabe
+ zeitliches Verhalten

### Testen, Verfikation

+ automatisierte Überprüfung
  + des Quellcodes  
  + eines abstraken Modells  
bezgl. der Spezifikation

### Modelierung

+ abstrakte Problembeschreibung
+ herausgreifen wesentlicher Aspekte

### Formal: mathematische Techniken

+ eindeutig und präzise
+ theoretisches begründetes Vertrauen in die Analyse

### Spezifikation

+ Anforderung != Spezifikation
  + Helligkeit des Displays bei Sonne erhöhen
+ Spezifikationen: beschreibt Systemschnittstelle/-verhalten
  + Beleuchtungsstärke gemäß Lichtsensor anpassen
  + Funktion abs gibt ein positives Ergebnis zurück

### Automatisierte Programmanalyse

+ System(Modell, Programm)
+ Spezifikation/Eigenschaft

### Testen vs Verifikation

+ Testen: beispielhaftes ausprobieren
+ Verifikaion: vollständige überprüfung oder Beweise

+ ####  Herausforderungen von beiden Varianten

  + große, komplexe Systeme
  + zu viele mögliche Zustände: Testen reicht nicht
  + Unendlicher Zustandsraum: Beides notwendig da schwierig zu automatisieren (Halteproblem/Rice's Theorem)

+ Verifikation in Praxis trozdem oft seh gut:
  + durch geeignete Analyse- und Beweistechnicken(Datenfluss, Model-Checking, Abstract Interpretation, SMT)
  + durch Abstraktion des Problems & Modelierung
  
### Kriterien für gute Modelierung

+ Führe Details schrittweise ein (Abstrakte und verfeinerte Modelle)
+ Betrachte Probleme auf der richtigen Abstraktionsebene (nicht zu wenig/zu viele Details)

## Vorlesung 2

### Testen

+ Dydnamische überprüfung des Systems
+ Kann nur damit Feheler finden nicht aber deren Abwesenheit beweisen
+ Vorteil: Tatsächliches System getestet, schafft Vertrauen ins System
+ z.B. Mathematische zahlen unterscheiden sich von zahlen die ein Computer nutzt
+ Performance probleme leichter zu betraachten
+ leicht zu schreiben und auszuführen
+ Hauptqualitätssicherung in der Praxis
+ Abwesenheit von offensichtlichen Fehlern  
ABER:
+ Deck nur (fast) immer einen Teil des Systems ab

+ ### Kenngrößen von Tests

  + Welche Anforderungen berücksichtigt wurden
  + Code-Abdeckung
  + Abdeckung der Werteberiche der Eingaben
  + Systemabdeckung
  + Automatisierung der Testausführung

+ ### Ansätze

  + Assertions
  + Unit-Tests
  + Automatische Testerzeugung (fuzzing)
  + Probery-directed Testing
  + Modellbasiertes Testen
  + Kobination von manuellen und autmatischen Test- und Verifikationstechniken haben die besten chancen auf hohe Codequalität

### Unit-Testen

+ Überprüfung einzelner Code-einheiten in Isolation
+ Test-Case: welcher Code, korekte Eingabe, erwartete Aisgabe
+ Test-Suit: Menge von Test-Cases (für eine Unit)
+ Fixture: Initialisierung der Umgebung
+ Automatisierte Ausführung der Test-Suits/Cases
+ Generierung eines Test-Reports
+ "test before you commit"
+ gegebenfalls Doku notwendig
+ EFFEKTIV: Tests sollen so vile Fehler wie möglich finden
+ EFFIZIENT: größte Anzahl an fehlern mit geringster Anzahl an Tests
+ Source-Code nicht notwendig
+Komplexe Szenarien möglich: genaue Beschreibung der erwarteten Ergebnisse
+ Einfach umsetzten & zu automatiseren
Fängt Regresseionen ab (neue Fehler)
+ ABER:
  + unklar, wie viel Code überprüft wurde
  + manueller Aufwand
  + unklar, wie viel Verhalten überprüft wurde
  + ABER:
    + Können engegen geewierkt werden

### Proberty-based-Testing

+ Ziele
  + automatische Auswahl der Test-Eingaben
  + automatische Berechnung der erwarteten Ausgaben für gegebene Eingaben
+ Ansatz
  + Propery (durch "Test-Orakel") programatische Ergebnisprüfung
  + Automatische Eingabegenerierung
+ 2 Wege Propertyy based testen zu machen
  + Eigenschaften von Ergebnissen testen
  + Aletnative Berchnungen, Referenzimpelementierung
+ Uni-testing vs Propertybased Testing
  + Unit Testing
    + Einfcher Einstieg
    + Nachvollziehbae konkrete Werte
    + deterministische Ausführung
    + ABER. Aufwand = #Tests
  + Propery-based + Generatoren
    + Hohe Automatiesierung
    + Flexible Anpassung möglich
    + "formale" Spezifikation
    + ABER: abstrakte aber präzise Properties sind schwierig zu formulieren
    + Evtl rechenaufwändig

## Vorlesung 3

### Kontraollflussautomaten und -abdeckungsmaße

 Haben eine Sysstematische Konstruktion

+ Knoten = Programmstellen ~ Programmzeilen
+ Kanten = Anweisung & Testes
+ Scleifen = Zyklen

Coverage

+ Anweisungs überdeckung (statment coverage)
  + verständlich
  + messbar:tatsächliche und bestmögliche Abdeckung
  + ABER: leine aussagen über funktionale Eigenschaften
  + evtl 100% nicht ereichbar (dead code)
+ Zweigüberdeckung (branch coverage)
+ Pfadüberdeckung (Path coverage)
  + sematisches Kriterium, genau die tatsächlich möglichen Ausfürungen
  + Grundlage für beweisbare Korrektheit
  + ABER: für die meisten systeme nicht erreichbar(Schelifen, Eingaben kann ins unedliche gehen)
    + Lösung: "Alle Pfade der Länge x Abdecken"

### Transitionen und Erreichbarkeit

Syntax = statische Sicht  
Semantik = dynamische Sicht  
Spezifikation von Eigenschaften  

+ Invarianete = erwünschte Eigenschaft aller ereichbarer Zustände
+ insbesondere: Zielzustände/Fehlerzustände

Verifikation

+ Erreichbarkeitsanalyse  durch expizites Aufzählen

### Transistionssysteme

+ Fehlerstellen wollen nicht erreicht werden
+ Testen ob diese erreichbar sind
+ wenn Fehler gelten ist Programm fehlerhaft, wenn nicht dann ist es korrekt
+ Laufzeit: proportional zur Anzahl der erreichbaren Transitionen
+ Vollständigkeit: alle erreichbaren Zustände werden gefunden( wenn endlich erreichbar, ohne Beweis)

## Vorlesung 4

### Nichtdeterminismus

+ Ergebins völlig beliebeig da "Eongabe nicht umbedingt klar"
+ asumes nutzen: "Data refinment by miracles"
+ nichdeterministische algorithmen immernoch als korrekt beweisbar
+ Wird veerwendet für spetifikation von Schnittstellen und Eingaben
+ Modellierung von Systemen
+ Modulare Beweise via Design by Contract
+ Probleme der expiziten Erreichbarkeitsanlayse
  + Zustandsexpolion bei Nitchdeterminismus
  + Annahme: aufgebrochene Ausführung
  + Annahme müssen ausfürbar sein

### Hoare Logik Regelgeln

+ Skip (davor und danach das selbe Ergebniss)
+ assume "x" (davor und assume danach)
  + assume false gilt kein möglicher nachzustand
+ assert "x" (an dieser stelle soll x gelten)
  + assert true == skip
  + assert false gilt nie
  