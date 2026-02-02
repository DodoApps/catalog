# Contributing to DodoHub Catalog

Thank you for your interest in listing your app on DodoHub! This guide explains everything you need to know about submitting your macOS application to the catalog.

## Table of contents

- [What is DodoHub?](#what-is-dodohub)
- [Requirements](#requirements)
- [Quality standards](#quality-standards)
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

DodoHub is a curated catalog of **premium-quality, open-source macOS applications** that serve as alternatives to paid software. Unlike general app directories, DodoHub focuses on:

- **Quality over quantity** - Only apps with excellent UI/UX are accepted
- **Paid alternatives** - Apps must replace or compete with commercial software
- **Open source** - All listed apps must have public source code
- **Trust and transparency** - Verification badges show users what they're installing
- **No fees** - Free for developers and users

DodoHub is not a dumping ground for any open-source app. We maintain strict quality standards to ensure every app in our catalog delivers a polished, professional experience comparable to paid alternatives.

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
| **Paid alternative** | Must be a quality alternative to an existing paid/commercial app |
| **Quality UI/UX** | Must meet our [quality standards](#quality-standards) |
| **Screenshots** | At least 2 screenshots showing the app in action |

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
- **Apps with poor or amateur UI/UX design**
- **Apps that don't serve as alternatives to paid software**
- **Apps using default Xcode icons or placeholder assets**
- **Apps without proper dark/light mode support**

---

## Quality standards

DodoHub maintains strict quality standards. Your app will be evaluated against the following criteria during review.

### Design quality checklist

Your app **must** meet all of these design requirements:

| Requirement | Description |
|-------------|-------------|
| **Native design language** | Follows Apple's Human Interface Guidelines |
| **System appearance** | Proper dark mode and light mode support |
| **Professional icon** | Custom app icon (not default Xcode icon) |
| **Window management** | Proper resizing, minimum sizes, and window behavior |
| **Typography** | Consistent, readable fonts using system defaults |
| **Spacing and layout** | Proper margins, padding, and visual hierarchy |
| **Error handling** | Graceful error states with helpful messages |
| **Loading states** | Progress indicators for async operations |
| **Empty states** | Helpful UI when no content is available |
| **Keyboard support** | Standard shortcuts (Cmd+Q, Cmd+W, Cmd+,) |

### UI/UX review criteria

During review, we evaluate:

1. **First impression** - Does the app look professional on first launch?
2. **Consistency** - Are colors, fonts, and spacing consistent throughout?
3. **Responsiveness** - Does the UI respond smoothly to interactions?
4. **Polish** - Are there rough edges, glitches, or unfinished areas?
5. **Accessibility** - Does it work with system accessibility features?
6. **Native feel** - Does it feel like a real macOS app, not a port?

### What "paid alternative" means

Your app must compete with or replace a commercial application. Examples:

| Your app type | Paid alternatives it could replace |
|---------------|-----------------------------------|
| Screenshot tool | CleanShot X, Snagit, Shottr Pro |
| Window manager | Magnet, Rectangle Pro, Moom |
| Clipboard manager | Paste, Copied, Alfred Clipboard |
| System monitor | iStatMenus, Stats Pro |
| Note-taking | Bear, Craft, Ulysses |
| Video player | Infuse, IINA Pro |

When submitting, you must specify which paid app(s) your app serves as an alternative to.

### Examples of rejection reasons

- "The app works but looks like a student project"
- "No dark mode support"
- "Using default SF Symbols for app icon"
- "Inconsistent spacing and alignment throughout"
- "Error messages show raw error codes instead of user-friendly text"
- "No loading indicators - UI freezes during network requests"
- "Doesn't follow macOS conventions (non-standard menu bar, etc.)"
- "Not clear what paid app this replaces"

---

## Submission process

### Step 1: Self-evaluate against quality standards

Before submitting, honestly evaluate your app:

- [ ] Does it look as polished as the paid alternatives?
- [ ] Would you pay for this if it weren't free?
- [ ] Does it follow Apple's Human Interface Guidelines?
- [ ] Do you have at least 2 high-quality screenshots?
- [ ] Is there a clear paid app this replaces?

If you answered "no" to any of these, consider improving your app before submitting.

### Step 2: Prepare your repository

Ensure your GitHub repository has:

1. **Clear README** - Explains what your app does
2. **License file** - `LICENSE` or `LICENSE.md` in the root
3. **App icon** - Custom icon (512x512 or larger)
4. **GitHub Release** - At least one release with a `.dmg` file attached
5. **Screenshots** - At least 2 screenshots in your README or assets folder

### Step 3: Prepare your assets

You'll need:

- **App icon** - PNG, 512x512px minimum, custom designed (not placeholder)
- **Screenshots** - 2-5 screenshots showing your app (required)
- **Feature list** - 3-6 key features as short bullet points

### Step 4: Create your catalog entry

Create a JSON entry for your app following the [catalog entry format](#catalog-entry-format) below.

### Step 5: Submit a pull request

1. Fork the [DodoApps/catalog](https://github.com/DodoApps/catalog) repository
2. Add your app to `apps.json` (maintain alphabetical order by `id`)
3. If you're a new publisher, add your publisher entry to the `publishers` array
4. Submit a pull request with the title: `Add [AppName] to catalog`
5. In your PR description, include:
   - Which paid app(s) this is an alternative to
   - Why you believe it meets our quality standards

### Step 6: Review process

We will review your submission for:

- [ ] All mandatory requirements are met
- [ ] JSON is valid and follows the schema
- [ ] App installs and runs correctly
- [ ] **UI/UX meets quality standards**
- [ ] **Clear paid alternative identified**
- [ ] **Screenshots demonstrate professional quality**
- [ ] No obvious security issues in source code
- [ ] Assets load correctly (icon, screenshots)

Review typically takes 3-7 days. We may ask for changes or reject if quality standards aren't met.

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
  "paidAlternatives": ["CleanShot X", "Snagit"],
  "icon": "https://raw.githubusercontent.com/YourOrg/yourapp/main/icon.png",
  "screenshots": [
    "https://raw.githubusercontent.com/YourOrg/yourapp/main/screenshots/main.png",
    "https://raw.githubusercontent.com/YourOrg/yourapp/main/screenshots/feature.png"
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
| `category` | Yes | One of: `productivity`, `utilities`, `security`, `analytics`, `developer`, `media`, `social`, `finance`, `education`, `other` |
| `featured` | No | Set to `false` (we feature apps manually) |
| `paidAlternatives` | Yes | Array of paid apps this replaces (1-5 names) |

#### Assets

| Field | Required | Description |
|-------|----------|-------------|
| `icon` | Yes | URL to PNG icon (512x512 minimum, custom designed) |
| `screenshots` | Yes | Array of 2-5 screenshot URLs (minimum 2 required) |

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
- **Design**: Must be custom designed - no default Xcode icons or SF Symbols
- **Quality**: Professional quality, recognizable at small sizes
- **Location**: Host in your repository (e.g., `/icon.png` or `/assets/icon.png`)
- **URL**: Use raw.githubusercontent.com URL

Example URL:
```
https://raw.githubusercontent.com/YourOrg/yourapp/main/icon.png
```

### Screenshots (Required)

- **Format**: PNG or JPEG
- **Size**: Ideally 1280x800 or similar aspect ratio
- **Count**: 2-5 screenshots (minimum 2 required)
- **Content**: Show your app in action, highlight key features
- **Location**: Host in your repository or use GitHub user-attachments

**Required screenshots:**
1. Main interface showing the app's primary function
2. At least one additional view showing a key feature

**Good screenshots:**
- Show the main interface clearly
- Demonstrate key features in action
- Use realistic content (not lorem ipsum)
- Are visually clean and well-composed
- Show both light and dark mode (if supported)
- Have consistent window sizes across screenshots

**Bad screenshots (will be rejected):**
- Blurry or low-resolution images
- Screenshots with lorem ipsum or placeholder content
- Showing error states or incomplete UI
- Inconsistent window sizes
- Desktop clutter visible around the app

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
- **Maintaining the quality standards** - We may remove apps that degrade in quality

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
   - Update `screenshots` if the UI has changed significantly

We plan to automate this process in the future via GitHub Actions.

---

## Removing your app

If you want to remove your app from DodoHub:

1. Submit a PR removing your app from `apps.json`
2. Explain why in the PR description

We may also remove apps that:

- Become abandoned (no updates for 2+ years with open security issues)
- Violate our requirements
- **Degrade in quality** (UI/UX quality drops significantly)
- Receive consistent user complaints about malicious behavior
- No longer function as a viable alternative to paid software

---

## FAQ

### Do I need to pay anything?

No. DodoHub is free for developers and users.

### Can I list a closed-source app?

No. All apps must be open source with publicly available code.

### What if my app doesn't have a direct paid competitor?

Your app should solve a problem that paid apps also solve. If there's no commercial equivalent, explain in your PR what professional need your app addresses and why users would otherwise pay for a solution.

### My app works but the UI is basic. Can I still submit?

Probably not. DodoHub has strict quality standards. If your UI looks "basic" or "functional but not polished," we recommend improving the design before submitting. Consider:
- Adding proper spacing and padding
- Ensuring dark/light mode support
- Using consistent colors and typography
- Adding loading states and error handling
- Following Apple's Human Interface Guidelines

### My app is on Homebrew. Should I still submit to DodoHub?

Maybe. Homebrew lists any working app; DodoHub only lists premium-quality apps. If your app meets our quality standards, yes - DodoHub provides a visual discovery layer with screenshots and trust badges.

### How long does review take?

Typically 3-7 days. Complex apps may take longer. Apps that don't meet quality standards will be rejected with feedback.

### Can I update my listing myself?

Yes, submit a PR with your changes and we'll review them.

### What if my app isn't notarized?

You can still list your app. The "Notarized" badge simply won't appear. DodoHub runs `xattr -cr` during installation to help users bypass Gatekeeper warnings.

### Can I be a "verified" publisher?

Publisher verification is manual. Once you have multiple well-maintained, high-quality apps in the catalog, contact us to discuss verification.

### My repository is new. Can I still submit?

Yes, but newer repositories receive extra scrutiny. We look more closely at UI quality and code for new repos.

### What categories are available?

Available categories: `productivity`, `utilities`, `security`, `analytics`, `developer`, `media`, `social`, `finance`, `education`, `other`. If your app doesn't fit, suggest a new category in your PR.

### Can I include my app in both DodoHub and the Mac App Store?

Yes. DodoHub is independent of the Mac App Store.

### My PR was rejected. Can I resubmit?

Yes, but only after addressing the feedback provided. Repeated submissions without improvements may result in a temporary submission ban.

---

## Questions?

- Open an issue in [DodoApps/catalog](https://github.com/DodoApps/catalog/issues)
- Check existing issues for similar questions

We're excited to see your high-quality app in DodoHub!
