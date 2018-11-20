
---
title: Set the Camera Focus
description: 
platform: Android
updatedAt: Tue Nov 20 2018 08:19:07 GMT+0000 (UTC)
---
# Set the Camera Focus
## Introduction

Camera focus is a commonly used function in video calls to enable high quality video capture.

Agora SDK provides a set of camera management methods on the Android platform, with which users can switch between the front and rear camera, set the camera zoom factor or set the focus position.

## Implementations

Before proceeding, ensure that you have finished preparing the development environment. See [Integrate the SDK](../../en/Video/android_video.md) for details.

```java
    //java
    // Check whether auto face-focus function is supported and enable auto-face focus
    boolean shouldSetFaceMode = rtcEngine.isCameraAutoFocusFaceModeSupported();
    rtcEngine.setCameraAutoFocusFaceModeEnabled(shouldSetFaceMode);

    // Check whether manual focus function is supported and set the focus
    boolean shouldManualFocus = rtcEngine.isCameraFocusSupported();
    if (shouldManualFocus) {
        // Set the camera focus at (50, 100)
        float positionX = 50.0f;
        float positionY = 100.0f;
        rtcEngine.setCameraFocusPositionInPreview(positionX, positionY);
    }
```

**Relevant APIs and descriptions**

-  [`isCameraFocusSupported`](https://docs.agora.io/en/Video/API%20Reference/java/classio_1_1agora_1_1rtc_1_1_rtc_engine.html#a0e20f04ccecfc41aa23bf63116c9a8cd): Checks whether the camera zoom function is supported.
- [`isCameraAutoFocusFaceModeSupported`](https://docs.agora.io/en/Video/API%20Reference/java/classio_1_1agora_1_1rtc_1_1_rtc_engine.html#a09f61f738cf7d8a1902761e03a7fa600): Checks whether the camera auto-face focus function is supported.
- [`setCameraFocusPositionInPreview`](https://docs.agora.io/en/Video/API%20Reference/java/classio_1_1agora_1_1rtc_1_1_rtc_engine.html#aba273e4337a760d883b6c7c1344183c0): Sets the camera manual focus position.
- [`setCameraAutoFocusModeEnabled`](https://docs.agora.io/en/Video/API%20Reference/java/classio_1_1agora_1_1rtc_1_1_rtc_engine.html#a7e67afe7ad0045448fe0bd97203afcee): Enables the camera auto-face focus function.