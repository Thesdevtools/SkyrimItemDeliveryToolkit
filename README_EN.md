[日本語](./README.md) | [English]

# Skyrim Item Delivery Toolkit (SIDT)

Send selected items to loaded NPCs or the player while Skyrim is running—without restarting the game and without editing NPC base records.

SIDT was originally developed for Skyrim VR, where leaving the VR environment to adjust an inventory is especially disruptive. After the same workflow was implemented and validated on Skyrim AE 1.6.1170, the project was expanded to support both runtimes.

## Download

- [SIDT 0.9.8 Release](https://github.com/Thesdevtools/SkyrimItemDeliveryToolkit/releases/tag/v0.9.8)
- For normal use, download `Skyrim-Item-Delivery-Toolkit-0.9.8.zip` from the release assets.
- The corresponding source is `Skyrim-Item-Delivery-Toolkit-0.9.8-src.zip` in the same release.

> GitHub's automatically generated `Source code (zip)` and `Source code (tar.gz)` archives contain only this distribution repository's metadata. They are not the corresponding SIDT source package.

## Security check after installation

Before installing or running SIDT, check the downloaded archive with the
security tools you normally trust. The SHA-256 value in the release notes lets
you confirm that your download matches the published artifact. A matching hash
does not, by itself, guarantee safety.

- **Windows 10/11:** Right-click the archive, choose **Show more options** when shown, then choose **Scan with Microsoft Defender**.
- **VirusTotal:** You may also upload the archive to [VirusTotal](https://www.virustotal.com/gui/home/upload) and review the result yourself.

Do not rely solely on a third-party scan result; decide for yourself whether to
use any downloaded binary.

## How it works

SIDT has two components:

- **Delivery Post** is a Windows desktop application that reads your MO2 setup and creates delivery instructions.
- **Delivery Courier** is an SKSE plugin that receives those instructions inside Skyrim and adds only the quantity needed to reach each configured minimum.

Courier never edits NPC base records, removes items, changes equipment, or triggers AI reevaluation.

SIDT is a specialized utility rather than a general-purpose quality-of-life or balance mod. Sending arbitrary items into a running game can be used like a cheat in normal play, but it is also useful for MOD development, setup verification, screenshots, and equipment testing without restarting Skyrim. It is not intended to replace existing item distributors, console tools, or inventory managers.

## Supported runtimes

- Skyrim VR 1.4.15 with SKSEVR 2.0.12 or later
- Skyrim AE 1.6.1170 with SKSE64 2.2.6 or later

Skyrim SE 1.5.97 is not supported.

## Requirements

- Mod Organizer 2
- The appropriate SKSE build for the selected Skyrim runtime
- .NET 8 Desktop Runtime (x64)

## Installation and basic use

1. Install the main archive with Mod Organizer 2.
2. In the FOMOD, select exactly one runtime: Skyrim VR or Skyrim AE 1.6.1170.
3. Open the installed MOD folder and run `SkyrimItemDeliveryPost.exe`.
4. On first launch, confirm the proposed MO2 mods folder, profile, and delivery output folder.
5. Start Skyrim, select recipients and items in Delivery Post, and choose **Send Delivery**.

The minimum count is a target: Courier adds items only when the recipient has fewer than the configured amount.

- **AE:** Delivery is immediate while gameplay is running. If Skyrim is paused or a menu is open, return to the game.
- **VR:** Timing depends on the headset, connection software, and runtime. If a delivery remains pending, open and close an in-game menu once.

Observed examples:

- Pico + SteamVR: immediate delivery observed
- Pico + Virtual Desktop / VDXR: delivery observed after a menu interaction

VR testing is necessarily limited by the headsets, connection software, and runtimes available to the author. Reports from other VR environments are very welcome.

## Current limitations

- Delivery Post currently scans selectable weapon and armor records, plus a small built-in Vanilla essentials catalog.
- **Food items are not yet available for selection. Food delivery support is planned for a future update.**
- Recipients must be loaded when Courier processes the instruction. Unloaded NPCs are not retried automatically.
- Broad compatibility with every other SKSE vtable hook cannot be guaranteed.

## Troubleshooting

- Confirm that Delivery Post and MO2 are using the same profile.
- Confirm that the output path is the physical MO2 `overwrite` folder or an explicitly selected output MOD.
- Check `SkyrimItemDeliveryCourier.log` in the SKSE log directory.
- In VR, open and close a menu when a delivery remains pending.
- In AE, close the menu and return to gameplay.

To reset Delivery Post completely, close it and remove `%LOCALAPPDATA%\SkyrimItemDeliveryPost`. Do not remove your entire MO2 overwrite folder.

## Source and license

SIDT is distributed under **GPL-3.0-only**. The corresponding source archive for each binary release is attached to the same release. Third-party copyright notices and license texts are included in the installed `SIDT Docs` folder.

This GitHub repository is used as a release distribution location. It is not the development repository, and Pull Requests or feature requests are not accepted here.

## Development and AI disclosure

SIDT is a human-directed utility project. The author defined its requirements, architecture, safety rules, user experience, and release decisions, and performed the VR and AE validation on real game environments.

As part of learning more about Skyrim MOD development, AI coding tools were used extensively during development, including implementation, refactoring, code review, technical investigation, documentation, localization, release packaging, and test planning. The author reviewed the resulting work, made the final design decisions, and verified the released behaviour through builds and real-hardware testing.

Some promotional illustrations and parts of the English and Japanese documentation were created or drafted with generative AI and then selected and edited by the author. AI-generated illustrations are concept images and are not in-game footage. SIDT does not include AI-generated voices, dialogue, game textures, meshes, or character assets.
