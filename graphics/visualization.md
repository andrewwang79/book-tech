# 可视化

## 库
* VTK公司出的前端库，支持pad和手机：https://kitware.github.io/vtk-js/

## 实现方式
| 渲染方式 | 技术 | 优势 | 劣势 |
| :-: | - | - | - |
| 后端 | 离屏渲染(VTK EGL)+websocket | 支持复杂操作，终端开发容易 | 依赖网络带宽，需要后端大量的内存和算力 |
| 前端H | H5+js库 | 终端不同可复用 | 依赖终端的内存和算力；复杂操作的支持度有限制 |
| 前端C | QT+VTK | 支持复杂操作 | 依赖终端的内存和算力；终端不同需重做，比如手机端要换QT |

## 资料
* https://www.incool3d.com/
* https://www.weiyunyingxiang.com/
