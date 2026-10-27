# capacitor-camera-preview-localfeed

The Local Feed's iPhone and Android apps ship [@capgo/camera-preview](https://github.com/Cap-go/capacitor-camera-preview) **8.11.9**, which is licensed under the Mozilla Public License 2.0 (`LICENSE`, the package's own), with a few changes of our own. The license asks that the source of what we ship — our changes included — be available to everyone who gets the app. This repository is that source.

## What we changed, and why

We changed four of its files so the camera never crashes the app when it stops, and so it tells the app when it stops or is interrupted. All 31 changes are in `capgo-camera-preview-8.11.9-localfeed.patch` (26 hunks):

- `ios/Sources/CapgoCameraPreviewPlugin/CameraController.swift`
- `ios/Sources/CapgoCameraPreviewPlugin/Plugin.swift`
- `android/src/main/java/app/capgo/capacitor/camera/preview/CameraPreview.java`
- `android/src/main/java/app/capgo/capacitor/camera/preview/CameraXView.java`

## The source

- @capgo/camera-preview 8.11.9 upstream: https://github.com/Cap-go/capacitor-camera-preview/tree/8.11.9
- The exact package the app is built from: https://registry.npmjs.org/@capgo/camera-preview/-/camera-preview-8.11.9.tgz

To get the files exactly as the app ships them:

```sh
npm pack @capgo/camera-preview@8.11.9
tar -xzf capgo-camera-preview-8.11.9.tgz
cd package
patch -p1 < ../capgo-camera-preview-8.11.9-localfeed.patch
```

(`git apply ../capgo-camera-preview-8.11.9-localfeed.patch` works too.) The patch is generated from the script that applies the same changes to the app's own build, and these files are replaced whenever that script changes.

Questions: hello@thelocalfeed.com
