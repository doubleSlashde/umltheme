# umltheme

This repo contains doubleSlash CI styling information to include in plantUML drawings.
Use stylings by including the theme file at the top of your code.

**Gen2 Theme Features:**

- 🌙 **Light and Dark Mode Support** - Choose between light and dark themes
- 🎨 **Improved Styling** - Enhanced colors and modern design
- 📦 **Consolidated Architecture** - Simplified theme structure
- 🔄 **Backward Compatibility** - Legacy themes still work via redirects

## Changelog

The changelog is maintained in [CHANGELOG.md](./CHANGELOG.md). For the latest version, see [releases](https://github.com/doubleSlashde/umltheme/releases).

## Quick Start (Gen2 Themes)

### Universal Theme (Recommended)

For most diagram types, use the universal gen2 theme:

``` txt
!include https://raw.githubusercontent.com/doubleSlashde/umltheme/main/doubleslash/doubleslash-gen2.puml
```

### Light Mode Theme

``` txt
!include https://raw.githubusercontent.com/doubleSlashde/umltheme/main/doubleslash/light.puml
```

### Dark Mode Theme

``` txt
!include https://raw.githubusercontent.com/doubleSlashde/umltheme/main/doubleslash/dark.puml
```

## Specialized Gen2 Themes

### For System Diagrams

``` txt
!include https://raw.githubusercontent.com/doubleSlashde/umltheme/main/doubleslash/puml-theme-gen2-system.puml
```

**System Diagram Levels:**
The system theme supports multiple architectural levels using stereotypes:

``` txt
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

**Available Levels:**

- `<<context>>` - System context level (C4 Level 1)
- `<<container>>` - Container level (C4 Level 2) 
- `<<component>>` - Component level (C4 Level 3)
- `<<module>>` - Module level (C4 Level 4)
- `<<code>>` - Code level (C4 Level 5)
- `<<external>>` - External systems/services

See [examples/gen2/systemmodel_with_levels.puml](examples/gen2/systemmodel_with_levels.puml) for a complete example.

### For Gantt Diagrams

``` txt
@startgantt
!include https://raw.githubusercontent.com/doubleSlashde/umltheme/main/doubleslash/puml-theme-gen2-gantt.puml
...
```

## Legacy Theme Support (Deprecated)

**Note:** Legacy themes are deprecated but still functional via redirects. Please migrate to gen2 themes above.
<!-- markdownlint-disable MD033 -->
<details>
<summary>Click to view legacy includes (deprecated)</summary>

### Include for use case diagram

``` txt
!include https://raw.githubusercontent.com/doubleSlashde/umltheme/main/puml-theme-doubleslash-usecase.puml
```

### Include for activity diagram

``` txt
!include https://raw.githubusercontent.com/doubleSlashde/umltheme/main/puml-theme-doubleslash-activity.puml
```

### Include for system diagram (C4 level 1 and 2)

``` txt
!include https://raw.githubusercontent.com/doubleSlashde/umltheme/main/puml-theme-doubleslash-system.puml
```

### Include for class diagram (also for ER-diagrams)

``` txt
!include https://raw.githubusercontent.com/doubleSlashde/umltheme/main/puml-theme-doubleslash-class.puml
```

### Include for sequence diagram

``` txt
!include https://raw.githubusercontent.com/doubleSlashde/umltheme/main/puml-theme-doubleslash-sequence.puml
```

### Include for Gantt diagram

``` txt
@startgantt
!include https://raw.githubusercontent.com/doubleSlashde/umltheme/main/pgantt-theme-doubleslash.puml
...
```

### Include for mind map

``` txt
@startmindmap
!include https://raw.githubusercontent.com/doubleSlashde/umltheme/main/puml-theme-doubleslash-mindmap.puml
...
```

</details>

## Support for the following diagrams

1. **Use Cases** (see [examples/gen2/usecase.puml](examples/gen2/usecase.puml)): diagram to support documentation of PEOPLE and PROCESS.
2. **Activity** (see [examples/gen2/activity_model.puml](examples/gen2/activity_model.puml)): diagram to illustrate activities in a PROCESS. It can be used as an alternative to BPMN diagrams.  
3. **System model** (see [examples/gen2/systemmodel.puml](examples/gen2/systemmodel.puml)): diagram for a functional SYSTEM view. Represents the first two layers of a C4 model (System context and Containers)
4. **Data model** (see [examples/gen2/datamodel.puml](examples/gen2/datamodel.puml)): illustrates a DATA model with or without system specific data types. Main purpose of this model is to have a ubiquitous language for software product development to avoid misunderstandings between users and developers.
5. **Class model** (see [examples/gen2/class_model.puml](examples/gen2/class_model.puml)): The class model forms the core of the module design. The classes can be used to represent both level 3 and level 4 in the C4 model. The methods of the classes are the basis of the messages in the sequence model.
6. **Sequence model** (see [examples/gen2/sequence.puml](examples/gen2/sequence.puml)): The sequence model shows the interactions of the modules from the class model.
7. **Mind maps** (see [examples/gen2/mindmap.puml](examples/gen2/mindmap.puml)): The mind map visualizes ideas and concepts in a tree-like structure.
8. **Gantt charts** (see [examples/gen2/gantt.puml](examples/gen2/gantt.puml)): Project timeline and task management visualization.
9. **State diagrams** (see [examples/gen2/state.puml](examples/gen2/state.puml)): State machine and workflow visualization.
10. **Deployment diagrams** (see [examples/gen2/deployment.puml](examples/gen2/deployment.puml)): Infrastructure and deployment architecture visualization.

## Migration from Legacy to Gen2

To migrate from legacy themes to gen2:

1. **Replace** old include statements with the universal gen2 theme:

   ```txt
   // Old (deprecated)
   !include https://raw.githubusercontent.com/doubleSlashde/umltheme/main/puml-theme-doubleslash-[type].puml
   
   // New (gen2)
   !include https://raw.githubusercontent.com/doubleSlashde/umltheme/main/doubleslash/doubleslash-gen2.puml
   ```

2. **Choose** your preferred color scheme:
   - Use `doubleslash/light.puml` for light mode
   - Use `doubleslash/dark.puml` for dark mode
   - Use `doubleslash/doubleslash-gen2.puml` for universal theme

3. **Update** examples to reference the gen2 directory if needed

## Usage in MkDocs Integration

To integrate the doubleSlash themes with MkDocs, install [mkdocs_puml](https://github.com/MikhailKravets/mkdocs_puml) and add the following configuration to your `mkdocs.yml`:

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

This configuration:

- Uses the official PlantUML server for rendering
- Automatically applies the light theme for light mode
- Automatically applies the dark theme for dark mode
- Switches themes based on your MkDocs theme's color scheme

## Contributing

Please feel free to contribute improvements, bug fixes, or new diagram type support. Make sure to update both legacy and gen2 themes for backward compatibility.
