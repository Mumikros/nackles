# Security

Please do not post tokens, cookies, personal files, clipboard contents or unredacted logs in public issues.
Use GitHub's private vulnerability reporting on this repository when available. If it is not enabled, open an issue asking for a private contact channel without exploit details or personal data.

## Boundaries

- Local windows use sandboxing, context isolation, disabled Node integration and a Content Security Policy.
- Desktop IPC accepts only the main frames of the application's own local windows. Gemini has no preload or desktop bridge.
- Claude hooks bind to IPv4 loopback only and require a random per-installation token. This token is not shipped in the source or installer.
- Gemini loads Google directly in a separate persistent browser partition. Its requests and data are governed by Google; this is not an offline feature.
- Installed CLI tools, their configuration, local executables and the Windows account are trusted. A read-only CLI sandbox is not a guarantee that files cannot be read or sent to the provider. Review your CLI/MCP configuration before using chat.
- Clipboard privacy depends on the source application marking sensitive data. Unmarked passwords or secrets can appear in history; disable clipboard history when necessary.
- The installer is currently unsigned. Verify its origin and checksum before running it. A checksum checks file integrity, not publisher identity.

## Release review

The initial source review includes secret-pattern searches, an explicit publication file list, dependency auditing, automated tests and an inspection of the packaged application. This is not an independent penetration test or a guarantee that no vulnerability exists.

The full dependency audit currently reports 15 moderate findings in development/build tooling, stemming from the minimatch advisory GHSA-g3hv-75wg-m249. The production-only npm audit reports no findings, but excludes Electron because it is declared as a development dependency; it must not be interpreted as an audit of Chromium or Electron's complete runtime. See the release review notes for the exact audit date and results.
