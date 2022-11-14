<h1>基于yolov5的烟盒检测</h1>
<h3>前言</h3>
目标检测是计算机视觉领域的一大任务，大致分为一阶段目标检测与两阶段目标检测。其中一阶段目标检测模型以<b>YOLO</b>系列为代表。最新的YOLOv5在各个数据集上体现出收敛速度快、模型可定制性强的特点，值得关注。本文主要讲解如何从零训练自己的YOLOv5模型与一些重要参数的含义。
 
<h3>项目目标：</h3>
根据客户需求，输入一张包烟橱窗的照片，识别照片中的包烟并且统计数量

<h5>数据准备和检测</h5>
和其他项目一样，在这个项目中，我们同样需要准备数据集进行训练和预测。 在这个项目中，我们使用了商店售烟橱窗的照片作为输入数据集，这些照片来源于商家所提供的现场拍摄照片。这些照片包含了多种不同品牌的包烟。

由于不同拍摄者和不同设备拍摄出的包烟橱窗照片尺寸大小不一。因此我们首先将数据做了预处理。将其大小调整为固定尺寸：宽为600px, 高为450px。将图片调整为固定尺寸之后，将使用标注工具labelimg[1]标注图像。该项目只识别包烟，因此只需要对图片中出现的包烟进行标注即可。需要注意的是，在labelimg中，需要在左侧将标注格式设置为yolo格式
![image](https://user-images.githubusercontent.com/30151896/201564435-2831eea4-2d6e-42dd-9085-f5ef7049bd03.png)

![image](https://user-images.githubusercontent.com/30151896/201564443-456a9aba-53dd-40dd-816a-4d4c20e24a30.png)

图片标注好后，将标注文件存储在data/labels文件夹下

![image](https://user-images.githubusercontent.com/30151896/201564466-1d06f51b-7e53-4069-9ba4-0379ea7e12cf.png)

将原图像存储在data/images文件夹下

![image](https://user-images.githubusercontent.com/30151896/201564477-73fcbaf5-742d-48a0-acfe-4ac3d248a747.png)




<h5>参数配置：</h5>
数据处理好后，我们就可以对文件进行配置了
首先，我们修改数据的配置文件: 在data文件下的tobaco.yaml。在这个配置文件中，我们需要设定训练数据集和验证数据集的目录。以及设定需要识别的目标。
例如，我们的训练路径为：data/images/train， 验证路径为：data/images/val。以及我们在上一步标注好的目标：tobaco
![image](https://user-images.githubusercontent.com/30151896/201565309-2b3b015b-49b0-4588-aa4b-f98725eb706c.png)


 







 






参考：
[1]	LabelImage: https://github.com/heartexlabs/labelImg
