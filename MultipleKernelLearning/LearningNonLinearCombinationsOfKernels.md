# Learning Non-Linear Combinations of Kernels

<script type="text/javascript"
 src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
</script>

(Optimize Nonlinear risk 2-step)

这篇文章研究的基于多项式结合的核学习。文中主要针对回归算法进行分析。核学习的最优化问题表现为极大极小问题，可以转换为一个简单的最小化问题。文章中采用梯度下降法来解决最优化问题。采用几个有效的数据集来证明算法的有效性。

## Introduction

核学习（learning kernels）的问题是用训练数据去选择适合的核函数而不是指定一个核。

这篇文章研究基于多项式结合的核学习。文章中展示了简化最优化问题从极大极小问题转换为更简单的最小化问题，并且证明最优化问题的全局解位于边缘。文中采用梯度下降法解决最小化问题（通过少的迭代达到收敛）。

这篇文章第二部分介绍非线性核；第三部分讨论学习问题，制定最优化问题和怎样解决；第四部分为本文算法在几个数据集上的表现。

## Kernel Family

令<img src="http://www.forkosh.com/mathtex.cgi? K_{1},\dots,K_{P}">为核，这些核作为基核（base kernels），要将它们结合成更复杂的核。这里用非负系数进行多项式结合的形式：![Ku](file:///Users/wangruchen/work/learningMaterials/MachineLearning/MultipleKernelLearning/figure/KuNLMKL.png)
其中![u](file:///Users/wangruchen/work/learningMaterials/MachineLearning/MultipleKernelLearning/figure/uNLMKL.png)
多项式结合就变成：![K](file:///Users/wangruchen/work/learningMaterials/MachineLearning/MultipleKernelLearning/figure/KNLMKL.png)

