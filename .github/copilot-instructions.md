# Copilot Instructions for Vare-Stealer

## Project Overview
- **Vare-Stealer** is a Node.js-based information stealer targeting Discord, browsers, Roblox, Instagram, and PC data. It is designed to be undetectable and bypass antivirus solutions.
- The project includes both a main stealer (`vare.js`) and an Electron-based injection module (`injection/index.js`).
- The build process uses `build.js` to obfuscate and package the stealer as a Windows executable via `electron-builder`.

## Key Files & Structure
- `vare.js`: Main logic for data extraction, exfiltration, and anti-analysis checks (HWID, username, hostname blacklists).
- `injection/index.js`: Obfuscated Electron injection script for Discord token and event interception.
- `build.js`: Handles obfuscation and building the Windows installer using Electron.
- `vare.bat`: Batch script for launching the menu (Windows only).
- `vare.json`: Likely configuration or metadata (inspect for details).

## Developer Workflows
- **Build**: Run `node build.js` to generate an obfuscated Windows installer in `./varebuild/`.
- **Configure**: Replace the webhook URL in `vare.js` before building.
- **Run**: Use `vare.bat` for a menu-driven interface on Windows.
- **Dependencies**: Requires Node.js v16, Python, and C++ build tools (see README for links).

## Patterns & Conventions
- **Obfuscation**: All production builds are heavily obfuscated; develop and debug on unobfuscated sources.
- **Anti-analysis**: Blacklists for HWIDs, usernames, and hostnames are enforced at runtime in `vare.js`.
- **Webhook**: Exfiltration is performed via a Discord webhook, set in `vare.js` as `%webhookstring%`.
- **Electron Injection**: `injection/index.js` is loaded remotely or injected into Discord clients.
- **No tests or CI**: No automated tests or CI/CD present; manual build and run.

## Integration Points
- **External APIs**: Uses Discord, Roblox, Instagram, and browser data stores.
- **Electron**: Injection relies on Electron APIs for Discord manipulation.
- **Obfuscation**: Uses `javascript-obfuscator` for code protection.

## Examples
- To add a new data source, extend the extraction logic in `vare.js`.
- To change build output, modify the `directories` or `win` config in `build.js`.

## Cautions
- All code is for educational purposes only. Do not use for malicious activity.
- The project is Windows-centric; cross-platform support is not implemented.

---

For further details, see `README.md` and inspect the main files listed above.
