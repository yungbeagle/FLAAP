### **Theoretischer Durchführungsplan für die Moodle-Plattform**

Dieses Dokument beschreibt die schrittweise Vorgehensweise zur technischen Implementierung der Moodle-Lernplattform gemäß dem Konzept aus [Evaluation und Konzeption](Evaluation_und_Konzeption.md)

#### **Phase 1: Vorbereitung der Infrastruktur (Voraussetzungen)**

Bevor die eigentliche Moodle-Installation beginnen kann, müssen die grundlegenden Systeme bereitgestellt und konfiguriert werden.

**1.1. Aufsetzen des Domain Controllers (DC):**
Eine zentrale Benutzerverwaltung ist die Voraussetzung für einen reibungslosen Betrieb. Daher wird auf dem Host-Server eine eigene virtuelle Maschine für den DC (Windows Server) aufgesetzt.
*   **Aktion:** Installation des Betriebssystems und der Active Directory Domain Services (AD DS).
*   **Konfiguration:**
    *   Einrichten der Domäne (z.B. `hans-memling.local`).
    *   Anlegen einer grundlegenden Organisationsstruktur (Organizational Units, OUs) zur Trennung von Benutzertypen, z.B. `OU=Schueler`, `OU=Lehrer`, `OU=Verwaltung`.
    *   Erstellen von Sicherheitsgruppen wie `Gruppe-Lehrer` und `Gruppe-Schueler`, die später zur Rechtevergabe in Moodle genutzt werden.
    *   Anlegen eines dedizierten **Service-Benutzers** (z.B. `svc-moodlesync`), der Moodle das Leserecht im Active Directory gewährt.

**1.2. Bereitstellung der Moodle-VM:**
*   **Aktion:** Im Hyper-V wird eine neue virtuelle Maschine (`HMS-MOODLE-01`) erstellt.
*   **Konfiguration:** Die VM erhält die im Konzept definierten Ressourcen (6 vCPUs, 16 GB RAM, 150 GB SSD-Speicher).
*   **Installation:** Das Basis-Betriebssystem (Ubuntu Server 22.04 LTS) wird installiert und eine feste IP-Adresse im Server-Netzwerk vergeben. Grundlegende Absicherungsmaßnahmen (Firewall-Konfiguration, Systemupdates) werden durchgeführt.

#### **Phase 2: Installation des Moodle-Software-Stacks**

In dieser Phase wird die eigentliche Software auf der vorbereiteten Moodle-VM installiert.

*   **2.1. Installation der Web-Dienste:** Installation der benötigten Software-Pakete: Apache2 (Webserver), PostgreSQL (Datenbank) und PHP 8.1 mit allen für Moodle erforderlichen Erweiterungen (z.B. `php-intl`, `php-xmlrpc`, `php-soap`).
*   **2.2. Datenbank-Setup:** Erstellen einer leeren Datenbank (`moodledb`) und eines zugehörigen Datenbank-Benutzers (`moodleuser`) mit den notwendigen Rechten.
*   **2.3. Moodle-Installation:**
    *   Herunterladen der aktuellen Moodle LTS-Version.
    *   Einrichten des Moodle-Programmverzeichnisses (`/var/www/html/moodle`) und des Datenverzeichnisses (`/opt/moodledata`). Die Trennung ist ein wichtiges Sicherheitsmerkmal.
    *   Starten des Web-Installers und Verbinden von Moodle mit der vorbereiteten Datenbank.
*   **2.4. Cronjob einrichten:** Konfiguration eines System-Cronjobs, der essenzielle Hintergrundprozesse von Moodle (z.B. Mails versenden, Kurse aufräumen) automatisiert ausführt.

#### **Phase 3: Konfiguration und Integration**

Nach der technischen Grundinstallation wird Moodle an die spezifischen Bedürfnisse der Schule angepasst.

*   **3.1. Konfiguration der LDAP-Authentifizierung:**
    *   **Aktion:** Aktivierung des LDAP-Plugins in Moodle.
    *   **Verbindung:** Eintragen der Verbindungsdaten zum Domain Controller unter Verwendung des zuvor erstellten Service-Benutzers (`svc-moodlesync`).
    *   **Synchronisation:** Konfiguration der Synchronisation, sodass Benutzer aus den Active Directory-Gruppen (`Gruppe-Lehrer`, `Gruppe-Schueler`) in Moodle automatisch den korrekten Rollen (Lehrer/Trainer, Schüler/Student) zugewiesen werden.
    *   **Feld-Mapping:** Zuweisung von AD-Feldern zu Moodle-Profilfeldern (z.B. `givenName` -> Vorname).
*   **3.2. Visuelle Anpassung (Branding):** Hochladen des Schullogos und Anpassung des Farbschemas an das Corporate Design der Schule.
*   **3.3. Systemeinstellungen:** Konfiguration des E-Mail-Versands (SMTP), der Systemsprache, Zeitzone und der Startseite für eingeloggte Benutzer.

#### **Phase 4: Qualitätssicherung und Abschluss**

In der letzten Phase wird die korrekte Funktion sichergestellt und die Arbeit dokumentiert.

*   **4.1. Funktionstests:** Anlegen von Test-Benutzern in den jeweiligen AD-Gruppen (1x Test-Lehrer, 1x Test-Schüler).
    *   **Szenario 1 (Lehrer):** Erfolgreicher Login, Erstellen eines Test-Kurses, Hochladen einer Datei.
    *   **Szenario 2 (Schüler):** Erfolgreicher Login, Einschreiben in den Test-Kurs, Herunterladen der Datei.
*   **4.2. Backup-Test:** Durchführung eines vollständigen Backups der Moodle-VM über Veeam und anschließende Test-Wiederherstellung in einer isolierten Umgebung, um die Funktionsfähigkeit des Backup-Konzepts zu verifizieren.
*   **4.3. Finalisierung der Dokumentation:** Vervollständigen der technischen Dokumentation mit allen relevanten Konfigurationsdetails, Zugangsdaten und Passwörtern (letztere werden sicher im Passwort-Manager hinterlegt).