
---
title: In-ear Monitoring
description: How to enable in-ear monitoring and adjust the volume
platform: iOS
updatedAt: Tue Nov 20 2018 02:47:55 GMT+0000 (UTC)
---
# In-ear Monitoring
In-ear monitoring can provide a mix of audio sources (for example the vocal and the music) to the host with a low latency, frequently used in professional scenarios such as concerts.
Agora SDK supports the in-ear monitoring function and adjusting the volume of the in-ear monitor.

## Implementation

```swift
// swift
// Enables in-ear monitoring. The default value is false.
agoraKit.enable(inEarMonitoring: true)

// Sets the volume of the in-ear monitor. The value range is 0 to 100, and the default is 100 which represents the original volume captured by the microphone.
agoraKit.setInEarMonitoringVolume(50)
```

```objective-c
// objective-c
// Enables in-ear monitoring. The default value is NO.
[agoraKit enableInEarMonitoring:YES];

// Sets the volume of the in-ear monitor. The value range is 0 to 100, and the default is 100 which represents the original volume captured by the microphone.
[agoraKit setInEarMonitoringVolume: 50];
```

## Considerations

The above methods have return values. If the API fails, the return is < 0.