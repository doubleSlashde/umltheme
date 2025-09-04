# Changelog

<!-- markdownlint-disable MD024-->

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

<!-- changelog -->

## [2.0.1] - 2025-09-04

### Added

- SWEP Examples

### Fixed

- Includes in dark & light mode, gantt and system styles
- Defined arrow font color to match general font color

## [2.0.0] - 2025-07-01

### Added

- Gen2 styling architecture with improved theme organization
- Light and dark mode support with dedicated theme files
- New consolidated theme files in `doubleslash/` directory:
  - `dark.puml` - Dark mode theme
  - `light.puml` - Light mode theme  
  - `doubleslash-gen2.puml` - Main gen2 theme
  - `puml-theme-gen2-gantt.puml` - Gen2 Gantt chart theme
  - `puml-theme-gen2-system.puml` - Gen2 system diagram theme
- Comprehensive gen2 example files in `examples/gen2/` directory
- Enhanced color schemes optimized for both light and dark environments
- Improved theme modularity and maintainability

### Changed

- Existing theme files now redirect to gen2 themes to preserve backward compatibility
- Theme architecture restructured for better organization and consistency
- Color palettes updated for improved accessibility and modern design standards
- Example files updated to demonstrate gen2 capabilities

### Deprecated

- Legacy theme files (individual `puml-theme-doubleslash-*.puml` files) are now deprecated
- Old styling approach superseded by gen2 architecture
- Direct usage of individual theme files discouraged in favor of consolidated gen2 themes

### Fixed

- Improved theme consistency across different diagram types
- Better color contrast ratios for accessibility compliance
- Enhanced readability in both light and dark environments

## [1.4.0] - 2025-07-01

### Added

- C4 level definitions and styling

### Changed

- Refactored skin parameters across multiple theme files for consistency
- Updated border color settings for C4 levels to 'none'
- Improved example files with local input files and consistent include paths
- Enhanced mind map styling with style enhancements

### Fixed

- Node borders fixed
- Removed duplicate and deprecated settings across theme files
- Improved spacing and layout settings

## [1.3.0] - 2025-06-11

### Changed

- Updated layout settings and skin parameters across multiple PUML theme files

## [1.2.0] - 2025-04-14

### Added

- Mind map style adjustments and enhancements
- Complete include URL examples (commented for direct visibility)
- .gitignore file
- Diagram hints for better usability

### Changed

- Linked examples in README.md for better navigation
- Corrected spacing in various theme files

### Fixed

- Fixed node borders in diagrams

## [1.1.0] - 2024-04-23

### Changed

- Font changed from "Arial" to "Helvetica" for better consistency

### Fixed

- Multiple sequence diagram theme updates and improvements

## [1.0.0] - 2024-01-04

### Added

- Initial PlantUML theme collection for doubleSlash CI styling
- Use case diagram theme (`puml-theme-doubleslash-usecase.puml`)
- Activity diagram theme (`puml-theme-doubleslash-activity.puml`) with piprocess support
- System diagram theme for C4 level 1 and 2 (`puml-theme-doubleslash-system.puml`)
- Class diagram theme, also supports ER-diagrams (`puml-theme-doubleslash-class.puml`)
- Sequence diagram theme (`puml-theme-doubleslash-sequence.puml`)
- Gantt diagram theme (`pgantt-theme-doubleslash.puml`)
- Mind map theme (`puml-theme-doubleslash-mindmap.puml`)
- General theme file (`puml-theme-doubleslash-general.puml`)
- Main theme file (`puml-theme-doubleslash.puml`)
- Initial `doubleslash_style.theme` file
- README with comprehensive usage instructions and examples
- Support for 7 different diagram types with examples

### Changed

- Font standardized to Helvetica across all themes
- Multiple refinements to styling parameters throughout development
- Timeline font size adjusted to 12 for better readability
- Various color and layout optimizations

### Fixed

- Consistent styling across all diagram types established
- Theme parameter conflicts resolved

[Unreleased]: https://github.com/doubleSlashde/umltheme/compare/v2.0.1...HEAD
[2.0.1]: https://github.com/doubleSlashde/umltheme/compare/v2.0.0...v2.0.1
[2.0.0]: https://github.com/doubleSlashde/umltheme/compare/v1.4.0...v2.0.0
[1.4.0]: https://github.com/doubleSlashde/umltheme/compare/v1.3.0...v1.4.0
[1.3.0]: https://github.com/doubleSlashde/umltheme/compare/v1.2.0...v1.3.0
[1.2.0]: https://github.com/doubleSlashde/umltheme/compare/v1.1.0...v1.2.0
[1.1.0]: https://github.com/doubleSlashde/umltheme/compare/v1.0.0...v1.1.0
[1.0.0]: https://github.com/doubleSlashde/umltheme/releases/tag/v1.0.0
