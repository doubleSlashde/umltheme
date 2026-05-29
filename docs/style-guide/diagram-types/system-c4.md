# System- & C4-Diagramme

**Organismus:** C4-Stereotypen, System-Bundle, orthogonales Layout.

**Golden Samples:**

- [`systemmodel.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/remote_testing/systemmodel.puml)
- [`systemmodel_with_levels.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/remote_testing/systemmodel_with_levels.puml)

## C4-Stereotypen

| Stereotyp       | Hintergrund-Token                 | Rahmen              |
| --------------- | --------------------------------- | ------------------- |
| `<<context>>`   | `$CONTEXT_BG`                     | `$DS_BLUE`          |
| `<<container>>` | `$CONTAINER_BG`                   | none                |
| `<<component>>` | `$COMPONENT_BG`                   | none                |
| `<<module>>`    | `$MODULE_BG`                      | none                |
| `<<code>>`      | `$CODE_BG`                        | none, Text `$WHITE` |
| `<<external>>`  | `$SUPERLIGHTGREY` (agent/class/…) | variiert            |

### [SG-42] C4-Verschachtelung

**Regel:** C4-Ebenen **SOLLTEN** als verschachtelte `rectangle`-Blöcke mit passendem Stereotyp modelliert werden.

=== "✅ Empfohlen"

    ```text
    --8<-- "_snippets/style-guide/c4-levels.puml"
    ```

### [SG-43] Externe Agenten

**Regel:** Externe Systeme **MÜSSEN** `agent`/`database`/`interface` mit `<<external>>` kennzeichnen.

## Layout

### [SG-44] Orthogonale Verbindungen

**Regel:** Systemdiagramme **SOLLTEN** orthogonale Linien nutzen (`Linetype ortho`, `!pragma layout smetana`).

## Light / Dark

=== "Light"

    ```text
    --8<-- "_snippets/style-guide/template-system.puml"
    ```

=== "Dark"

    ```text
    --8<-- "_snippets/style-guide/template-system-dark.puml"
    ```
