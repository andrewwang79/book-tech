# 流媒体

## 知识
* [理解RTMP、HttpFlv和HLS的正确姿势](https://www.jianshu.com/p/32417d8ee5b6)
* [流媒体传输协议（rtp/rtcp/rtsp/rtmp/mms/hls）](https://zhuanlan.zhihu.com/p/27442401)

| 术语 | 说明 | 开发商 |
| :-: | - | - |
| HLS（ HTTP Live Streaming） | 适合视频点播，不适合直播 | Apple |
| RTSP（Real-Time Stream Protocol） | 摄像头事实标准 | Real Networks 和 Netscape |
| RTMP（Real Time Message Protocol） | 直播 | Adobe |

### HLS
直接把流媒体切片成一段段，信息保存到m3u列表文件中，可以将不同速率的版本切成相应的片；播放器可以直接使用http协议请求流数据，可以在不同速率的版本间自由切换，实现无缝播放；省去使用其他协议的烦恼。缺点是延迟大小受切片大小影响，不适合直播，适合视频点播。

### RTSP
由Real Networks 和 Netscape共同提出的，基于文本的多媒体播放控制协议。RTSP定义流格式，流数据经由RTP传输；RTSP实时效果非常好，适合视频聊天，视频监控等方向。

### RTMP
用来解决多媒体数据传输流的多路复用（Multiplexing）和分包（packetizing）的问题，优势在于低延迟，稳定性高，支持所有摄像头格式，浏览器加载 flash插件就可以直接播放。

### 总结
HLS 延迟大，适合视频点播；RTSP虽然实时性最好，但是实现复杂，适合视频聊天和视频监控；RTMP强在浏览器支持好，加载flash插件后就能直接播放，所以非常火，相反在浏览器里播放rtsp就很困难了。

## 方案
### 实现
* [HTML5播放RTSP视频](https://zhuanlan.zhihu.com/p/75406976)
* [rtsp-ffmpeg](https://www.npmjs.com/package/rtsp-ffmpeg)
* [Ffmpeg+Node.js+jsmpeg.js实现html5播放rtsp](https://blog.csdn.net/l15738519366/article/details/105844281)

### 资料
* [视频点播流媒体服务器调研](https://www.qingtingip.com/h_251689.html)
* [Linux下视频流媒体服务器搭建详解](https://blog.csdn.net/u011596455/article/details/79431116)
* [基于Nginx配置Web视频流媒体服务器](https://leefige.github.io/2019/03/05/%E5%9F%BA%E4%BA%8ENginx%E9%85%8D%E7%BD%AEWeb%E8%A7%86%E9%A2%91%E6%B5%81%E5%AA%92%E4%BD%93%E6%9C%8D%E5%8A%A1%E5%99%A8/)
* [基于nginx-rtmp-module实现的直播项目小结](https://juejin.im/post/5d2182b75188250501476c17)

## 系统
### srs
ossrs/srs:3
### OBS
* [腾讯云直播OBS推流教程](https://www.jianshu.com/p/bf4066028882)
