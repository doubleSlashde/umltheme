# Theme-Entwicklung

Regeln für Maintainer des Repositories `doubleSlashde/umltheme`.

## Rollen & Verantwortlichkeiten

| Rolle                | Darf ändern                          | Darf nicht ändern             |
| -------------------- | ------------------------------------ | ----------------------------- |
| **Diagramm-Autor**   | Inhalt der eigenen `.puml`           | Theme-Tokens, Gen2-Dateien    |
| **Theme-Maintainer** | `doubleslash/*.puml`, Golden Samples | Breaking Changes ohne Major   |
| **Docs-Maintainer**  | `docs/style-guide/*`                 | Theme-Verhalten ohne Theme-PR |

## Atomic Design bei Änderungen

```txt
Neues Styling benötigt?
├─ Neue Farbe?              → Atom in doubleslash-gen2.puml (oder colors.puml einbinden)
├─ Neues Element über Typen? → Molekül (!startsub / Stereotyp)
├─ Nur ein Diagrammtyp?     → Organismus (!startsub oder <style>)
├─ Nur System/Gantt?        → Bundle-Override
└─ Nur Doku?                 → docs/style-guide/
```

## CSS-first bei neuen Regeln

Neue Styling-Regeln **SOLLTEN** als `<style>` implementiert werden (PlantUML ≥ 1.2026.3).
Legacy-`skinparam` parallel pflegen bis Legacy-Support endet.

**Referenz:** [`padding-apply-css.puml`](https://github.com/doubleSlashde/umltheme/blob/main/doubleslash/padding-apply-css.puml)

## PR-Checkliste (Theme-Änderungen)

- [ ] Token-Änderung in [design-tokens.md](design-tokens.md) dokumentiert
- [ ] Betroffene [Diagrammtyp-Seite](diagram-types/sequence.md) aktualisiert
- [ ] Golden Samples in `examples/gen2/` gerendert und visuell geprüft (light **und** dark)
- [ ] PlantUML **≥ 1.2026.3** und **Legacy** getestet (Padding-Gate)
- [ ] [CHANGELOG.md](https://github.com/doubleSlashde/umltheme/blob/main/CHANGELOG.md) Eintrag
- [ ] Style-Guide-Regel-ID ergänzt oder Status aktualisiert
- [ ] Keine neuen Hardcoded-Hex außerhalb Token-Definition
- [ ] Backward Compatibility: Legacy-Includes funktionieren weiter

## Breaking-Change-Kriterien

| Änderung                                   | SemVer |
| ------------------------------------------ | ------ |
| Bugfix, Kontrast-Fix                       | Patch  |
| Neues Stereotyp-Styling, neues `!startsub` | Minor  |
| Token-Umbenennung, Include-Pfad-Entfernung | Major  |
| Entfernung Legacy-Root-Themes              | Major  |

Details: [Versionierung](versioning.md)

## CI & Validierung

Aktuell: [`.github/workflows/docs.yml`](https://github.com/doubleSlashde/umltheme/blob/main/.github/workflows/docs.yml) baut MkDocs.

**Empfohlen (Soll):**

```yaml
# Zukünftige Erweiterung
- PlantUML JAR 1.2026.3: Render examples/gen2/local_testing/*.puml
- PlantUML JAR Legacy: Padding-Fallback smoke test
- mkdocs build --strict
```

## Governance

- Token-Änderungen **MÜSSEN** per PR mit visuellem Diff (Golden Samples) reviewed werden
- Style-Guide **MUSS** mit Theme-PR synchron gehalten werden
- Deprecations **MÜSSEN** mindestens ein Minor-Release vor Entfernung dokumentiert sein
