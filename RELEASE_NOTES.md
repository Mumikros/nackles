# Nackles 1.0.0

First public Windows x64 release. Turkish and English interface.

## Included

- Claude Code and Codex activity display, music controls, notes, clipboard history, file shelf and focus protection.
- Claude / Codex / ChatGPT chat through separately installed CLI tools and the user's own account.
- Gemini's web interface inside the island, using a separate sandboxed browser profile.
- Async Electron clipboard compatibility, settings-window visibility fixes and desktop IPC sender validation.

## Review on 2026-11-01

- 33 automated tests passed, including clipboard privacy markers, hook authentication, navigation restrictions and rejected IPC senders.
- Gitleaks 8.30.1 found no secrets in the reviewed initial Git commit. Publication checks also inspect personal-email patterns, developer home paths and PNG metadata.
- The packaged application contains 43 expected files (source/assets and package metadata). Packaged source/assets match the reviewed working files. No personal profile, cookies, notes, logs, local hook token, development notes or test conversations are included.
- A real Electron check confirmed that packaged Settings IPC succeeds and an untrusted window is rejected.
- `npm audit`: 15 moderate findings in build-tool dependencies; zero high or critical findings. These share minimatch advisory [GHSA-g3hv-75wg-m249](https://github.com/advisories/GHSA-g3hv-75wg-m249). No forced major-version downgrade or incompatible override was applied.
- `npm audit --omit=dev`: zero findings. This does not cover Electron/Chromium runtime because Electron is a devDependency. Electron 45.2.1 and electron-builder 26.18.0 matched npm's latest versions when checked.

## Known limitations

The Windows installer is unsigned. Gemini's embedded Google sign-in is not verified and Google may restrict it. The ChatGPT tab uses Codex CLI, not the ChatGPT website. CLI configuration, tools and MCP services remain a trust boundary; review them before sending private content. See [Security](SECURITY.md) and the privacy section of [README](README.md).

Financial support has not been activated. See [Support](SUPPORT.md) for maintainer setup.

## Installer integrity

`Nackles-Kurulum-1.0.0.exe`

SHA-256: `9343fdd1ba2834038cf9b430aff3eaff126d57e34818fc3c3d5f4ec1941b3d89`

Checks and source review reduce risk; they do not certify the software as free of vulnerabilities.
