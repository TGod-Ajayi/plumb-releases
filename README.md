# Plumb for Mac

Plumb finds the build output, caches, Docker images and forgotten tools filling your Mac, sorts every item by how safe it is to delete, and shows you each path before anything goes.

This repository holds Plumb's downloads and release notes. **[Download the latest Plumb.dmg](https://github.com/TGod-Ajayi/plumb-releases/releases/latest/download/Plumb.dmg)** · [All releases](https://github.com/TGod-Ajayi/plumb-releases/releases)

Plumb is in beta. It needs macOS 14 or later, on Apple silicon or Intel.

## Install

1. Download **Plumb.dmg** and open it.
2. Drag **Plumb** onto **Applications**.
3. Open Plumb from Applications.

### The first time you open it

The beta isn't notarized by Apple yet, so macOS stops it the first time:

1. macOS says it can't check Plumb for malware. Click **Done**.
2. Open **System Settings → Privacy & Security**.
3. Scroll down to the message about Plumb and click **Open Anyway**.
4. Confirm with your password or Touch ID.

You only do this once. Later versions will be notarized and open straight away.

## Using Plumb

- **Scan** looks through your Mac and sorts what it finds into three levels:
  - **Safe**: rebuilds itself, like package-manager caches. Ticked for you.
  - **Check first**: safe to remove, but costs a rebuild, like a project's build folder. Ticked for you.
  - **Your call**: only you can decide, like an app you haven't opened in two years. Never ticked for you, and it goes to the Trash so you can put it back.
- **Nothing is deleted until you've seen it.** Open any row to see every path, then press **Review and clean**.
- Build folders are only suggested if git ignores them, nothing inside changed for two days, and no dev server is running in that project. Each one is checked again just before it's removed.
- Every clean writes a plain-text log of each path to `~/Library/Logs/Plumb`.
- **Large and old files** also lists videos, audio and photo exports you haven't opened in a year. They're never ticked or counted, because they may be your only copy.
- **Full Disk Access** is optional. It lets Plumb measure Mail, Messages and Safari data. Without it, Plumb says what it couldn't measure.

The **menu-bar panel** shows free space, dev servers you can stop, apps by memory, your network and connected devices. Turn it on or off in Settings.

The **tools** in the sidebar (Ports and servers, Disk map, Projects, Toolchains, Docker, Startup items, Secrets check and Growth watch) each explain themselves on their page.

## The plumb command

Plumb comes with a command-line tool. In Plumb, go to **Settings → Command line** and click **Install the plumb command…**. Then, in Terminal:

```bash
plumb scan            # only reports; never deletes anything
plumb scan --why      # also lists skipped items and why
plumb clean --plan    # prints the full plan and stops
plumb clean --safe    # deletes only the Safe level, without asking
plumb clean           # cleans Safe and Check first, then asks about each Your call item
```

## Privacy

Plumb has no accounts, analytics or crash reporting, and sends nothing about you off your Mac. The one exception is the menu-bar speed test, which runs only when you click Test speed and uses macOS's own `networkQuality` tool against Apple's servers.

## Uninstall

Quit Plumb and move it from Applications to the Trash. To remove its data too, delete `~/Library/Application Support/Plumb` and `~/Library/Logs/Plumb`. If you installed the command, also remove `/usr/local/bin/plumb`.

## Feedback

Found a bug, or something Plumb should (or shouldn't) clean? [Open an issue](https://github.com/TGod-Ajayi/plumb-releases/issues). A screenshot and your macOS version help.

Made by [TGA](https://tgodajayi.com).
