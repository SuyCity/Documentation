
---
title: Audio-related Issues
description: 
platform: Audio-related Issues
updatedAt: Fri Nov 23 2018 02:54:54 GMT+0000 (UTC)
---
# Audio-related Issues
### My H5 game integrates the Agora SDK v2.2.0 for iOS. When the host uses WKWebview with Layabox and joins the channel, why is the game volume very low?
The H5 game loaded by WKWebView plays audio by AVAudioSession instead of the SDK.

To fix this issue, call the `AudioProfile` method and set `scenario` to the `Game Streaming` mode:
`self.agoraEngine setAudioProfile:(AgoraRtc_AudioProfile_Default) scenario:(AgoraRtc_AudioScenario_GameStreaming)`.

Setting `scenario` to the `Game Streaming` mode may lead to echo issues. If you have any concerns, please contact Agora technical support.
