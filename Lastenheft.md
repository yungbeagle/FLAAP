# Lastenheft

## Projekt: Aufbau der IT-Basisinfrastruktur der Hans-Memling-Schule

| Projektinformationen    |                                                    |
| :---------------------- | :------------------------------------------------- |
| **Projektbezeichnung:** | IT-Infrastruktur Hans-Memling-Schule               |
| **Auftraggeber:**       | Hans-Memling-Schule (vertreten durch Hr. Süssmann) |
| **Auftragnehmer:**      | FLAAP IT-Solutions                                 |
| **Datum:**              | 27.11.2025                                         |

---

### 1. Ausgangssituation und Zielsetzung

#### 1.1 Ist-Zustand
Die Hans-Memling-Schule bezieht einen Neubau. Es ist keine aktive IT-Infrastruktur (Server, Switches, WLAN) vorhanden ("Greenfield"). Ein klimatisierter Serverraum sowie eine strukturierte Gebäude-Verkabelung (LAN-Dosen) werden bauseitig bereitgestellt. Es existiert kein Budget für jährlich wiederkehrende Lizenzkosten pro Benutzer.

#### 1.2 Projektziel
Ziel ist die Herstellung der Betriebsbereitschaft einer IT-Infrastruktur zum ersten Schultag. Das System soll die **digitale Souveränität** der Schule sichern (Datenhaltung im eigenen Haus) und langfristig kosteneffizient sein (Vermeidung von "Vendor-Lock-in").

#### 1.3 Zielgruppen
Das System muss für ca. 800 Schüler und 30 Lehrkräfte ausgelegt sein, mit einer Reserve für zukünftiges Wachstum.

---

### 2. Funktionale Anforderungen (Was muss das System tun?)

#### 2.1 Administration und Benutzermanagement
*   **Anforderung 2.1.1 (Einfache Verwaltung):** Da die Administration durch eine Lehrkraft (ohne tiefe Server-Kenntnisse) erfolgt, **muss** die Verwaltung der Benutzer, Gruppen und Rechte über eine intuitive, grafische Web-Oberfläche möglich sein. Die Nutzung einer Kommandozeile darf für Standardaufgaben nicht notwendig sein.
*   **Anforderung 2.1.2 (Single Sign-On):** Benutzer sollen sich mit *einem* zentralen Account an allen Diensten (PCs, WLAN, Lernplattform) anmelden können.
*   **Anforderung 2.1.3 (Hierarchie):** Die Schulleitung benötigt Rechte, um hierarchische Strukturen (Klassen, Kurse) anzulegen.

#### 2.2 Dateiablage und Zugriff
*   **Anforderung 2.2.1 (Speicherbereiche):** Das System muss persönliche Speicherbereiche für jeden Benutzer sowie gemeinsame Austauschlaufwerke für Klassen und Lehrer bereitstellen.
*   **Anforderung 2.2.2 (Kompatibilität):** Der Zugriff auf Dateien muss von gängigen Betriebssystemen (Windows, macOS, Linux) nativ möglich sein.
*   **Anforderung 2.2.3 (Fernzugriff):** Lehrkräfte müssen in der Lage sein, von extern sicher (verschlüsselt) auf ihre schulischen Daten zuzugreifen.

#### 2.3 Netzwerkinfrastruktur
*   **Anforderung 2.3.1 (WLAN-Abdeckung):** Eine stabile WLAN-Verbindung ist zwingend in allen Klassenzimmern sowie im Verwaltungsbereich erforderlich. Eine Abdeckung der Flure ist explizit **nicht** gefordert.
*   **Anforderung 2.3.2 (Netzwerktrennung):** Das Netz muss logisch getrennt sein, um sensible Verwaltungsdaten vom Schülerverkehr und Gastzugängen abzuschirmen.
*   **Anforderung 2.3.3 (Gastzugang):** Es muss eine Möglichkeit geben, Gästen (z.B. Referenten) zeitlich begrenzten Internetzugriff zu gewähren (z.B. via Voucher).

#### 2.4 Lernplattform (LMS)
*   **Anforderung 2.4.1 (Software):** Gemäß Kundenwunsch ist die Lernplattform **Moodle** einzurichten.
*   **Anforderung 2.4.2 (Erreichbarkeit):** Die Plattform muss sowohl aus dem internen Netz als auch über das Internet für alle Nutzer erreichbar sein.

#### 2.5 Projektmanagement
*   **Anforderung 2.5.1:** Bereitstellung einer Softwarelösung zur Unterstützung der Schulleitung bei der Planung und Überwachung von Schulprojekten.

---

### 3. Nicht-funktionale Anforderungen (Wie gut muss das System sein?)

#### 3.1 Wirtschaftlichkeit und Lizenzen
*   **Anforderung 3.1.1:** Um laufende Kosten zu minimieren, soll vorrangig auf **Open-Source-Software** gesetzt werden.
*   **Anforderung 3.1.2:** Es sollen keine Lösungen implementiert werden, die Lizenzkosten pro Benutzer (CALs) verursachen.

#### 3.2 Datensicherheit und Datenschutz
*   **Anforderung 3.2.1 (Datensouveränität):** Personenbezogene Daten (Noten, Schülerakten) müssen auf schuleigenen Servern gespeichert werden (On-Premise). Eine Speicherung in einer Public Cloud ist für sensible Daten unzulässig.
*   **Anforderung 3.2.2 (Backup):** Eine automatisierte, tägliche Datensicherung aller Systemkomponenten ist einzurichten.

#### 3.3 Verfügbarkeit und Performance
*   **Anforderung 3.3.1:** Das System muss leistungsfähig genug sein, um Video-Streaming in HD-Qualität in mehreren Klassenräumen gleichzeitig zu ermöglichen.
*   **Anforderung 3.3.2:** Kritische Hardwarekomponenten müssen gegen Stromausfall und Spannungsschwankungen abgesichert sein.

---

### 4. Lieferumfang und Rahmenbedingungen

Der Auftragnehmer ist verantwortlich für:
1.  Lieferung und physikalischen Einbau der notwendigen Server- und Netzwerkkomponenten in das vorhandene Rack.
2.  Installation und Konfiguration der Software gemäß den oben genannten Anforderungen.
3.  Erstellung einer Dokumentation (Netzwerkpläne, Installationsberichte).
4.  Einweisung des administrierenden Lehrpersonals.

---

### 5. Abnahmekriterien (Überprüfbarkeit)

Die Abnahme erfolgt durch Prüfung der folgenden Kriterien am lebenden System:
1.  **Funktionstest WLAN:** Ein Endgerät erhält in einem Klassenzimmer stabilen Empfang und Internetzugriff.
2.  **Funktionstest Login:** Ein Test-Benutzer kann sich mit identischen Zugangsdaten an einem PC und in Moodle anmelden.
3.  **Funktionstest Admin-GUI:** Der IT-Verantwortliche kann über die Web-Oberfläche eigenständig einen neuen Schüler anlegen und dessen Passwort zurücksetzen, ohne die Konsole zu nutzen.
4.  **Funktionstest VPN:** Zugriff auf das Home-Laufwerk von einem externen Anschluss ist erfolgreich.
5.  **Dokumentation:** Vollständige Übergabe der Pläne und Zugangsdaten.
