# TrashDash Spatial

TrashDash 垃圾跑酷·空间版，基于 Unity Technologies 的 Trash Dash 跑酷示例，使用 PICO Spatial Adapter 在 Shared Space 的立体窗口中呈现游戏。

支持换道、跳跃、滑铲、空间按钮与捏合短拖，保留角色、配饰、道具、任务、商店与本地进度。本版本为开发预览。

## Repository

This repository contains the Android Gradle export prepared for PICO Vibe Lab. Gameplay is compiled into the ARM64 IL2CPP library; exported Spatial scenes, models, UI and Addressables are packaged with it.

The editable Unity project is maintained separately. Any gameplay, scene, package or content change requires a new full Unity export and IL2CPP prebuild.

## Build

- Unity: 6000.3.25f1
- Mode: PICO Spatial / Shared Space
- Android application ID: `com.yangel.TrashDashVR`
- Version: 1.3
- Backend / ABI: IL2CPP / ARM64
- Minimum Android SDK: 29

Run `gradle assembleRelease` with an Android SDK and a compatible JDK/Gradle installation. The generated Gradle configuration records the Android toolchain versions.

`libil2cpp.so` is precompiled. `buildIl2Cpp` is disabled and `Il2CppOutputProject` is omitted so the cloud build does not need a local Unity Editor or its IL2CPP toolchain. `.vibelab-prebuilt.json` records the native library and metadata hashes.

## PICO Vibe Lab

`vibelab.yaml` contains the application description, repository URL and release metadata. `vibelab-assets/` contains the 1024×1024 icon, 2560×1440 cover and three detail images. Detail images are labelled development previews and were captured in the Unity Editor.

Release workflow:

```powershell
pico-release-cli-cn add
pico-release-cli-cn commit
pico-release-cli-cn push
pico-release-cli-cn state
```

The preview page must have the required agreements accepted before submission.

## Validation scope

Local Gradle validation checks both the complete export and the precompiled build, including native library inventories, hashes and APK alignment. This does not replace headset testing of Spatial input, window manipulation, text rendering and performance.

Some SDK native libraries may retain 4 KB ELF LOAD alignment. The export reports these as warnings and does not claim full 16 KB page compatibility.
