# Contributing to DodoHub Catalog

Thank you for your interest in listing your app on DodoHub! This guide explains everything you need to know about submitting your macOS application to the catalog.

## Table of contents

- [What is DodoHub?](#what-is-dodohub)
- [Requirements](#requirements)
- [Submission process](#submission-process)
- [Catalog entry format](#catalog-entry-format)
- [Asset guidelines](#asset-guidelines)
- [Verification badges](#verification-badges)
- [After submission](#after-submission)
- [Updating your app](#updating-your-app)
- [Removing your app](#removing-your-app)
- [FAQ](#faq)

---

## What is DodoHub?

DodoHub is a native macOS app store for discovering, downloading, and managing open-source macOS applications. Unlike traditional app stores, DodoHub focuses on:

- **Open-source apps** - All listed apps must have public source code
- **Trust and transparency** - Verification badges show users what they're installing
- **No fees** - Free for developers and users
- **Direct downloads** - Apps are downloaded directly from your GitHub releases

DodoHub is not a replacement for Homebrew. If your app is already on Homebrew, DodoHub adds a visual discovery layer with screenshots, feature lists, and trust badges.

---

## Requirements

### Mandatory requirements

Your app **must** meet all of these criteria:

| Requirement | Description |
|-------------|-------------|
| **Open source** | Public GitHub repository with visible source code |
| **macOS native** | Built for macOS (SwiftUI, AppKit, or Catalyst) |
| **DMG release** | Distributable as a `.dmg` file via GitHub Releases |
| **Working app** | Installs and runs without critical bugs |
| **No malware** | No malicious code, adware, or unwanted behavior |
| **Valid license** | Open-source license (MIT, Apache 2.0, GPL, etc.) |

### Recommended (for verification badges)

These are optional but help users trust your app:

| Badge | Requirement |
|-------|-------------|
| **Notarized** | App is notarized by Apple |
| **Sandboxed** | App uses macOS sandboxing |
| **No analytics** | App doesn't collect usage data or telemetry |
| **Code reviewed** | Source code has been reviewed for security |

### What we don't accept

- Closed-source applications
- Apps that require payment to use core features
- Apps with excessive telemetry or tracking
- Cryptocurrency miners or similar resource-heavy background processes
- Apps that haven't been updated in 2+ years (unless stable and complete)
- Wrappers around web apps (Electron apps wrapping a website)
- Apps that violate macOS security guidelines

---

## Submission process

### Step 1: Prepare your repository

Ensure your GitHub repository has:

1. **Clear README** - Explains what your app does
2. **License file** - `LICENSE` or `LICENSE.md` in the root
3. **App icon** - `icon.png` (512x512 or larger) in the root or a known path
4. **GitHub Release** - At least one release with a `.dmg` file attached

### Step 2: Prepare your assets

You'll need:

- **App icon** - PNG, 512x512px minimum, hosted on GitHub (raw URL)
- **Screenshots** - 1-5 screenshots showing your app (optional but highly recommended)
- **Feature list** - 3-6 key features as short bullet points

### Step 3: Create your catalog entry

Create a JSON entry for your app following the [catalog entry format](#catalog-entry-format) below.

### Step 4: Submit a pull request

1. Fork the [DodoApps/catalog](https://github.com/DodoApps/catalog) repository
2. Add your app to `apps.json` (maintain alphabetical order by `id`)
3. If you're a new publisher, add your publisher entry to the `publishers` array
4. Submit a pull request with the title: `Add [AppName] to catalog`

### Step 5: Review process

We will review your submission for:

- [ ] All mandatory requirements are met
- [ ] JSON is valid and follows the schema
- [ ] App installs and runs correctly
- [ ] No obvious security issues in source code
- [ ] Assets load correctly (icon, screenshots)

Review typically takes 3-7 days. We may ask for changes or clarifications.

---

## Catalog entry format

### Publisher entry

If you're a new publisher, add yourself to the `publishers` array:

```json
{
  "id": "your-publisher-id",
  "name": "Your Name or Company",
  "description": "Short description of what you build",
  "website": "https://yourwebsite.com",
  "github": "https://github.com/YourOrg",
  "email": "contact@yourwebsite.com",
  "sponsorUrl": "https://github.com/sponsors/YourOrg",
  "verified": false,
  "verifiedAt": null,
  "joinedAt": "2026-01-31"
}
```

| Field | Required | Description |
|-------|----------|-------------|
| `id` | Yes | Unique lowercase identifier (letters, numbers, hyphens) |
| `name` | Yes | Display name |
| `description` | Yes | Short tagline (under 60 characters) |
| `website` | No | Your website URL |
| `github` | Yes | GitHub profile or organization URL |
| `email` | No | Contact email |
| `sponsorUrl` | No | GitHub Sponsors or similar URL |
| `verified` | No | Set to `false` (we verify publishers manually) |
| `verifiedAt` | No | Set to `null` |
| `joinedAt` | Yes | Date you joined (YYYY-MM-DD) |

### App entry

Add your app to the `apps` array:

```json
{
  "id": "yourapp",
  "name": "YourApp",
  "publisherId": "your-publisher-id",
  "tagline": "A short catchy description",
  "description": "A longer description of what your app does and why someone would want to use it. Keep it under 200 characters.",
  "category": "utilities",
  "featured": false,
  "icon": "https://raw.githubusercontent.com/YourOrg/yourapp/main/icon.png",
  "screenshots": [
    "https://raw.githubusercontent.com/YourOrg/yourapp/main/screenshots/main.png"
  ],
  "version": "1.0.0",
  "minMacOS": "14.0",
  "downloadUrl": "https://github.com/YourOrg/yourapp/releases/download/v1.0.0/YourApp-1.0.0.dmg",
  "downloadSize": 5000000,
  "releaseDate": "2026-01-31T12:00:00Z",
  "bundleId": "com.yourorg.yourapp",
  "features": [
    "First key feature",
    "Second key feature",
    "Third key feature",
    "Fourth key feature"
  ],
  "verification": {
    "openSource": true,
    "repoUrl": "https://github.com/YourOrg/yourapp",
    "license": "MIT",
    "notarized": false,
    "codeReviewed": false,
    "sandboxed": false,
    "noAnalytics": true,
    "repoCreatedAt": "2025-06-15",
    "verifiedAt": null
  },
  "repoStats": {
    "lastCommitAt": "2026-01-31T12:00:00Z",
    "openIssues": 5,
    "stars": 42,
    "archived": false,
    "fetchedAt": "2026-01-31T12:00:00Z"
  }
}
```

### Field reference

#### Basic info

| Field | Required | Description |
|-------|----------|-------------|
| `id` | Yes | Unique lowercase identifier (letters, numbers, hyphens) |
| `name` | Yes | Display name of your app |
| `publisherId` | Yes | Must match a publisher in the `publishers` array |
| `tagline` | Yes | Short catchy description (under 60 characters) |
| `description` | Yes | Longer description (under 200 characters) |
| `category` | Yes | One of: `productivity`, `utilities`, `security`, `analytics` |
| `featured` | No | Set to `false` (we feature apps manually) |

#### Assets

| Field | Required | Description |
|-------|----------|-------------|
| `icon` | Yes | URL to PNG icon (512x512 minimum) |
| `screenshots` | No | Array of screenshot URLs (recommended: 1-5) |

#### Version info

| Field | Required | Description |
|-------|----------|-------------|
| `version` | Yes | Current version string (e.g., "1.0.0") |
| `minMacOS` | Yes | Minimum macOS version (e.g., "14.0") |
| `downloadUrl` | Yes | Direct URL to the `.dmg` file |
| `downloadSize` | Yes | File size in bytes |
| `releaseDate` | Yes | ISO 8601 date of the release |
| `bundleId` | Yes | macOS bundle identifier |

#### Features

| Field | Required | Description |
|-------|----------|-------------|
| `features` | Yes | Array of 3-6 feature strings (keep each under 40 characters) |

#### Verification

| Field | Required | Description |
|-------|----------|-------------|
| `openSource` | Yes | Must be `true` |
| `repoUrl` | Yes | URL to the GitHub repository |
| `license` | Yes | License identifier (MIT, Apache-2.0, GPL-3.0, etc.) |
| `notarized` | Yes | Is the app notarized by Apple? |
| `codeReviewed` | No | Has the code been security reviewed? (set to `false`) |
| `sandboxed` | Yes | Does the app use macOS sandboxing? |
| `noAnalytics` | Yes | Does the app avoid telemetry/analytics? |
| `repoCreatedAt` | Yes | Date the repository was created (YYYY-MM-DD) |
| `verifiedAt` | No | Set to `null` (we verify manually) |

#### Repository stats

| Field | Required | Description |
|-------|----------|-------------|
| `lastCommitAt` | Yes | ISO 8601 date of last commit |
| `openIssues` | Yes | Number of open issues |
| `stars` | Yes | Number of GitHub stars |
| `archived` | Yes | Is the repository archived? |
| `fetchedAt` | Yes | When you fetched these stats |

---

## Asset guidelines

### App icon

- **Format**: PNG with transparency
- **Size**: 512x512 pixels minimum (1024x1024 recommended)
- **Location**: Host in your repository (e.g., `/icon.png` or `/assets/icon.png`)
- **URL**: Use raw.githubusercontent.com URL

Example URL:
```
https://raw.githubusercontent.com/YourOrg/yourapp/main/icon.png
```

### Screenshots

- **Format**: PNG or JPEG
- **Size**: Ideally 1280x800 or similar aspect ratio
- **Count**: 1-5 screenshots recommended
- **Content**: Show your app in action, highlight key features
- **Location**: Host in your repository or use GitHub user-attachments

Good screenshots:
- Show the main interface
- Demonstrate key features
- Use realistic content (not lorem ipsum)
- Are visually clean and well-composed

### Feature list

Write features as short, action-oriented phrases:

**Good examples:**
- "Clipboard history with search"
- "Touch ID unlock"
- "Real-time CPU monitoring"
- "Drag-and-drop file organization"

**Avoid:**
- "This app has a really great feature that lets you..."
- "Feature 1"
- Anything over 40 characters

---

## Verification badges

DodoHub displays trust badges to help users make informed decisions:

| Badge | Icon | Meaning |
|-------|------|---------|
| **Open source** | Code icon | Source code is publicly available |
| **Notarized** | Checkmark | Apple has verified the app |
| **Sandboxed** | Shield | App uses macOS sandboxing |
| **Privacy focused** | Lock | No analytics or telemetry |
| **Actively maintained** | Clock | Recent commits, responsive to issues |

### How to earn badges

- **Open source**: Required for all apps
- **Notarized**: Notarize your app with Apple ([documentation](https://developer.apple.com/documentation/security/notarizing_macos_software_before_distribution))
- **Sandboxed**: Enable App Sandbox in Xcode
- **Privacy focused**: Don't include any analytics SDKs or telemetry
- **Actively maintained**: Commit regularly, respond to issues

---

## After submission

Once your app is merged:

1. **Appears in DodoHub** - Users can discover and install your app
2. **Direct downloads** - Downloads come directly from your GitHub releases
3. **No ongoing fees** - Keep your app updated and that's it

### What we provide

- Listing in the DodoHub catalog
- Visibility to DodoHub users
- Trust badges based on your verification status

### What you're responsible for

- Maintaining your app and releases
- Keeping your `downloadUrl` working
- Responding to user issues
- Updating the catalog when you release new versions

---

## Updating your app

When you release a new version:

1. Create a new GitHub Release with the `.dmg` attached
2. Submit a PR to update your entry in `apps.json`:
   - Update `version`
   - Update `downloadUrl`
   - Update `downloadSize`
   - Update `releaseDate`
   - Update `repoStats` fields

We plan to automate this process in the future via GitHub Actions.

---

## Removing your app

If you want to remove your app from DodoHub:

1. Submit a PR removing your app from `apps.json`
2. Explain why in the PR description

We may also remove apps that:
- Become abandoned (no updates for 2+ years with open security issues)
- Violate our requirements
- Receive consistent user complaints about malicious behavior

---

## FAQ

### Do I need to pay anything?

No. DodoHub is free for developers and users.

### Can I list a closed-source app?

No. All apps must be open source with publicly available code.

### My app is on Homebrew. Should I still submit to DodoHub?

Yes! DodoHub provides a visual discovery layer. Users who don't use Homebrew can find and install your app through DodoHub.

### How long does review take?

Typically 3-7 days. Complex apps may take longer.

### Can I update my listing myself?

Yes, submit a PR with your changes and we'll review them.

### What if my app isn't notarized?

You can still list your app. The "Notarized" badge simply won't appear. DodoHub runs `xattr -cr` during installation to help users bypass Gatekeeper warnings.

### Can I be a "verified" publisher?

Publisher verification is manual. Once you have multiple well-maintained apps in the catalog, contact us to discuss verification.

### My repository is new. Can I still submit?

Yes, but newer repositories may receive extra scrutiny during review. We recommend having at least one stable release before submitting.

### What categories are available?

Currently: `productivity`, `utilities`, `security`, `analytics`. If your app doesn't fit, suggest a new category in your PR.

### Can I include my app in both DodoHub and the Mac App Store?

Yes. DodoHub is independent of the Mac App Store.

---

## Questions?

- Open an issue in [DodoApps/catalog](https://github.com/DodoApps/catalog/issues)
- Check existing issues for similar questions

We're excited to have your app in DodoHub!
