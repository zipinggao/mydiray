# 文化传承—汉字书法多场景识别
这次比赛主要是实现书法文字的自动识别，解决实际场景中有些书法文字难以识别的问题。
比赛网址：[汉字书法多场景识别](https://www.datafountain.cn/competitions/334/details)

## 比赛分析
这次比赛主要识别图片中的一些中文（包含大量的生僻字），对于比赛中参赛给予的baseline采用的检测+识别两个步骤。先检测出图片中包含文字的不规则四边形区域（大部分为矩形或是平行四边形），再识别检测出的区域中文字。baseline中检测采用的是East，识别模型采用的是CRNN.基于此，我和的队友采用的也是AdvancedEAST + CRNN ，AdvancedEAST是基于East的改进，使长文本预测更准确。这里提一下，我和队友原本有想过采用检测+识别端到端的结构，但是发现在图像文本检测领域检测+识别端到端的模型较少，曾看过华科白翔老师团队ECCV2018 OCR论文：Mask TextSpotter。但发现文中Mask TextSpotter方法主要是对英文字符进行分割，面对众多的中文汉字以及文字结构形态的多样性，明显采用Mask TextSpotter方法是不合适的，而且识别的精度依赖于检测的精度，这是一个递进的过程，分开并行实现似乎并不会有好的效果。于是我们也采用了分两步的方案。

###数据分析
比赛数据集：训练集:50000张，验证集：10000张，测试集：10000张。

###文本检测
数据处理：AdvancedEAST 模型要求图片的长和宽为32的倍数：于是对图片进行了如下缩放：
$$ new\_width = ori\_width + (32 - ori\_width\%32) $$
$$ new\_height = ori\_height + (32 - ori\_height\%32) $$
将图片的长和宽同时放大为32的倍数。因感觉图片放大后文字区域相比缩小更容易检测，因此采用了放大。图片训练采用彩色图。因为图片的大小尺寸是不统一的，因此在使用GPU进行训练时：batch_size = 1.训练3个epochs后模型便已经收敛的可以看到较好的效果。


对于检测模型AdvancedEAST
文本检测模型采用AdvancedEAST，对于检测模型AdvancedEAST可以参考：
github——AdvancedEAST[](https://github.com/huoyijie/AdvancedEAST)


