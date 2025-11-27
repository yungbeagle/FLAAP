# Lastenheft

## Projekt: Aufbau der IT-Basisinfrastruktur der Hans-Memling-Schule

| Projektinformationen    |                                                    |
| :---------------------- | :------------------------------------------------- |
| **Projektbezeichnung:** | IT-Infrastruktur Hans-Memling-Schule               |
| **Auftraggeber:**       | Hans-Memling-Schule (vertreten durch Hr. Süssmann) |
| **Auftragnehmer:**      | FLAAP IT-Solutions                                 |
| **Datum:**              | 27.11.2025                                         |

---

### 1. Einleitung und Ausgangssituation

#### 1.1 Projektziel
Ziel des Projektes ist die Konzeption und Implementierung einer zukunftsfähigen, skalierbaren IT-Infrastruktur für den Neubau der Hans-Memling-Schule.
Der Fokus liegt auf **digitaler Souveränität** und **Kosteneffizienz**. Es soll eine reine **Open-Source-Lösung (Linux-basiert)** realisiert werden, um Lizenzkosten zu minimieren und die volle Datenhoheit im Haus zu behalten (On-Premise). Das System muss so gestaltet sein, dass der laufende Betrieb durch eine Lehrkraft (mit mathematisch-technischem Hintergrund, aber begrenzten Zeitressourcen) verwaltet werden kann.

#### 1.2 Ist-Zustand
*   **Gebäude:** Es handelt sich um einen Erstbezug ("Greenfield"-Projekt). Es ist keine aktive IT-Infrastruktur vorhanden. Ein anderer Dienstleister kümmert sich um die Verlegung der Netzwerk-Kabel.
*   **Infrastruktur:** Ein zentraler Serverraum (klimatisiert, abschließbar) ist vorhanden. Eine strukturierte Netzwerkverkabelung (LAN-Dosen in den Räumen) wird bauseitig vorausgesetzt.
*   **Hardware/Software:** Keine Bestandsgeräte oder Lizenzen vorhanden.

#### 1.3 Zielgruppen und Mengengerüst
Das System ist für folgende Benutzerzahlen auszulegen (mit Puffer für Wachstum in den nächsten 3 Jahren):
*   **Schüler:** 600 – 800
*   **Lehrkräfte:** 25 – 30
*   **Verwaltung:** Schulleitung und Sekretariat.

---

### 2. Funktionale Anforderungen

#### 2.1 Benutzerverwaltung und Authentifizierung
*   **Zentrales Verzeichnis:** Einrichtung eines zentralen Benutzerverzeichnisses (LDAP / Samba 4) zur Verwaltung aller Identitäten.
*   **Single Sign-On (SSO):** Die Benutzeranmeldung soll einheitlich erfolgen ("Ein Passwort für alles"). Dies gilt für die Windows-Clients, das WLAN und die Lernplattform Moodle.
*   **Verwaltungsoberfläche:** Da die Administration durch eine Lehrkraft erfolgt, ist zwingend eine **grafische, webbasierte Benutzeroberfläche (Web-GUI)** erforderlich. Die Erstellung von Benutzern, das Zurücksetzen von Passwörtern und die Zuweisung zu Klassen/Gruppen muss ohne Nutzung der Linux-Kommandozeile möglich sein.
*   **Rollenkonzept:** Abbildung verschiedener Berechtigungen für "Schüler", "Lehrer", "Verwaltung" und "Gäste" (Role Based Access Control).

#### 2.2 Dateidienste und Speicher
*   **Persönliche Laufwerke:** Bereitstellung persönlicher Home-Verzeichnisse für jeden Benutzer (Lehrer und Schüler).
*   **Tauschlaufwerke:** Einrichtung von Gruppenlaufwerken für Klassen, Fachbereiche und das Lehrerkollegium.
*   **Protokolle:** Zugriff über SMB/CIFS für volle Kompatibilität mit Windows-Clients und BYOD-Geräten.

#### 2.3 Netzwerk und WLAN
*   **Abdeckung:** Eine stabile WLAN-Abdeckung ist in folgenden Bereichen zu gewährleisten:
    *   Alle Klassenzimmer.
    *   Verwaltungsräume und Lehrerzimmer.
    *   *Hinweis:* Eine Ausleuchtung der Flure ist **nicht** gefordert.
*   **Netzwerksegmentierung:** Trennung des Datenverkehrs mittels VLANs (z.B. Management, Lehrernetz, Schülernetz, Gäste).
*   **Gast-Zugang:** Einrichtung eines isolierten Gast-WLANs für Referenten (Zugang via temporäres Passwort/Voucher).
*   **Performance:** Das Netzwerk muss HD-Streaming in mehreren Klassenräumen gleichzeitig ermöglichen.

#### 2.4 Lernplattform (LMS)
*   **Software:** Installation und Konfiguration von **Moodle**.
*   **Integration:** Anbindung an das zentrale Benutzerverzeichnis (LDAP) zur Authentifizierung.
*   **Funktionen:** Bereitstellung von Kursen, Dateien, Upload-Möglichkeiten und Foren.
*   **Hierarchie:** Abbildung einer hierarchischen Kursstruktur (Kategorien) für die Schulleitung.

#### 2.5 Fernzugriff (Remote Access)
*   **VPN:** Einrichtung eines VPN-Zugangs für Lehrkräfte, um von extern sicher auf die internen Dateilaufwerke zugreifen zu können.
*   **Web-Zugriff:** Moodle muss für alle Nutzer (auch Schüler) über das Internet erreichbar sein.

#### 2.6 Projektmanagement-Tool
*   Auswahl und Bereitstellung einer Softwarelösung zur Unterstützung der Schulleitung bei Entwicklungsprojekten (z.B. Kanboard, OpenProject oder vergleichbare Open-Source-Lösungen, alternativ Cloud-Dienst nach DSGVO-Prüfung).

---

### 3. Nicht-funktionale Anforderungen

#### 3.1 Datensicherheit und Datenschutz
*   **Datensouveränität:** Alle sensiblen Daten (insbesondere personenbezogene Daten von Schülern) müssen auf den schuleigenen Servern verbleiben.
*   **Backup:** Implementierung einer automatisierten, täglichen Datensicherung aller VMs und Datenbestände.
*   **Disaster Recovery:** Die Wiederherstellbarkeit des Gesamtsystems nach einem Hardwareausfall muss dokumentiert und gewährleistet sein.

#### 3.2 Verfügbarkeit und Wartbarkeit
*   **Betriebszeit:** Das System muss zu den Schulzeiten hochverfügbar sein. Wartungsfenster und kürzere Ausfälle sind am Wochenende oder in den Ferien akzeptabel.
*   **USV:** Absicherung der zentralen Server- und Netzwerkkomponenten gegen Stromausfälle und Spannungsschwankungen. Automatisches Herunterfahren (Shutdown) des Servers bei kritischem Batteriestand.

#### 3.3 Systemumgebung
*   **Open Source First:** Es sollen primär Open-Source-Technologien (Linux, Samba, Moodle, Proxmox/KVM) eingesetzt werden, um Lizenzkosten dauerhaft niedrig zu halten und Vendor-Lock-in zu vermeiden.

---

### 4. Technische Rahmenbedingungen

#### 4.1 Server-Hardware
*   **Typ:** 1x Physischer Server (Rackmount), ausgelegt für Virtualisierung.
*   **Leistung:** Ausreichend Ressourcen für ca. 850 Benutzer (Empfehlung: mind. 128 GB RAM, performanter Multi-Core Prozessor).
*   **Storage:** Hybrider Speicher oder All-Flash für optimale Datenbank-Performance (Moodle) bei gleichzeitig hoher Kapazität für Dateien.

#### 4.2 Software-Stack (Soll-Konzept)
*   **Virtualisierung:** Proxmox VE oder vergleichbarer Open-Source Hypervisor.
*   **Betriebssysteme:** Linux (z.B. Debian Stable, Ubuntu LTS).
*   **Identity Management:** Univention Corporate Server (Core), Linuxmuster.net oder vergleichbare Lösung mit GUI.

#### 4.3 Netzwerkhardware
*   19-Zoll Serverschrank (42 HE).
*   Core-Switch (Managed, Layer 2/3).
*   Access-Switches mit PoE+ (Power over Ethernet) für die Versorgung der Access Points.
*   Wi-Fi 6 Access Points.

---

### 5. Lieferumfang und Abnahme

#### 5.1 Zu erbringende Leistungen
1.  Beschaffung und Lieferung der Hardware.
2.  Einbau der Komponenten in den Serverraum.
3.  Installation der Virtualisierungsumgebung.
4.  Einrichtung der Linux-Server-VMs (Domain Controller, File Server, Moodle Server).
5.  Konfiguration der Netzwerkinfrastruktur (VLANs, WLAN-SSIDs).
6.  Einrichtung der VPN-Lösung.
7.  Einweisung des IT-Verantwortlichen (Mathelehrer) in die Verwaltungsoberfläche.

#### 5.2 Dokumentation
Dem Auftraggeber sind nach Projektabschluss folgende Unterlagen zu übergeben:
*   Netzwerkplan (Topologie).
*   IP-Adressplan und VLAN-Konfiguration.
*   Passwortliste (Übergabe an Schulleitung).
*   Administrationshandbuch (Schwerpunkt: Benutzer anlegen, Backup prüfen, Moodle-Grundlagen).
*   Notfallplan für Wiederherstellung.

#### 5.3 Abnahmekriterien
Das Projekt gilt als erfolgreich abgenommen, wenn:
*   Die Hardware fehlerfrei läuft.
*   Ein Test-Benutzer (Schüler) sich erfolgreich im WLAN und Moodle anmelden kann.
*   Ein Test-Benutzer (Lehrer) von extern per VPN auf sein Laufwerk zugreifen kann.
*   Ein Backup erfolgreich erstellt und testweise wiederhergestellt wurde.
*   Das System bis zum vereinbarten Stichtag (Erster Schultag / Ende Testphase) betriebsbereit ist.
