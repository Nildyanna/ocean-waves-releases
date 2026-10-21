# Ocean Simulation and Wallpaper

Download the [latest release](https://github.com/Nildyanna/ocean-waves-releases/releases/latest). This repository contains installers, release metadata and verification material. Development source is maintained separately in a private repository. No GitHub Actions are used.

## Choose a package

- **Windows x64:** `Ocean-Setup-0.1.0-Windows-x64.exe`. The installer offers interactive browser view, live desktop wallpaper, or both. Browser mode uses your WebGPU-capable browser and needs no Python. Wallpaper uses Microsoft WebView2; the installer includes Microsoft's runtime bootstrapper if needed. The wallpaper starts its coastal/reef tour by default.
- **Linux x86-64:** `Ocean-Setup-0.1.0-Linux-x86_64.run`. Run `sh Ocean-Setup-0.1.0-Linux-x86_64.run`. Choose browser, wallpaper, or both. The full package includes Electron. GNOME and KDE Plasma adapters cover X11/Wayland; other X11 desktops use a desktop-layer window.
- **Linux browser only:** `Ocean-Simulation-0.1.0-Linux.tar.gz`. Extract, then `sh Launch-Ocean.sh`. Python 3.9+ and a current browser with working WebGPU/GPU drivers are required. OpenSSL is needed for signed updates.

Windows installer selection, local serving, signature verification and uninstallation were tested. Linux installation, local serving and signed updates were tested under WSL. **Linux wallpaper GPU presentation and native GNOME/Plasma placement remain experimental and unverified:** WSL rendering tests failed to present the scene correctly. Consult `linux/README.md` inside the Linux package for dependencies and desktop setup. Installation does not automatically enable extensions or replace wallpaper settings.

## Updates and controls

Launchers check the signed update feed automatically at launch. In the simulation, press **H → Check for updates**, then **Install update** when offered. Offline startup keeps the installed version. Linux retains previous version folders and switches the current version atomically; relaunch after a menu update. Windows preserves component choices and external settings. Add `--no-update` to the launcher to skip a launch check.

WASD moves, mouse-look changes view, both mouse buttons held moves forward, T starts the tour, V allows diving. Standard gamepads work in the interactive view. Passive wallpaper ignores gamepads.

## Verify downloads

Download the package, its matching `.sig`, and `PUBLIC-KEY.pem`. With OpenSSL:

```sh
openssl dgst -sha256 -verify PUBLIC-KEY.pem -signature Ocean-Setup-0.1.0-Linux-x86_64.run.sig Ocean-Setup-0.1.0-Linux-x86_64.run
```

Use the same command with the Windows installer or browser archive filenames. `SHA256SUMS` and `update-manifest.json` have separate signatures. The updater pins this RSA-3072 public key and checks signed package hashes and sizes before installation. Obtain the key from a trusted first installation or this repository. Detached release signatures are not Windows Authenticode certificates; Windows may show an unknown-publisher warning.

## Credits and licensing

The original ocean renderer is **web-ocean by Maksymilian Dendura (Noniv)**, [github.com/Noniv/web-ocean](https://github.com/Noniv/web-ocean), MIT License, copyright 2026 Maksymilian Dendura. The original license and credit appear in installers and packages. This independent adaptation is not endorsed by the original author.

Models/textures have separate licenses recorded in packaged `assets/README.md`, `assets/premade/README.md` and `assets/premade/replacement-catalog.json`. Some wildlife assets are non-commercial; these packages do not grant commercial rights to those assets. Electron and WebView2 retain their own notices.
