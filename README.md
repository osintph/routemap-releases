# Route Map: downloads and beta feedback

**Route Map** draws the path your packets take to a host on a map, starting
where you are. It runs the traceroute on your own machine, places each router
from its own hostname first, checks every location against the speed of light,
and shows what it could not place and why.

This repository holds the **release downloads** and the **issue tracker for
beta testers**. It contains no source code. The geolocation engine is open
source separately: [osintph/routemap-engine](https://github.com/osintph/routemap-engine).

**Downloads: [latest release](https://github.com/osintph/routemap-releases/releases)**

## Before you install: the builds are not code-signed yet

Your system will warn you the first time. This is expected for an unsigned beta.

### Windows 10 and 11

Download `routemap-<version>-windows-x86_64.exe` and run it. When SmartScreen
says **"Windows protected your PC"**, choose **More info**, then **Run anyway**.

`routemap.exe` is the app: it opens a window and never a console. For the
command line, also download `routemap-cli-<version>-windows-x86_64.exe` and run
it from a terminal (it asks SmartScreen separately).

### macOS 12 or later

Download the `.dmg` for your Mac: `macos-arm64` for Apple silicon (M1 and
later), `macos-x86_64` for Intel. Open it and drag **Route Map** to
**Applications**. The first time, **right-click** Route Map in Applications,
choose **Open**, then **Open** again. If macOS offers no Open button, run once
in Terminal:

```bash
xattr -d com.apple.quarantine "/Applications/Route Map.app"
```

### Linux x86_64

Use the `.AppImage` (`chmod +x` it, then run it) or unpack the `.tar.gz` and run
`./routemap`. Tracing needs the system traceroute: `sudo apt install traceroute`
(Debian, Ubuntu), `sudo dnf install traceroute` (Fedora) or `sudo pacman -S
traceroute` (Arch). `mtr` is optional.

### Check your download

Each release has a `SHA256SUMS` file:

```bash
sha256sum -c SHA256SUMS --ignore-missing          # Linux
shasum -a 256 -c SHA256SUMS --ignore-missing      # macOS
```

On Windows, in PowerShell: `Get-FileHash .\routemap-<version>-windows-x86_64.exe`
and compare with the line in `SHA256SUMS`.

## Reporting a problem

[Open an issue](https://github.com/osintph/routemap-releases/issues/new/choose).
Please include your OS and version, the Route Map version (Help > About), what
you traced, and what you expected. A screenshot helps. If the problem is with a
trace, **File > Export > JSON** captures the trace and every placement decision;
attach it only if you are comfortable sharing the routers on your path.

## Privacy, in one paragraph

No telemetry and no automatic update checks. When you trace, router hostnames go
to CAIDA Hoiho, public hop addresses to RIPEstat, and reverse-DNS queries to your
own resolver; your public IP is looked up once to find your city unless you set
an origin in Settings. Private and carrier-NAT addresses are never looked up.
Help > Privacy in the app lists everything.

## Licence

Route Map is proprietary software; all rights reserved. The binaries here may be
used for evaluation during the beta. Third-party components keep their own
licences; each download includes `THIRD_PARTY_NOTICES.md`.
