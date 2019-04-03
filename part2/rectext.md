##场景文字识别检测与识别

###背景及意义
目前，OCR应用（如手写数字识别、邮政编码识别、汽车牌号识别、汉字识别、条形码识别等），以及生物特征识别（如人脸识别、指纹识别、虹膜识别等）在人类日常生活中广泛应用。

###相关方法
![检测方法](/assets/recmoth.png)

####端到端方案
![端到端](/assets/recmoth1.png)

 经典方法：Deep TextSpotter、Mask TextSpotter 、FOTS Rotation-Sensitive Regression 和 STN-OCR等。

 ####先检测再识别
![检测+识别](/assets/recmoth2.png)

检测方案： AdvancedEAST 、CTPN、FTSN、DMPNet、EAST、SegLink、PixelLink、Textboxes和WordSup等。
识别方案：CRNN 、OCR-Attention、RARE等。

###论文理解
**论文** : Zhou X, Yao C, Wen H, et al. EAST: an efficient and accurate scene text detector[C] //Proceedings of the IEEE conference on Computer Vision and Pattern Recognition. 2017: 5551-5560.


**网络结构**:![](/assets/east.png)

**优点**： 

1、由全卷积网络和NMS两阶段组成的场景文本检测方法。
2、可基于单字和句子的检测，检测形状可以为旋转框（RBOX）和四边形(QUAD)。

**网络输出**： 

1、Score map ：1位 ，是否在文本框； 
2、RBOX： 5位，其中4位表示文本区域内局部像素点到RBOX四条边的距离，1位表示旋转角度𝜃；
3、QUAD: 8位，表示文本区域内局部像素点到四边形4个顶点的距离。

**符号表示**：
![](/assets/eastres.png)

优化：文本区域默认为四边形，采用缩小版的四边形作为实际文本区域。
![文本区域缩减](/assets/scale.png)

**损失函数**
![](/assets/loss1.png)
![](/assets/loss2.png)
![](/assets/loss3.png)

**论文实验**
Results on ICDAR 2015 Challenge Scene Text Localization task
![](/assets/lab1.png)

Results on MSRA-TD500
![](/assets/lab2.png)