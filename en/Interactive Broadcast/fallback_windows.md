
---
title: Improve Expereience Under Poor Network Conditions
description: 
platform: Windows
updatedAt: Wed Nov 21 2018 14:06:37 GMT+0000 (UTC)
---
# Improve Expereience Under Poor Network Conditions
## Introduction

The audio and video quality of a live broadcast or a video chat will deteriorate under unreliable network conditions. To improve the efficiency of a live broadcast or a video chat, the `setLocalPublishFallbackOption` and `setRemoteSubscribeFallbackOption` interfaces are added. These interfaces allow the SDK to automatically disable the video stream when the network conditions cannot support both audio and video, and enable the video when the network conditions improve. `onLocalPublishFallbackToAudioOnly` or `onRemoteSubscribeFallbackToAudioOnly` is triggered when the stream falls back to audio-only or when the stream switches back to the video.

## Implementation

```C++
// Initialize the RtcEngineParameters object. 
RtcEngineParameters rep(*lpAgoraEngine);

// Enable the dual-stream mode (Configuration for the local)
int nRet = rep.enableDualStreamMode(static_cast<bool>(true));

// Configurations for the publisher
// When the network condition is poor, send video stream only. 
nRet = rep.setLocalPublishFallbackOption(static_cast<STREAM_FALLBACK_OPTIONS>(STREAM_FALLBACK_OPTION_AUDIO_ONLY));

// Configurations for the subscriber.
// Try to receive low stream under poor network conditions. When the current network conditions are not sufficient for video streams, receive audio stream only. 
nRet = rep.setRemoteSubscribeFallbackOption(static_cast<STREAM_FALLBACK_OPTIONS>(STREAM_FALLBACK_OPTION_AUDIO_ONLY));

```

## API Reference
* [enableDualStreamMode](https://docs.agora.io/en/Interactive%20Broadcast/API%20Reference/cpp/classagora_1_1rtc_1_1_rtc_engine_parameters.html#a65faf883ce4aa9d596741552825cbd33)
* [setLocalPublishFallbackOption](https://docs.agora.io/en/Interactive%20Broadcast/API%20Reference/cpp/classagora_1_1rtc_1_1_rtc_engine_parameters.html#a0402734b50749081b20db3826f6f00ec)
* [setRemoteSubscribeFallbackOption](https://docs.agora.io/en/Interactive%20Broadcast/API%20Reference/cpp/classagora_1_1rtc_1_1_rtc_engine_parameters.html#a50e727c34b662de64c03b0479a7fe8e7)

## Considerations

When the network conditions are poor, the SDK will automatically fallback to the user-defined low stream. 
