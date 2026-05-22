# Getting started

Add a remote `!include` for the gen2 bundle you need. Replace `TAG` only if you want to pin an exact revision (omit for `main`). All URLs below assume the **upstream** repo `doubleSlashde/umltheme`.

<!-- prettier-ignore -->
!!! note "Branches & tags"
    Use `main` for bleeding edge, or a **release/tag** URL for repeatable builds:

    `https://raw.githubusercontent.com/doubleSlashde/umltheme/vX.Y.Z/doubleslash/doubleslash-gen2.puml`

!!! note "PlantUML version (padding styling)"
    From **PlantUML 1.2026.3** onward, the engine deprecates `skinparam Padding` and `skinparam ParticipantPadding` in favor of `<style>` rules. Themes in this repo follow that migration automatically: on 1.2026.3+ they emit CSS-like styles; on older builds they fall back to the previous `skinparam` settings.

    To force the legacy `skinparam` path even on a newer JAR (for debugging), set **`!$PUML_FORCE_LEGACY_PADDING = true`** in your `.puml` **before** the theme `!include`.

## Universal Gen2 theme (recommended)

Works for **most diagram types**:

```txt
!include https://raw.githubusercontent.com/doubleSlashde/umltheme/main/doubleslash/doubleslash-gen2.puml
```

## Light mode only

```txt
!include https://raw.githubusercontent.com/doubleSlashde/umltheme/main/doubleslash/light.puml
```

## Dark mode only

```txt
!include https://raw.githubusercontent.com/doubleSlashde/umltheme/main/doubleslash/dark.puml
```

## Verify locally or in CI

### Using PlantUML JAR

```sh
java -jar plantuml.jar filename.puml
```

### Using PlantUML Online

Copy your `.puml` content to [PlantUML Online Server](http://www.plantuml.com/plantuml/).

### Using IDE

VS Code (or derivate) with [PlantUML Extension](https://marketplace.visualstudio.com/items?itemName=jebbs.plantuml) recommended.

Open your `.puml` file and press <kbd>Alt</kbd>+<kbd>D</kbd> to preview the diagram.

## Example layouts in this repository

Generated examples are grouped for different workflows:

| Folder                                                                                                              | Purpose                                             |
| ------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------- |
| [`examples/gen2/remote_testing/`](https://github.com/doubleSlashde/umltheme/tree/main/examples/gen2/remote_testing) | Includes use GitHub **`raw`** URLs                  |
| [`examples/gen2/local_testing/`](https://github.com/doubleSlashde/umltheme/tree/main/examples/gen2/local_testing)   | Includes use **relative** paths into `doubleslash/` |

Browse either set on GitHub to mirror your environment.
