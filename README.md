# umltheme

This repo contains doubleSlash CI styling information to include in PlantUML drawings. Use styling by including the theme file at the top of your drawing.

**Gen2 theme features:**

- Light and dark mode support
- Improved styling — refined palette and clearer defaults
- Consolidated architecture under `doubleslash/`
- Backward compatibility — legacy theme URLs remain available via redirects

## Documentation

**User guide (usage, specialized themes, examples, MkDocs integration, migration):**  
[**https://doubleslashde.github.io/umltheme/**](https://doubleslashde.github.io/umltheme/)

The site is built from [`docs/`](./docs/) and deployed with [`.github/workflows/docs.yml`](./.github/workflows/docs.yml) on pushes to `main`. To preview locally: install [`requirements-docs.txt`](./requirements-docs.txt) and run `mkdocs serve`.

## Changelog

The changelog is maintained in [CHANGELOG.md](./CHANGELOG.md). For tagged releases, see [GitHub Releases](https://github.com/doubleSlashde/umltheme/releases).

## Contributing

Please feel free to contribute improvements, bug fixes, or new diagram type support. Keep legacy and Gen2 themes aligned where backward compatibility matters.
