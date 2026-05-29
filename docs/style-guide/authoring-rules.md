# Autoren-Regeln

Normative Vorgaben für Autoren von `.puml`-Diagrammen in Projekten mit doubleSlash Gen2 Theme.

## Notation & Benennung

### Element-Namen

| Element            | Konvention                       | Beispiel                         |
| ------------------ | -------------------------------- | -------------------------------- |
| Klassen, Services  | PascalCase                       | `OrderService`, `PaymentGateway` |
| Use Cases          | Sentence case in Klammern        | `(Place order)`                  |
| Aktoren            | Klartext, ggf. Anführungszeichen | `Actor "Customer"`               |
| Packages / Systeme | Klartext                         | `rectangle "Online Shop"`        |

### Titel-Format

**Soll:** `[Projekt] — [Diagrammtyp]: [Subject]`

```txt
title [Shop] — Sequence: Checkout Flow
title [ERP] — Datenmodell: Auftragsverwaltung
```

### Sprache

| Kontext                               | Empfehlung                          |
| ------------------------------------- | ----------------------------------- |
| Architektur-Diagramme in DE-Projekten | Deutsch (Labels, Titel, Notes)      |
| Code-Artefakte                        | Englisch (Klassennamen, Dateinamen) |
| PUML-Kommentare                       | Englisch (Repo-Konvention)          |

## Struktur einer `.puml`-Datei

```txt
@startuml eindeutiger-name
!include .../doubleslash/doubleslash-gen2.puml   ' oder light/dark/system/gantt
title [Projekt] — [Typ]: [Subject]
' Diagramminhalt
@enduml
```

## Do / Don't-Galerie

### 1. Theme-Include statt Inline-skinparam

=== "✅ Do"

    ```text
    --8<-- "_snippets/style-guide/do-theme-include.puml"
    ```

=== "❌ Don't"

    ```text
    --8<-- "_snippets/style-guide/dont-hardcoded-hex.puml"
    ```

### 2. Stereotyp statt manueller Farbe

=== "✅ Do"

    ```text
    --8<-- "_snippets/style-guide/do-stereotype-vs-hex.puml"
    ```

=== "❌ Don't"

    ```text
    --8<-- "_snippets/style-guide/dont-hardcoded-hex.puml"
    ```

### 3. Gen2 statt Legacy-Theme

=== "✅ Do"

    ```txt
    !include .../doubleslash/doubleslash-gen2.puml
    ```

=== "❌ Don't"

    ```text
    --8<-- "_snippets/style-guide/dont-legacy-theme.puml"
    ```

### 4. Konsistenter Modus

=== "✅ Do"

    ```txt
    !include .../doubleslash/dark.puml
    ```

=== "❌ Don't"

    ```text
    --8<-- "_snippets/style-guide/dont-mixed-includes.puml"
    ```

### 5. CSS-Padding (PlantUML ≥ 1.2026.3)

=== "✅ Do"

    ```text
    --8<-- "_snippets/style-guide/do-css-style-block.puml"
    ```

=== "❌ Don't"

    ```text
    skinparam ParticipantPadding 200
    skinparam Padding 99
    ```

### 6. Externe Systeme kennzeichnen

=== "✅ Do"

    ```text
    --8<-- "_snippets/style-guide/sequence-participant-external.puml"
    ```

=== "❌ Don't"

    ```text
    participant "Legacy" #CCCCCC
    ```

### 7. System-Bundle für C4

=== "✅ Do"

    ```text
    --8<-- "_snippets/style-guide/template-system.puml"
    ```

=== "❌ Don't"

    ```text
    !include .../doubleslash-gen2.puml
    skinparam RectangleBorderColor red
    ```

### 8. Gantt-Doppel-Include

=== "✅ Do"

    ```text
    --8<-- "_snippets/style-guide/template-gantt.puml"
    ```

=== "❌ Don't"

    ```txt
    @startgantt
    !include .../pgantt-theme-doubleslash.puml
    @endgantt
    ```

### 9. Keine überladenen Diagramme

=== "✅ Do"

    Fokussiertes Sequenzdiagramm mit 4–6 Participant, gruppiert mit `==`

=== "❌ Don't"

    20+ Participant ohne Gruppierung, Inline-Farben pro Nachricht

### 10. Semantik über Theme-Prozeduren

=== "✅ Do"

    ```text
    note right: $success(Completed) $failure(Failed)
    ```

=== "❌ Don't"

    ```text
    note right: <color:#00FF00>Completed</color>
    ```

### 11. Keine Schattierung aktivieren

=== "✅ Do"

    Theme-Default (`shadowing false`)

=== "❌ Don't"

    ```text
    skinparam shadowing true
    ```

### 12. Titel über Theme, nicht inline formatieren

=== "✅ Do"

    ```txt
    title [Project] — Class: Domain Model
    ```

=== "❌ Don't"

    ```txt
    title <size:40><color:red>Huge Red Title</color></size>
    ```

## Autor-Lokal: Wann erlaubt?

| Erlaubt (mit Begründung)         | Verboten                        |
| -------------------------------- | ------------------------------- |
| `left to right direction`        | Hardcoded Hex-Farben            |
| `hide stereotype`, `hide circle` | Globale `skinparam`-Overrides   |
| `top to bottom direction`        | Legacy-Theme-URLs               |
| Diagramm-spezifisches Layout     | Mix light + dark Includes       |
| `!pragma` für Einzelfall-Layout  | Duplizieren von Theme-Molekülen |

## Siehe auch

- [Design Tokens](design-tokens.md)
- [Globale Defaults](global-defaults.md)
- [Anti-Patterns](anti-patterns.md)
