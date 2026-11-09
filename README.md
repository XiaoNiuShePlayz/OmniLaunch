OmniLaunch
A fast, native Minecraft: Java Edition launcher for Windows, built for performance.

OmniLaunch is written in C++ with a Direct2D interface. It has no Electron and no web view, and it doesn't keep a heavy background process running while you play. The whole launcher is one small .exe file.

⚠️ Status: in development. Microsoft sign-in is built and is waiting for Mojang to approve the app. Until then you can play singleplayer with an offline name.

Features
🎮 Any version, separate instances
Create an instance of any Minecraft release since 1.7.10 (snapshots optional), vanilla or Fabric.
Each instance has its own mods, settings, resource packs and worlds.
The right Java version is downloaded automatically (Java 8, 17, 21 or 25, Mojang's own builds).
⚡ One-click performance profiles
Profile	What it does
Max FPS	Lowers the screen resolution while you play, render distance 8, no motion blur, no clouds
Balanced	Native resolution, render distance 8, no motion blur, no clouds
Lean	Loads only the core performance mods, for the steadiest frame times
My setup	Your own settings, unchanged
Profiles are applied each time you press Play. Every setting can also be changed by hand. The resolution change is temporary: Windows switches back as soon as the game closes.

📊 Built-in benchmark
With the CorePilot mod installed, one click opens the game in fullscreen, flies over terrain for about a minute and reports your average FPS and 1% lows, so you can compare profiles with real numbers.

🧩 Mod browser
Search Modrinth and CurseForge for mods, resource packs and shaders inside the launcher.
Install picks the newest version that fits your instance and adds required dependencies automatically.
Installed mods show their real name and icon, can be switched on or off, removed (moved to a trash folder, not deleted), and updated in one click.
📥 Bring your setup with you
OmniLaunch finds existing setups from the Minecraft Launcher, Prism Launcher, CurseForge, Modrinth App, GDLauncher and OneClient and imports them in one click: mods, settings, worlds, server list and packs. When another launcher doesn't record the version, it's detected from your mods. Importing copies files; the original is never changed.

👤 Microsoft account sign-in
Sign in on Microsoft's own website with the device code flow. OmniLaunch never sees your password.
Your sign-in token is stored only on your PC, encrypted with Windows DPAPI.
An offline name is also available for singleplayer.
☕ Java tuning
Choose memory and garbage collector: generational ZGC (smoothest frame times), tuned G1, or vanilla defaults.

Safety and privacy
Official sources only. Game files, libraries and Java come from Mojang, and Fabric from FabricMC. Mods come only from cdn.modrinth.com and CurseForge's CDN.
Every download is hash-checked (SHA-1 / SHA-512) against what Mojang, Fabric, Modrinth or CurseForge publish, and rejected if it doesn't match.
No servers of our own. OmniLaunch sends nothing to us: no analytics and no tracking.
Your data stays local in %USERPROFILE%\.omnilaunch.
Requirements
Windows 10 or 11 (64-bit)
A copy of Minecraft: Java Edition for online play
Download and run
Download OmniLaunch.exe from the Releases page.
Run it. There's no installer, and no DLLs or extra runtimes are needed.
Command line
omnilaunch-cli.exe uses the same engine:

omnilaunch-cli instances | versions | create NAME --mc VERSION [--vanilla] | detect | import N
omnilaunch-cli install | play | bench | mods | search QUERY | add PROJECT
Run omnilaunch-cli --help for all options.

Building from source
You need MinGW-w64 (g++ 13 or newer).

cd launcher
powershell -ExecutionPolicy Bypass -File build.ps1
This builds OmniLaunch.exe (the window) and omnilaunch-cli.exe as static executables.

File	Purpose
engine.hpp	Version install, instances, profiles, launching, benchmark
auth.hpp	Microsoft sign-in (device code → Xbox Live → Minecraft)
mods.hpp	Modrinth / CurseForge, mod management, importing from other launchers
gui.cpp	The launcher window (Direct2D, DirectWrite, WIC)
cli.cpp	Command-line interface
API keys for your own build
Microsoft sign-in needs an Azure app registration with "Allow public client flows" enabled, approved by Mojang at https://aka.ms/mce-reviewappid. Enter its Application (client) ID in Settings.
CurseForge browsing needs a free API key from https://console.curseforge.com. Modrinth needs no key.
Disclaimer
OmniLaunch is an independent project. It is not affiliated with, endorsed by or connected to Mojang Studios or Microsoft. Minecraft is a trademark of Mojang Studios. You need to own Minecraft: Java Edition to play online.
