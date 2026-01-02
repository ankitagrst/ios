# CI: Build iOS on GitHub Actions (macOS runner)

This repo includes a GitHub Actions workflow that builds an iOS archive and exports an IPA on `macos-latest`.

## What the workflow does
- Installs Ruby gems and CocoaPods
- Runs `pod install` in the `ios` workspace
- (Optional) Imports code signing materials if you provide secrets
- Archives the app with `xcodebuild` and exports an IPA
- Uploads artifacts (IPA and xcarchive)

## Required secrets (Repository → Settings → Secrets)
- `P12_BASE64` — base64-encoded `.p12` certificate containing the private key (for manual signing)
- `P12_PASSWORD` — password for the `.p12` file
- `PROV_PROFILE_BASE64` — base64-encoded `.mobileprovision` file
- `TEAM_ID` — your Apple Team ID (used in `ExportOptions.plist`)

Notes:
- To create base64 values:
  - macOS / Linux: `base64 -i certificate.p12 | pbcopy` and paste into the secret
  - For provisioning profile: `base64 -i myprofile.mobileprovision | pbcopy`
- For App Store builds you can set `EXPORT_METHOD` to `app-store` in the workflow (or change the `env` default).

## Triggering the workflow
- Push to `main` (default in the workflow), open a PR, or run manually via the Actions -> workflow -> Run workflow button.

## Signing alternatives
- Fastlane Match or App Store Connect API Key are recommended for teams to manage signing securely at scale.
- If you prefer Match, I can add a Fastlane setup to the repo instead.

## Next steps I can do for you
- Add Fastlane + `match` integration for automated signing (recommended)
- Add an alternate workflow that performs tests and code signing using App Store Connect API Key

If you want, I can also add a small README snippet with example commands to download the artifact and install on a device using `ios-deploy` or `Apple Configurator`.