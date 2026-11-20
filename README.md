# Re:Play Mod

Re:Play Mod is a low-memory derivative of [ReplayMod](https://github.com/ReplayMod/ReplayMod), aimed at Minecraft
players using PCs with about 4 GB of system RAM. It retains ReplayMod's features while changing the unsafe memory
defaults that matter most on constrained systems.

## Low-memory changes

- The recording writer has a bounded 32-packet queue. If storage cannot keep up, recording applies back-pressure
  instead of retaining an unlimited number of packets until the game runs out of memory.
- Automatic replay post-processing is off by default. It can still be enabled in the recording settings.
- Gradle uses a 1.2 GB heap, one worker, no parallel execution and no persistent daemon.
- The produced archive is named `re-play-mod-<minecraft>-<version>.jar` and the in-game name is **Re:Play Mod**.

The internal mod id and resource namespace remain `replaymod`. This preserves `.mcpr` compatibility, existing
configuration and third-party integrations. Do not install Re:Play Mod and upstream ReplayMod together.

## Recommended 4 GB setup

- Allocate **1536 MB** to Minecraft. Do not exceed 2 GB on a 4 GB system.
- Use Fabric with Sodium and Lithium where those mods support your Minecraft version.
- Keep render distance at 6-8 chunks and simulation distance at 5 chunks.
- Close browsers and launchers after Minecraft starts.
- Export video after closing other programs. FFmpeg rendering still needs substantial CPU, disk space and memory.

These changes cap Re:Play Mod's recording backlog; they cannot make modern Minecraft itself fit every 4 GB computer.
Recording on a slow HDD may briefly reduce FPS when the queue applies back-pressure, which is preferable to a crash.

## Building one Minecraft version

Use JDK 21, initialize submodules, then build only the version you need:

```text
git submodule update --init --recursive
./gradlew :1.21.11:build
```

For Minecraft 26.1.2, use the upstream `26.1` target (Minecraft patch releases share that target):

```text
./gradlew :26.1:build
```

Building all supported Minecraft versions is not suitable for a 4 GB PC. Output is written under
`versions/<minecraft-version>/build/libs/`.

## License and attribution

Re:Play Mod is based on ReplayMod by CrushedPixel, johni0702 and contributors. It is distributed under the GNU General
Public License, version 3 or (at your option) any later version. See `LICENSE.md` and `NOTICE.md`.
