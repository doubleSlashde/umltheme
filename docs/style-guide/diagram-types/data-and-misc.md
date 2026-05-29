# JSON, YAML, nwdiag & weitere Typen

Ergänzende Diagrammtypen mit Gen2-Styling oder Theme-Defaults.

## Übersicht

| Typ    | Mechanismus             | Golden Sample                                                                                                 | Status |
| ------ | ----------------------- | ------------------------------------------------------------------------------------------------------------- | ------ |
| JSON   | Globale Defaults        | [`json.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/remote_testing/json.puml)     | ✅     |
| YAML   | Globale Defaults        | [`yaml.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/remote_testing/yaml.puml)     | ✅     |
| nwdiag | `<style> nwdiagDiagram` | [`nwdiag.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/remote_testing/nwdiag.puml) | ✅     |
| Timing | Globale Defaults        | [`timing.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/remote_testing/timing.puml) | ✅     |
| Object | `!startsub object`      | [`object.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/remote_testing/object.puml) | ✅     |

## Hinweis zu nicht gestylten Typen

Salt, Ditaa, Math, Graphviz und reine Icon-Diagramme nutzen Globals (Schrift, Hintergrund), haben aber **keine** dedizierten Organismen im Theme. Autoren **SOLLTEN** diese Typen sparsam einsetzen und keine Inline-Farben setzen.
