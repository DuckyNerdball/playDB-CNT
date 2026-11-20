# Changelog

## 1.5.0 (2026-11-19)

### New: the Mods tab

The launcher has a third tab, **Mods**. Each mod is added to the emulator's mod folder when you
press **Start game** and removed again when you untick it, so you can switch them on and off at any
time. Untick everything to play the network test exactly as it is.

* **Bot Match (Solo) and Bot Match (Duo)** (on by default): unchanged from 1.4.x, now a checkbox
  here (it was in the Setup tab).
* **CPU player names** (on by default): the random names for the 7 CPU players, now a separate
  checkbox. Untick it to keep the game's own `PCBot_1` ... `PCBot_7`.
* **NT Unlocks** (experimental): opens what the network test closes off:
  * the curtain in the House of Night (*"Cannot venture past this point in the network test"*)
  * the courtyard boundary (*"Here lies the boundary of the network test"*).

  The hall behind the curtain is empty in this version of the game.
* **Burning Forest Exploration** (experimental): lets you go down into the burning forest below the
  cliffs of the first tutorial map and walk around there. For your own character only:
  * no fall damage and no fall death
  * no warp back up the cliff
  * the camera keeps following you instead of switching to the fall-death camera.

  Enemies and CPU players still fall and die as usual. While ticked it applies in every mode
  (also Bot Match). Where there is no ground at all you keep falling: restart the mission.
* **Courtyard training targets** (experimental): train against bosses in the courtyard
  (**Travel > Courtyard Remembrance**). Each of the three targets (Giant adherent, Adherent,
  Graveyard Scarecrow) can become another character:
  * **10 bosses**: Vampyr, Beastridden, Giant Beastridden, Lady of the Bog, Rana, three Milhüsa
    Cavalry variants, Dark Leopard, Nikke
  * **8 kin**: Thaumaturge Avester, Gunslinger Beatrice, Baritone, Undead Marlowe, Nia, Valentius
    the Unwise, Black Wulf of Mors, Gargoyle
  * **the 6 Bloodsworn**: Albert, Bloodhand Jan, Trang Lanh, Sniper Layla, Senator Samir Patres and
    Zork, with their own look and gear and the AI of the tutorial's duel opponent
  * the three original targets, so they can be swapped around.

  A boss, kin or Bloodsworn always comes alone (the Adherent target normally spawns three). The
  target menu shows the character's name in your language. The picture stays the original one,
  because the game has no other pictures.

## 1.4.1 (2026-11-19)

* **Patch Lichii works with Lichii build 341 and later** ([#19](https://github.com/sikoGD/playDB-CNT/issues/19)).
  Those builds broke the patch in two ways, both fixed:
  * Their block list of Nintendo server names is stored differently, so the patch no longer found
    it and the game's login lookups were refused ("Online connection is required").
  * They connect to the login server through IPv6 sockets, which the patch did not redirect.
    The patch now handles IPv6 too: it redirects IPv6 connections, treats `::1` as this PC, and
    also handles the newer `GetAddrInfoExW` lookups.
  Tested with Lichii build 341: the game logs in and starts a new game. If you already patched
  your Lichii, the launcher updates the patch by itself the next time you press **Start game**.
* README rewritten: shorter, with the current state of things.

## 1.4.0 (2026-11-14)

> **Online play is not ready yet, but it is getting close.** We are a small team right now. If you
> want to take part in future online test matches, join our Discord server:
> **https://discord.gg/jX3KK8T4P**

### New

* **CPU players have names.** In Bot Match the 7 CPU players are no longer called `PCBot_1` ...
  `PCBot_7`: each session they get random names from a list of 20 (Quellyn, Morholt, Folcard,
  Leofric, Hunter Schmidt, Shira, Settler Heloise, Sieglinde, Amalric, Hieronymus, The Darkwraith,
  McDonnell, Laurentius, Cleric Isolde, Abelard, Nymue, Elana, Knight Wulfric, Thale of Shulva,
  Alvina). The launcher log lists the names picked for the session. The game only shows names of up
  to 16 characters, so the longer titles are shortened.
* **Allow in firewall** button (Online tab, Windows). One admin prompt adds inbound rules for the
  emulator and the launcher, so friends' games can reach yours. The tab shows whether the rule
  exists.
* **Lobby watcher** while hosting: the launcher log now reports friends' launchers joining (and warns
  when someone typed a different room password), their games connecting, each match that forms and
  whether the games went back to searching.
* **Match connection data.** The match server now hands the games the game-server address and
  session key in the format the game reads (traced on 2026-11-12), so matched games try to connect
  to each other on UDP port 15500.
* **Patch Lichii** (`version.dll`) logs the first game-match UDP packets in each direction, so a test
  run shows how far the connection got.

### Unchanged

* **Bot Match (Solo)** (mission 8000) and **Bot Match (Duo)** (mission 8020) keep their names and
  work as in 1.3.x.

### Online play: where it stands

Players can connect, sign in, meet in the same room and be matched together. Behind the scenes we
now get a single game into a running online match against our own stand-in game server: the game
accepts a remote player, loads the stage with CPU players, shows the start-point map, and has
briefly reached gameplay. What is still missing is the part where the stand-in server runs the
match phases (start-point choice and phase timer) the way the real servers do, and then relaying a
second real player into the same match. Until then, real online matches still return to searching.

## 1.3.2

* Hosting a room works on PCs with Radmin VPN or Hamachi installed.

## 1.3.1

* Bot Match comes in two modes: **Bot Match (Solo)** (mission 8000) and **Bot Match (Duo)**
  (mission 8020).

## 1.3.0

* **Patch Lichii**: a `version.dll` that lets stock Lichii / Eden builds go online through the
  launcher's servers.

## 1.2.1

* Resizable, scrollable window; Lichii 160+ data folder; custom PyInstaller loader (no antivirus
  false positive).

## 1.2.0

* **Bot Match**: a full Dusk Battle against 7 CPU players.
