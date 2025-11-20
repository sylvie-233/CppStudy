# FFmpeg



## 基础介绍




## 核心内容




直播推流整体流程：
```
【主播端】
摄像头/麦克风 → 编码（H.264/AAC） → 推流协议(RTMP/SRT/WebRTC)
    ↓
【云端直播服务器】
接入 → 转码 → 切片/分发(HLS/FLV/WebRTC) → CDN加速
    ↓
【观众端】
CDN取流 → 解码 → 播放器渲染

主播端：rtmp://live.example.com/live/stream_123?token=xxxx
- 摄像头视频 → H.264 压缩编码
- 麦克风音频 → AAC 压缩编码
- 视频帧 + 音频帧 → 推流封包 → RTMP/SRT 发送

流媒体服务器：RTMP（输入） → 多种协议（输出）(SRS、Nginx-rtmp、FFmpeg、腾讯云直播)
- 接收 RTMP/SRT 流：把主播上传的直播流接收进来
- 解析视频和音频帧：视频：H.264 NALU、音频：AAC frame
- 重封装：为了让不同观众用不同方式播放，服务器会转换格式（FLV、HLS (m3u8/ts)、WebRTC、DASH）

观众端：解码播放

完整直播流程：
摄像头/麦克风
       ↓
    编码（H.264/AAC）
       ↓
    推流（RTMP/SRT/WebRTC）
       ↓
────────【流媒体服务器】────────
       ↓        ↓          ↓
    转码     重封装     切片
       ↓        ↓          ↓
     1080p     FLV/HLS    TS + m3u8
       ↓        ↓          ↓
────────【CDN分发】────────
                ↓
────────【观众播放器】────────
                ↓
          解码 → 播放
```


## MP4

MP4 文件是由 Box（盒子/Atom） 组成的，每个 Box 都有自己的 类型、大小和数据




### Box

常见 Box 类型：
1. ftyp（File Type Box）：标识文件类型和兼容性
2. moov（Movie Box）：文件的核心索引信息
3. mdat（Media Data Box）：存储实际音视频数据
4. free：占位或保留



### H.264

视频编码中的帧类型（Frame Types），属于 视频压缩（编码）概念
1. I 帧（Intra Frame，自内编码帧）：视频解码参考点（随机访问点）
2. P 帧（Predicted Frame，预测帧）：依赖之前的 I 帧或 P 帧
3. B 帧（Bi-predictive Frame，双向预测帧）：依赖前后的 I 或 P 帧
4. GOP（Group of Pictures）：一组 I/P/B 帧的组合



## HLS
### m3u8


m3u8/m3u/meU8（其实是 m3u8）格式，指的是 HLS（HTTP Live Streaming）直播/点播使用的播放清单文件
M3U 原本是 MP3 播放器的播放列表格式（文本文件）。M3U8 是 UTF-8 编码的 M3U 文件（8 = UTF-8）。

在视频网站、直播平台中常用于 HLS 分段视频
```
video.m3u8  ← 播放列表文件
├─ segment1.ts
├─ segment2.ts
├─ segment3.ts
└─ ...
```

m3u8 关键标签：
- #EXTM3U：所有 m3u8 开头必须有
- #EXT-X-VERSION:3：HLS 版本
- #EXT-X-TARGETDURATION:6：每个 ts 最大持续时间（秒）
- #EXT-X-MEDIA-SEQUENCE:1：第一个 ts 的序号（直播时会不断递增）
- #EXT-X-KEY:METHOD=AES-128：AES-128 加密
- #EXTINF:6.0,：媒体分段标签，表示下一个 ts 文件时长 6 秒



### ts

MPEG-TS（MPEG Transport Stream）传输流
```
[ TS Packet 0 (188 bytes) ]
[ TS Packet 1 (188 bytes) ]
[ TS Packet 2 (188 bytes) ]
...
```

TS 是一种 分段小、同步性强、抗错误能力强 的流式视频格式
1. 固定大小：每个 TS packet = 188 字节（永远如此）
2. 内含同步字节 0x47，保证快速同步
3. 分段小（188 bytes），流媒体友好
4. 抗丢包能力强，不依赖容器结构
5. 支持多路视频/音频/字幕
6. 可边下载边播放，非常适合 HLS

1. 4 字节：TS 包头（Header）
    - Sync Byte	8	一定是 0x47（同步标记）
    - Transport Error Indicator	1	错误指示
    - Payload Unit Start Indicator	1	PES 开始标记
    - Transport Priority	1	优先级
    - PID	13	该包属于哪一路视频/音频
    - Scrambling Control	2	加密标记
    - Adaptation field Control	2	是否有填充字段
    - Continuity Counter	4	包序号（判断丢包）
2. 0~184 字节：Payload
    - PAT 表
    - PMT 表
    - PES（视频/音频数据）：TS 包 → PES → ES（原始视频流）
    - 填充字节

#### PES

PES（Packetized Elementary Stream）层
- PES header	起始码、流 ID、PTS/DTS 时间戳
- PES payload	H.264/H.265/AAC 数据


ES（Elementary Stream）




## RTMP

主流推流协议
```
主播（RTMP/SRT）→ 流媒体服务器（SRS/FFmpeg/Nginx-rtmp）
       ↓ 转码
     观众: HLS(m3u8) / WebRTC / FLV
```


## SRT


## WebRTC