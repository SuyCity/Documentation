
---
title: Set the Video Profile
description: 
platform: Windows
updatedAt: Tue Nov 20 2018 03:13:27 GMT+0000 (UTC)
---
# Set the Video Profile
## Introduction

Setting the video profile, either before or after a user joins a channel, enables the user to enjoy better video quality during a video call or video live broadcast.

## Implementations

Before proceeding, ensure that you have finished preparing the development environment. See [Integrate the SDK](../../en/Interactive%20Broadcast/windows_video.md) for more information.

Agora SDK uses the `setVideoEncoderConfiguration` API to set the video profile and each video profile corresponds to a set of video parameters, including the resolution, frame rate, bitrate and video orientation.

The parameters specified in this API are the ideal values under ideal network conditions. If the video engine cannot render the video with the specified parameters dut to poor network conditions, the parameters further down the list are considered.

```cpp
//cpp
// set video profile before join the channel

VideoEncoderConfiguration lpVideoConfig(640, 360, FRAME_RATE_FPS_15, 800, ORIENTATION_MODE_ADAPTIVE);

lpAgoraEngine->setVideoEncoderConfiguration(lpVideoConfig);
```

**Relevant APIs and descriptions**
* [`setVideoEncoderConfiguration`](https://docs.agora.io/en/Interactive%20Broadcast/API%20Reference/cpp/classagora_1_1rtc_1_1_i_rtc_engine.html#a9bcbdcee0b5c52f96b32baec1922cf2e)

## Considerations

- If you do not need to set the video profile after joining the channel, call `setVideoEncoderConfiguration` before `enableVideo` to reduce the render time of the first video frame.
- Adjustments to the set parameters can be made by the Agora SDK under poor network conditions. 
-  A live broadcast channel generally requires a higher bitrate for better video quality. Therefore, Agora recommends setting the bitrate in the live broadcast mode twice that in the communication mode. See [Set the bitrate](https://docs.agora.io/en/Interactive%20Broadcast/API%20Reference/cpp/structagora_1_1rtc_1_1_video_encoder_configuration.html#af10ca07d888e2f33b34feb431300da69) for details.
- For better video quality during a live broadcast, stable network connection is recommended.

## Frequently Asked Questions

### How to choose the video resolution, frame rate and bitrate?

Video profiles vary from case to case. For example, in a one-to-one online class, the video windows of the teacher and student are both large, which requires higher resolutions, frame rates, and bitrates. While in a one-to-four online class, the video windows of the teacher and students are smaller, so lower resolutions, frame rates, and bitrates are used to accommodate the downward bandwidth.

 The following profiles for different scenario are recommended:

- One-to-one video call: 
  - Resolution: 320 x 240; frame rate: 15 fps; bitrate: 200 Kbps
  - Resolution: 640 x 360; frame rate: 15 fps; bitrate: 400 Kbps
- One-to-many video call: 
  - Resolution: 160 x 120; frame rate: 15 fps; bitrate: 65 Kbps
  - Resolution: 320 x 180; frame rate: 15 fps; bitrate: 140 Kbps
  - Resolution: 320 x 240; frame rate: 15 fps; bitrate: 200 Kbps 

You can also customize the video parameters, such as by increasing the bitrate to ensure the video quality with the `setVideoEncoderConfiguration` API.