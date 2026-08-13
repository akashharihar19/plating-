# Terminal QC Android Prototype

Camera-based QC prototype for reel-to-reel brass/gold terminal pins.

## Features in v0.1
- Android phone camera using CameraX
- Manual part number, batch, expected count, bend tolerance and calibration settings
- Pin candidate counting
- Straight-line fit through detected pin centers
- Per-pin bend deviation in pixels
- PASS/FAIL and NG count
- CSV inspection log
- NG image storage in app external files
- GitHub Actions APK build

## Detection method
The prototype segments high-contrast metallic pin candidates, finds connected components, sorts their centers along X, fits a least-squares straight line, and flags pins whose perpendicular distance from the fitted line exceeds the configured pixel tolerance.

This is an engineering prototype. Before factory acceptance, use controlled backlighting, fixed camera geometry, perspective correction, robust OpenCV morphology/contours, reference templates per part, and validated OK/NG datasets. Do not use the prototype alone for safety-critical or customer-release decisions.

## Build
Open the project in Android Studio with JDK 17, or let GitHub Actions build it. The workflow uses Gradle 8.13 and produces `app-debug.apk` as an Actions artifact.

CameraX 1.6.1 is used; Android Developers lists it as the current stable CameraX release as of July 2026.
