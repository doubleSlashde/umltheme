# Deployment & Component

**Organismus:** `!startsub component`, `node`, `cloud`, `artifact`, `deployment`.

**Golden Sample:** [`deployment.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/remote_testing/deployment.puml)

## Element-Styling

| Element     | Hintergrund     | Rahmen                  | Besonderheit          |
| ----------- | --------------- | ----------------------- | --------------------- |
| `component` | `$DS_LIGHTBLUE` | `$DS_BLUE`, Thickness 0 | Standard              |
| `node`      | `$PUML_BGCOLOR` | `$LIGHT`                | Deployment-Knoten     |
| `cloud`     | transparent     | `$DARK`                 | Keine Füllung         |
| `artifact`  | `$DARK_BG`      | `$DARK_DARK`            | Dunkler Kasten        |
| `storage`   | `$WARNING_BG`   | `$WARNING_DARK`         | Semantik Orange       |
| `database`  | `$DS_LIGHTBLUE` | Thickness 0             | `<<external>>` → grau |

### [SG-51] Externe Interfaces

**Regel:** Externe Interfaces **MÜSSEN** `<<external>>`.
