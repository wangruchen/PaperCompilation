# More Generality in Efficient Multiple Kernel Learning

<script type="text/javascript"
 src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
</script>

(Optimize Nonlinear risk 2-step)

一个好的SVM分类器依赖于好的核和特征，手动调整参数和结合恰当的特征是比较困难的。MKL通过从训练集中学习核来解决这些问题。此外，MKL还解决怎样线性结合基核来得到核。

## Introduction

这篇文章将传统MKL扩展为handle generic kernel combinations，该方法采用的是非线性核结合，其核函数为：![核函数](file:///Users/wangruchen/work/learningMaterials/MachineLearning/MultipleKernelLearning/figure/KernelGMKL.png)

此外，梯度下降优化（SimpleMKL 2008中使用的）继续在文章中使用。

<!--（GMKL是结合L1范式和L2范式的新稀疏多核学习算法）-->

这篇文章第二部分是MKL的相关工作。第三部分是本文的算法公式，这个公式可以用在核结合、核参数调整、非线性特征选取和降维。第四部分特征选择。第五部分结果对比。第六部分结论。

## Generalized MKL

SVM需要根据训练集学习w和b的最优值，此外，MKL还需要计算出核函数参数d。

文中将Varma & Rayon（2007）中的公式：![VR2007](file:///Users/wangruchen/work/learningMaterials/MachineLearning/MultipleKernelLearning/figure/VR2007.png)

扩展为：![](file:///Users/wangruchen/work/learningMaterials/MachineLearning/MultipleKernelLearning/figure/minGMKL.png)

其中r为正则化矩阵；<img src="http://www.forkosh.com/mathtex.cgi? l">为损失函数，在分类问题中<img src="http://www.forkosh.com/mathtex.cgi? l=C\max(0,1-y_{i}f(x_{i}))">。

在外圈循环中优化参数d，在内圈循环中学习SVM参数，上式可以被写为：![](file:///Users/wangruchen/work/learningMaterials/MachineLearning/MultipleKernelLearning/figure/min2GMKL.png)

如果在外循环中利用梯度下降法，那必须证明<img src="http://www.forkosh.com/mathtex.cgi? \nabla_{d} T">存在。这里可以通过转换为T的对偶问题实现（对于分类问题）：![Wc](file:///Users/wangruchen/work/learningMaterials/MachineLearning/MultipleKernelLearning/figure/WcGMKL.png)

![](file:///Users/wangruchen/work/learningMaterials/MachineLearning/MultipleKernelLearning/figure/daoGMKL.png)
<img src="http://www.forkosh.com/mathtex.cgi? H=YKY">。为了得到梯度下降的步长，我们需要得到<img src="http://www.forkosh.com/mathtex.cgi? \alpha^{*}">，他可以通过带入任何一个SVM中求出。

