# Versionierung & Legacy

SemVer-Regeln und Deprecation-Pfad für doubleSlash PlantUML Themes.

## Semantic Versioning

Projekt folgt [SemVer 2.0](https://semver.org/) — siehe [CHANGELOG.md](https://github.com/doubleSlashde/umltheme/blob/main/CHANGELOG.md).

| Version   | Bedeutung                                               | Beispiel                      |
| --------- | ------------------------------------------------------- | ----------------------------- |
| **Patch** | Bugfix, Kontrast, Padding-Gate-Fix                      | 2.0.3 — CSS default fail-open |
| **Minor** | Neues Stereotyp, neuer `!startsub`, Docs                | 2.0.2 — MkDocs-Site           |
| **Major** | Token-Umbenennung, Legacy-Entfernung, Breaking Includes | 2.0.0 — Gen2-Architektur      |

## Gen2 vs. Legacy

| Generation          | Pfad                                                             | Status        |
| ------------------- | ---------------------------------------------------------------- | ------------- |
| **Gen2**            | `doubleslash/doubleslash-gen2.puml`                              | ✅ aktiv      |
| **Gen2 Light/Dark** | `doubleslash/light.puml`, `dark.puml`                            | ✅ aktiv      |
| **Gen2 Bundles**    | `puml-theme-gen2-system.puml`, `puml-theme-gen2-gantt.puml`      | ✅ aktiv      |
| **Legacy Root**     | `puml-theme-doubleslash-*.puml`, `pgantt-theme-doubleslash.puml` | ⚠️ deprecated |

### Deprecation-Pfad

1. **Jetzt:** Legacy-URLs leiten auf Gen2 um; Warnung in [Theme usage](../theme-usage.md)
2. **Minor:** Style Guide + CHANGELOG markieren deprecated URLs
3. **Major (geplant):** Redirect-Dateien entfernen; nur `doubleslash/`-Includes

## Include-Pinning

Für reproduzierbare Builds **SOLLTEN** Autoren Release-Tags pinnen:

```txt
!include https://raw.githubusercontent.com/doubleSlashde/umltheme/v2.0.3/doubleslash/doubleslash-gen2.puml
```

Bleeding edge: `main` — siehe [Getting started](../getting-started.md)

## PlantUML-Version

| PlantUML                 | Padding-Mechanismus      |
| ------------------------ | ------------------------ |
| ≥ 1.2026.3               | CSS `<style>` (Standard) |
| < 1.2026.3               | `skinparam` Fallback     |
| Unparseable `%version()` | CSS (fail-open)          |

**Changelog:** 2.0.3 — Gate-Default geändert

## Style-Guide-Versionierung

Der Style Guide wird **mit dem Theme-Repo** versioniert — kein separates SemVer.
Bei Major Theme-Releases Style Guide und Golden Samples synchron aktualisieren.
