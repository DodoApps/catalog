# Catalog Schema

Version: 1.0

## Root Object

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `schemaVersion` | string | Yes | Schema version (e.g., "1.0") |
| `lastUpdated` | ISO8601 | Yes | When the catalog was last updated |
| `apps` | App[] | Yes | Array of app objects |

## App Object

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `id` | string | Yes | Unique identifier (lowercase, no spaces) |
| `name` | string | Yes | Display name |
| `tagline` | string | Yes | One-line description (< 80 chars) |
| `description` | string | Yes | 2-3 sentence description |
| `category` | string | Yes | One of: `productivity`, `utilities`, `analytics` |
| `icon` | URL | Yes | 512x512 PNG icon URL |
| `screenshots` | URL[] | Yes | 1-5 screenshot URLs (can be empty array) |
| `version` | string | Yes | Semantic version (e.g., "1.2.9") |
| `minMacOS` | string | Yes | Minimum macOS version (e.g., "14.0") |
| `downloadUrl` | URL | Yes | Direct download URL for DMG |
| `downloadSize` | number | Yes | Size in bytes |
| `releaseDate` | ISO8601 | Yes | Last release date |
| `repoUrl` | URL | No | GitHub repository URL |
| `bundleId` | string | Yes | macOS bundle identifier |
| `features` | string[] | No | 3-6 key features |
| `changelog` | string | No | Latest version changes |

## Categories

- `productivity` - Apps that help users create or manage content
- `utilities` - System tools and helpers
- `analytics` - Data and metrics apps

## Example

```json
{
  "id": "dodoshot",
  "name": "DodoShot",
  "tagline": "A beautiful screenshot tool for macOS",
  "description": "Lightweight native macOS screenshot application...",
  "category": "productivity",
  "icon": "https://raw.githubusercontent.com/DodoApps/dodoshot/main/icon.png",
  "screenshots": ["https://..."],
  "version": "1.2.9",
  "minMacOS": "14.0",
  "downloadUrl": "https://github.com/DodoApps/dodoshot/releases/download/v1.2.9/DodoShot-1.2.9.dmg",
  "downloadSize": 4072828,
  "releaseDate": "2026-01-30T11:58:53Z",
  "repoUrl": "https://github.com/DodoApps/dodoshot",
  "bundleId": "com.dodoapps.dodoshot",
  "features": [
    "Area, window, fullscreen capture",
    "Annotation tools"
  ]
}
```
