# 放射科

## 术语
### 名词
| 英文 | 中文 | 说明 |
| :----: | ---- | ---- |
| patient | 病患 |  |
| nidus | 病灶 | 疾病集中的部位或是综合病症、感染的主要部位 |
| nodule | 结节 | 生物体表面或内部组织中圆形的小突起 |
| registration | 影像配准 |  |
| series | 影像序列 |  |
| study | 检查 |  |

### 医学成像
| 名称 | 说明 |
| :----: | ---- |
| X光 | 用X光给你的身体拍了一张照片的检查方式。所以也叫拍片子 |
| CT(计算机体层成像) | 实际上也是用X光给身体拍照片的检查方式。不过不是拍一张，而是要拍很多张，一层一层地查。 |
| B超 | 发出超声波，然后用反射的回声来画像的检查方式 |
| 核磁共振(MRI) | 是利用一个强大的磁场，让身体里的氢原子，先排好队再解散，接受这期间的电磁波信号，再给身体内部画像 |
| DR(数字化放射成像) |  |
| CR(计算机成像) |  |

| 名称 | 说明 |
| :----: | ---- |
| HU | CT图像上每个像素所对应的物质对X线线性衰减量平均大小的表示，称为CT值，其单位为HU（豪斯菲尔德Housfield，英国科学家，发明了CT扫描仪） |
| POI | point of interest，兴趣点，GIS是坐标点 |
| ROI | region of interest，GIS是区域 |

## 影像文件
| 类型 | 全称 | 说明 |
| :----: | ---- | ---- |
| dcm |  | Orthanc - DICOM Server。内容格式是{x，y，灰度(float？)} |
| mha/mhd |  |  |
| nrrd |  |  |
| nii |  | 压缩比好。主要用于分割后的二值（2种灰度） |
| NIFTI | Neuroimaging Informatics Technology Initiative | 文件后缀名为.nii.gz，其实是nii的压缩版本。Data Format Working Group (DFWG), [参考](https://blog.csdn.net/DoronLee/article/details/78597868) |
| stl |  | 基于dcm等图像，三维重建模型 |
| hdr |  |  |
| JPG/PNG/tiff |  | 图片 |

### dicom
#### 资料
* [官网](https://www.dicomlibrary.com/)
* [Transfer Syntax](https://blog.csdn.net/u014738683/article/details/54573611)
* [SOP](https://blog.csdn.net/u014738683/article/details/54573728)
* [数据类型](https://blog.csdn.net/inter_peng/article/details/46513847)
* [GE](http://www3.gehealthcare.co.uk/~/media/documents/us-global/products/interoperability/dicom/radiology-pacs-ris/gehc-dicom-conformance_pathspeedpacs-v8-1_iisfp10282_rev2.pdf)
* [GE Private TS](https://blog.csdn.net/zssureqh/article/details/47222685)

#### 常用字段
| 类型 | 名称 | 说明 |
| :----: | ---- | ---- |
| 最小图像像素值 | SmallestImagePixelValue(0028,0106) | 射线衰减值 |
| 最大图像像素值 | LargestImagePixelValue(0028,0107) | 射线衰减值 |
| 窗位 | WindowCenter(0028,1050) | 密度值，单位是HU |
| 窗宽 | WindowWidth(0028,1051) | 密度值，单位是HU |
| 缩放截距 | RescaleIntercept(0028,1052) |  |
| 缩放率 | RescaleSlope(0028,1053) |  |

#### 公式
1. 密度值 = (像素值 * RescaleSlope) + RescaleIntercept
1. RGB = 像素值 * (LargestImagePixelValue - SmallestImagePixelValue) / 255
1. 密度值窗位选择: zoneMin < [WindowCenter-WindowWidth/2, WindowCenter+WindowWidth/2] < zoneMax。zoneMin的密度值是最小窗，zoneMax的密度值是最大窗

## 资料
### 显示器
* 普通显示器分辨率1920*1080，DELL E2216HV
* 医用专业显示器
  * 黑白影像诊断显示器分辨率是1600*1200。巨鲨JUSHA-M21
* 产品用普通显示器，点击分屏时会把影像及其功能投放到医用专业显示器

### 第三方库
| 类型 | 名称 | 说明 |
| :----: | ---- | ---- |
| ITK | 图像操作工具包 | 图像分析和处理 |
| VTK | 图像可视化操作工具包 | 三维显示和三维模型操作，visualization |

* [ITK与VTK数据转换](https://blog.csdn.net/menjiawan/article/details/47283809)

### 坐标系

| 类型 | 坐标原点 | 图像首个像素(左上角)存储位置 |
| :----: | ---- | ---- |
| ITK | 图像的左下角 | 左上角 |
| VTK | 图像的左下角 | 左下角 |

### 软件
| 类型 | 名称 | 说明 |
| :----: | ---- | ---- |
| [itksnap](http://www.itksnap.org) |  |  |
| [NDP.view2](https://www.hamamatsu.com/jp/en/product/type/U12388-01/index.html) |  |  |
| eFilm Workstation |  |  |
