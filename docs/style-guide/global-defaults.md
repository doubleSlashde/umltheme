# Globale Defaults

Globale Regeln gelten **diagrammunabhängig** für alle `@start…`-Typen. Sie bilden die gemeinsame visuelle Basis, bevor diagrammspezifische Regeln greifen.

Die Werte werden über den globalen CSS-Style-Selektor `element` (bzw. `root` für Canvas-weite Vorgaben) gesetzt — analog zur [PlantUML CSS-Style-Spezifikation](https://plantuml.com/de/style). Farb- und Modus-Token sind in [Design Tokens](design-tokens.md) definiert; hier steht, **welche Eigenschaften global gelten** und **welcher Soll-Wert** verbindlich ist.

<!-- prettier-ignore-start -->

!!! note "Abgrenzung"
    Diagrammtyp-spezifische Abweichungen (z. B. Gantt-Eckenradius, Sequence-Padding) gehören auf die jeweilige [Diagrammtyp-Seite](diagram-types/sequence.md) — nicht in diese Tabelle.

<!-- prettier-ignore-end -->

## Globale Werte

### Hintergrund

| Eigenschaft                               | Soll-Wert (Light)            | Soll-Wert (Dark)           | Geltung                                                                 |
| ----------------------------------------- | ---------------------------- | -------------------------- | ----------------------------------------------------------------------- |
| **BackGroundColor** (Canvas / Export)     | White · `#FFFFFF`            | Dark Canvas · `#15202B`    | Gerendertes Diagrammbild; undurchsichtiger Hintergrund für MkDocs/PDF   |
| **BackGroundColor** (Standard-Elemente)   | Blau-Tint · `#D7E9F4`        | Dark Blau-Grau · `#22303C` | Formen, Participants, States, Activities — sofern kein Stereotyp greift |
| **BackGroundColor** (Container / Gruppen) | Super Light Grey · `#F8F8F8` | Dark Surface · `#2D2D2D`   | Groups, Swimlane-Header, Reference-Boxen                                |
| **BackGroundColor** (Interface-Stereotyp) | Primary Cyan · `#00A5E1`     | Primary Cyan · `#00A5E1`   | `interface`-Stereotyp — modusunabhängig                                 |
| **BackGroundColor** (Legende, Notes)      | transparent                  | transparent                | Keine Füllfläche; nur Text und ggf. Rahmen                              |

### Linien

| Eigenschaft                          | Soll-Wert (Light)           | Soll-Wert (Dark)        | Geltung                                                                                        |
| ------------------------------------ | --------------------------- | ----------------------- | ---------------------------------------------------------------------------------------------- |
| **LineColor** (Pfeile, Verbindungen) | Medium Grey · `#7A7A7A`     | Medium Grey · `#7A7A7A` | Standard-Pfeile, Activity-Kanten, Assoziationen                                                |
| **LineColor** (Element-Rahmen)       | Deep Ocean Blue · `#00759E` | Bright Sky · `#77DDFF`  | Primary / Markenblau — Rahmen von Class, State, Activity, Component, Participant               |
| **LineThickness** (Element-Rahmen)   | **1**                       | **1**                   | Standard-Rahmenstärke                                                                          |
| **LineThickness** (Interface-Rahmen) | **2**                       | **2**                   | Interface-Stereotyp — visuell hervorgehoben                                                    |
| **LineThickness** (Pfeile)           | **1.5**                     | **1.5**                 | Standard-Pfeilstärke (`ArrowThickness`)                                                        |
| **LineStyle**                        | **solid**                   | **solid**               | Keine gestrichelten Standard-Kanten; gestrichelt nur semantisch (z. B. Abhängigkeit, optional) |

### Schrift

| Eigenschaft                       | Soll-Wert                                                                  | Geltung                                                |
| --------------------------------- | -------------------------------------------------------------------------- | ------------------------------------------------------ |
| **FontName**                      | **Helvetica**                                                              | Alle Diagrammtexte                                     |
| **FontSize** (Body)               | **12 pt**                                                                  | Standard-Labels, Attribute, Fließtext                  |
| **FontSize** (Titel)              | **28 pt**                                                                  | Diagrammtitel (`skinparam title`)                      |
| **FontSize** (Notes)              | **11 pt**                                                                  | Notes, Caption, Footer, Stereotyp-Labels               |
| **FontSize** (Pfeilbeschriftung)  | **11 pt**                                                                  | Beschriftungen an Pfeilen und Kanten (`ArrowFontSize`) |
| **FontColor** (Body)              | Default / Darkmode Text · Light Black `#000000` · Dark Blau-Tint `#D7E9F4` | Standard-Fließtext, Legende, Caption, Footer           |
| **FontColor** (Pfeilbeschriftung) | wie Body (`ArrowFontColor`)                                                | Beschriftungen an Pfeilen und Kanten                   |
| **FontColor** (Stereotyp-Label)   | wie Body (`StereotypeFontColor`)                                           | Stereotyp-Text in Klammern                             |
| **FontColor** (Element-Labels)    | Element-Labels · Light Black `#000000` · Dark Blau-Tint `#D7E9F4`          | Beschriftungen auf farbigen Formen                     |
| **FontStyle** (Body)              | **normal**                                                                 | Kein Bold in Fließtext, Notes oder Attributen          |
| **FontStyle** (Titel)             | **normal** (nicht bold)                                                    | Diagrammtitel                                          |

Diagrammtyp-spezifische Schriftgrößen (z. B. Class-Header, Swimlanes, Sequence-Divider): jeweilige [Diagrammtyp-Seite](diagram-types/sequence.md). Token-Name `$FONTNAME`: [Typografie in Design Tokens](design-tokens.md#typografie).

### Schatten

| Eigenschaft   | Soll-Wert           | Geltung                        |
| ------------- | ------------------- | ------------------------------ |
| **Shadowing** | **0** (deaktiviert) | Alle Elemente — keine Schatten |

### Eckenradius

| Eigenschaft                   | Soll-Wert | Geltung                                                             |
| ----------------------------- | --------- | ------------------------------------------------------------------- |
| **RoundCorner**               | **16**    | Alle abgerundeten Elemente (Class, State, Activity, Participant, …) |
| **BorderRoundCorner** (Titel) | **16**    | Diagrammtitel (`skinparam title`)                                   |

Ausnahme Gantt: **6** — siehe [Gantt](diagram-types/gantt.md).

### Padding & Margins

| Eigenschaft            | Soll-Wert | Geltung                                                        |
| ---------------------- | --------- | -------------------------------------------------------------- |
| **Padding** (Elemente) | **4**     | Innenabstand aller Standard-Elemente (`$PUML_ELEMENT_PADDING`) |

Sequence-Abstände: [Sequence-Diagramme](diagram-types/sequence.md#css-soll-participant-abstand).

### Ausrichtung

| Eigenschaft                     | Soll-Wert  | Geltung                                                      |
| ------------------------------- | ---------- | ------------------------------------------------------------ |
| **DefaultTextAlignment**        | **center** | Standard-Labels in Formen (`skinparam DefaultTextAlignment`) |
| **HorizontalAlignment** (Notes) | **left**   | Anmerkungen (`skinparam note` · `TextAlignment left`)        |

### Richtung & Layout-Logik

| Aspekt                      | Soll-Wert               | Geltung                                                                                           |
| --------------------------- | ----------------------- | ------------------------------------------------------------------------------------------------- |
| **Leserichtung** (Standard) | **top to bottom**       | Diagrammfluss, sofern der Typ keine andere Richtung vorschreibt                                   |
| **Linetype** (Soll)         | **polyline**            | Standard-Kantenführung für Autoren                                                                |
| **Layout-Engine** (Soll)    | _(kein globaler Zwang)_ | Orthogonale Linien und `!pragma layout smetana` nur für [System & C4](diagram-types/system-c4.md) |

Autoren **DÜRFEN** `left to right direction` lokal setzen, wenn der Diagrammtyp es empfiehlt (z. B. Use Case).

### Stereotyp-Badges (Buchstaben C / A / I / E / N)

PlantUML-Klassifikations-Buchstaben — global über `skinparam stereotype` (semantische Hintergrund-/Rahmen-Token):

| Buchstabe | Rolle (PlantUML) | Semantik         |
| --------- | ---------------- | ---------------- |
| **C**     | class            | Secondary        |
| **A**     | abstract         | Success (Valid)  |
| **I**     | interface        | Danger (Invalid) |
| **E**     | enum             | Warning (Orange) |
| **N**     | notes            | Info (Primary)   |

Abgeleitete Token (`$SECONDARY_LIGHT`, `$SUCCESS_LIGHT`, …): [Design Tokens — Übersicht](design-tokens.md#ubersicht).

### Rendering & Engine

| Eigenschaft         | Soll-Wert  | Geltung                                                            |
| ------------------- | ---------- | ------------------------------------------------------------------ |
| **BackgroundColor** | wie Canvas | Export-Hintergrund (`skinparam BackgroundColor` · `$PUML_BGCOLOR`) |
| **useBetaStyle**    | **false**  | CSS-Style-Pfad statt PlantUML-Beta-Styling                         |
| **dpi**             | **100**    | Export-Auflösung gerendertes Bild                                  |
| **Shadowing**       | **false**  | Entspricht [Schatten](#schatten)                                   |

### Titel & Meta-Elemente

Farben und Schriftgrößen der Meta-Elemente folgen den Tabellen [Schrift](#schrift) und [Hintergrund](#hintergrund), sofern nicht anders angegeben.

| Element              | Eigenschaft                | Soll-Wert                                                                                        |
| -------------------- | -------------------------- | ------------------------------------------------------------------------------------------------ |
| **Diagrammtitel**    | FontSize / -Color / -Style | wie [Schrift](#schrift) (Titel 28 pt, Default / Darkmode Text, normal)                           |
|                      | BorderRoundCorner          | **16** — siehe [Eckenradius](#eckenradius)                                                       |
|                      | Format                     | `[Projekt] — [Diagrammtyp]: [Subject]` — siehe [Autoren-Regeln](authoring-rules.md#titel-format) |
| **Legende**          | FontColor                  | Default / Darkmode Text (wie Body)                                                               |
|                      | LineColor (Rahmen)         | Medium Grey · `#7A7A7A`                                                                          |
|                      | BackGroundColor            | transparent                                                                                      |
| **Notes**            | FontSize / -Color          | **11 pt** · Default / Darkmode Text                                                              |
|                      | BackGroundColor            | transparent                                                                                      |
|                      | HorizontalAlignment        | **left** — siehe [Ausrichtung](#ausrichtung)                                                     |
| **Caption / Footer** | FontSize / -Color          | **11 pt** · Default / Darkmode Text                                                              |
| **Stereotyp-Label**  | FontSize / -Color          | **11 pt** · Default / Darkmode Text (wie Body)                                                   |

---

## Konfiguration

Normative Regeln, die über die Default-Tabelle hinausgehen.

### Keine Schattierung

**Regel:** `Shadowing` **MUSS** `0` bleiben.
**Begründung:** Lesbarkeit, Drucktauglichkeit, CI-Richtlinie „Weniger ist mehr“.

### Export-Auflösung

**Regel:** Export **SOLL** mit **100 DPI** erfolgen (`skinparam dpi`) — siehe [Rendering & Engine](#rendering-engine).
**Begründung:** Balance zwischen Dateigröße und Schärfe für MkDocs/PDF.

### Modus & Palette

Light/Dark und Outline werden **vor** dem Theme-Laden gewählt; sie beeinflussen alle globalen Farb-Defaults. Details: [Modus-Schalter](design-tokens.md#modus-schalter).

**Siehe auch:** [Barrierefreiheit](accessibility.md) · [Design Tokens — Abstände & Form](design-tokens.md#abstande-form)
