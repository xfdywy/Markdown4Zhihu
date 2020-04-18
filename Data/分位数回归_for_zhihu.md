---
title:  分位数回归
date: 2020-4-17
idx: 2
tags:
    -   分位数回归
mathjax: true
categories: math
grammar_linkify: true
---

# 分位数回归的直观

给定一些样本数据  <img src="https://www.zhihu.com/equation?tex=(x_i, y_i)" alt="(x_i, y_i)" class="ee_img tr_noresize" eeimg="1"> ，我们可以理解成 给定一个  <img src="https://www.zhihu.com/equation?tex=x_i" alt="x_i" class="ee_img tr_noresize" eeimg="1"> , 我们就有一个  <img src="https://www.zhihu.com/equation?tex=Y_i" alt="Y_i" class="ee_img tr_noresize" eeimg="1">  的分布， <img src="https://www.zhihu.com/equation?tex=y_i" alt="y_i" class="ee_img tr_noresize" eeimg="1">  是一个采样出来的样本，被我们所观测。 最小二乘估计是要去拟合  <img src="https://www.zhihu.com/equation?tex=x" alt="x" class="ee_img tr_noresize" eeimg="1">  和  <img src="https://www.zhihu.com/equation?tex=mean(Y)" alt="mean(Y)" class="ee_img tr_noresize" eeimg="1">  之间的关系。 而分位数回归则是要拟合某分位数。

<!-- more -->

 
 
 
# 分位数回归的数学方法
随机变量  <img src="https://www.zhihu.com/equation?tex=Y" alt="Y" class="ee_img tr_noresize" eeimg="1">  的  <img src="https://www.zhihu.com/equation?tex=\tau" alt="\tau" class="ee_img tr_noresize" eeimg="1">  分位数 的定义是

<img src="https://www.zhihu.com/equation?tex=Q_{Y}(\tau)=F_{Y}^{-1}(\tau)=\inf\left\lbrace y:F_{Y}(y)\geq\tau\right\rbrace " alt="Q_{Y}(\tau)=F_{Y}^{-1}(\tau)=\inf\left\lbrace y:F_{Y}(y)\geq\tau\right\rbrace " class="ee_img tr_noresize" eeimg="1">

为了简单起见，我们定义如下函数


<img src="https://www.zhihu.com/equation?tex=\rho_{\tau}(y)=y(\tau-\mathbb{I}_{(y<0)}) " alt="\rho_{\tau}(y)=y(\tau-\mathbb{I}_{(y<0)}) " class="ee_img tr_noresize" eeimg="1">
 
 
考虑如下最优化问题的最优解  <img src="https://www.zhihu.com/equation?tex=u^*" alt="u^*" class="ee_img tr_noresize" eeimg="1"> 

$ <img src="https://www.zhihu.com/equation?tex= \underset{u}{\min}E(\rho_{\tau}(Y-u))=\underset{u}{\min}\left\lbrace(\tau-1)\int_{-\infty}^{u}(y-u)dF_{Y}(y)+\tau\int_{u}^{\infty}(y-u)dF_{Y}(y)\right\rbrace  \tag{1}" alt=" \underset{u}{\min}E(\rho_{\tau}(Y-u))=\underset{u}{\min}\left\lbrace(\tau-1)\int_{-\infty}^{u}(y-u)dF_{Y}(y)+\tau\int_{u}^{\infty}(y-u)dF_{Y}(y)\right\rbrace  \tag{1}" class="ee_img tr_noresize" eeimg="1"> $ 

我们可以通过求导，令导函数等于0，反解出 <img src="https://www.zhihu.com/equation?tex=u^\ast" alt="u^\ast" class="ee_img tr_noresize" eeimg="1">  ， 可以看到  <img src="https://www.zhihu.com/equation?tex=F_{Y}( u^\ast)=\tau" alt="F_{Y}( u^\ast)=\tau" class="ee_img tr_noresize" eeimg="1"> 

从而，我们可以令   <img src="https://www.zhihu.com/equation?tex=u = f_w(x)" alt="u = f_w(x)" class="ee_img tr_noresize" eeimg="1"> , 例如，线性情况下   <img src="https://www.zhihu.com/equation?tex=u = w\cdot x" alt="u = w\cdot x" class="ee_img tr_noresize" eeimg="1"> . 从而 公式 (1)的  <img src="https://www.zhihu.com/equation?tex=min_u" alt="min_u" class="ee_img tr_noresize" eeimg="1">  变成  <img src="https://www.zhihu.com/equation?tex=min_w" alt="min_w" class="ee_img tr_noresize" eeimg="1"> 就是分位数回归的目标函数了。


 

 # 一些参考资料
  
 ## 代码
 >>  http://www.statsmodels.org/dev/examples/notebooks/generated/quantile_regression.html
 >>  
 
 .