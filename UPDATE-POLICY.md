# Workshop update policy

Official downloads and feeds are published by **The-Mercenary/Workshop**. App source/builds remain in an organization-private repository. No account, document server, analytics backend or always-running update service is required.

## Current behavior

- Velopack **1.2.161** manages native packages and application replacement on macOS, Windows and Linux.
- Each CPU/OS uses its own feed: `releases.<runtime>-alpha.json`, where runtime is `osx-arm64`, `osx-x64`, `win-x64`, `win-arm64`, `linux-x64` or `linux-arm64`.
- Alpha clients include prereleases. Stable builds use separate `-stable` channels and exclude prereleases. GitHub's `releases/latest` endpoint is not used for alpha discovery.
- Automatic checks are enabled by default, start after the app is usable and are throttled to once per 24 hours across restarts. The user can disable them or choose Check now. Checks/downloads run off the UI thread; offline editing remains available.
- Download and installation require the user's choice. Save all modified documents before Install and restart. Busy native editors, pending dialogs and unsaved documents prevent the restart. No silent automatic installation occurs.
- Requested data comprises GitHub release metadata and app packages. Workshop does not upload Workgroup paths, file names, document contents or telemetry. GitHub and its asset CDN necessarily receive ordinary connection information such as the request IP.

## Verification and trust boundary

The client uses a fixed official GitHub repository over HTTPS, validates product ID, full-package type, bounded size, expected version/no downgrade and a SHA-256 checksum before installation. macOS bundles and DMGs also have Developer ID signatures, Apple notarization and stapled tickets. Current Windows alpha installers are **not Authenticode signed**; SmartScreen and managed-device policies may restrict them.

SHA-256 checks corruption; it is not an independent publisher signature. This release relies on the official GitHub account/HTTPS supply chain and OS signing where present. It does not implement a separate Ed25519-signed feed or Sparkle. Protect GitHub release permissions and Apple signing credentials accordingly. Signing credentials are not embedded in the app or public repository.

## Publishing, channels and recovery

1. Build/test on the native target and verify the actual package plus an older-to-newer installed update with synthetic documents.
2. Keep the same package ID and newer semantic version. Do not replace published package bytes under an existing version.
3. Upload versioned installers, portable archives, full `.nupkg` files, SHA256SUMS and per-runtime feeds to a draft release. Validate its authenticated assets, publish the complete prerelease together, then verify anonymous downloads. `updates/alpha.json` is human/download metadata; executable updates use the Velopack release feeds attached to GitHub Releases.
4. Promote to stable only after validation. Publish stable feeds for stable clients; an explicit alpha feed alias to the same stable package is required to let existing alpha installations move forward. Stable feeds must never point to an alpha package.
5. Keep previous releases for manual recovery. Remove a faulty version from discovery and publish a newer repair. The app blocks automatic downgrades. To restore a previous installer manually, first back up the Workgroup folder; never remove its files or the settings profile as part of app replacement.

Documents and `.workgroup/` metadata stay in the selected folder. Settings live in the per-OS user-data directory listed in README. Downloaded update files are confined to its `updates/packages` directory. App replacement does not migrate document formats or change Workgroup schema 1 in this release. A future schema change requires explicit compatibility/migration and recovery checks.

Legacy `0.1.0-alpha.1` has no in-app updater: its users must manually install an updater-enabled version once. Linux installs should stay in a user-writable extracted folder with the `Workshop` launcher and `Workshop.AppImage` together; the launcher uses extract-and-run to avoid requiring FUSE. Updates may fail if the app location is read-only, disk space is insufficient or system policy blocks execution; local document files remain separate and a fresh official installer is the recovery route.

## References

- [Velopack Rust integration](https://docs.velopack.io/getting-started/rust)
- [Velopack packaging runtimes](https://docs.velopack.io/packaging/runtime)
- [Velopack signing](https://docs.velopack.io/packaging/signing)
- [GitHub Releases](https://docs.github.com/en/repositories/releasing-projects-on-github/about-releases)
- [Apple notarization](https://developer.apple.com/documentation/security/notarizing-macos-software-before-distribution)
