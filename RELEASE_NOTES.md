# Re:Play Mod for Minecraft 26.1.2

Low-memory ReplayMod derivative intended for PCs with around 4 GB of system RAM.

## Changes from upstream ReplayMod

- Bounded 32-packet recording queue to prevent an unlimited in-memory backlog.
- Back-pressure when storage cannot keep up with incoming replay packets.
- Automatic replay post-processing disabled by default.
- Low-memory Gradle defaults for local source builds.
- Re:Play Mod product name and JAR filename.

## Installation

Install Fabric Loader and the matching Fabric API for Minecraft 26.1.2, then place the Re:Play Mod JAR in the `mods`
folder. Do not install upstream ReplayMod at the same time because both use the `replaymod` internal mod id.

This derivative is licensed under GPL-3.0-or-later. It is not an official ReplayMod release.
