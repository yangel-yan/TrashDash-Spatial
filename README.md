# TrashDash Spatial

TrashDash 垃圾跑酷·空间版，基于 Unity Technologies 的 Trash Dash 跑酷示例，使用 PICO Spatial Adapter 在 Shared Space 的立体窗口中呈现游戏。

看向跑道，捏一下短跳，捏住高跳。越过高低路障，收集鱼骨，连续过栏可将技巧加分提高到四倍。游戏保留角色、配饰、道具、任务、商店与本地进度。本版本为开发预览。

## Repository

This repository contains the Android Gradle export prepared for PICO Vibe Lab. Gameplay is compiled into the ARM64 IL2CPP library; exported Spatial scenes, models, UI and Addressables are packaged with it.

The editable Unity project is maintained separately. Any gameplay, scene, package or content change requires a new full Unity export and IL2CPP prebuild.

## Build

- Unity: 6000.3.25f1
- Mode: PICO Spatial / Shared Space
- Android application ID: `com.yangel.TrashDashSpatial`
- Version: 1.3
- Backend / ABI: IL2CPP / ARM64
- Minimum Android SDK: 29

Run `./gradlew assembleRelease` on macOS/Linux or `.\gradlew.bat assembleRelease` on Windows with an Android SDK and a compatible JDK. The generated Gradle configuration records the Android toolchain versions.

`libil2cpp.so` is precompiled. `buildIl2Cpp` is disabled and `Il2CppOutputProject` is omitted so the cloud build does not need a local Unity Editor or its IL2CPP toolchain. `.vibelab-prebuilt.json` records the native library and metadata hashes.

## PICO Vibe Lab

`vibelab.yaml` contains the application description, repository URL and release metadata. `vibelab-assets/` contains the 1024×1024 icon, 2560×1440 cover and three detail images. The existing poster and detail images are earlier development previews. The controls in this export are described above.

Release workflow:

```powershell
pico-release-cli-cn add
pico-release-cli-cn commit
pico-release-cli-cn push
pico-release-cli-cn state
```

The preview page must have the required agreements accepted before submission.

## Validation scope

Local Gradle validation checks both the complete export and the precompiled build, including native library inventories, hashes and APK alignment. The Unity project used for this export was also tested on PICO hardware. HUD and results text were verified with the window stationary.

Some SDK native libraries may retain 4 KB ELF LOAD alignment. The export reports these as warnings and does not claim full 16 KB page compatibility.
