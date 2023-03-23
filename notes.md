# 1. Vorlesung  

## Motivation  

+ Anforderungen erfüllen
+ Fehler vermeiden
+ Testen, Modelierung, Simulationen
+ Beweisen das Systeme sich verhalten wie man geplant hat
+ Man will möglichst verständliche und präzise Abstarktion

## Spezifikation (des Sollverhaltens, z.B.)

+ keine Abstürze
+ korrekte Ein-/Ausgabe
+ zeitliches Verhalten

## Testen, Verfikation

+ automatisierte Überprüfung
  + des Quellcodes  
  + eines abstraken Modells  
bezgl. der Spezifikation

## Modelierung

+ abstrakte Problembeschreibung
+ herausgreifen wesentlicher Aspekte

## Formal: mathematische Techniken

+ eindeutig und präzise
+ theoretisches begründetes Vertrauen in die Analyse

## Spezifikation

+ Anforderung != Spezifikation
  + Helligkeit des Displays bei Sonne erhöhen
+ Spezifikationen: beschreibt Systemschnittstelle/-verhalten
  + Beleuchtungsstärke gemäß Lichtsensor anpassen
  + Funktion abs gibt ein positives Ergebnis zurück

## Automatisierte Programmanalyse

+ System(Modell, Programm)
+ Spezifikation/Eigenschaft

## Testen vs Verifikation

+ Testen: beispielhaftes ausprobieren
+ Verifikaion: vollständige überprüfung oder Beweise

+ ###  Herausforderungen von beiden Varianten

  + große, komplexe Systeme
  + zu viele mögliche Zustände: Testen reicht nicht
  + Unendlicher Zustandsraum: Beides notwendig da schwierig zu automatisieren (Halteproblem/Rice's Theorem)

+ Verifikation in Praxis trozdem oft seh gut:
  + durch geeignete Analyse- und Beweistechnicken(Datenfluss, Model-Checking, Abstract Interpretation, SMT)
  + durch Abstraktion des Problems & Modelierung
  
## Kriterien für gute Modelierung

+ Führe Details schrittweise ein (Abstrakte und verfeinerte Modelle)
+ Betrachte Probleme auf der richtigen Abstraktionsebene (nicht zu wenig/zu viele Details)
