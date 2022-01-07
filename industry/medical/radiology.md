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
| dicom | Digital Imaging and Communication In Medicine | Orthanc - DICOM Server |
| mha/mhd |  | 体数据，mhd包含图像的meta data（信息头）和图像裸数据 |
| NIFTI | Neuroimaging Informatics Technology Initiative | 体数据，nii/nii.gz |
| nrrd |  |  |
| stl |  | 基于dcm等图像，三维重建模型 |
| JPG/PNG/tiff |  | 图片 |

### NIFTI
* [资料1](https://blog.csdn.net/weixin_42089190/article/details/116710684), [资料2](https://blog.csdn.net/DoronLee/article/details/78597868)
* NIFTI格式主要包含三部分：hdr,ext,img
* Data Format Working Group (DFWG)

### dicom
#### 资料
* [官网](https://www.dicomlibrary.com/)
* [Transfer Syntax](https://blog.csdn.net/u014738683/article/details/54573611)
* [SOP](https://blog.csdn.net/u014738683/article/details/54573728)
* [数据类型](https://blog.csdn.net/inter_peng/article/details/46513847)
* [DICOM：C-GET与C-MOVE对比剖析](https://blog.csdn.net/zssureqh/article/details/46868695)

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

### NIFTI
* [NIFTI格式(.Nii)数据version 1格式分析](https://blog.csdn.net/DoronLee/article/details/78597868)
* [NIfTI-1 Data Format](https://nifti.nimh.nih.gov/nifti-1)
* [niftilib i/o libraries for nifti-1](http://niftilib.sourceforge.net/)
* [体数据NIfTI和DICOM的格式互转](https://blog.csdn.net/weixin_39944074/article/details/110636490) : nifti2dicom

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
* [坐标系](https://www.cnblogs.com/biaohuang/p/14419118.html)
| 坐标系 | 说明 |
| :----: | ---- |
| 世界坐标系 |  |
| 人体/解剖学坐标系 | 单位是mm |
| 图像坐标系 | 单位是点(因为间距不定，点的mm也不定)，原点在左上角。i坐标轴向右递增，j坐标轴向下递增，k坐标轴向后递增。 |
* [【相机标定】四个坐标系之间的变换关系](https://cloud.tencent.com/developer/article/1820935)

#### 人体坐标系和图像坐标系
![人体坐标系](/s/industry/medical/PatientCoordinateSystem.png)
* 轴状位/横断面（The axial plane）:脚部(Inferior), 头部(Superior)
* 图像坐标系转换到人体坐标系：通过图像的原点和间距，计算其在人体坐标系中的对应位置

#### Dicom坐标tag
| TAG | 英文说明 | 说明 |
| :----: | ---- | ---- |
| Image Position (Patient) | The x, y and z coordinates of the upper left hand corner of the image, in mm. | 图像的左上角在空间坐标系中的x,y,z坐标,单位是毫米. 如果在检查中,则指该序列中第一张影像左上角的坐标. |
| Image Orientation (Patient) | The direction cosines of the first row and the first column with respect to the patient. | 人体扫描时的朝向 |

#### 第三方库的坐标信息
| 类型 | 坐标系 | 坐标原点 | 图像首个像素(左上角)存储位置 |
| :----: | ---- | ---- | ---- |
| ITK | LPS：（Left，Posterior，Superior）| 图像的左下角 | 左上角 |
| VTK |  | 图像的左下角 | 左下角 |
| 3D Slicer | RAS：（Right，Anterior，Superior） |  |  |

### 软件
| 类型 | 名称 | 说明 |
| :----: | ---- | ---- |
| [ITK-SNAP](http://www.itksnap.org) |  |  |
| RadiAnt DICOM Viewer |  |  |
| [NDP.view2](https://www.hamamatsu.com/jp/en/product/type/U12388-01/index.html) |  |  |
| eFilm Workstation |  |  |
