### **Fragenkatalog zur Anforderungsanalyse: IT-Infrastruktur Hans-Memling-Schule**

**Ziel:** Dieser Fragenkatalog dient dazu, die Anforderungen, Wünsche und Rahmenbedingungen für die neue IT-Infrastruktur der Hans-Memling-Schule systematisch zu erfassen. Die Antworten bilden die Grundlage für die Erstellung des Lastenhefts.

**Ansprechpartner:**  Herr Süssmann


#### **1. Allgemeine Projektziele & Ausgangssituation**

*   **1.1 Projektvision:** Was ist das übergeordnete Ziel, das Sie mit der neuen IT-Infrastruktur erreichen wollen?
* digitale souveränität, hohheit über daten behalten
*   **1.2 Dringlichkeit:** Welche Teile der Infrastruktur müssen bis zu welchem Datum zwingend betriebsbereit sein? Gibt es einen Stichtag (z.B. erster Schultag)?
* erster schultag, testphase vor sommerferien
*   **1.3 Ausgangslage:** Können Sie bestätigen, dass absolut keine IT-Infrastruktur (Server, Netzwerkkomponenten, Software) vorhanden ist, auf der wir aufbauen müssen?
* nichts
*   **1.4 Zukunftspläne:** Gibt es bereits Pläne für die Zukunft, die wir bei der jetzigen Planung berücksichtigen sollten? (z.B. Einführung digitaler Tafeln, BYOD-Konzepte, Schulverwaltungssoftware in den nächsten 1-3 Jahren).
* ausscheibung
*   **1.5 Budget:** Gibt es einen festgelegten Budgetrahmen für die Erstausstattung (Hardware & Software)?
* -


#### **2. Anwender und Zielgruppen**

*   **2.1 Benutzerzahlen:** Mit wie vielen Benutzern planen Sie zum Start und in den nächsten 3 Jahren?
    *   Anzahl der Lehrkräfte?
    * 25-30
    *   Anzahl der Schüler?
    * 600-800
    *   Anzahl der Verwaltungsmitarbeiter?
    * -
*   **2.2 Benutzerrollen:** Welche unterschiedlichen Benutzergruppen mit verschiedenen Rechten wird es geben? (z.B. Schulleitung, Lehrer, Schüler, Sekretariat, externe Gäste).
* Schulleitung, Lehrer, Schüler, Sekretariat, externe Gäste, freigaben, role based access control
*   **2.3 IT-Kenntnisse:** Wie schätzen Sie die durchschnittlichen IT-Kenntnisse der zukünftigen Lehrkräfte und Mitarbeiter ein? (Anfänger, Fortgeschrittene, Experten).
* mathelehrer macht it
*   **2.4 Typische Arbeitsabläufe:** Können Sie typische digitale Arbeitsprozesse beschreiben?
    *   *Für eine Lehrkraft:* Wie bereitet sie den Unterricht vor? Wie interagiert sie mit Schülern?
    * hierrarchische erstellung von kursen durch leitung
    *   *Für die Verwaltung:* Welche administrativen Aufgaben sollen digital unterstützt werden?
    * 



#### **3. Funktionale Anforderungen (Was soll das System können?)**

*   **3.1 Lernplattform (Moodle):**
    *   Welche konkreten Funktionen sind Ihnen bei einer Lernplattform am wichtigsten? (z.B. Nur Dateien bereitstellen, oder auch Online-Tests, Foren, Abgabe von Hausaufgaben?).
    * erwähnte
    *   Soll die Plattform nur intern oder auch von zu Hause aus erreichbar sein?
    * ja
*   **3.2 Dateiablage & Zusammenarbeit:**
    *   Benötigt jeder Mitarbeiter einen persönlichen, nur für ihn zugänglichen Speicherbereich (Home-Laufwerk)?
    * ja auch schüler
    *   Welche gemeinsamen Ablagebereiche werden benötigt? (z.B. pro Fachschaft, für die gesamte Lehrerschaft, für die Verwaltung?).
    * pro klasse, pro rolle, pro fachbereich, sso
    *   Wie sollen die Zugriffsrechte darauf geregelt sein?
    * sso einbinden für auth
*   **3.3 Netzwerk und WLAN:**
    *   In welchen Bereichen des Schulgebäudes wird eine WLAN-Abdeckung zwingend benötigt? (z.B. nur Lehrerzimmer und Verwaltung, oder in allen Klassenzimmern?).
    * jeder kr, verwaltung, lr, kein flure
    *   Welche Arten von Geräten werden sich hauptsächlich mit dem WLAN verbinden? (Schuleigene Laptops, private Smartphones der Lehrer?).
    * 
    *   Ist ein separates Gast-WLAN (z.B. für Referenten) erforderlich?
    * ja, temp passwort
*   **3.4 Externer Zugriff (Home-Office):**
    *   Welche Benutzergruppen sollen von zu Hause aus auf das Schulnetzwerk zugreifen können? (Nur Lehrkräfte?).
    * alle (moodle), laufwerke nur lehrer
    *   Auf welche Ressourcen genau soll der Zugriff von extern möglich sein? (Nur auf die Dateiablage, oder auch auf andere Systeme?).
    * 
*   **3.5 Projektmanagement-Tool:**
    *   Für welche Zwecke genau benötigt die Schulleitung ein Projektmanagement-Tool? (z.B. Organisation von Schulfesten, Koordination von Baumaßnahmen, Unterrichtsplanung?).
    * schulentwicklungsprojekte (z.B. Neubauten, neue Schwerpunkte)
    *   Gibt es bereits Erfahrungen mit solchen Tools oder bestimmte Präferenzen?
    * 


#### **4. Nicht-funktionale Anforderungen (Qualität, Performance, Sicherheit)**

*   **4.1 Verfügbarkeit:** Wie kritisch ist ein Ausfall des Systems? Ist es akzeptabel, wenn das System z.B. für einige Stunden nicht verfügbar ist? Muss es auch am Wochenende laufen?
* ein paar stunden sind okay
*   **4.2 Datensicherheit & Backup:** Wie wichtig ist die tägliche Sicherung der Daten? Welche Daten sind am kritischsten? Wie schnell müssten Daten im Notfall wiederherstellbar sein?
* täglich, alle
*   **4.3 Performance:** Gibt es Erwartungen an die Geschwindigkeit? (z.B. „Ein 100-MB-Video sollte in unter 30 Sekunden aus dem internen Netzwerk heruntergeladen werden können“).
* genug für streaming mehrere klassen gleichzeitig (HD-Quali
*   **4.4 Skalierbarkeit:** Soll die Infrastruktur problemlos für eine Verdopplung der Schülerzahl in den nächsten 5 Jahren ausgelegt sein?
* -
*  **4.5 Datenschutz:** Welche Arten von personenbezogenen oder sensiblen Daten werden verarbeitet? (z.B. Noten, Adressdaten, Gesundheitsdaten). Gibt es einen Datenschutzbeauftragten an der Schule?
* dsb ja, noten etc.


#### **5. Technische und räumliche Rahmenbedingungen**

*   **5.1 Serverraum:** Gibt es einen geeigneten, abschließbaren und idealerweise klimatisierten Raum für die zentralen Server und Netzwerkkomponenten?
* ja 19 zoll rack
*   **5.2 Netzwerkverkabelung:** Ist das Gebäude bereits mit einer strukturierten LAN-Verkabelung ausgestattet? Wenn ja, in welchem Umfang und welcher Qualität (Cat5/6/7)?
* 
*   **5.3 Stromversorgung:** Gibt es eine stabile Stromversorgung? Ist eine Absicherung gegen Stromausfälle (USV) gewünscht?
  usv ja
*   **5.4 Software-Präferenzen:** Gibt es Vorgaben oder Präferenzen für bestimmte Hersteller oder Betriebssysteme (z.B. Microsoft Windows Server, Linux)?
* moodle, open source software, dass daten eu nicht verlassen



#### **6. Abnahme und Betrieb**

*   **6.1 Projektabschluss:** Woran messen Sie am Ende den Erfolg des Projekts? Was muss erfüllt sein, damit Sie sagen: „Ja, das Projekt ist erfolgreich abgeschlossen“?
* 
*   **6.2 Dokumentation:** Welche Art von Dokumentation benötigen Sie am Projektende, um das System zu verstehen und zu betreiben?
* hardwarepläne, lizenzpläne, softwareintsallplaäne, allg. doku
*   **6.3 Zukünftiger Betrieb:** Wer wird nach der Projektrealisierung für die Administration und Wartung der Systeme verantwortlich sein? (z.B. ein IT-beauftragter Lehrer, ein externer Dienstleister?).
* mathelehrer
