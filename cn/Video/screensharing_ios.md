
---
title: 进行屏幕共享
description: 
platform: iOS
updatedAt: Tue Nov 20 2018 08:17:05 GMT+0000 (UTC)
---
# 进行屏幕共享
## 功能简介
在视频通话或互动直播中进行屏幕共享，可以将说话人或主播的屏幕内容，以视频的方式分享给其他说话人或观众观看，以提高沟通效率。

屏幕共享在如下场景中应用广泛：

- 视频会议场景中，屏幕共享可以将讲话者本地的文件、数据、网页、PPT 等画面分享给其他与会人；
- 在线课堂场景中，屏幕共享可以将老师的课件、笔记、讲课内容等画面展示给学生观看。

## 实现方法
在开始屏幕共享前，请确保你已完成环境准备、安装包获取等步骤，详见 [集成客户端](../../cn/Video/ios_video.md)。

屏幕共享在 iOS 平台上的实现，主要通过如下步骤：
* 使用 Broadcast Upload Extension 开启一个新的进程
* 使用 Apple ReplayKit 框架进行屏幕录制
* 使用 Agora SDK 进行视频流的传输

```
//swift
override func processSampleBuffer(_ sampleBuffer: CMSampleBuffer, with sampleBufferType: RPSampleBufferType) {
        DispatchQueue.main.async {
            switch sampleBufferType {
            case RPSampleBufferType.video:
                AgoraUploader.sendVideoBuffer(sampleBuffer)
                break
            case RPSampleBufferType.audioApp:
                AgoraUploader.sendAudioAppBuffer(sampleBuffer)
                break
            case RPSampleBufferType.audioMic:
                AgoraUploader.sendAudioMicBuffer(sampleBuffer)
                break
            }
        }
    }
```

```objective-c
//objective-c
- (void)processSampleBuffer:(CMSampleBufferRef)sampleBuffer withType:(RPSampleBufferType)sampleBufferType {
    dispatch_async(dispatch_get_main_queue(), ^{
    	switch (sampleBufferType) {
        case RPSampleBufferTypeVideo:
            [agoraUpload sendVideoBuffer:sampleBuffer];
             NSLog(@"RPSampleBufferTypeVideo App~~~~");
            break;
        case RPSampleBufferTypeAudioApp:
            [agoraUpload sendAudioAppBuffer:sampleBuffer];
            NSLog(@"RPSampleBufferTypeAudio App+++");
            break;
        case RPSampleBufferTypeAudioMic:
            [agoraUpload sendMicAppBuffer:sampleBuffer];
            break;
    	}
    })
}
```

你也可以参考详细的 [Agora Screen Sharing](https://github.com/AgoraIO/Advanced-Video/tree/master/Screensharing/Agora-Screen-Sharing-iOS) 示例代码实现屏幕共享。