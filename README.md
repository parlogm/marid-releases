# Marid

**Command your APIs.** A desktop API client — build, send, and inspect HTTP, gRPC,
GraphQL, and WebSocket requests, with collections, environments, and history stored
on your own machine.

This repository hosts the **downloads only**. There is no source code here.

## Download

Get the latest build from the [**Releases**](https://github.com/parlogm/marid-releases/releases) page.

| Platform | File | Requirements |
| --- | --- | --- |
| macOS | `Marid-<version>-arm64.dmg` | Apple Silicon (M1 or newer). **Intel Macs are not supported.** |
| Windows | `Marid Setup <version>.exe` | 64-bit (x64) |

Each release also publishes `SHA256SUMS-mac.txt` and `SHA256SUMS-win.txt`. Verifying is
optional but recommended — see [Verifying your download](#verifying-your-download).

## Installing

Marid is ad-hoc signed but **not notarized** — notarization needs a paid Apple
Developer account — so both operating systems warn you the first time you open it.
This is expected. Here is the one-time ritual on each platform.

> If macOS says **"Marid is damaged and can't be opened"**, you have a build from
> before 2026-08-18, which shipped without a valid signature. Download again from
> the Releases page, or clear the quarantine flag on the copy you have:
>
> ```bash
> xattr -dr com.apple.quarantine /Applications/Marid.app
> ```

### macOS

1. Open the `.dmg` and drag **Marid** to your Applications folder.
2. Open Marid. macOS will refuse and say it cannot verify the developer.
3. Click **Done** (not "Move to Trash").
4. Open **System Settings → Privacy & Security**, scroll down, and click
   **Open Anyway** next to the message about Marid.
5. Confirm. Marid opens, and subsequent launches are normal.

> On macOS Sequoia and later, Control-clicking the app no longer bypasses this —
> the Privacy & Security route is the only one.

### Windows

1. Run the `.exe`. Windows SmartScreen will show "Windows protected your PC".
2. Click **More info**, then **Run anyway**.
3. Follow the installer.

Because the build is unsigned, SmartScreen rebuilds its reputation on every release,
so expect this prompt each time you update.

## Verifying your download

Compare the checksum of the file you downloaded against `SHA256SUMS.txt` from the
same release.

macOS:

```bash
shasum -a 256 ~/Downloads/Marid-0.1.0-arm64.dmg
```

Windows (PowerShell):

```powershell
Get-FileHash -Algorithm SHA256 "$env:USERPROFILE\Downloads\Marid Setup 0.1.0.exe"
```

The value printed should appear in the matching `SHA256SUMS-*.txt`. If it doesn't,
don't run the file — re-download it, and if it still doesn't match, open an issue.

## Your data

Marid stores everything locally in `~/.marid` (`C:\Users\<you>\.marid` on Windows) —
collections, requests, environments, and history. Nothing is uploaded, there is no
account to create, and there is no telemetry.

Uninstalling does **not** remove `~/.marid`. Delete that folder yourself if you want
the data gone.

## Updating

There is no auto-update yet. To upgrade, download the newer release and install it
over the existing copy. Your `~/.marid` data is preserved.

## Support

Bug reports and questions: [open an issue](https://github.com/parlogm/marid-releases/issues).

Please include your OS and version, the Marid version (shown in the app), and what
you were doing. Do not paste request bodies, tokens, or API keys into an issue.

## Licence

Marid is proprietary software, © MPM Tech IT SRL. See [LICENSE](LICENSE) for the terms
that apply to these binaries.
