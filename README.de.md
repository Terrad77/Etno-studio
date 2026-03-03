# Vanilla App Template

Dieses Projekt wurde mit Vite erstellt. Zur Einführung und Konfiguration zusätzlicher
Funktionen [beachte die Dokumentation](https://vitejs.dev/).

## Repository aus der Vorlage erstellen

Verwende dieses GoIT-Organisations-Repository als Vorlage, um dein eigenes Projekt-Repository
zu erstellen. Klicke dazu auf die Schaltfläche `«Use this template»` und wähle die Option
`«Create a new repository»`, wie im Bild gezeigt.

![Creating repo from a template step 1](./assets/template-step-1.png)

Im nächsten Schritt öffnet sich die Seite zur Erstellung eines neuen Repositorys.
Fülle das Namensfeld aus, stelle sicher, dass das Repository öffentlich ist, und klicke
dann auf `«Create repository from template»`.

![Creating repo from a template step 2](./assets/template-step-2.png)

Nachdem das Repository erstellt wurde, navigiere in den Einstellungen des Repositorys
zur Registerkarte `Settings` > `Actions` > `General`, wie im Bild gezeigt.

![Settings GitHub Actions permissions step 1](./assets/gh-actions-perm-1.png)

Scrolle bis zum Ende der Seite. Wähle im Abschnitt `«Workflow permissions»` die Option
`«Read and write permissions»` aus und setze das Häkchen. Dies ist erforderlich, um den
Deployment-Prozess des Projekts zu automatisieren.

![Settings GitHub Actions permissions step 2](./assets/gh-actions-perm-2.png)

Du verfügst nun über ein persönliches Projekt-Repository mit der Datei- und Ordnerstruktur
des Vorlagen-Repositorys. Arbeite damit wie mit jedem anderen persönlichen Repository —
klone es auf deinen Computer, schreibe Code, erstelle Commits und übertrage sie auf GitHub.

## Vorbereitung

1. Stelle sicher, dass die LTS-Version von Node.js auf deinem Computer installiert ist.
   [Lade sie herunter und installiere sie](https://nodejs.org/en/), falls nötig.
2. Installiere die Basis-Abhängigkeiten des Projekts mit dem Befehl `npm install` im Terminal.
3. Starte den Entwicklungsmodus mit dem Befehl `npm run dev` im Terminal.
4. Öffne deinen Browser und navigiere zu
   [http://localhost:5173](http://localhost:5173). Diese Seite wird nach dem Speichern
   von Änderungen an Projektdateien automatisch neu geladen.

## Dateien und Ordner

- Markup-Dateien für Seitenkomponenten sollten im Ordner `src/partials` abgelegt und
  in die Datei `index.html` importiert werden. Zum Beispiel wird die Header-Markup-Datei
  `header.html` im Ordner `partials` erstellt und in `index.html` importiert.
- Style-Dateien sollten im Ordner `src/css` abgelegt und in die HTML-Dateien der
  jeweiligen Seiten importiert werden. Zum Beispiel heißt die Stylesheet-Datei für
  `index.html` `index.css`.
- Bilder werden im Ordner `src/img` abgelegt. Der Bundler optimiert sie, jedoch nur
  beim Build der Produktionsversion. Dieser Prozess läuft in der Cloud, um deinen
  Computer nicht zu belasten, da er auf schwächeren Rechnern sehr lange dauern kann.

## Deployment

Die Produktionsversion des Projekts wird automatisch kompiliert und auf GitHub Pages
im Branch `gh-pages` deployt, sobald der Branch `main` aktualisiert wird — zum Beispiel
nach einem direkten Push oder einem akzeptierten Pull-Request. Dazu muss der Wert des
Flags `--base=/<REPO>/` für den Befehl `build` in der Datei `package.json` angepasst
werden: Ersetze `<REPO>` durch den Namen deines Repositorys und übertrage die Änderungen
auf GitHub.

```json
"build": "vite build --base=/<REPO>/",
```

Gehe anschließend in die GitHub-Repository-Einstellungen (`Settings` > `Pages`) und
stelle die Auslieferung der Produktionsdateien aus dem Ordner `/root` des Branches
`gh-pages` ein, falls dies nicht automatisch geschehen ist.

![GitHub Pages settings](./assets/repo-settings.png)

### Deployment-Status

Der Deployment-Status des letzten Commits wird durch ein Symbol neben seiner ID angezeigt.

- **Gelb** — das Projekt wird gerade gebaut und deployt.
- **Grün** — Deployment wurde erfolgreich abgeschlossen.
- **Rot** — beim Linting, Build oder Deployment ist ein Fehler aufgetreten.

Genauere Statusinformationen erhältst du, indem du auf das Symbol klickst und im
Dropdown-Fenster dem Link `Details` folgst.

![Deployment status](./assets/deploy-status.png)

### Live-Seite

Nach einigen Minuten ist die Live-Version der Seite unter der URL verfügbar, die unter
`Settings` > `Pages` in den Repository-Einstellungen angegeben ist. Hier ist zum Beispiel
der Link zur Live-Version dieses Repositorys:

[https://goitacademy.github.io/vanilla-app-template/](https://goitacademy.github.io/vanilla-app-template/).

Wenn eine leere Seite geöffnet wird, überprüfe den `Console`-Tab in den Browser-Entwicklerwerkzeugen
auf Fehler bezüglich falscher Pfade zu CSS- und JS-Dateien (**404**). Wahrscheinlich ist
der Wert des Flags `--base` für den Befehl `build` in der Datei `package.json` falsch.

## So funktioniert es

![How it works](./assets/how-it-works.png)

1. Nach jedem Push in den Branch `main` des GitHub-Repositorys wird ein spezielles Skript
   (GitHub Action) aus der Datei `.github/workflows/deploy.yml` ausgeführt.
2. Alle Repository-Dateien werden auf den Server kopiert, wo das Projekt initialisiert,
   gelinted und vor dem Deployment gebaut wird.
3. Wenn alle Schritte erfolgreich abgeschlossen wurden, werden die kompilierten
   Produktionsdateien in den Branch `gh-pages` übertragen. Andernfalls wird im
   Ausführungsprotokoll des Skripts beschrieben, wo das Problem liegt.
