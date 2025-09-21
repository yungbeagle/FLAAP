### **Betriebskonzept und Service Level Agreement (SLA) für die Moodle-Plattform**

#### **1. Ziel des Dokuments**

Dieses Dokument definiert die Prozesse und Verantwortlichkeiten, um die Stabilität, Sicherheit und den reibungslosen Betrieb der Moodle-Plattform nach der initialen Projektdurchführung sicherzustellen. Es dient als Vereinbarung zwischen der FLAAP "IT-Solutions" (als Dienstleister) und der Hans-Memling-Schule (als Auftraggeber).

#### **2. Support und Ansprechpartner (Helpdesk-Prozess)**

Ein klar definierter Meldeweg für Probleme und Anfragen ist essenziell.

*   **First-Level-Support:** Der primäre Ansprechpartner für alle Benutzer (Lehrer und Schüler) ist der **IT-Beauftragte der Schule**. Er leistet Hilfestellung bei einfachen Anfragen wie Passwort-Resets (via Active Directory) und allgemeinen Anwendungsfragen.

*   **Second-Level-Support:** Technische Probleme, die der IT-Beauftragte nicht lösen kann (z.B. Systemfehler, Performance-Probleme, Ausfälle), werden an die FLAAP "IT-Solutions" eskaliert.

| Kontaktart | Details | Reaktionszeit (innerhalb der Geschäftszeiten) |
| :--- | :--- | :--- |
| **Support-E-Mail:** | `support-hms@flaap-it.de` | Bestätigung innerhalb von 4 Stunden |
| **Support-Telefon:** | `[Telefonnummer]` | Nur für kritische Ausfälle (System nicht erreichbar) |

#### **3. Regelmäßige Wartung (Proaktive Maßnahmen)**

Um die Systemsicherheit und -stabilität zu gewährleisten, werden folgende Wartungsarbeiten regelmäßig durchgeführt. Diese finden in der Regel in einem vorher angekündigten Wartungsfenster (z.B. sonntags, 6:00 - 8:00 Uhr) statt.

| Tätigkeit | Frequenz | Verantwortlich |
| :--- | :--- | :--- |
| **Installation von System-Updates** (Ubuntu Server) | Monatlich | IT-Solutions |
| **Installation von Moodle-Sicherheitsupdates** (Minor-Versionen) | Innerhalb von 7 Tagen nach Veröffentlichung | IT-Solutions |
| **Durchführung von Moodle-Major-Upgrades** (z.B. von 4.1 auf 4.2) | Jährlich, nach Test in einer Staging-Umgebung | IT-Solutions |
| **Prüfung der Backup-Integrität** | Wöchentlich | IT-Solutions |
| **Überprüfung der Server-Logfiles auf Anomalien** | Wöchentlich | IT-Solutions |
| **Kontrolle der Speicherauslastung** (SSD & HDD) | Monatlich | IT-Solutions |

#### **4. Backup und Wiederherstellung (Disaster Recovery)**

Das Backup-Konzept ist ein kritischer Bestandteil des Betriebs.

*   **Backup-Strategie:** Tägliche, inkrementelle Sicherung der gesamten Moodle-VM durch die Software Veeam Backup & Replication.
*   **Recovery Point Objective (RPO):** Maximal 24 Stunden. Dies ist der maximal tolerierbare Datenverlust im Falle eines Totalausfalls.
*   **Recovery Time Objective (RTO):** Maximal 4 Stunden. Dies ist die Zeit, die benötigt wird, um die Moodle-Plattform nach einem Totalausfall aus dem Backup vollständig wiederherzustellen.

Ein Wiederherstellungstest wird halbjährlich durchgeführt, um die Einhaltung des RTOs zu verifizieren.

#### **5. Monitoring**

Das System wird proaktiv überwacht, um potenzielle Probleme frühzeitig zu erkennen.

*   **Überwachte Metriken:**
    *   CPU-Auslastung
    *   RAM-Auslastung
    *   Freier Speicherplatz auf den System- und Daten-Partitionen
    *   Erreichbarkeit des Webservers (Ping-Check)
*   **Alarmierung:** Bei Überschreitung vordefinierter Schwellenwerte wird das Team von "IT-Solutions" automatisch per E-Mail benachrichtigt.

#### **6. Weiterentwicklung**

Die IT-Landschaft und die pädagogischen Anforderungen entwickeln sich stetig weiter.

*   **Jährliches Strategiegespräch:** Einmal pro Jahr findet ein Gespräch zwischen der Schulleitung und "IT-Solutions" statt, um:
    *   den Betrieb des vergangenen Jahres zu evaluieren.
    *   neue Anforderungen und Wünsche aufzunehmen.
    *   die Implementierung sinnvoller Erweiterungen (z.B. BigBlueButton, H5P) für das kommende Jahr zu planen.

Dieses Betriebskonzept stellt sicher, dass die Investition in die Moodle-Plattform nachhaltig geschützt ist und die Schule einen verlässlichen Partner für den technischen Betrieb hat.