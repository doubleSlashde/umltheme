# Design Tokens (Atome)

Design Tokens sind die **kleinsten fest definierten Bausteine** des doubleSlash PlantUML Style Guides - vergleichbar mit den [Farben im doubleSlash Web Style Guide](https://doubleslash.style/?path=/docs/styles-colors-web--all).

Auf dieser Seite finden Sie die **Standard-Werte**, die in allen Diagrammen gelten.

<!-- prettier-ignore-start -->
!!! tip "Autoren vs. Maintainer"
    **Diagramm-Autoren** sollen Tokens und Stereotypen referenzieren - keine eigenen Hex-Werte oder `skinparam`-Overrides. **Theme-Maintainer** ändern Werte zentral im Repo und passen diese Seite an.
    Verbindliche Do/Don't-Regeln: [Autoren-Regeln](authoring-rules.md) · Implementierungsdetails: [Theme-Entwicklung](theme-development.md)
<!-- prettier-ignore-end -->

---

## Farb-Tokens

Die Farbpalette folgt dem [doubleSlash Web Style Guide – Colors](https://doubleslash.style/?path=/docs/styles-colors-web--all). Token-Namen entsprechen [`doubleslash/colors.puml`](https://github.com/doubleSlashde/umltheme/blob/main/doubleslash/colors.puml) (`$DS_CYAN`, `$TEXT_BLACK`, …).

Die meisten Farben sind **modusabhängig** (`light` / `dark`). **Primary Cyan** ist die einzige Markenfarbe und gilt in beiden Modi identisch.

Die Übersicht definiert den **verbindlichen Soll-Standard** für PlantUML-Diagramme. Tokens sind nach **Elementkategorien** gruppiert (Formen, Verbindungen, Text, Container, Diagramm-Metadaten, Semantik). Wird derselbe HEX-Wert für unterschiedliche Rollen genutzt, steht er in **eigenen Zeilen**.

### Übersicht { #ubersicht }

| Kategorie                  | Element / Rolle              | Token                                                          | Verwendung (PlantUML)                                                              | Light                                                                                                                                                                                                                                                                                     | Dark                                                                                                                                                                                                                                                                                      |
| -------------------------- | ---------------------------- | -------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Markenfarbe**            | Primary Cyan                 | `$DS_CYAN`, `$INFO`                                            | Markenidentität, Akzente, Info-Hervorhebung                                        | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#00A5E1;border-radius:2px;vertical-align:middle;"></span> `#00A5E1`                                                                                                                                               | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#00A5E1;border-radius:2px;vertical-align:middle;"></span> `#00A5E1`                                                                                                                                               |
| **Primär (Clickable)**     | Deep Ocean Blue / Bright Sky | `$DS_CLICKABLE` / `$DS_DARK_CLICKABLE`                         | Interaktive Elemente: Rahmen, Links, Buttons, Sequence-Lifeline, Group-Header      | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#00759E;border-radius:2px;vertical-align:middle;"></span> `#00759E`                                                                                                                                               | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#77DDFF;border-radius:2px;vertical-align:middle;"></span> `#77DDFF`                                                                                                                                               |
| **Formen – Rahmen**        | Primary / Markenblau         | `$DS_BLUE`, `$PRIMARY`                                         | Rahmen Class, State, Activity, Component; Start/End-State; Package-Rahmen          | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#00759E;border-radius:2px;vertical-align:middle;"></span> `#00759E`                                                                                                                                               | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#77DDFF;border-radius:2px;vertical-align:middle;"></span> `#77DDFF`                                                                                                                                               |
| **Formen – Füllung**       | Blau-Tint                    | `$DS_LIGHTBLUE`, `$SECONDARY`                                  | Hintergrund Class, State, Activity, Use Case, Component, Participant, Collections  | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#D7E9F4;border:1px solid #ccc;border-radius:2px;vertical-align:middle;"></span> `#D7E9F4`                                                                                                                         | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#22303C;border-radius:2px;vertical-align:middle;"></span> `#22303C`                                                                                                                                               |
| **Formen – Füllung**       | Interface                    | `$DS_CYAN`                                                     | Interface-Hintergrund und -Rahmen (BorderThickness 2)                              | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#00A5E1;border-radius:2px;vertical-align:middle;"></span> `#00A5E1`                                                                                                                                               | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#00A5E1;border-radius:2px;vertical-align:middle;"></span> `#00A5E1`                                                                                                                                               |
| **Formen – Füllung**       | Extern / Fremdsystem         | `$SUPERLIGHTGREY` ‡                                            | `<<external>>`, `<<External>>`: Class, Agent, Database, Participant, Use Case      | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#F8F8F8;border:1px solid #ccc;border-radius:2px;vertical-align:middle;"></span> `#F8F8F8`                                                                                                                         | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#2D2D2D;border-radius:2px;vertical-align:middle;"></span> `#2D2D2D`                                                                                                                                               |
| **Formen – Füllung**       | Actor                        | `$DS_LIGHTGREY`                                                | Use-Case-Actor-Hintergrund und -Rahmen                                             | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#C6C6C6;border-radius:2px;vertical-align:middle;"></span> `#C6C6C6`                                                                                                                                               | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#B6B6B6;border-radius:2px;vertical-align:middle;"></span> `#B6B6B6`                                                                                                                                               |
| **Formen – Füllung**       | Extern-Interface             | `$DS_GREY`                                                     | `<<external>>` Interface-Hintergrund und -Rahmen                                   | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#7A7A7A;border-radius:2px;vertical-align:middle;"></span> `#7A7A7A`                                                                                                                                               | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#7A7A7A;border-radius:2px;vertical-align:middle;"></span> `#7A7A7A`                                                                                                                                               |
| **Verbindungen**           | Pfeile & Linien              | `$DS_GREY`                                                     | `ArrowColor`, Sequence-Pfeile, Activity-Pfeile; Legenden-Rahmen; Group-/Box-Rahmen | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#7A7A7A;border-radius:2px;vertical-align:middle;"></span> `#7A7A7A`                                                                                                                                               | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#7A7A7A;border-radius:2px;vertical-align:middle;"></span> `#7A7A7A`                                                                                                                                               |
| **Verbindungen**           | Rahmen dezent                | `$DS_LIGHTGREY`                                                | Swimlane-Rahmen; Sequence-Reference-Rahmen                                         | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#C6C6C6;border-radius:2px;vertical-align:middle;"></span> `#C6C6C6`                                                                                                                                               | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#B6B6B6;border-radius:2px;vertical-align:middle;"></span> `#B6B6B6`                                                                                                                                               |
| **Text – Standard**        | Default / Darkmode Text      | `$TEXT_BLACK` / `$TEXT_DARK`, `$FGCOLOR`                       | Standard-Fließtext; Titel, Legende, Notes, Pfeilbeschriftung, Stereotyp-Labels     | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#000000;border-radius:2px;vertical-align:middle;"></span> `#000000`                                                                                                                                               | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#D7E9F4;border:1px solid #ccc;border-radius:2px;vertical-align:middle;"></span> `#D7E9F4`                                                                                                                         |
| **Text – auf Formen**      | Element-Labels               | `$BLACK`                                                       | Class-Header, Participant, Activity, State, Component, Package, Rectangle          | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#000000;border-radius:2px;vertical-align:middle;"></span> `#000000`                                                                                                                                               | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#D7E9F4;border:1px solid #ccc;border-radius:2px;vertical-align:middle;"></span> `#D7E9F4`                                                                                                                         |
| **Text – Actor**           | Actor-Label                  | `$TERTIARY_TINT` / `$TEXT_DARK_SECONDARY`                      | Use-Case-Actor-Beschriftung                                                        | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#6D6D6D;border-radius:2px;vertical-align:middle;"></span> `#6D6D6D`                                                                                                                                               | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#AFC1C7;border-radius:2px;vertical-align:middle;"></span> `#AFC1C7`                                                                                                                                               |
| **Text – Tertiary**        | Tertiary Tint / Secondary    | `$TERTIARY_TINT` / `$TEXT_DARK_SECONDARY`                      | Bullets, Subheader-Nummerierung; Sequence Box-/Delay-/Group-Font                   | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#6D6D6D;border-radius:2px;vertical-align:middle;"></span> `#6D6D6D`                                                                                                                                               | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#AFC1C7;border-radius:2px;vertical-align:middle;"></span> `#AFC1C7`                                                                                                                                               |
| **Text – Invers**          | White / Disabled             | `$TEXT_WHITE` / `$DS_DARK_DISABLED`                            | Text auf dunklem oder farbigem Hintergrund; Dark-Mode deaktivierter Text           | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#FFFFFF;border:1px solid #ccc;border-radius:2px;vertical-align:middle;"></span> `#FFFFFF`                                                                                                                         | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#84999F;border-radius:2px;vertical-align:middle;"></span> `#84999F`                                                                                                                                               |
| **Container**              | Systemgrenze                 | `$ALICEBLUE` ‡                                                 | Use-Case-System-`rectangle`, Package-Hintergrund                                   | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#F0F8FF;border:1px solid #ccc;border-radius:2px;vertical-align:middle;"></span> `#F0F8FF`                                                                                                                         | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#3A3A3A;border-radius:2px;vertical-align:middle;"></span> `#3A3A3A`                                                                                                                                               |
| **Container**              | Gruppe / Swimlane            | `$SUPERLIGHTGREY` ‡                                            | Sequence-Groups, Divider, Activity-Swimlane-Titel, Reference-Header                | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#F8F8F8;border:1px solid #ccc;border-radius:2px;vertical-align:middle;"></span> `#F8F8F8`                                                                                                                         | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#2D2D2D;border-radius:2px;vertical-align:middle;"></span> `#2D2D2D`                                                                                                                                               |
| **Container**              | Frame / Folder               | `$DS_CYAN`, `$DS_ORANGE`                                       | Rahmen- und Textfarbe für `frame` bzw. `folder` (Semantik-Hervorhebung)            | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#00A5E1;border-radius:2px;vertical-align:middle;"></span> `#00A5E1` / <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#DB6A00;border-radius:2px;vertical-align:middle;"></span> `#DB6A00` | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#00A5E1;border-radius:2px;vertical-align:middle;"></span> `#00A5E1` / <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#DB6A00;border-radius:2px;vertical-align:middle;"></span> `#DB6A00` |
| **Diagramm – Hintergrund** | Export / Canvas              | `$PUML_BGCOLOR`, `$DS_BASE_BACKGROUND` / `$DS_DARK_BACKGROUND` | Gerendeter Diagramm-Hintergrund; Sequence-Box/Group-Body; Surface Base             | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#FFFFFF;border:1px solid #ccc;border-radius:2px;vertical-align:middle;"></span> `#FFFFFF`                                                                                                                         | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#15202B;border-radius:2px;vertical-align:middle;"></span> `#15202B`                                                                                                                                               |
| **Diagramm – Metadaten**   | Titel                        | `$FGCOLOR`                                                     | `skinparam title` · FontColor                                                      | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#000000;border-radius:2px;vertical-align:middle;"></span> `#000000`                                                                                                                                               | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#D7E9F4;border:1px solid #ccc;border-radius:2px;vertical-align:middle;"></span> `#D7E9F4`                                                                                                                         |
| **Diagramm – Metadaten**   | Legende                      | `$FGCOLOR`, `$DS_GREY`                                         | Legenden-Text; Rahmen `$DS_GREY`, Hintergrund transparent                          | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#000000;border-radius:2px;vertical-align:middle;"></span> `#000000` / `#7A7A7A`                                                                                                                                   | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#D7E9F4;border:1px solid #ccc;border-radius:2px;vertical-align:middle;"></span> `#D7E9F4` / `#7A7A7A`                                                                                                             |
| **Diagramm – Metadaten**   | Notes                        | `$FGCOLOR`                                                     | Note-Text (Hintergrund transparent)                                                | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#000000;border-radius:2px;vertical-align:middle;"></span> `#000000`                                                                                                                                               | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#D7E9F4;border:1px solid #ccc;border-radius:2px;vertical-align:middle;"></span> `#D7E9F4`                                                                                                                         |
| **Semantik – Erfolg**      | Valid / Valid Dark           | `$DS_GREEN`, `$SUCCESS` / `$DS_DARK_GREEN`                     | Erfolg, positive Status, Bestätigungen                                             | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#6B9714;border-radius:2px;vertical-align:middle;"></span> `#6B9714`                                                                                                                                               | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#B9D478;border-radius:2px;vertical-align:middle;"></span> `#B9D478`                                                                                                                                               |
| **Semantik – Warnung**     | Orange                       | `$DS_ORANGE`, `$WARNING`                                       | Warnmeldungen, Storage-Semantik, Akzent                                            | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#DB6A00;border-radius:2px;vertical-align:middle;"></span> `#DB6A00`                                                                                                                                               | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#DB6A00;border-radius:2px;vertical-align:middle;"></span> `#DB6A00`                                                                                                                                               |
| **Semantik – Fehler**      | Invalid / Invalid Dark       | `$DS_RED`, `$DANGER` / `$DS_DARK_RED`                          | Fehler, negative Status, kritische Pfade                                           | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#C63328;border-radius:2px;vertical-align:middle;"></span> `#C63328`                                                                                                                                               | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#E85F63;border-radius:2px;vertical-align:middle;"></span> `#E85F63`                                                                                                                                               |
| ‡ **C4 – Context**         | Context-Ebene                | `$CONTEXT_BG`                                                  | `<<context>>` Hintergrund                                                          | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#FFFFFF;border:1px solid #ccc;border-radius:2px;vertical-align:middle;"></span> `#FFFFFF`                                                                                                                         | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#2A2A2A;border-radius:2px;vertical-align:middle;"></span> `#2A2A2A`                                                                                                                                               |
| ‡ **C4 – Container**       | Container-Ebene              | `$CONTAINER_BG`                                                | `<<container>>` Hintergrund                                                        | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#EEF8FE;border:1px solid #ccc;border-radius:2px;vertical-align:middle;"></span> `#EEF8FE`                                                                                                                         | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#353535;border-radius:2px;vertical-align:middle;"></span> `#353535`                                                                                                                                               |
| ‡ **C4 – Component**       | Component-Ebene              | `$COMPONENT_BG`                                                | `<<component>>` Hintergrund (gleicher HEX wie Form-Füllung Light)                  | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#D7E9F4;border:1px solid #ccc;border-radius:2px;vertical-align:middle;"></span> `#D7E9F4`                                                                                                                         | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#404040;border-radius:2px;vertical-align:middle;"></span> `#404040`                                                                                                                                               |
| ‡ **C4 – Module**          | Module-Ebene                 | `$MODULE_BG`                                                   | `<<module>>` Hintergrund (gleicher HEX wie Text Tertiary Dark)                     | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#AFC1C7;border-radius:2px;vertical-align:middle;"></span> `#AFC1C7`                                                                                                                                               | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#4A4A4A;border-radius:2px;vertical-align:middle;"></span> `#4A4A4A`                                                                                                                                               |
| ‡ **C4 – Code**            | Code-Ebene                   | `$CODE_BG`                                                     | `<<code>>` Hintergrund (gleicher HEX wie Text Disabled Dark)                       | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#84999F;border-radius:2px;vertical-align:middle;"></span> `#84999F`                                                                                                                                               | <span style="display:inline-block;width:1.1rem;height:1.1rem;background:#555555;border-radius:2px;vertical-align:middle;"></span> `#555555`                                                                                                                                               |

‡ **Nicht im doubleSlash Living Style Guide (Web-CI)** – PlantUML-spezifische Erweiterung.

**Typografie** (Schriftart/-größe, kein Farb-Token): siehe Abschnitt [Typografie](#typografie) – u. a. `$FONTNAME` (`Helvetica`), Body 12 pt, Titel 28 pt, Notes 11 pt, Class-Header 15 pt bold.

### Farbdefinitionen

Detailierte Beschreibungen zu den Farben aus der [Übersicht](#ubersicht).

<div class="ds-color-grid">

<article class="ds-color-card">
  <div class="ds-color-card__swatch" style="background:#00A5E1"></div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Primary Cyan</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$DS_CYAN</code>, <code>$INFO</code></dd>
      <dt>HEX</dt>
      <dd><code>#00A5E1</code></dd>
      <dt>Verwendung</dt>
      <dd>Markenidentität, Interface-Füllung, Frame-Rahmen, Info-Hervorhebung</dd>
    </dl>
    <p class="ds-color-card__desc">Zentrale Markenfarbe der doubleSlash Corporate Identity – modusunabhängig.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch" style="background:#00759E"></div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Deep Ocean Blue</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$DS_CLICKABLE</code>, <code>$DS_BLUE</code>, <code>$PRIMARY</code></dd>
      <dt>HEX</dt>
      <dd><code>#00759E</code></dd>
      <dt>Verwendung</dt>
      <dd>Interaktive Elemente, Form-Rahmen, Links, Sequence-Lifeline</dd>
    </dl>
    <p class="ds-color-card__desc">Kräftiges Ozeanblau für klickbare Elemente und Primary-Rahmen.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch" style="background:#77DDFF"></div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Bright Sky</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$DS_DARK_CLICKABLE</code>, <code>$DS_BLUE</code>, <code>$PRIMARY</code></dd>
      <dt>HEX</dt>
      <dd><code>#77DDFF</code></dd>
      <dt>Verwendung</dt>
      <dd>Interaktive Elemente, Form-Rahmen, Links, Sequence-Lifeline</dd>
    </dl>
    <p class="ds-color-card__desc">Helles Himmelblau – Primary- und Clickable-Variante auf dunklem Hintergrund.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch ds-color-card__swatch--bordered" style="background:#D7E9F4"></div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Blau-Tint</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$DS_LIGHTBLUE</code>, <code>$SECONDARY</code>, <code>$TEXT_DARK</code>, <code>$FGCOLOR</code>, <code>$BLACK</code>, <code>$COMPONENT_BG</code> ‡</dd>
      <dt>HEX</dt>
      <dd><code>#D7E9F4</code></dd>
      <dt>Verwendung</dt>
      <dd>Form-Füllung, Standard-Text, Element-Labels, C4-Component-Hintergrund</dd>
    </dl>
    <p class="ds-color-card__desc">Helles Blau-Grau – häufigste Flächen- und Textfarbe in der Palette.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch" style="background:#22303C"></div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Dark Blau-Grau</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$DS_LIGHTBLUE</code>, <code>$SECONDARY</code>, <code>$DARK_GRADIENT1</code>, <code>$DS_DARK_CONTAINER</code></dd>
      <dt>HEX</dt>
      <dd><code>#22303C</code></dd>
      <dt>Verwendung</dt>
      <dd>Form-Füllung, Container-Hintergrund, Gradient</dd>
    </dl>
    <p class="ds-color-card__desc">Dunkle Blau-Grau-Fläche für Formen und Container auf dunklem Canvas.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch ds-color-card__swatch--bordered" style="background:#EEF8FE"></div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Container Tint</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$CONTAINER_BG</code> ‡</dd>
      <dt>HEX</dt>
      <dd><code>#EEF8FE</code></dd>
      <dt>Verwendung</dt>
      <dd><code>&lt;&lt;container&gt;&gt;</code> Hintergrund</dd>
    </dl>
    <p class="ds-color-card__desc">Leicht bläuliche Fläche für C4-Container-Ebene.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch ds-color-card__swatch--bordered" style="background:#F0F8FF"></div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Alice Blue</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$ALICEBLUE</code> ‡</dd>
      <dt>HEX</dt>
      <dd><code>#F0F8FF</code></dd>
      <dt>Verwendung</dt>
      <dd>Use-Case-System-<code>rectangle</code>, Package-Hintergrund</dd>
    </dl>
    <p class="ds-color-card__desc">Sehr helles Blau für Systemgrenzen und Packages.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch ds-color-card__swatch--bordered" style="background:#FFFFFF"></div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">White</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$TEXT_WHITE</code>, <code>$DS_BASE_BACKGROUND</code>, <code>$PUML_BGCOLOR</code>, <code>$CONTEXT_BG</code> ‡</dd>
      <dt>HEX</dt>
      <dd><code>#FFFFFF</code></dd>
      <dt>Verwendung</dt>
      <dd>Inverse Textfarbe, Canvas, Export-Hintergrund, C4-Context</dd>
    </dl>
    <p class="ds-color-card__desc">Reines Weiß – Canvas-Grundfläche und helle Container-Ebene.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch ds-color-card__swatch--bordered" style="background:#F8F8F8"></div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Super Light Grey</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$SUPERLIGHTGREY</code> ‡</dd>
      <dt>HEX</dt>
      <dd><code>#F8F8F8</code></dd>
      <dt>Verwendung</dt>
      <dd><code>&lt;&lt;external&gt;&gt;</code>, Sequence-Groups, Swimlanes, Reference-Header</dd>
    </dl>
    <p class="ds-color-card__desc">Fast weiße Grautönung für externe Elemente und Gruppierungen.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch" style="background:#C6C6C6"></div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Light Grey</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$DS_LIGHTGREY</code>, <code>$DISABLED_GREY</code></dd>
      <dt>HEX</dt>
      <dd><code>#C6C6C6</code></dd>
      <dt>Verwendung</dt>
      <dd>Use-Case-Actor, dezente Rahmen, Swimlane-Rahmen</dd>
    </dl>
    <p class="ds-color-card__desc">Helles Neutralgrau für Akteure und zurückhaltende Rahmen.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch" style="background:#B6B6B6"></div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Medium Light Grey</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$DS_LIGHTGREY</code></dd>
      <dt>HEX</dt>
      <dd><code>#B6B6B6</code></dd>
      <dt>Verwendung</dt>
      <dd>Use-Case-Actor, dezente Rahmen, Swimlane-Rahmen</dd>
    </dl>
    <p class="ds-color-card__desc">Mittleres Hellgrau – Akteur- und Rahmenvariante auf dunklem Canvas.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch" style="background:#7A7A7A"></div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Medium Grey</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$DS_GREY</code></dd>
      <dt>HEX</dt>
      <dd><code>#7A7A7A</code></dd>
      <dt>Verwendung</dt>
      <dd>Pfeile, Legenden-Rahmen, Extern-Interface, Group-/Box-Rahmen</dd>
    </dl>
    <p class="ds-color-card__desc">Modusunabhängiges Mittelgrau für Verbindungen und neutrale Interfaces.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch" style="background:#6D6D6D"></div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Tertiary Tint</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$TERTIARY_TINT</code></dd>
      <dt>HEX</dt>
      <dd><code>#6D6D6D</code></dd>
      <dt>Verwendung</dt>
      <dd>Actor-Label, Bullets, Subheader, Sequence Box-/Delay-/Group-Font</dd>
    </dl>
    <p class="ds-color-card__desc">Gedämpftes Grau für untergeordnete und ergänzende Beschriftungen.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch" style="background:#AFC1C7"></div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Secondary Tint</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$TEXT_DARK_SECONDARY</code>, <code>$TERTIARY_TINT</code>, <code>$MODULE_BG</code> ‡</dd>
      <dt>HEX</dt>
      <dd><code>#AFC1C7</code></dd>
      <dt>Verwendung</dt>
      <dd>Tertiärer Text, C4-Module-Hintergrund</dd>
    </dl>
    <p class="ds-color-card__desc">Blau-graues Sekundärgrau für Text und C4-Module-Ebene.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch" style="background:#84999F"></div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Disabled Grey</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$DS_DARK_DISABLED</code>, <code>$CODE_BG</code> ‡</dd>
      <dt>HEX</dt>
      <dd><code>#84999F</code></dd>
      <dt>Verwendung</dt>
      <dd>Deaktivierter Text, C4-Code-Hintergrund</dd>
    </dl>
    <p class="ds-color-card__desc">Gedämpftes Blau-Grau für inaktive Zustände und C4-Code-Ebene.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch" style="background:#000000"></div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Black</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$TEXT_BLACK</code>, <code>$BLACK</code>, <code>$FGCOLOR</code></dd>
      <dt>HEX</dt>
      <dd><code>#000000</code></dd>
      <dt>Verwendung</dt>
      <dd>Standard-Text, Element-Labels, Titel, Legende, Notes, Pfeilbeschriftung</dd>
    </dl>
    <p class="ds-color-card__desc">Maximaler Kontrast für Fließtext und Beschriftungen auf hellen Flächen.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch" style="background:#15202B"></div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Dark Canvas</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$DS_DARK_BACKGROUND</code>, <code>$PUML_BGCOLOR</code>, <code>$DARK_GRADIENT2</code></dd>
      <dt>HEX</dt>
      <dd><code>#15202B</code></dd>
      <dt>Verwendung</dt>
      <dd>Export-Hintergrund, Canvas, Sequence-Box/Group-Body</dd>
    </dl>
    <p class="ds-color-card__desc">Dunkelblaues Schwarz – Grundfläche für Dark-Mode-Diagramme.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch" style="background:#2D2D2D"></div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Dark Surface</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$SUPERLIGHTGREY</code> ‡</dd>
      <dt>HEX</dt>
      <dd><code>#2D2D2D</code></dd>
      <dt>Verwendung</dt>
      <dd><code>&lt;&lt;external&gt;&gt;</code>, Sequence-Groups, Swimlanes, Reference-Header</dd>
    </dl>
    <p class="ds-color-card__desc">Dunkle Oberfläche für externe Elemente und Gruppierungen.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch" style="background:#3A3A3A"></div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Dark Surface Alt</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$ALICEBLUE</code> ‡</dd>
      <dt>HEX</dt>
      <dd><code>#3A3A3A</code></dd>
      <dt>Verwendung</dt>
      <dd>Use-Case-System-<code>rectangle</code>, Package-Hintergrund</dd>
    </dl>
    <p class="ds-color-card__desc">Alternative dunkle Fläche für Systemgrenzen und Packages.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch" style="background:#2A2A2A"></div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">C4 Context</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$CONTEXT_BG</code> ‡</dd>
      <dt>HEX</dt>
      <dd><code>#2A2A2A</code></dd>
      <dt>Verwendung</dt>
      <dd><code>&lt;&lt;context&gt;&gt;</code> Hintergrund</dd>
    </dl>
    <p class="ds-color-card__desc">Hintergrund der äußersten C4-Ebene auf dunklem Canvas.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch" style="background:#353535"></div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">C4 Container</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$CONTAINER_BG</code> ‡</dd>
      <dt>HEX</dt>
      <dd><code>#353535</code></dd>
      <dt>Verwendung</dt>
      <dd><code>&lt;&lt;container&gt;&gt;</code> Hintergrund</dd>
    </dl>
    <p class="ds-color-card__desc">Hintergrund der C4-Container-Ebene auf dunklem Canvas.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch" style="background:#404040"></div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">C4 Component</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$COMPONENT_BG</code> ‡</dd>
      <dt>HEX</dt>
      <dd><code>#404040</code></dd>
      <dt>Verwendung</dt>
      <dd><code>&lt;&lt;component&gt;&gt;</code> Hintergrund</dd>
    </dl>
    <p class="ds-color-card__desc">Hintergrund der C4-Component-Ebene auf dunklem Canvas.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch" style="background:#4A4A4A"></div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">C4 Module</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$MODULE_BG</code> ‡</dd>
      <dt>HEX</dt>
      <dd><code>#4A4A4A</code></dd>
      <dt>Verwendung</dt>
      <dd><code>&lt;&lt;module&gt;&gt;</code> Hintergrund</dd>
    </dl>
    <p class="ds-color-card__desc">Hintergrund der C4-Module-Ebene auf dunklem Canvas.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch" style="background:#555555"></div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">C4 Code</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$CODE_BG</code> ‡</dd>
      <dt>HEX</dt>
      <dd><code>#555555</code></dd>
      <dt>Verwendung</dt>
      <dd><code>&lt;&lt;code&gt;&gt;</code> Hintergrund</dd>
    </dl>
    <p class="ds-color-card__desc">Hintergrund der innersten C4-Code-Ebene auf dunklem Canvas.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch" style="background:#6B9714"></div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Valid Green</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$DS_GREEN</code>, <code>$SUCCESS</code></dd>
      <dt>HEX</dt>
      <dd><code>#6B9714</code></dd>
      <dt>Verwendung</dt>
      <dd>Erfolg, positive Status, Bestätigungen</dd>
    </dl>
    <p class="ds-color-card__desc">Semantisches Grün für Erfolgs- und Valid-Zustände.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch" style="background:#B9D478"></div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Valid Green Light</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$DS_DARK_GREEN</code>, <code>$SUCCESS</code></dd>
      <dt>HEX</dt>
      <dd><code>#B9D478</code></dd>
      <dt>Verwendung</dt>
      <dd>Erfolg, positive Status, Bestätigungen</dd>
    </dl>
    <p class="ds-color-card__desc">Helle Valid-Variante mit gutem Kontrast auf dunklem Hintergrund.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch" style="background:#DB6A00"></div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Orange</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$DS_ORANGE</code>, <code>$WARNING</code></dd>
      <dt>HEX</dt>
      <dd><code>#DB6A00</code></dd>
      <dt>Verwendung</dt>
      <dd>Warnmeldungen, Storage-Semantik, Folder-Rahmen, Akzent</dd>
    </dl>
    <p class="ds-color-card__desc">Modusunabhängiges Warn- und Akzentorange der Corporate Identity.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch" style="background:#C63328"></div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Invalid Red</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$DS_RED</code>, <code>$DANGER</code></dd>
      <dt>HEX</dt>
      <dd><code>#C63328</code></dd>
      <dt>Verwendung</dt>
      <dd>Fehler, negative Status, kritische Pfade</dd>
    </dl>
    <p class="ds-color-card__desc">Semantisches Rot für Fehler- und Invalid-Zustände.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch" style="background:#E85F63"></div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Invalid Red Light</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$DS_DARK_RED</code>, <code>$DANGER</code></dd>
      <dt>HEX</dt>
      <dd><code>#E85F63</code></dd>
      <dt>Verwendung</dt>
      <dd>Fehler, negative Status, kritische Pfade</dd>
    </dl>
    <p class="ds-color-card__desc">Helle Invalid-Variante mit gutem Kontrast auf dunklem Hintergrund.</p>
  </div>
</article>

</div>

### Farbnutzung

<div class="ds-color-grid">
<article class="ds-color-card">
  <div class="ds-color-card__swatch ds-color-card__swatch--dual">
    <div class="ds-color-card__swatch-part" style="background:#00759E"></div>
    <div class="ds-color-card__swatch-part" style="background:#77DDFF"></div>
  </div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Deep Ocean Blue / Bright Sky</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$DS_CLICKABLE</code> / <code>$DS_DARK_CLICKABLE</code></dd>
      <dt>Light</dt>
      <dd><code>#00759E</code></dd>
      <dt>Dark</dt>
      <dd><code>#77DDFF</code></dd>
      <dt>Verwendung</dt>
      <dd>Interaktive Elemente: Rahmen, Links, Buttons, Sequence-Lifeline, Group-Header</dd>
    </dl>
    <p class="ds-color-card__desc">Primärfarbe für klickbare und interaktive Elemente – Deep Ocean Blue im Light Mode, Bright Sky im Dark Mode.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch ds-color-card__swatch--dual">
    <div class="ds-color-card__swatch-part" style="background:#00759E"></div>
    <div class="ds-color-card__swatch-part" style="background:#77DDFF"></div>
  </div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Primary / Markenblau</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$DS_BLUE</code>, <code>$PRIMARY</code></dd>
      <dt>Light</dt>
      <dd><code>#00759E</code></dd>
      <dt>Dark</dt>
      <dd><code>#77DDFF</code></dd>
      <dt>Verwendung</dt>
      <dd>Rahmen Class, State, Activity, Component; Start/End-State; Package-Rahmen</dd>
    </dl>
    <p class="ds-color-card__desc">Rahmenfarbe für zentrale Formen – identischer HEX wie Clickable, eigene Token-Zuordnung für Form-Rahmen.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch ds-color-card__swatch--dual">
    <div class="ds-color-card__swatch-part ds-color-card__swatch--bordered" style="background:#D7E9F4"></div>
    <div class="ds-color-card__swatch-part" style="background:#22303C"></div>
  </div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Blau-Tint</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$DS_LIGHTBLUE</code>, <code>$SECONDARY</code></dd>
      <dt>Light</dt>
      <dd><code>#D7E9F4</code></dd>
      <dt>Dark</dt>
      <dd><code>#22303C</code></dd>
      <dt>Verwendung</dt>
      <dd>Hintergrund Class, State, Activity, Use Case, Component, Participant, Collections</dd>
    </dl>
    <p class="ds-color-card__desc">Standard-Füllfarbe für Diagramm-Formen – helles Blau-Tint im Light Mode, dunkles Blau-Grau im Dark Mode.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch" style="background:#00A5E1"></div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Interface</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$DS_CYAN</code></dd>
      <dt>HEX</dt>
      <dd><code>#00A5E1</code></dd>
      <dt>Verwendung</dt>
      <dd>Interface-Hintergrund und -Rahmen (BorderThickness 2)</dd>
    </dl>
    <p class="ds-color-card__desc">Interfaces nutzen Primary Cyan als Füll- und Rahmenfarbe – modusunabhängig, mit verstärktem Rahmen.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch ds-color-card__swatch--dual">
    <div class="ds-color-card__swatch-part ds-color-card__swatch--bordered" style="background:#F8F8F8"></div>
    <div class="ds-color-card__swatch-part" style="background:#2D2D2D"></div>
  </div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Extern / Fremdsystem</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$SUPERLIGHTGREY</code> ‡</dd>
      <dt>Light</dt>
      <dd><code>#F8F8F8</code></dd>
      <dt>Dark</dt>
      <dd><code>#2D2D2D</code></dd>
      <dt>Verwendung</dt>
      <dd><code>&lt;&lt;external&gt;&gt;</code>, <code>&lt;&lt;External&gt;&gt;</code>: Class, Agent, Database, Participant, Use Case</dd>
    </dl>
    <p class="ds-color-card__desc">Füllfarbe für externe Systeme und Fremdakteure – PlantUML-spezifische Erweiterung außerhalb der Web-CI.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch ds-color-card__swatch--dual">
    <div class="ds-color-card__swatch-part" style="background:#C6C6C6"></div>
    <div class="ds-color-card__swatch-part" style="background:#B6B6B6"></div>
  </div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Actor</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$DS_LIGHTGREY</code></dd>
      <dt>Light</dt>
      <dd><code>#C6C6C6</code></dd>
      <dt>Dark</dt>
      <dd><code>#B6B6B6</code></dd>
      <dt>Verwendung</dt>
      <dd>Use-Case-Actor-Hintergrund und -Rahmen</dd>
    </dl>
    <p class="ds-color-card__desc">Neutrale Grautöne für Use-Case-Akteure – Hintergrund und Rahmen in einem Token-Paar.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch" style="background:#7A7A7A"></div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Extern-Interface</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$DS_GREY</code></dd>
      <dt>HEX</dt>
      <dd><code>#7A7A7A</code></dd>
      <dt>Verwendung</dt>
      <dd><code>&lt;&lt;external&gt;&gt;</code> Interface-Hintergrund und -Rahmen</dd>
    </dl>
    <p class="ds-color-card__desc">Mittleres Grau für externe Interfaces – modusunabhängig, unterscheidet sich von internen Cyan-Interfaces.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch" style="background:#7A7A7A"></div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Pfeile &amp; Linien</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$DS_GREY</code></dd>
      <dt>HEX</dt>
      <dd><code>#7A7A7A</code></dd>
      <dt>Verwendung</dt>
      <dd><code>ArrowColor</code>, Sequence-Pfeile, Activity-Pfeile; Legenden-Rahmen; Group-/Box-Rahmen</dd>
    </dl>
    <p class="ds-color-card__desc">Standardfarbe für Verbindungen und Pfeile – dezent und gut lesbar auf hellem und dunklem Hintergrund.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch ds-color-card__swatch--dual">
    <div class="ds-color-card__swatch-part" style="background:#C6C6C6"></div>
    <div class="ds-color-card__swatch-part" style="background:#B6B6B6"></div>
  </div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Rahmen dezent</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$DS_LIGHTGREY</code></dd>
      <dt>Light</dt>
      <dd><code>#C6C6C6</code></dd>
      <dt>Dark</dt>
      <dd><code>#B6B6B6</code></dd>
      <dt>Verwendung</dt>
      <dd>Swimlane-Rahmen; Sequence-Reference-Rahmen</dd>
    </dl>
    <p class="ds-color-card__desc">Dezenter Rahmen für untergeordnete Container – weniger dominant als Primary-Rahmen.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch ds-color-card__swatch--dual">
    <div class="ds-color-card__swatch-part" style="background:#000000"></div>
    <div class="ds-color-card__swatch-part ds-color-card__swatch--bordered" style="background:#D7E9F4"></div>
  </div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Default / Darkmode Text</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$TEXT_BLACK</code> / <code>$TEXT_DARK</code>, <code>$FGCOLOR</code></dd>
      <dt>Light</dt>
      <dd><code>#000000</code></dd>
      <dt>Dark</dt>
      <dd><code>#D7E9F4</code></dd>
      <dt>Verwendung</dt>
      <dd>Standard-Fließtext; Titel, Legende, Notes, Pfeilbeschriftung, Stereotyp-Labels</dd>
    </dl>
    <p class="ds-color-card__desc">Primäre Textfarbe für Diagramm-Metadaten und Fließtext – Schwarz im Light Mode, helles Blau-Grau im Dark Mode.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch ds-color-card__swatch--dual">
    <div class="ds-color-card__swatch-part" style="background:#000000"></div>
    <div class="ds-color-card__swatch-part ds-color-card__swatch--bordered" style="background:#D7E9F4"></div>
  </div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Element-Labels</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$BLACK</code></dd>
      <dt>Light</dt>
      <dd><code>#000000</code></dd>
      <dt>Dark</dt>
      <dd><code>#D7E9F4</code></dd>
      <dt>Verwendung</dt>
      <dd>Class-Header, Participant, Activity, State, Component, Package, Rectangle</dd>
    </dl>
    <p class="ds-color-card__desc">Beschriftung direkt auf Formen – hoher Kontrast zur Blau-Tint-Füllung.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch ds-color-card__swatch--dual">
    <div class="ds-color-card__swatch-part" style="background:#6D6D6D"></div>
    <div class="ds-color-card__swatch-part" style="background:#AFC1C7"></div>
  </div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Actor-Label</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$TERTIARY_TINT</code> / <code>$TEXT_DARK_SECONDARY</code></dd>
      <dt>Light</dt>
      <dd><code>#6D6D6D</code></dd>
      <dt>Dark</dt>
      <dd><code>#AFC1C7</code></dd>
      <dt>Verwendung</dt>
      <dd>Use-Case-Actor-Beschriftung</dd>
    </dl>
    <p class="ds-color-card__desc">Sekundäre Textfarbe speziell für Actor-Labels – zurückhaltender als Element-Labels.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch ds-color-card__swatch--dual">
    <div class="ds-color-card__swatch-part" style="background:#6D6D6D"></div>
    <div class="ds-color-card__swatch-part" style="background:#AFC1C7"></div>
  </div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Tertiary Tint / Secondary</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$TERTIARY_TINT</code> / <code>$TEXT_DARK_SECONDARY</code></dd>
      <dt>Light</dt>
      <dd><code>#6D6D6D</code></dd>
      <dt>Dark</dt>
      <dd><code>#AFC1C7</code></dd>
      <dt>Verwendung</dt>
      <dd>Bullets, Subheader-Nummerierung; Sequence Box-/Delay-/Group-Font</dd>
    </dl>
    <p class="ds-color-card__desc">Tertiäre Textfarbe für untergeordnete und ergänzende Beschriftungen.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch ds-color-card__swatch--dual">
    <div class="ds-color-card__swatch-part ds-color-card__swatch--bordered" style="background:#FFFFFF"></div>
    <div class="ds-color-card__swatch-part" style="background:#84999F"></div>
  </div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">White / Disabled</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$TEXT_WHITE</code> / <code>$DS_DARK_DISABLED</code></dd>
      <dt>Light</dt>
      <dd><code>#FFFFFF</code></dd>
      <dt>Dark</dt>
      <dd><code>#84999F</code></dd>
      <dt>Verwendung</dt>
      <dd>Text auf dunklem oder farbigem Hintergrund; Dark-Mode deaktivierter Text</dd>
    </dl>
    <p class="ds-color-card__desc">Inverse Textfarbe für Kontrast auf farbigen Flächen – im Dark Mode auch für deaktivierte Zustände.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch ds-color-card__swatch--dual">
    <div class="ds-color-card__swatch-part ds-color-card__swatch--bordered" style="background:#F0F8FF"></div>
    <div class="ds-color-card__swatch-part" style="background:#3A3A3A"></div>
  </div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Systemgrenze</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$ALICEBLUE</code> ‡</dd>
      <dt>Light</dt>
      <dd><code>#F0F8FF</code></dd>
      <dt>Dark</dt>
      <dd><code>#3A3A3A</code></dd>
      <dt>Verwendung</dt>
      <dd>Use-Case-System-<code>rectangle</code>, Package-Hintergrund</dd>
    </dl>
    <p class="ds-color-card__desc">Hintergrund für Systemgrenzen und Packages – dezente Abgrenzung vom Diagramm-Hintergrund.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch ds-color-card__swatch--dual">
    <div class="ds-color-card__swatch-part ds-color-card__swatch--bordered" style="background:#F8F8F8"></div>
    <div class="ds-color-card__swatch-part" style="background:#2D2D2D"></div>
  </div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Gruppe / Swimlane</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$SUPERLIGHTGREY</code> ‡</dd>
      <dt>Light</dt>
      <dd><code>#F8F8F8</code></dd>
      <dt>Dark</dt>
      <dd><code>#2D2D2D</code></dd>
      <dt>Verwendung</dt>
      <dd>Sequence-Groups, Divider, Activity-Swimlane-Titel, Reference-Header</dd>
    </dl>
    <p class="ds-color-card__desc">Container-Hintergrund für Gruppierungen und Swimlanes – identischer HEX wie Extern/Fremdsystem, andere Rolle.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch ds-color-card__swatch--dual">
    <div class="ds-color-card__swatch-part" style="background:#00A5E1"></div>
    <div class="ds-color-card__swatch-part" style="background:#DB6A00"></div>
  </div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Frame / Folder</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$DS_CYAN</code>, <code>$DS_ORANGE</code></dd>
      <dt>Frame</dt>
      <dd><code>#00A5E1</code></dd>
      <dt>Folder</dt>
      <dd><code>#DB6A00</code></dd>
      <dt>Verwendung</dt>
      <dd>Rahmen- und Textfarbe für <code>frame</code> bzw. <code>folder</code></dd>
    </dl>
    <p class="ds-color-card__desc">Semantische Hervorhebung: Cyan für Frames, Orange für Folders – in beiden Modi identisch.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch ds-color-card__swatch--dual">
    <div class="ds-color-card__swatch-part ds-color-card__swatch--bordered" style="background:#FFFFFF"></div>
    <div class="ds-color-card__swatch-part" style="background:#15202B"></div>
  </div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Export / Canvas</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$PUML_BGCOLOR</code>, <code>$DS_BASE_BACKGROUND</code> / <code>$DS_DARK_BACKGROUND</code></dd>
      <dt>Light</dt>
      <dd><code>#FFFFFF</code></dd>
      <dt>Dark</dt>
      <dd><code>#15202B</code></dd>
      <dt>Verwendung</dt>
      <dd>Gerenderter Diagramm-Hintergrund; Sequence-Box/Group-Body; Surface Base</dd>
    </dl>
    <p class="ds-color-card__desc">Canvas- und Export-Hintergrund – bestimmt die sichtbare Fläche des gerenderten Diagramms.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch ds-color-card__swatch--dual">
    <div class="ds-color-card__swatch-part" style="background:#000000"></div>
    <div class="ds-color-card__swatch-part ds-color-card__swatch--bordered" style="background:#D7E9F4"></div>
  </div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Titel</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$FGCOLOR</code></dd>
      <dt>Light</dt>
      <dd><code>#000000</code></dd>
      <dt>Dark</dt>
      <dd><code>#D7E9F4</code></dd>
      <dt>Verwendung</dt>
      <dd><code>skinparam title</code> · FontColor</dd>
    </dl>
    <p class="ds-color-card__desc">Diagrammtitel – nutzt die Standard-Vordergrundfarbe des aktiven Modus.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch ds-color-card__swatch--dual">
    <div class="ds-color-card__swatch-part" style="background:#000000"></div>
    <div class="ds-color-card__swatch-part" style="background:#7A7A7A"></div>
  </div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Legende</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$FGCOLOR</code>, <code>$DS_GREY</code></dd>
      <dt>Light</dt>
      <dd><code>#000000</code> (Text) · <code>#7A7A7A</code> (Rahmen)</dd>
      <dt>Dark</dt>
      <dd><code>#D7E9F4</code> (Text) · <code>#7A7A7A</code> (Rahmen)</dd>
      <dt>Verwendung</dt>
      <dd>Legenden-Text; Rahmen <code>$DS_GREY</code>, Hintergrund transparent</dd>
    </dl>
    <p class="ds-color-card__desc">Legende kombiniert modusabhängigen Text mit modusunabhängigem Grau-Rahmen.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch ds-color-card__swatch--dual">
    <div class="ds-color-card__swatch-part" style="background:#000000"></div>
    <div class="ds-color-card__swatch-part ds-color-card__swatch--bordered" style="background:#D7E9F4"></div>
  </div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Notes</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$FGCOLOR</code></dd>
      <dt>Light</dt>
      <dd><code>#000000</code></dd>
      <dt>Dark</dt>
      <dd><code>#D7E9F4</code></dd>
      <dt>Verwendung</dt>
      <dd>Note-Text (Hintergrund transparent)</dd>
    </dl>
    <p class="ds-color-card__desc">Textfarbe für Anmerkungen – Hintergrund bleibt transparent.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch ds-color-card__swatch--dual">
    <div class="ds-color-card__swatch-part" style="background:#6B9714"></div>
    <div class="ds-color-card__swatch-part" style="background:#B9D478"></div>
  </div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Valid / Valid Dark</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$DS_GREEN</code>, <code>$SUCCESS</code> / <code>$DS_DARK_GREEN</code></dd>
      <dt>Light</dt>
      <dd><code>#6B9714</code></dd>
      <dt>Dark</dt>
      <dd><code>#B9D478</code></dd>
      <dt>Verwendung</dt>
      <dd>Erfolg, positive Status, Bestätigungen</dd>
    </dl>
    <p class="ds-color-card__desc">Semantisches Grün für Erfolgs- und Valid-Zustände – kräftiger im Light, heller im Dark Mode.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch" style="background:#DB6A00"></div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Orange</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$DS_ORANGE</code>, <code>$WARNING</code></dd>
      <dt>HEX</dt>
      <dd><code>#DB6A00</code></dd>
      <dt>Verwendung</dt>
      <dd>Warnmeldungen, Storage-Semantik, Akzent</dd>
    </dl>
    <p class="ds-color-card__desc">Warn- und Akzentfarbe – modusunabhängig, auch für Folder-Semantik genutzt.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch ds-color-card__swatch--dual">
    <div class="ds-color-card__swatch-part" style="background:#C63328"></div>
    <div class="ds-color-card__swatch-part" style="background:#E85F63"></div>
  </div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">Invalid / Invalid Dark</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$DS_RED</code>, <code>$DANGER</code> / <code>$DS_DARK_RED</code></dd>
      <dt>Light</dt>
      <dd><code>#C63328</code></dd>
      <dt>Dark</dt>
      <dd><code>#E85F63</code></dd>
      <dt>Verwendung</dt>
      <dd>Fehler, negative Status, kritische Pfade</dd>
    </dl>
    <p class="ds-color-card__desc">Semantisches Rot für Fehler- und Invalid-Zustände – kräftiger im Light, heller im Dark Mode.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch ds-color-card__swatch--dual">
    <div class="ds-color-card__swatch-part ds-color-card__swatch--bordered" style="background:#FFFFFF"></div>
    <div class="ds-color-card__swatch-part" style="background:#2A2A2A"></div>
  </div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">C4 – Context</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$CONTEXT_BG</code> ‡</dd>
      <dt>Light</dt>
      <dd><code>#FFFFFF</code></dd>
      <dt>Dark</dt>
      <dd><code>#2A2A2A</code></dd>
      <dt>Verwendung</dt>
      <dd><code>&lt;&lt;context&gt;&gt;</code> Hintergrund</dd>
    </dl>
    <p class="ds-color-card__desc">C4-Context-Ebene – PlantUML-spezifische Erweiterung für System-Context-Diagramme.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch ds-color-card__swatch--dual">
    <div class="ds-color-card__swatch-part ds-color-card__swatch--bordered" style="background:#EEF8FE"></div>
    <div class="ds-color-card__swatch-part" style="background:#353535"></div>
  </div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">C4 – Container</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$CONTAINER_BG</code> ‡</dd>
      <dt>Light</dt>
      <dd><code>#EEF8FE</code></dd>
      <dt>Dark</dt>
      <dd><code>#353535</code></dd>
      <dt>Verwendung</dt>
      <dd><code>&lt;&lt;container&gt;&gt;</code> Hintergrund</dd>
    </dl>
    <p class="ds-color-card__desc">C4-Container-Ebene – leicht bläulicher Hintergrund im Light Mode.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch ds-color-card__swatch--dual">
    <div class="ds-color-card__swatch-part ds-color-card__swatch--bordered" style="background:#D7E9F4"></div>
    <div class="ds-color-card__swatch-part" style="background:#404040"></div>
  </div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">C4 – Component</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$COMPONENT_BG</code> ‡</dd>
      <dt>Light</dt>
      <dd><code>#D7E9F4</code></dd>
      <dt>Dark</dt>
      <dd><code>#404040</code></dd>
      <dt>Verwendung</dt>
      <dd><code>&lt;&lt;component&gt;&gt;</code> Hintergrund (gleicher HEX wie Form-Füllung Light)</dd>
    </dl>
    <p class="ds-color-card__desc">C4-Component-Ebene – im Light Mode identisch mit Blau-Tint-Formfüllung.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch ds-color-card__swatch--dual">
    <div class="ds-color-card__swatch-part" style="background:#AFC1C7"></div>
    <div class="ds-color-card__swatch-part" style="background:#4A4A4A"></div>
  </div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">C4 – Module</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$MODULE_BG</code> ‡</dd>
      <dt>Light</dt>
      <dd><code>#AFC1C7</code></dd>
      <dt>Dark</dt>
      <dd><code>#4A4A4A</code></dd>
      <dt>Verwendung</dt>
      <dd><code>&lt;&lt;module&gt;&gt;</code> Hintergrund (gleicher HEX wie Text Tertiary Dark)</dd>
    </dl>
    <p class="ds-color-card__desc">C4-Module-Ebene – im Light Mode identisch mit Tertiary-Tint-Dark-Textfarbe.</p>
  </div>
</article>

<article class="ds-color-card">
  <div class="ds-color-card__swatch ds-color-card__swatch--dual">
    <div class="ds-color-card__swatch-part" style="background:#84999F"></div>
    <div class="ds-color-card__swatch-part" style="background:#555555"></div>
  </div>
  <div class="ds-color-card__body">
    <h4 class="ds-color-card__title">C4 – Code</h4>
    <dl class="ds-color-card__meta">
      <dt>Token</dt>
      <dd><code>$CODE_BG</code> ‡</dd>
      <dt>Light</dt>
      <dd><code>#84999F</code></dd>
      <dt>Dark</dt>
      <dd><code>#555555</code></dd>
      <dt>Verwendung</dt>
      <dd><code>&lt;&lt;code&gt;&gt;</code> Hintergrund (gleicher HEX wie Text Disabled Dark)</dd>
    </dl>
    <p class="ds-color-card__desc">C4-Code-Ebene – im Light Mode identisch mit Disabled-Text-Dark-Farbe.</p>
  </div>
</article>

</div>

<!-- Weitere Farben: Copy-Vorlagen in docs/_snippets/style-guide/color-token-card.html -->

## Typografie

Einheitliche Schrift sorgt für lesbare Diagramme in Präsentationen, MkDocs und Druck.

| Rolle                 | Verwendung                 | Wert                                                                     |
| --------------------- | -------------------------- | ------------------------------------------------------------------------ |
| **Standardschrift**   | Alle Diagrammtexte         | `Helvetica` (`$FONTNAME`)                                                |
| **Body**              | Standard-Labels, Attribute | 12 pt                                                                    |
| **Titel**             | Diagrammtitel              | 28 pt, normal (nicht bold)                                               |
| **Notes**             | Anmerkungen, Erläuterungen | 11 pt, linksbündig                                                       |
| **Class-Header**      | Klassennamen, Typ-Header   | 15 pt, **bold**                                                          |
| **Pfeilbeschriftung** | Kanten- und Pfeil-Labels   | 11 pt (`ArrowFontSize`) — [Globale Defaults](global-defaults.md#schrift) |
| **Swimlane-Titel**    | Activity-Swimlanes         | 16 pt                                                                    |
| **Sequence-Divider**  | Trennlinien-Beschriftung   | 14 pt                                                                    |

**Grundsätze:**

- **Bold** nur in Headern (Titel, Class-Header) - Fließtext in Notes und Attributen bleibt normal.
- Deutsche **Umlaute** können direkt in Labels verwendet werden (UTF-8).
- Diagrammtyp-spezifische Abweichungen: jeweilige [Diagrammtyp-Seite](diagram-types/sequence.md).

---

## Abstände & Form

Globale Abstands- und Formwerte gelten diagrammübergreifend.

| Token / Parameter          | Wert      | Gilt für                                                |
| -------------------------- | --------- | ------------------------------------------------------- |
| `roundcorner`              | **16**    | Eckenradius aller Elemente (Ausnahme: Gantt-Bundle → 6) |
| `BoxPadding`               | **32**    | Innenabstand von Sequence-Boxen                         |
| `$PUML_ELEMENT_PADDING`    | **4**     | Element-Padding (CSS-Pfad ab PlantUML 1.2026.3)         |
| `$PUML_SEQUENCE_GAP_H`     | **32**    | Horizontaler Abstand zwischen Sequence-Participants     |
| `$PUML_SEQ_MARGIN_V`       | **4**     | Vertikaler Participant-Rand                             |
| `$PUML_SEQ_INNER_V` / `$H` | **16**    | Inneres Participant-Padding                             |
| `ArrowThickness`           | **1.5**   | Standard-Pfeilstärke                                    |
| `shadowing`                | **false** | Keine Schatten (CI: „Weniger ist mehr“)                 |
| `dpi`                      | **100**   | Export-Auflösung                                        |

---

## Modus-Schalter

Modus-Schalter steuern **Palette, Hintergrund und Darstellungsvariante**. Sie werden **vor** dem Theme-Include gesetzt - typischerweise über die fertigen Entry-Points:

```txt
!include .../doubleslash/light.puml    ' Light Mode (Default)
!include .../doubleslash/dark.puml     ' Dark Mode
```

| Schalter         | Standard (Light) | Standard (Dark) | Wirkung                                                                                                  |
| ---------------- | ---------------- | --------------- | -------------------------------------------------------------------------------------------------------- |
| `$PUML_MODE`     | `"light"`        | `"dark"`        | Schaltet die gesamte Farbpalette                                                                         |
| `$PUML_BGCOLOR`  | `#FFFFFF`        | `#15202B`       | Export-Hintergrund des gerenderten Bildes                                                                |
| `$PUML_OUTLINE`  | `"false"`        | `"false"`       | `"true"` → Outline-Modus: Füllfarben werden transparent, Text nutzt helle Varianten (Druck/Präsentation) |
| `$PUML_GRADIENT` | `20`             | `15`            | Stärke für abgeleitete Farbtöne (`$PRIMARY_DARK`, `$SUCCESS_LIGHT`, …)                                   |

### Light / Dark wählen

| Ziel                                    | Include                             |
| --------------------------------------- | ----------------------------------- |
| Helle Präsentationen, Druck, helle Docs | `doubleslash/light.puml`            |
| Dunkle Präsentationen, Dark-Mode-Docs   | `doubleslash/dark.puml`             |
| Neutral (Light Default)                 | `doubleslash/doubleslash-gen2.puml` |

`$PUML_MODE` **nach** dem Include zu ändern wirkt nicht - abgeleitete Tokens sind bereits gesetzt.

### Outline-Modus

Bei `$PUML_OUTLINE = "true"` (vor dem Include setzen) werden semantische Füllfarben (`$INFO_BG`, `$DANGER_BG`, …) auf den Export-Hintergrund gesetzt; Textfarben wechseln zu den `*_LIGHT`-Varianten. Geeignet für schwarz-weiß-Druck und reduzierte Folien.

---

## Weiterführend

| Thema                                                 | Seite                                                          |
| ----------------------------------------------------- | -------------------------------------------------------------- |
| Do/Don't für Autoren (keine Hex-Werte, Theme-Include) | [Autoren-Regeln](authoring-rules.md)                           |
| Globale skinparam, Padding-Gate, Titel                | [Globale Defaults](global-defaults.md)                         |
| C4-Stereotypen im Detail                              | [System & C4](diagram-types/system-c4.md)                      |
| Include-Patterns Light/Dark/System                    | [Style Guide - Templates](index.md#templates-include-patterns) |
| Bekannte Abweichungen                                 | [Anti-Patterns](anti-patterns.md)                              |
