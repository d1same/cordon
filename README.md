<p align="center">
  <img src="assets/cordon-icon.png" width="112" alt="Cordon icon">
</p>

<h1 align="center">Cordon</h1>

<p align="center">
  <b>One browser for every client. Nothing crosses between them.</b><br>
  A secure, multi-tenant browser for MSP technicians.
</p>

<p align="center">
  <a href="https://github.com/d1same/cordon-releases/releases/latest"><b>⬇ Download the latest version</b></a>
</p>

---

## What it does

- **Every client in its own sealed session.** Sign into Acme's and Globex's Microsoft 365, Google and Adobe admin portals at the same time. Cookies and sign-ins never mix.
- **Your MSP tools, one click away:** Halo, IT Glue, Hudu, NinjaOne, N-sight, Huntress, Duo, Cove, CIPP and more, each isolated too.
- **Wrong-tenant warning:** a red bar if a client's tab signs into a different tenant.
- **PIN lock:** locks on launch, after idle time and when your PC locks.
- **Ad and tracker blocking:** strict in admin portals, full (including video ads) in the Web group.
- **Tab groups per client, multiple windows, and sites as apps** with their own taskbar icons.
- **Updates itself, safely:** every update is signed and checked before it installs.

## Install (Windows 10/11)

1. Open the **[latest release](https://github.com/d1same/cordon-releases/releases/latest)** and download **`Cordon Setup x.y.z.exe`**.
2. Run it. Windows may show **"Windows protected your PC"** the first time. Click **More info → Run anyway**. (Cordon isn't signed with a paid Microsoft certificate. Updates are protected by Cordon's own signature, below.)
3. Pick **Only for me** (recommended) and finish.
4. On first launch, create your **PIN** (8+ characters, or 6 with a letter). Then import a profile or bookmarks, or start fresh.

**Updating:** nothing to do. Cordon checks every few hours and installs updates when you close it, or when you click **Relaunch** on the update banner.

**Uninstalling:** Windows Settings → Apps → Cordon → Uninstall. This also erases all saved sign-ins on that PC.

## Files in each release

| File | What it is |
|---|---|
| `Cordon Setup x.y.z.exe` | The installer, the only file you need |
| `cordon-update.sig.json` | Cordon's signature for this installer (used by the built-in updater) |
| `latest.yml`, `*.blockmap` | Update feed files read by the app |
| `cordon-policy.json` + `.sig` | Only on critical security releases: tells older versions to update |

## How updates are protected

Every installer is signed with an offline key that never touches GitHub. Before installing anything, Cordon checks that:

1. the signature matches the key built into the app,
2. the version is the one announced (an old installer can't be re-sent as a new one),
3. the downloaded file is byte-for-byte the one that was signed.

If any check fails, the update is deleted and not installed. Even someone who took over this GitHub repository couldn't push an update to your PCs.

Release signing key fingerprint: `f985ce6f6a50a969`

<details>
<summary><b>Check a download yourself (optional)</b></summary>

In PowerShell, in the folder with the installer:

```powershell
$f = Get-Item ".\Cordon Setup *.exe"
[Convert]::ToBase64String([Security.Cryptography.SHA512]::Create().ComputeHash([IO.File]::ReadAllBytes($f.FullName)))
```

The output must equal the `sha512:` line in that release's `latest.yml`.
</details>

## Security at a glance

- Every page runs in Chromium's sandbox; websites get no access to your files or to Cordon itself.
- https only; certificate errors are never bypassed.
- Camera, microphone, location, notifications and USB/Bluetooth are blocked for websites.
- Downloads need your approval every time.
- Saved sign-ins are encrypted with your Windows account.
- Cordon refuses to start with debugging or proxy flags that could expose sessions.

## FAQ

**Is it free?** It's built for our MSP team. Ask your administrator before installing it on a client device.

**Mac?** Not yet; Windows first.

**Something wrong?** Tell your MSP administrator and include the version (Settings → About).
