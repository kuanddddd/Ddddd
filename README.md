# Ddddd

**Ddddd 1.0.0 Beta** — Android application source repository.

## Repository contents

- `Ddddd/` — extracted Android project source, Gradle configuration, resources, and related module/probe projects.
- `Ddddd-1.0.0-Beta-source.zip` — original source archive supplied for this project.
- `.github/workflows/build-apk.yml` — GitHub Actions workflow for building a Debug APK and publishing it as a GitHub Release.

The Android project is in the `Ddddd/` directory. The launcher icon and app resources are kept in the source tree.

## Build

The project uses Gradle and JDK 21. From the repository root:

```bash
cd Ddddd
gradle --no-daemon :app:assembleDebug
```

The APK is generated at:

```
Ddddd/app/build/outputs/apk/debug/app-debug.apk
```

## Download APK

When a build has completed and the release is published, download the APK from the [GitHub Releases page](https://github.com/kuanddddd/Ddddd/releases).

The release workflow is configured to publish the build without the in-app update checker.

## Source changes

Keep the extracted `Ddddd/` project directory in the repository so it can be browsed and reused directly without re-uploading the source archive.
