# playDB-CNT - Play Duskbloods (Network Test) launcher

A launcher for Windows, Linux and macOS that runs **The Duskbloods Network Test** on Switch 2
emulators (Eglantine, Lichii, Eden). The game needs its online services even to play alone, so the
launcher runs small stand-in servers on your own PC and starts the emulator pointed at them.

> **Online play with other people is not ready yet, but it is close.** We are a small team. To
> take part in future online test matches, join our **Discord: https://discord.gg/jX3KK8T4P**

## What you get

* **Play offline**: the game boots past *"Online connection is required"* and plays normally. All
  traffic stays on your PC (127.0.0.1).
* **Bot Match**: two extra entries in **Battle Remembrance > Tutorials**, each a full Dusk Battle
  on the whole map against 7 CPU players, from the first phase to the final battle:
  **Bot Match (Solo)** (everyone for themselves) and **Bot Match (Duo)** (alliances of two). The CPU
  players get random names each session.
* **Patch Lichii** (Windows): lets stock Lichii and Eden builds play (see below).
* **Online rooms** (in testing): friends can connect and be matched together, but the match itself
  does not start yet. See [ONLINE.md](ONLINE.md).

What changed in each version: [CHANGELOG.md](CHANGELOG.md).

## Download and start

Get the newest files from the [Releases page](https://github.com/sikoGD/playDB-CNT/releases).

**Windows**: download `Play.Duskbloods.exe`, put it anywhere (next to your emulator is easiest)
and run it.

**Linux**: download `Play-Duskbloods-linux.tar.gz`, then:

```
sudo apt install python3 python3-venv python3-tk     # once (Fedora: python3 python3-tkinter)
tar xf Play-Duskbloods-linux.tar.gz && cd Play-Duskbloods-linux
./play-duskbloods.sh
```

**macOS**: install Python 3 from python.org, unzip `Play-Duskbloods-mac.zip` and double-click
**Play Duskbloods.command** (the first time: right-click, **Open**).

On Linux and macOS the first start takes a minute to install three small Python libraries. More
detail: [linux/README-LINUX.md](linux/README-LINUX.md), [mac/README-MAC.md](mac/README-MAC.md).

Then, in the launcher:

1. Pick the **game**: a `.nup` file (**Browse**) or the game folder that contains
   `base/exefs/main` (**Folder**).
2. Pick the **emulator** (`eglantine`, `lichii`, `eden`; found automatically when it's next to the
   launcher).
3. Have your own `prod.keys` and `title.keys` in the emulator's `keys` folder. The launcher shows
   the exact folder if they are missing.
4. Press **Start game**.

## Which emulator?

* **Duskbloods builds of Eglantine or Lichii** (v31 and later): best results, nothing else needed.
* **Stock Lichii or Eden on Windows** (including Lichii build 341 and later): press **Patch
  Lichii** (or **Patch Eden**) once in the Setup tab. It adds one file, `version.dll`, next to the
  emulator; **Remove patch** deletes it. The patch only acts when the launcher starts the game.
* **Stock Lichii or Eden on Linux or macOS**: not supported yet (Patch Lichii is Windows-only).
  Without it the game stops at *"Online connection is required"* (error 2321-4992).

## Problems

* **"Online connection is required" / "Unable to connect to the internet"**: the emulator has no
  Duskbloods online support. On Windows use **Patch Lichii**; with Lichii build 341+ you need
  launcher 1.4.1 or later.
* **"Virus detected" when downloading**: a false positive that some antivirus programs report
  for Python programs packed into one exe. You can also run the launcher from source
  (`python play_duskbloods.py`).
* **"Port 18443 is already in use"**: an earlier session is still running; close it and retry.
* **Reporting a bug**: press **Open logs** and attach the newest `runs/<time>` folder to an
  [issue](https://github.com/sikoGD/playDB-CNT/issues), or post it on our
  [Discord](https://discord.gg/jX3KK8T4P).

## Privacy

* Offline, the servers listen on **127.0.0.1 only** and nothing is sent to any real service.
* Online rooms only talk to the host's PC. The room password is never sent, only a hash of it.
* No keys, game files, saves or certificates are in this repository or the exe. Test certificates
  are created on your own PC the first time you play.

## For developers

| Path | What |
|---|---|
| `play_duskbloods.py` | the launcher (Tk window, emulator discovery, sessions) |
| `dusk_mods.py` | Bot Match: regulation patch, menu text, CPU player names |
| `tools/npln_server/`, `tools/dusk_server/` | the stand-in servers and the room matchmaking |
| `tools/online_shim/` | the Patch Lichii `version.dll`, with source |
| `tools/ooz/` | the Kraken decompressor ooz (GPL-3.0, with source), to read the game's menu text |
| `build_exe.py` | builds the Windows exe with PyInstaller |

Build the exe: `pip install pyinstaller cryptography grpcio zstandard`, then
`python build_exe.py` (output in `dist/`).

## Legal

You must provide your own legally obtained game and keys. This project is not affiliated with
FromSoftware, Nintendo or any emulator project, and contains no copyrighted game files. The banner
and icon are screenshots of the game's title screen, used for identification only.

## About

Made by **sikoGD**, part of the work to get The Duskbloods Network Test running on Switch 2
emulators. Discord: https://discord.gg/jX3KK8T4P

If this saved you time and you'd like to support the work:

[![Buy Me a Coffee](https://img.shields.io/badge/Buy%20Me%20a%20Coffee-support-d8a657?logo=buymeacoffee&logoColor=white)](https://buymeacoffee.com/rickjrbfl)
