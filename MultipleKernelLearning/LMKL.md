# Localized Multiple Kernel Learning

这篇文章提出了LMKL算法，采用gating model来选择合适的核函数。

## Introduction

SVM判别函数为：![](file:///Users/wangruchen/work/learningMaterials/MachineLearning/MultipleKernelLearning/figure/dfLMKL.png)
其中w为权重参数，b为阈值，<img src="http://www.forkosh.com/mathtex.cgi? \phi (x)">为特征空间中的mapping function。
选择核函数是SVM训练中的重要一步，通常采用交叉验证。

这篇文章，第二部分更改MKL的决策函数，并且描叙怎样采用2-step来优化参数；第三部分介绍这个算法的一个重要性质；第四部分证明算法的性能；第五部分结论。

## Localized Multiple Kernel Learning

改写传统多核学习的判别函数为：![](file:///Users/wangruchen/work/learningMaterials/MachineLearning/MultipleKernelLearning/figure/dfMKL.png)
其中<img src="http://www.forkosh.com/mathtex.cgi? \eta _{m}(x)">为gating function。

得到的优化问题为：![](file:///Users/wangruchen/work/learningMaterials/MachineLearning/MultipleKernelLearning/figure/optimLMKL.png)

为了解上面的优化问题，文中采用2-step交替优化。首先，固定<img src="http://www.forkosh.com/mathtex.cgi? \eta _{m}(x)">来解<img src="http://www.forkosh.com/mathtex.cgi? w _{m}(x),b,\xi">，然后用目标函数的梯度下降步长来更新<img src="http://www.forkosh.com/mathtex.cgi? \eta _{m}(x)">。

gating model表示为：![](file:///Users/wangruchen/work/learningMaterials/MachineLearning/MultipleKernelLearning/figure/nLMKL.png)其中<img src="http://www.forkosh.com/mathtex.cgi? v _{m},v_{m0}">是gating model的参数。要得到gating model首先需要计算得到参数<img src="http://www.forkosh.com/mathtex.cgi? v _{m},v_{m0}">。

用<img src="http://www.forkosh.com/mathtex.cgi? J(\eta)">对<img src="http://www.forkosh.com/mathtex.cgi? v _{m},v_{m0}">的导数和梯度下降法得到：![](file:///Users/wangruchen/work/learningMaterials/MachineLearning/MultipleKernelLearning/figure/gdLMKL.png)

LMKL计算linear gating model的算法流程如图：![](file:///Users/wangruchen/work/learningMaterials/MachineLearning/MultipleKernelLearning/figure/gatingALMKL.png)

得到最终的<img src="http://www.forkosh.com/mathtex.cgi? \eta _{m}(x)">后可以得到判别函数：![](file:///Users/wangruchen/work/learningMaterials/MachineLearning/MultipleKernelLearning/figure/disfunLMKL.png)