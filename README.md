# DodoApps Catalog

Central catalog for all DodoApps applications. Used by [DodoHub](https://github.com/DodoApps/dodohub) to display and distribute apps.

## Submit your app

Want to list your app on DodoHub? See the **[Contributing Guide](CONTRIBUTING.md)** for complete submission guidelines.

**Requirements:**
- Open source (public GitHub repository)
- Native macOS app
- Distributable as DMG via GitHub Releases
- Valid open-source license

## Usage

The catalog is available at:
```
https://raw.githubusercontent.com/DodoApps/catalog/main/apps.json
```

## Schema

See [SCHEMA.md](SCHEMA.md) for the full schema documentation.

## Apps

| App | Description | Category | Version |
|-----|-------------|----------|---------|
| [DodoShot](https://github.com/DodoApps/dodoshot) | Screenshot tool | Productivity | v1.2.9 |
| [DodoClip](https://github.com/DodoApps/dodoclip) | Clipboard manager | Productivity | v1.2.2 |
| [DodoPulse](https://github.com/DodoApps/dodopulse) | System monitoring | Utilities | v1.1.0 |
| [DodoTidy](https://github.com/DodoApps/dodotidy) | System cleaner | Utilities | v1.0.5 |
| [DodoCount](https://github.com/DodoApps/dodocount) | Analytics menubar | Analytics | v1.1.0 |
| [DodoNest](https://github.com/DodoApps/dodonest) | Menu bar organizer | Utilities | v1.1.0 |
| [DodoPass](https://github.com/DodoApps/dodopass) | Password manager | Security | v1.0.0 |

## Updating the catalog

The catalog is automatically updated when a new release is published in any DodoApps repository via GitHub Actions.

To manually update, edit `apps.json` and commit.

## Links

- [DodoHub](https://github.com/DodoApps/dodohub) - The app store
- [Contributing Guide](CONTRIBUTING.md) - How to submit your app
- [Schema Documentation](SCHEMA.md) - Full JSON schema
