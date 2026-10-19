# Workshop update policy

## Current alpha

- Official distribution owner: `The-Mercenary/Workshop` on GitHub.
- Download assets: versioned, Developer ID signed and notarized macOS app archives, with SHA-256 checksums.
- Channels: `alpha` now; a separate `stable` feed when a stable version is released.
- Updates are manual. The app performs no startup update request and installs no update service.
- `updates/alpha.json` is public download metadata, not an executable-code trust mechanism.

GitHub's `releases/latest` endpoint excludes prereleases. The alpha download links and metadata therefore use explicit version tags. Stable clients must not be silently moved to alpha.

## Recommended in-app updater

For macOS, use Sparkle 2 rather than implementing a custom app replacement mechanism. Adding that framework is a separate application change; it is not included in this release.

1. The user chooses **Check for Updates**. Optional periodic checks require an explicit preference; default remains off for the local-first app.
2. A channel-specific HTTPS feed supplies version, minimum macOS, supported architecture, release notes and archive location. Use one stable URL per channel and versioned assets on GitHub Releases.
3. The client checks an Ed25519 signature with a public key embedded in the app, and the expected Developer ID identity. A checksum by itself is not a signature or publisher-authentication mechanism.
4. Show release notes and require the user's choice before download/install. Respect unsaved work across all six editors before restart.
5. Replace the application through the updater's verified installation flow. Documents, Workgroup metadata and application support settings stay outside the app bundle.
6. A failed feed request leaves local editing fully available. Back off retries; avoid launch-blocking checks and user document/filename transmission.

Keep signing/notarization credentials in Keychain or a protected CI signing environment. Keep update-signing private keys separate from the public release repository. Publish verified archives before publishing a feed that points at them. Do not replace an already published version with different bytes; ship a new version.

Retain previous release assets for recovery. Remove a bad version from the update feed, then issue a fixed version; do not silently downgrade a user's data. Any future Workgroup schema or document-format change needs compatibility checks, backup/migration rules and release notes before automatic rollout.

## Official references

- [GitHub Releases](https://docs.github.com/en/repositories/releasing-projects-on-github/about-releases)
- [GitHub Releases API](https://docs.github.com/en/rest/releases/releases)
- [Apple notarization](https://developer.apple.com/documentation/security/notarizing-macos-software-before-distribution)
- [Sparkle documentation](https://sparkle-project.org/documentation/)

An app distribution server, login backend, analytics service and document cloud storage are not required for this update architecture.
