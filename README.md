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

- Scan und Konsolen-Gate laufen **ohne Lizenz**.
- Kundenreport/PDF (`report-pdf`, `client-name`), `git-commit` und `create-pr` brauchen eine gültige Lizenz
  (`license: ${{ secrets.CPCG_LICENSE }}`). Ohne sie werden diese Schritte mit Hinweis übersprungen.
- Alle Inputs und Outputs stehen in [`action.yml`](action.yml); die ausführliche Dokumentation liegt im
  README des npm-Pakets.

Lizenz und Kauf: <https://cuonztech.ch/privacy-chaos-gate-landing-v01.html> · Support: support@cuonztech.ch

Die Software steht unter der proprietären Lizenz in [`LICENSE`](LICENSE) (Fassung 2026-10-23).
