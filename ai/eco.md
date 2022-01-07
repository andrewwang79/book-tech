# 生态库

## 技能点
| 项 | 工作内容 | 框架，库，协议等 |
| :-: | - | - |
| 流媒体处理框架 | 维护 | GStreamer/DeepStream/CNStream，RTSP/RTMP等流媒体网络传输协议  |
| 视频处理 | 开发，重点是视频编解码 | FFmpeg/live555，H264 |
| AI推理服务框架 | 维护 | DeepStream/CNStream |
| AI算子插件 | 开发 | CUDA |

## 框架
| 项 | 说明 |
| :-: | - |
| [Gstreamer](https://www.cnblogs.com/xleng/p/10948838.html) |  |
| [DeepStream](https://blog.csdn.net/Tosonw/article/details/104154090) | 基于GStreamer的NVIDIA框架，应用于视觉整个流程的解决方案，覆盖视频编解码、图像推理，画面显示等。采用pipeline的模块化插件，每个插件代表一个功能块。|

### NVIDIA的
* [MONAI（Medical Open Network for AI）](http://www.cww.net.cn/article?id=480005) : 基于PyTorch的框架
* [clara](https://developer.nvidia.com/clara) : 医疗框架，基于MONAI，https://blog.csdn.net/qq_19765635/article/details/108798962

## 库
### RAPIDS
* [RAPIDS](https://www.nvidia.cn/deep-learning-ai/software/rapids/) : 基于GPU的机器学习Python库, [资料](https://www.datalearner.com/blog/1051562381920769)
* 数据科学和分析流程，以及一些传统的经典机器学习算法
* 三个模块处理数据：cuDF相当于Pandas，cuML相当于scikit-learn，cuGraph则是处理图数据的（如PageRank算法）

## 资料
* [流媒体](https://tech.wangyaqi.cn/#/common/streammedia)
