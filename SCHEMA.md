# Catalog Schema

Version: 1.1

## Root Object

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `schemaVersion` | string | Yes | Schema version (e.g., "1.1") |
| `lastUpdated` | ISO8601 | Yes | When the catalog was last updated |
| `publishers` | Publisher[] | Yes | Array of publisher objects |
| `apps` | App[] | Yes | Array of app objects |

---

## Publisher Object

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `id` | string | Yes | Unique identifier (lowercase, no spaces) |
| `name` | string | Yes | Display name |
| `description` | string | No | One-liner about the publisher |
| `website` | URL | No | Publisher's homepage |
| `github` | URL | Yes | GitHub org/user URL (required for open source) |
| `icon` | URL | No | Publisher logo (defaults to GitHub avatar) |
| `email` | string | No | Contact email |
| `sponsorUrl` | URL | No | GitHub Sponsors / Ko-fi / Patreon link |
| `verified` | boolean | Yes | Passed verification process |
| `verifiedAt` | date | Yes | When publisher was verified |
| `joinedAt` | date | Yes | When publisher joined the platform |

---

## App Object

### Basic Info

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `id` | string | Yes | Unique identifier (lowercase, no spaces) |
| `name` | string | Yes | Display name |
| `publisherId` | string | Yes | Reference to publisher.id |
| `tagline` | string | Yes | One-line description (< 80 chars) |
| `description` | string | Yes | 2-3 sentence description |
| `category` | string | Yes | One of: `productivity`, `utilities`, `analytics` |
| `featured` | boolean | No | Editor's pick / highlighted app |

### Media

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `icon` | URL | Yes | 512x512 PNG icon URL |
| `screenshots` | URL[] | Yes | 1-5 screenshot URLs (can be empty array) |

### Distribution

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `version` | string | Yes | Semantic version (e.g., "1.2.9") |
| `minMacOS` | string | Yes | Minimum macOS version (e.g., "14.0") |
| `downloadUrl` | URL | Yes | Direct download URL for DMG |
| `downloadSize` | number | Yes | Size in bytes |
| `releaseDate` | ISO8601 | Yes | Last release date |
| `bundleId` | string | Yes | macOS bundle identifier |

### Metadata

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `features` | string[] | No | 3-6 key features |
| `changelog` | string | No | Latest version changes |

---

## Verification Object

Nested under each app. Documents verification status.

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `openSource` | boolean | Yes | Source code is publicly available |
| `repoUrl` | URL | Yes | Link to source code repository |
| `license` | string | Yes | License type (MIT, GPL, Apache, etc.) |
| `notarized` | boolean | Yes | Apple notarization status |
| `codeReviewed` | boolean | Yes | Code has been reviewed by DodoHub team |
| `sandboxed` | boolean | Yes | Uses macOS App Sandbox |
| `noAnalytics` | boolean | Yes | No tracking or telemetry |
| `repoCreatedAt` | date | Yes | When the repo was created (1 year rule) |
| `verifiedAt` | date | Yes | When this app passed verification |

### Verification Requirements

To be listed on DodoHub, apps must meet ALL of the following:

1. **Open source** - Public repository with recognized license
2. **1 year existence** - Repo must be at least 1 year old
3. **Code reviewed** - Reviewed by DodoHub team
4. **Notarized** - Signed and notarized by Apple

---

## Repo Stats Object

Nested under each app. Auto-updated by GitHub Actions.

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `lastCommitAt` | ISO8601 | Yes | Last commit timestamp |
| `openIssues` | number | Yes | Number of open issues |
| `stars` | number | Yes | GitHub stars |
| `archived` | boolean | Yes | Whether repo is archived |
| `fetchedAt` | ISO8601 | Yes | When stats were last fetched |

### Maintenance Status (Computed by Client)

DodoHub computes maintenance status from `lastCommitAt`:

| Status | Criteria |
|--------|----------|
| **Active** | Commit within last 3 months |
| **Maintained** | Commit within last 6 months |
| **Stale** | Commit within last 12 months |
| **Abandoned** | No commit in 12+ months OR `archived: true` |

---

## Categories

| Category | Description |
|----------|-------------|
| `productivity` | Apps that help users create or manage content |
| `utilities` | System tools and helpers |
| `analytics` | Data, metrics, and monitoring apps |

---

## Example

```json
{
  "schemaVersion": "1.1",
  "lastUpdated": "2026-01-31T04:30:00Z",

  "publishers": [
    {
      "id": "dodoapps",
      "name": "DodoApps",
      "description": "Beautiful native macOS utilities",
      "website": null,
      "github": "https://github.com/DodoApps",
      "icon": "https://avatars.githubusercontent.com/u/198424587",
      "email": null,
      "sponsorUrl": null,
      "verified": true,
      "verifiedAt": "2026-01-31",
      "joinedAt": "2026-01-31"
    }
  ],

  "apps": [
    {
      "id": "dodoshot",
      "name": "DodoShot",
      "publisherId": "dodoapps",
      "tagline": "A beautiful screenshot tool for macOS",
      "description": "Lightweight native macOS screenshot application...",
      "category": "productivity",
      "featured": true,
      "icon": "https://raw.githubusercontent.com/DodoApps/dodoshot/main/icon.png",
      "screenshots": ["https://..."],
      "version": "1.2.9",
      "minMacOS": "14.0",
      "downloadUrl": "https://github.com/.../DodoShot-1.2.9.dmg",
      "downloadSize": 4072828,
      "releaseDate": "2026-01-30T11:58:53Z",
      "bundleId": "com.dodoapps.dodoshot",
      "features": [
        "Area, window, fullscreen capture",
        "Annotation tools"
      ],
      "verification": {
        "openSource": true,
        "repoUrl": "https://github.com/DodoApps/dodoshot",
        "license": "MIT",
        "notarized": false,
        "codeReviewed": true,
        "sandboxed": false,
        "noAnalytics": true,
        "repoCreatedAt": "2026-01-29",
        "verifiedAt": "2026-01-31"
      },
      "repoStats": {
        "lastCommitAt": "2026-01-30T11:58:53Z",
        "openIssues": 1,
        "stars": 13,
        "archived": false,
        "fetchedAt": "2026-01-31T04:30:00Z"
      }
    }
  ]
}
```
