# Nackles

A Dynamic Island for Windows. A small island at the top of your screen shows what **Claude Code** and **Codex** are doing, lets you answer permission prompts without switching windows, and keeps music, notes, a clipboard history, a file shelf and a focus guard one click away.

*Türkçe ve İngilizce arayüz. Turkish and English UI.*

## Features

- **AI status:** live state of Claude Code and Codex sessions (working, waiting for you, done, error), with a separate tint for each agent.
- **Permission prompts:** allow or deny a Claude Code permission request right from the island.
- **Chat:** Claude, Codex and ChatGPT (via Codex login) use your installed CLI and account. Gemini opens its own web interface **inside the island**, with a separate persistent web session; no Gemini CLI or API key is needed. Open the selected service in its own app or website with ↗.
- **Music:** shows and controls what is playing (Spotify, browsers, anything that uses Windows media controls).
- **Notes, clipboard history, file shelf:** drop files on the island, convert or merge them with [Filee](https://github.com/KnifeLemon/Filee) if it is installed.
- **Focus guard:** a gentle breathing screen when you open distracting sites during a focus session. Free.
- **Make it yours:** rename the assistant, pick one of four mascots or add your own image, choose a color palette.
- Gets out of the way: tucks into a thin line when a full-screen window is in front.

## Install

Download `Nackles-Kurulum-x.y.z.exe` from [Releases](../../releases) and run it.

The installer is not code-signed yet, so Windows SmartScreen may show a warning. Verify the release source and SHA-256 checksum before deciding whether to run it. A checksum verifies integrity; it does not authenticate the publisher.

Requirements: Windows 10/11 (x64). Claude Code and/or Codex are optional; the island works without them.

## Privacy

Nackles has **no telemetry, no analytics, no Nackles accounts and no servers**. Selecting Gemini loads Google's website directly.

What it touches on your computer:

| What | Why |
| --- | --- |
| `~/.claude/settings.json` | Only when you press **Connect** for Claude Code: adds `http` hooks that point to `127.0.0.1` (your own machine). A backup is written next to it first (`settings.json.nackles-yedek`). **Disconnect** or uninstalling removes them again. |
| `~/.codex/sessions/**` | Read-only, to show Codex activity. Nackles never writes to Codex files. |
| `%APPDATA%\Nackles\` | Settings, notes, shelf file paths, recent job titles, a random local token, custom mascots, a compiled media helper, focus counters and a debug log (rotated at 512 KB, with one previous copy). These local files can contain private information; do not upload the profile folder or raw logs. |
| Gemini web session | Google's Gemini website runs in a sandboxed view inside the island. Sign-in cookies stay in its own persistent profile on this computer. Your regular browser and Gemini CLI logins are separate; they are not copied. Google may restrict sign-in from embedded browsers. Nackles does not inject scripts, automate the site or read your conversations. |
| Clipboard | History is kept in memory only and cleared on quit. Recognized private clipboard markers are respected. Unmarked secrets can still be captured; history can be disabled in Settings. |
| Files you drop on the shelf | Only opened, converted or moved to the Recycle Bin when you ask. Nothing is permanently deleted. |

The hook server listens only on `127.0.0.1` and rejects any request without the secret token stored in your profile.
Claude, Codex and ChatGPT chat runs the official `claude` / `codex` programs already on your computer; their traffic goes to Anthropic / OpenAI under your own account. Gemini uses Google's website directly.

Codex activity monitoring and clipboard history are enabled by default and can be disabled in Settings. The media helper reads the foreground window title/process for island visibility and focus protection; titles are not persisted by the helper. Recent AI job titles can include prompt excerpts. CLI tools may retain their own conversation logs outside Nackles. Review your CLI tools and MCP configuration: a read-only filesystem sandbox does not prevent reading files or sending information to the provider.

## Uninstall

Windows Settings → Apps → Nackles → Uninstall. The uninstaller also removes Nackles' hooks from Claude Code and the "Start with Windows" entry. Your notes and settings in `%APPDATA%\Nackles` are kept; delete that folder if you want them gone.

## Build from source

```bash
npm ci
npm start        # run
npm test         # tests
npm run dist     # build the installer into dist/
```

## Notes

Nackles is an independent project. It is not affiliated with or endorsed by Anthropic, OpenAI, Google, Apple or Microsoft. Product names and trademarks belong to their respective owners. Filee is a separate MIT-licensed project by KnifeLemon and is not bundled. Gemini embedded sign-in has not been verified and may be restricted by Google.

## Support and security

See [Support Nackles](SUPPORT.md) for contribution and funding status, and [Security](SECURITY.md) for security boundaries and reporting guidance.

## License

[MIT](LICENSE)
