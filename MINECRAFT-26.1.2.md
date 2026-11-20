# Minecraft 26.1.2 build

This Re:Play Mod source package supports Minecraft **26.1.2** through ReplayMod's `26.1` Gradle target. The upstream
multi-version project names the target after the 26.1 release family rather than creating a separate target for every
patch release.

## Requirements

- JDK 21
- Fabric Loader
- Fabric API for the Minecraft 26.1 release family
- Submodules initialized with `git submodule update --init --recursive`
- Several gigabytes of temporary disk space because the upstream preprocessor materializes intermediate versions

## Build

On Windows:

```text
gradlew.bat :26.1:build
```

On Linux or macOS:

```text
./gradlew :26.1:build
```

The finished JAR is written below `versions/26.1/build/libs/` and begins with `re-play-mod-26.1-`.
