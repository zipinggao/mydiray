##场景文字识别检测与识别

###背景及意义
目前，OCR应用（如手写数字识别、邮政编码识别、汽车牌号识别、汉字识别、条形码识别等），以及生物特征识别（如人脸识别、指纹识别、虹膜识别等）在人类日常生活中广泛应用。

![ 核对快递单](/assets/1.png)  ![身份证识别](/assets/idcord2.png) 
![执照识别](/assets/xxxx3.png) 

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
**论文题目** :
