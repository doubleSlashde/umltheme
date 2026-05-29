# Beispiel-Galerie & Traceability

Kuratierte Golden Samples aus [`examples/gen2/remote_testing/`](https://github.com/doubleSlashde/umltheme/tree/main/examples/gen2/remote_testing/).

## Traceability-Matrix

| Diagrammtyp         | Theme-Mechanismus                    | Golden Sample                                                                                                                                       | Style-Guide-Kapitel                                 |
| ------------------- | ------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------- |
| Sequence            | `!startsub sequence`, CSS Padding    | [`sequencemodel.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/remote_testing/sequencemodel.puml)                         | [Sequence](diagram-types/sequence.md)               |
| Sequence (Elemente) | `participant`, `actor`, …            | [`sequence.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/remote_testing/sequence.puml)                                   | [Sequence](diagram-types/sequence.md)               |
| Class               | `!startsub class`                    | [`class_model.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/remote_testing/class_model.puml)                             | [Class & Data](diagram-types/class-and-data.md)     |
| Datenmodell (ER)    | `entity`, `<<external>>`             | [`datamodel.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/remote_testing/datamodel.puml)                                 | [Class & Data](diagram-types/class-and-data.md)     |
| Use Case            | `!startsub usecase`, `rectangle`     | [`usecase.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/remote_testing/usecase.puml)                                     | [Use Case](diagram-types/use-case.md)               |
| Activity            | `!startsub activity`, swimlane       | [`activity_model.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/remote_testing/activity_model.puml)                       | [Activity](diagram-types/activity.md)               |
| Activity (Prozess)  | partition, PI-Prozess                | [`piprocess.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/remote_testing/piprocess.puml)                                 | [Activity](diagram-types/activity.md)               |
| State               | `!startsub state`                    | [`state.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/remote_testing/state.puml)                                         | [State](diagram-types/state.md)                     |
| System / C4         | Bundle + C4-Stereotypen              | [`systemmodel_with_levels.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/remote_testing/systemmodel_with_levels.puml)     | [System & C4](diagram-types/system-c4.md)           |
| System (L1/L2)      | `puml-theme-gen2-system`             | [`systemmodel.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/remote_testing/systemmodel.puml)                             | [System & C4](diagram-types/system-c4.md)           |
| Gantt               | `<style> ganttDiagram` + Bundle      | [`gantt.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/remote_testing/gantt.puml)                                         | [Gantt](diagram-types/gantt.md)                     |
| Projektplan         | Gantt Bundle                         | [`projectplan.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/remote_testing/projectplan.puml)                             | [Gantt](diagram-types/gantt.md)                     |
| Mindmap             | `<style> mindmapDiagram` (hardcoded) | [`mindmap.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/remote_testing/mindmap.puml)                                     | [Mindmap & WBS](diagram-types/mindmap-wbs.md)       |
| WBS                 | `<style> wbsDiagram` (hardcoded)     | [`wbs.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/remote_testing/wbs.puml)                                             | [Mindmap & WBS](diagram-types/mindmap-wbs.md)       |
| Deployment          | `component`, `node`, …               | [`deployment.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/remote_testing/deployment.puml)                               | [Deployment](diagram-types/deployment-component.md) |
| nwdiag              | `<style> nwdiagDiagram`              | [`nwdiag.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/remote_testing/nwdiag.puml)                                       | [Data & Misc](diagram-types/data-and-misc.md)       |
| JSON                | Global defaults                      | [`json.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/remote_testing/json.puml)                                           | [Data & Misc](diagram-types/data-and-misc.md)       |
| YAML                | Global defaults                      | [`yaml.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/remote_testing/yaml.puml)                                           | [Data & Misc](diagram-types/data-and-misc.md)       |
| Timing              | Global defaults                      | [`timing.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/remote_testing/timing.puml)                                       | [Data & Misc](diagram-types/data-and-misc.md)       |
| Object              | `!startsub object`                   | [`object.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/remote_testing/object.puml)                                       | [Data & Misc](diagram-types/data-and-misc.md)       |
| SWEP Datamodel      | Class + rectangle                    | [`softwarefactory_datamodel.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/remote_testing/softwarefactory_datamodel.puml) | [Class & Data](diagram-types/class-and-data.md)     |

## Light / Dark — zentrale Beispiele

### Sequence

=== "Light"

    ```text
    --8<-- "_snippets/style-guide/do-theme-include.puml"
    ```

=== "Dark"

    ```text
    @startuml
    !include https://raw.githubusercontent.com/doubleSlashde/umltheme/main/doubleslash/dark.puml
    participant A
    participant B
    A -> B : request
    @enduml
    ```

### Class

=== "Light"

    ```text
    --8<-- "_snippets/style-guide/template-light.puml"
    ```

=== "Dark"

    ```text
    --8<-- "_snippets/style-guide/template-dark.puml"
    ```

### System / C4

=== "Light"

    ```text
    --8<-- "_snippets/style-guide/c4-levels.puml"
    ```

=== "Dark"

    ```text
    --8<-- "_snippets/style-guide/template-system-dark.puml"
    ```

### Activity

=== "Light"

    ```text
    @startuml
    !include https://raw.githubusercontent.com/doubleSlashde/umltheme/main/doubleslash/light.puml
    start
    :Activity;
    stop
    @enduml
    ```

=== "Dark"

    ```text
    @startuml
    !include https://raw.githubusercontent.com/doubleSlashde/umltheme/main/doubleslash/dark.puml
    start
    :Activity;
    stop
    @enduml
    ```

### Mindmap

=== "Light"

    ```text
    @startmindmap
    !include https://raw.githubusercontent.com/doubleSlashde/umltheme/main/doubleslash/light.puml
    * Root
    ** Branch
    @endmindmap
    ```

=== "Dark (eingeschränkt)"

    !!! warning
        Mindmap `<style>` nutzt hardcoded Light-Farben — Dark-Rendering weicht ab.
        Siehe [Mindmap & WBS](diagram-types/mindmap-wbs.md).

## Lokale vs. Remote Includes

| Ordner                                                                                                | Include-Stil                           |
| ----------------------------------------------------------------------------------------------------- | -------------------------------------- |
| [`local_testing/`](https://github.com/doubleSlashde/umltheme/tree/main/examples/gen2/local_testing)   | Relative Pfade `../../doubleslash/...` |
| [`remote_testing/`](https://github.com/doubleSlashde/umltheme/tree/main/examples/gen2/remote_testing) | GitHub raw URLs                        |

## Weitere Kataloge

Narrated Beispiele: [`examples/input/`](https://github.com/doubleSlashde/umltheme/tree/main/examples/input) — siehe [Examples](../examples.md)
