# CuonzTech Privacy Chaos Gate — GitHub Action

Prüft in der CI, ob eine Website Tracker **vor** der Einwilligung lädt (Cookie-/Consent-Leaks), und lässt den Build
bei Verstössen scheitern. Die Action installiert das veröffentlichte npm-Paket
[`cuonztech-privacy-chaos-gate`](https://www.npmjs.com/package/cuonztech-privacy-chaos-gate) in einer fest
eingetragenen Version und führt es aus. Dieses Repository enthält nur die Action-Definition (`action.yml`).

```yaml
- uses: cuonztech/privacy-chaos-gate-action@v1
  with:
    staging-url: ${{ vars.STAGING_URL }}
```

- **Ohne gültige Lizenz** läuft der Scan vollständig, Gate-Zustand und Exit-Code sind echt. Die Ausgabe zeigt nur das
  Ergebnis in Zahlen: keine Tracker-Namen und Belege, keine Reports, kein PDF, kein Auto-Fix, kein Commit, kein PR.
- **Mit gültiger Lizenz** (`license: ${{ secrets.CPCG_LICENSE }}`) gibt es die vollständige Ausgabe, die Reports,
  Kundenreport/PDF (`report-pdf`, `client-name`), Auto-Fix sowie `git-commit` und `create-pr`.
- **Laufzeit und Actions-Minuten:** Die Action läuft in Ihrem GitHub-Konto und verbraucht dessen Minuten. Gemessen auf
  einem GitHub-Runner: Installation samt Browser etwa 35 Sekunden, Scan einer einfachen Seite etwa 110 Sekunden, zusammen
  rund 2,5 Minuten; Seiten mit viel Werbetechnik und Tiefenläufe (`deep-budget`, Standard 300 s) brauchen länger. Private
  Repositories im kostenlosen Tarif haben 2.000 Minuten im Monat, öffentliche Repositories kosten nichts. Scannen Sie
  deshalb lieber nach dem Deployment (`deployment_status` oder `repository_dispatch`), zeitgesteuert (`schedule`) oder von
  Hand (`workflow_dispatch`) als bei jedem Push, und setzen Sie `concurrency` mit `cancel-in-progress: true`.
- Alle Inputs und Outputs stehen in [`action.yml`](action.yml); die ausführliche Dokumentation liegt im
  README des npm-Pakets.

Lizenz und Kauf: <https://cuonztech.ch/privacy-chaos-gate-landing-v01.html> · Support: support@cuonztech.ch

Die Software steht unter der proprietären Lizenz in [`LICENSE`](LICENSE) (Fassung 2026-10-23).
