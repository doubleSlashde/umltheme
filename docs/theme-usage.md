# Theme usage & specialized bundles

Beyond the universal gen2 bundle, specialized entry points exist for diagrams that benefit from extra tweaks.

<!-- prettier-ignore -->
!!! info "Source files"
    Theme `.puml` sources live under [`doubleslash/`](https://github.com/doubleSlashde/umltheme/tree/main/doubleslash) in this repository.

## System / C4-style diagrams

```txt
!include https://raw.githubusercontent.com/doubleSlashde/umltheme/main/doubleslash/puml-theme-gen2-system.puml
```

### Architectural levels via stereotypes

The system theme recognises stereotypes for layering:

```txt
rectangle "Online Shop System" <<context>> {
    rectangle "Web Application" <<container>> {
        rectangle "Order Management" <<component>> {
            rectangle "Order Service" <<module>> {
                rectangle "OrderController.java" <<code>>
            }
        }
    }
}
```

| Stereotype      | Typical C4 lens                  |
| --------------- | -------------------------------- |
| `<<context>>`   | System context                   |
| `<<container>>` | Containers                       |
| `<<component>>` | Components                       |
| `<<module>>`    | Modules / subsystems             |
| `<<code>>`      | Code-level artefacts             |
| `<<external>>`  | External systems / third parties |

Full sample: [`systemmodel_with_levels.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/local_testing/systemmodel_with_levels.puml) (mirror under `remote_testing/` with raw URLs).

## Gantt diagrams

Wrap with `@startgantt` … `@endgantt` and include the Gantt-oriented theme:

```txt
@startgantt
!include https://raw.githubusercontent.com/doubleSlashde/umltheme/main/doubleslash/puml-theme-gen2-gantt.puml
' ...your tasks...
@endgantt
```

## Legacy themes (deprecated)

Older per-diagram URLs under the repo root (e.g. `puml-theme-doubleslash-*.puml`, `pgantt-theme-doubleslash.puml`) still resolve but are **deprecated**—prefer gen2 URLs from [`getting-started.md`](getting-started.md).

<details>
<summary>Legacy include snippets (collapse)</summary>

### Use case

```txt
!include https://raw.githubusercontent.com/doubleSlashde/umltheme/main/puml-theme-doubleslash-usecase.puml
```

### Activity

```txt
!include https://raw.githubusercontent.com/doubleSlashde/umltheme/main/puml-theme-doubleslash-activity.puml
```

### System (C4 L1/L2 legacy)

```txt
!include https://raw.githubusercontent.com/doubleSlashde/umltheme/main/puml-theme-doubleslash-system.puml
```

### Class / ER-oriented

```txt
!include https://raw.githubusercontent.com/doubleSlashde/umltheme/main/puml-theme-doubleslash-class.puml
```

### Sequence

```txt
!include https://raw.githubusercontent.com/doubleSlashde/umltheme/main/puml-theme-doubleslash-sequence.puml
```

### Gantt legacy

```txt
@startgantt
!include https://raw.githubusercontent.com/doubleSlashde/umltheme/main/pgantt-theme-doubleslash.puml
...
@endgantt
```

### Mind map

```txt
@startmindmap
!include https://raw.githubusercontent.com/doubleSlashde/umltheme/main/puml-theme-doubleslash-mindmap.puml
...
@endmindmap
```

</details>

## Migration cheat sheet

1. Swap legacy includes for the universal gen2 line or light/dark as needed:

   ```txt
   // Old (deprecated)
   !include https://raw.githubusercontent.com/doubleSlashde/umltheme/main/puml-theme-doubleslash-[type].puml

   // New (gen2)
   !include https://raw.githubusercontent.com/doubleSlashde/umltheme/main/doubleslash/doubleslash-gen2.puml
   ```

2. Choose **light** (`doubleslash/light.puml`), **dark** (`doubleslash/dark.puml`), or **universal** (`doubleslash/doubleslash-gen2.puml`).

## Consumption from MkDocs (mkdocs_puml)

Integrate themes in **your documentation project** using [mkdocs_puml](https://github.com/MikhailKravets/mkdocs_puml):

```yaml
plugins:
  - search
  - plantuml:
      puml_url: https://www.plantuml.com/plantuml/
      theme:
        url: https://raw.githubusercontent.com/doubleSlashde/umltheme/main/
        light: doubleslash/light
        dark: doubleslash/dark
```

This uses the official PlantUML server for rendering and follows your MkDocs / Material palette for light vs dark skins.
