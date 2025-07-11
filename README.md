# umltheme

This repo contains doubleSlash CI styling information to include in plantUML drawings
Use stylings by including the theme file at the top of your code.

## Changelog

The changelog is maintained in [CHANGELOG.md](./CHANGELOG.md). For the latest version, see [releases](https://github.com/doubleSlashde/umltheme/releases).

## Supported themes

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

## Support for the following diagrams

1. Use Cases (see [examples/usecase.puml](examples/usecase.puml)): diagram to support documentation of PEOPLE and PROCESS.
2. Activity (see [examples/activity_model.puml](examples/activity_model.puml)): diagram to illustrate activities in a PROCESS. It can be used as an alternative to BPMN diagrams.  
3. System model (see [examples/systemmodel.puml](examples/systemmodel.puml)): diagram for a functional SYSTEM view. Represents the first two layers of a C4 model (System context and Containers)
4. Data model (see [examples/datamodel.puml](examples/datamodel.puml)): illustrates a DATA model with or without system specific data types. Main purpose of this model is to have a ubiquitous language for software product deveopment to avoid misunderstandings between users and developers.
5. Class model (see [examples/class_model.puml](/examples/class_model.puml)): The class model forms the core of the module design. The classes can be used to represent both level 3 and level 4 in the C4 model. The methods of the classes are the basis of the messages in the sequence model.
6. Sequence model (see [examples/systemmodel.puml](examples/systemmodel.puml) ): The seqence model shows the interactions of the modules from the class model.
7. Mind maps (see [examples/mindmap.puml](examples/mindmap.puml)): The mind map visualizes ideas and concepts in a tree-like structure.
