# Anrufliste

Eigenständige Ein-Datei-Web-App (GitHub Pages) für einen externen Sales: Firmenliste abtelefonieren, Status setzen, Kommentar erfassen. Unabhängig vom Apriko-CRM.

## Einrichten

**1. App-Registrierung (Azure-Portal → Microsoft Entra ID → App-Registrierungen → Neue Registrierung)**
- Name: `Anrufliste`
- Unterstützte Kontotypen: «Nur Konten in diesem Organisationsverzeichnis» (Gäste des Tenants sind damit eingeschlossen)
- Umleitungs-URI: Plattform **Single-Page-Anwendung (SPA)**, URI `https://benleuz.github.io/apriko-calls/`
- Nach dem Erstellen: **API-Berechtigungen** → Microsoft Graph → Delegiert → `Files.ReadWrite.All` und `User.Read` hinzufügen → «Administratorzustimmung erteilen»
- Die **Anwendungs-ID (Client-ID)** kopieren und in `index.html` bei `CONFIG.clientId` eintragen

**2. Repo**
- Neues GitHub-Repo `apriko-calls`, `index.html` hochladen
- Settings → Pages → Branch `main` → Speichern

**3. Daten**
- Selbst anmelden, Excel importieren (Spalten `name`, `custom ( id`, `region`, `city`, `website`). Dabei entsteht der Ordner `Anrufliste` im eigenen OneDrive mit `anrufliste.json`.

**4. Sales freischalten**
- Microsoft 365 Admin Center → Benutzer → Gastbenutzer → Gast hinzufügen (seine Mailadresse). Kostenlos, keine Lizenz nötig.
- In OneDrive den Ordner `Anrufliste` mit dem Gast teilen (Bearbeiten), «Link kopieren»
- Diesen Link in `index.html` bei `CONFIG.folderUrl` eintragen, neu deployen
- Dem Sales die Seiten-URL schicken; er meldet sich mit seiner Mailadresse an (Einmalcode oder eigenes Microsoft-Konto)

## Betrieb
- Speichern passiert automatisch beim Verlassen des Kommentarfelds bzw. beim Klick auf einen Status
- Erneuter Excel-Import aktualisiert nach ID und behält Kommentare
- «Kommentare als CSV» exportiert alles (Semikolon-getrennt, Excel-tauglich)
