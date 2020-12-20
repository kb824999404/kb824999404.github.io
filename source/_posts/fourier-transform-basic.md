---
title: 傅里叶变换和频域滤波基础
tags:
  - 傅里叶变换
  - 频域滤波
categories:
  - 数字图像处理
top_img: /images/fourier.jpg
cover: /images/fourier.jpg
date: 2020-12-20 12:46:00
---

## 傅里叶变换和频域滤波基础
---
### 1. 傅里叶变换

#### 1.1 从傅里叶级数到傅里叶变换的推导

* 欧拉公式：$e^{j\theta}=cos\theta+jsin\theta$
* 从傅里叶级数到傅里叶变换：
  1. 利用欧拉公式，将傅里叶级数从三角函数形式化为指数形式
  2. 利用黎曼和，将其中的累加形式化为积分形式
* 傅里叶级数三角函数形式：
  * $f(t)$为具有周期T的周期函数，可以表示为$f(t)=\frac{a_0}{2}+\sum_{n=1}^{\infin}(a_n cos(n\omega t)+b_n sin(n\omega t))$
  * 其中，$\omega=\frac{2\pi}{T},a_n=\frac{2}{T}\int_{-\frac{T}{2}}^{\frac{T}{2}}f(t)cos(n\omega t)\ dt,b_n=\frac{2}{T}\int_{-\frac{T}{2}}^{\frac{T}{2}}f(t)sin(n\omega t)\ dt$  
  * $n=0$时，$a_0=\frac{2}{T}\int_{-\frac{T}{2}}^{\frac{T}{2}}f(t)dt$ 
* 三角函数形式到指数形式的推导：
  * 根据欧拉公式$e^{j\theta}=cos\theta+jsin\theta$有：$cos\theta=\frac{e^{j\theta}+e^{-j\theta}}{2},sin\theta=\frac{e^{j\theta}-e^{-j\theta}}{2i}=-j\cdot\frac{e^{j\theta}-e^{-j\theta}}{2}$ 
  * 代入得$f(t)=\frac{a_0}{2}+\sum_{n=1}^{\infin}(a_n cos(n\omega t)+b_n sin(n\omega t)\\=\frac{a_0}{2}+\sum_{n=1}^{\infin}(a_n \frac{e^{jn\omega t}+e^{-jn\omega t}}{2} -j\cdot b_n\frac{e^{jn\omega t}-e^{-jn\omega t}}{2})\\=\frac{a_0}{2}+\sum_{n=1}^{\infin}(\frac{a_n-jb_n}{2}e^{jn\omega t}+\frac{a_n+jb_n}{2}e^{-jn\omega t})$ 
  * 令$c_0=\frac{a_0}{2},c_n=\frac{a_n-jb_n}{2},d_n=\frac{a_n+jb_n}{2},$则$f(t)=c_0+\sum_{n=1}^{\infin}(c_ne^{jn\omega t}+d_ne^{-jn\omega t})$
  * 则$c_0=\frac{1}{T}\int_{-\frac{T}{2}}^{\frac{T}{2}}f(t)dt,\\c_n=\frac{1}{T}\int_{-\frac{T}{2}}^{\frac{T}{2}}f(t)(cos(n\omega t)-jsin(n\omega t))dt=\frac{1}{T}\int_{-\frac{T}{2}}^{\frac{T}{2}}f(t)e^{-jn\omega t}dt,\\d_n=\frac{1}{T}\int_{-\frac{T}{2}}^{\frac{T}{2}}f(t)(cos(n\omega t)+jsin(n\omega t))dt=\frac{1}{T}\int_{-\frac{T}{2}}^{\frac{T}{2}}f(t)e^{jn\omega t}dt$  
  * 可以看出$d_n=c_{-n},\sum_{n=1}^{\infin}d_ne^{-jn\omega t}=\sum_{n=1}^{\infin}c_{-n}e^{-jn\omega t}=\sum_{-\infin}^{-1}c_{n}e^{jn\omega t}$ 
  * 则$f(t)=c_0+\sum_{n=1}^{\infin}(c_ne^{jn\omega t}+d_ne^{-jn\omega t})\\=c_0e^{j0\omega t}+\sum_{n=1}^{\infin}c_ne^{jn\omega t}+\sum_{n=1}^{\infin}d_ne^{-jn\omega t}\\=c_0e^{j0\omega t}+\sum_{n=1}^{\infin}c_ne^{jn\omega t}+\sum_{n=-\infin}^{-1}c_ne^{jn\omega t}\\=\sum_{n=-\infin}^{\infin}c_n e^{jn\omega t}\\=\frac{1}{T}\sum_{n=-\infin}^{\infin}\int_{-\frac{T}{2}}^{\frac{T}{2}}f(t)e^{-jn\omega t}dt\cdot e^{jn\omega t}$ 
* 将累加形式化为积分形式，推导省略(看不懂@~@)，可参考[傅里叶变换的推导](https://zhuanlan.zhihu.com/p/41875010)
  * $f(t)=\frac{1}{2\pi}\int_{-\infin}^{\infin}(\int_{-\infin}^{\infin}f(t)e^{-js t}dt)e^{js t}ds,s=n\omega$ 
  * 令$F(s)=\int_{-\infin}^{\infin}f(t)e^{-js t}dt$，则  $f(t)=\frac{1}{2\pi}\int_{-\infin}^{\infin}F(s)e^{js t}ds$ 
* 由此得到：
  * 傅里叶变换：$F(s)=\int_{-\infin}^{\infin}f(t)e^{-js t}dt$
  * 反傅里叶变换：$f(t)=\frac{1}{2\pi}\int_{-\infin}^{\infin}F(s)e^{js t}ds$
  * 一般写成：$F(\mu)=\int_{-\infin}^{\infin}f(t)e^{-j2\pi\mu t}dt$，$f(t)=\int_{-\infin}^{\infin}F(\mu)e^{j2\pi\mu t}d\mu$，$\mu=\frac{s}{2\pi}$，即$\mu$为频率(单位Hz)

#### 1.2 一些函数的傅里叶变换

* 盒状函数的傅里叶变换：$f(t)=\begin{cases} A,& -W/2<t<W/2\\ 0,& t\leq -W/2,t\geq W/2  \end{cases}$ 
  * $F(\mu)=\int_{-\infin}^{\infin}f(t)e^{-j2\pi\mu t}dt\\=\int_{-W/2}^{W/2}Ae^{-j2\pi \mu t}dt\\=\frac{A}{-j2\pi\mu}[e^{-j\pi\mu W}-e^{j\pi\mu W}]\\=AW\frac{sin(\pi\mu W)}{(\pi\mu W)}\\=AWsinc(\mu W)(sinc(m)=\frac{sin(\pi m)}{\pi m})$  
  * 幅值：$|F(\mu)|=AW|\frac{sin(\pi\mu W)}{(\pi\mu W)}|$ 
  * 函数图像：![盒状函数](https://ian824.gitee.io/blogpic/img/fourier-transform-basic/boxfunction.PNG)
  * 函数性质：在0函数值为$AW$，对于$\mu=\frac{n}{W}$的其他整数值，$F(\mu)=0$，波瓣的高度随函数距原点的距离降低 

#### 1.3 傅里叶变换的性质

* 对偶性质(傅里叶变换的傅里叶变换)：函数$f(t)$有傅里叶变换$F(\mu)$，则$F(t)$的傅里叶变换为$f(-\mu)$ 
* $F(-\mu)=F^*(\mu)$
* $f(t)$为偶函数，则其傅里叶变换只包含实数，同样为偶函数
* $f(t)$为奇函数，则其傅里叶变换只包含虚数，同样为奇函数

#### 1.4 傅里叶变换公式的理解

* 参考：[3Blue1Brown：形象展示傅里叶变换](https://www.bilibili.com/video/BV1pW411J7s8)

* $F(s)=\int_{-\infin}^{\infin}f(t)e^{-js t}dt$：
  * $e^{-js t}$指数项意味着将函数进行旋转缠绕在圆上，$s$为旋转的频率
  * 频谱图横坐标为旋转的频率，纵坐标为缠绕图像的质心
  * 当旋转频率和函数本身频率相同时，会出现峰值
  * 积分意味着取质心，并乘以时间区间长度，这意味着存在时间长的频率会被放大
  * ![形象展示傅里叶变换](https://ian824.gitee.io/blogpic/img/fourier-transform-basic/fourier_comprehension.png)

---
### 2. 冲激函数及其性质

#### 2.1 连续冲激

* 冲激函数定义：t为连续变量，$\delta(t)=\begin{cases} \infin,& t=0\\ 0,& t\neq 0 \end{cases}$ 
* 物理意义：一个冲激可看出是幅度无限，持续时间为0，具有单位面积的尖峰信号
* 性质：
  * $\int_{-\infin}^{\infin}\delta(t)dt=1$
  * 取样特性：
    * $\int_{-\infin}^{\infin}f(t)\delta(t)dt=f(0)$ 
    * $\int_{-\infin}^{\infin}f(t)\delta(t-t_0)dt=f(t_0)$ 

#### 2.2 离散冲激

* 定义：x为离散变量，$\delta(x)=\begin{cases} 1,& x=0\\ 0,& x\neq 0 \end{cases}$
* 性质：
  * $\sum_{x=-\infin}^{\infin}\delta(x)=1$ 
  * 取样特性：
    * $\sum_{x=-\infin}^{\infin}f(x)\delta(x)=f(0)$
    * $\sum_{x=-\infin}^{\infin}f(x)\delta(x-x_0)=f(x_0)$ 

#### 2.3 冲激函数常用性质

* 冲激函数的傅里叶变换：$F(\delta(t))=1$
  * 证明：$F(\mu)=\int_{-\infin}^{\infin}\delta(t)e^{-j2\pi \mu t}dt=e^{-j2\pi \mu t}|_{t=0}=e^{-j2\pi \mu 0}=1$ 
  * 同理可得： $F(\delta(t-t_0))=e^{-j2\pi ut_0}$ 
* $f(t)=1$的傅里叶变换为$\delta(\mu)$
  * 证明(求$\delta(\mu)$的反傅里叶变换)：$f(t)=\int_{-\infin}^{\infin}\delta(\mu)\cdot e^{j2\pi \mu t}dt=1$
* $f(t)=e^{jat}$的傅里叶变换为$\delta(\mu-\frac{a}{2\pi})$
  * 证明：$f(t)=\int_{-\infin}^{\infin}\delta(\mu-\frac{a}{2\pi})\cdot e^{j2\pi\mu t}dt=e^{j2\pi\frac{a}{2\pi}t}=e^{jat}$ 
* $f(t)=sinat$的傅里叶变换为$\frac{\delta(\mu-\frac{a}{2\pi})-\delta(\mu+\frac{a}{2\pi})}{2j}$ 
  * 证明：$sinat=\frac{e^{jat}-e^{-jat}}{2j},F(sinat)=\frac{F(e^{jat})-F(e^{-jat})}{2j}$ 
* $f(t)=cosat$的傅里叶变换为$\frac{\delta(\mu-\frac{a}{2\pi})+\delta(\mu+\frac{a}{2\pi})}{2}$  
* 上述性质的由来：
  * 由傅里叶变换的对偶性质和$F(\delta(t-t_0))=e^{-j2\pi ut_0}$ 可得，$F(e^{-j2\pi t t_0})=\delta(-\mu-t_0)$ 
  * 令$-2\pi t_0=a$，可得$F(e^{jat})=\delta(-\mu +\frac{a}{2\pi})=\delta(\mu -\frac{a}{2\pi})$（$\delta(t-t_0)$关于$t_0$对称）

#### 2.4 冲激串及其傅里叶变换

* 冲激串：$s_{\Delta T}(t)=\sum_{n=-\infin}^{\infin}\delta(t-n\Delta T)$ ,周期为$\Delta T$
  * 函数图像：

  ![冲激串](https://ian824.gitee.io/blogpic/img/fourier-transform-basic/impulseString.PNG)

* 冲激串的傅里叶变换：
  * 将其用傅里叶级数表示：$s_{\Delta T}(t)=\sum_{n=-\infin}^{\infin}c_n e^{j\frac{2\pi n}{\Delta T} t}$ ，$c_n=\frac{1}{\Delta T}\int_{-\frac{\Delta T}{2}}^{\frac{\Delta T}{2}}s_{\Delta T}(t)e^{-j\frac{2\pi n}{\Delta T} t}dt$ 
  * 区间$[-\Delta T/2,\Delta T/2]$的积分仅包含位于原点的冲激$s_{\Delta T}(t)$，因此$c_n=\frac{1}{\Delta T}e^0=\frac{1}{\Delta T}$ 
  * 则其傅里叶级数为$s_{\Delta T}(t)=\frac{1}{\Delta T}\sum_{n=-\infin}^{\infin}e^{j\frac{2\pi n}{\Delta T} t}$ 
  * 由$F(e^{j\frac{2\pi n}{\Delta T}t})=\delta(\mu-\frac{n}{\Delta T})$得$S(\mu)=F(s_{\Delta T}(t))=\frac{1}{\Delta T}\sum_{n=-\infin}^{\infin}\delta(\mu-\frac{n}{\Delta T})$ 
  * 由此可知，周期为$\Delta T$的冲激串的傅里叶变换还是周期冲激串，其周期为$1/\Delta T$ 

---

### 3. 一维卷积及其性质

* 一维卷积：$f(t)*h(t)=\int_{-\infin}^{\infin}f(\tau)h(t-\tau)d\tau$ 

* 卷积定理：$F(f(t))=F(\mu),F(h(t))=H(\mu)$

  * $F(f(t)*h(t))=F(\mu)\cdot H(\mu),F^{-1}(F(\mu)\cdot H(\mu))=f(t)*h(t)$

  * $F(f(t)\cdot h(t))=F(\mu)* H(\mu),F^{-1}(F(\mu)* H(\mu))=f(t)\cdot h(t)$ 

  * 空间域中两个函数的卷积的傅里叶变换等于两个函数的傅里叶变换在频率域中的乘积

  * 在频率域中有两个变换的乘积，那么我们可以通过计算傅里叶反变换得到空间域的卷积

  * 空间域中两个函数的乘积的傅里叶变换等于两个函数的傅里叶变换在频率域中的卷积

  * 在频率域中有两个变换的卷积，那么我们可以通过计算傅里叶反变换得到空间域的乘积

  * 证明：

    > $F(f(t)*h(t))=\int_{-\infin}^{+\infin}(\int_{-\infin}^{+\infin}f(\tau)h(t-\tau)d\tau)e^{-j2\pi \mu t}dt$ 
    >
    > $=\int_{-\infin}^{+\infin}f(\tau)(\int_{-\infin}^{+\infin}h(t-\tau)e^{-j2\pi \mu t}dt)d\tau$ (令$x=t-\tau$)
    >
    > $=\int_{-\infin}^{+\infin}f(\tau)(\int_{-\infin}^{+\infin}h(x)e^{-j2\pi \mu (x+\tau)}dx)d\tau$
    >
    > $=\int_{-\infin}^{+\infin}f(\tau)(\int_{-\infin}^{+\infin}h(x)e^{-j2\pi \mu x}dx)e^{-j2\pi \mu \tau}d\tau$ 
    >
    > $=\int_{-\infin}^{+\infin}f(\tau)H(\mu)e^{-j2\pi \mu \tau}d\tau$ 
    >
    > $=H(\mu)\int_{-\infin}^{+\infin}f(\tau)e^{-j2\pi \mu \tau}d\tau=H(\mu)F(\mu)$ 

---

### 4. 取样及其傅里叶变换

#### 4.1 取样

* 用计算机处理之前，连续函数必须转换为离散值序列，通过取样和量化来完成

* 取样：对一个连续函数$f(t)$，以独立变量$t$的均匀间隔$\Delta T$取样，用一个$\Delta T$单位间隔的冲激串作为取样函数乘以$f(t)$，即$\overset{\sim}f(t)=f(t)s_{\Delta T}(t)=\sum_{n=-\infin}^{\infin}f(t)\delta(t-n\Delta T)$ ,$\overset{\sim}f(t)$表示取样后的函数

* 该和式中每一个分量都是由在该冲激位置处$f(t)$的值加权后的冲激，每个取样值由加权后的冲激"强度"给出，可以通过积分得到它，即序列中的任意取样值$f_k=\int_{-\infin}^{\infin}f(t)\delta(t-k\Delta T)dt=f(k\Delta T)$ 

* 连续函数，冲激串，取样结果：

  ![取样](https://ian824.gitee.io/blogpic/img/fourier-transform-basic/sample.PNG)

#### 4.2 取样函数的傅里叶变换

* 取样后的函数$\overset{\sim}f(t)$的傅里叶变换$\overset{\sim}F(\mu)=F(\overset{\sim}f(t))=F(f(t)s_{\Delta T}(t))=F(\mu)*S(\mu)$ (根据卷积定理)

* 根据冲激串的傅里叶变换$S(\mu)=\frac{1}{\Delta T}\sum_{n=-\infin}^{\infin}\delta(\mu-\frac{n}{\Delta T})$  可得：

  $\overset{\sim}F(\mu)=F(\mu)*S(\mu)$

  $=\int_{-\infin}^{\infin}F(\tau)S(\mu-\tau)d\tau$

  $=\frac{1}{\Delta T}\sum_{n=-\infin}^{\infin}\int_{-\infin}^{\infin}\delta(\mu-\tau-\frac{n}{\Delta T})d\tau$

  $=\frac{1}{\Delta T}\sum_{n=-\infin}^{\infin}F(\mu-\frac{n}{\Delta T})$ (根据冲激的取样特性)

* 取样后的函数$\overset{\sim}f(t)$的傅里叶变换$\overset{\sim}F(\mu)$是$F(\mu)$的一个拷贝的无限、周期序列，也是原始连续函数的傅里叶变换，其周期为$1/\Delta T$ 即取样率

  ![取样函数的傅里叶变换](https://ian824.gitee.io/blogpic/img/fourier-transform-basic/sample_Fourier.PNG)

---

### 5. 单变量的离散傅里叶变换(DFT)

#### 5.1 DFT推导

* 取样过的数据的傅里叶变换两种形式：

  * 关于原始数据：$\overset{\sim}F(\mu)=\frac{1}{\Delta T}\sum_{n=-\infin}^{\infin}F(\mu-\frac{n}{\Delta T})\quad(1)$ (前面的推导)
  * 关于取样后的数据：$\overset{\sim}F(\mu)=\int_{-\infin}^{\infin}\overset{\sim}f(t)e^{-j2\pi \mu t}dt\\=\int_{-\infin}^{\infin}\sum_{n=-\infin}^{\infin}f(t)\delta(t-n\Delta T)e^{-j2\pi \mu t}dt\\=\sum_{n=-\infin}^{\infin}\int_{-\infin}^{\infin}f(t)\delta(t-n\Delta T)e^{-j2\pi \mu t}dt\\=\sum_{n=-\infin}^{\infin}f(n\Delta T)e^{-j2\pi\mu n\Delta T}\quad(2)$  

* $\overset{\sim}F(\mu)$是一个连续函数，要在$\mu=0$到$\mu=1/\Delta T$之间得到$\overset{\sim}F(\mu)$的M个等间距的样本，可通过在以下频率处取样得到：$\mu=\frac{m}{M\Delta T},m=0,1,2,\cdots,M-1$，把该结果代入式(1)，用$F_m$表示得到的结果，则有：

  $F_m=\overset{\sim}F(\frac{m}{M\Delta T})=\sum_{n=-\infin}^{\infin}f(n\Delta T)e^{-j2\pi\mu n\Delta T}\\=\sum_{n=0}^{M-1}f(n\Delta T)e^{-j2\pi mn/M},m=0,1,2,\cdots,M-1$ 

* 要得到$-\frac{1}{2\Delta T}\leq \mu\leq \frac{1}{2\Delta T}$之间的值，可将$m=M/2$右边部分平移至$m=0$ 左边

* 由式(1)和$\overset{\sim}F(\mu)$的函数图像可得：当$|\mu|\leq\frac{1}{2\Delta T}$时，$F(u)=\Delta T\overset{\sim}F(\mu)\\=\Delta T\sum_{n=0}^{M-1}f(n\Delta T)e^{-j2\pi\mu n\Delta T}$ 

* 对一个连续信号利用数值方法计算它的傅里叶变换的步骤：

  * 根据信号带宽确定采样间隔$\Delta T$ ，然后对 $f(t)$ 采样得到 $f(n\Delta T)$

  * 对离散值 $f(n\Delta T)$求傅里叶变换得到$\overset{\sim}F(\mu)$

  * 对$\overset{\sim}F(\mu)$执行平移操作并乘以$\Delta T$得到$F(\mu)$的M个取样点

  * 过程如图：

    ![DFT](https://ian824.gitee.io/blogpic/img/fourier-transform-basic/dft.PNG)

#### 5.2 一维离散傅里叶变换

* DFT：$F(\mu)=\sum_{x=0}^{M-1}f(x)e^{-j2\pi \mu x/M},\mu=0,1,2,\dots,M-1$ 
* IDFT：$f(x)=\frac{1}{M}\sum^{M-1}_{\mu=0}F(\mu)e^{j2\pi \mu x/M}$ 

---

### 6. 二维傅里叶变换

#### 6.1 二维连续冲激

* 定义：$\delta(t,z)=\begin{cases} \infin,&t=z=0 \\0,&Others \end{cases}$
* 性质：
  * $\int_{-\infin}^{\infin}\int_{-\infin}^{\infin}\delta(t,z)dtdz=1$ 
  * 取样特性：
    * $\int_{-\infin}^{\infin}\int_{-\infin}^{\infin}f(t,z)\delta(t,z)dtdz=f(0,0)$
    * $\int_{-\infin}^{\infin}\int_{-\infin}^{\infin}f(t,z)\delta(t-t_0,z-z_0)dtdz=f(t_0,z_0)$ 

#### 6.2 二维离散冲激

* 定义：$\delta(x,y)=\begin{cases} 1,&x=y=0 \\0,&Others \end{cases}$
* 取样特性：
  * $\sum_{x=-\infin}^{\infin}\sum_{y=-\infin}^{\infin}f(x,y)\delta(x,y)=f(0,0)$
  * $\sum_{x=-\infin}^{\infin}\sum_{y=-\infin}^{\infin}f(x,y)\delta(x-x_0,y-y_0)=f(x_0,y_0)$ 

#### 6.3 二维连续傅里叶变换

* $F(u,v)=\int_{-\infin}^{\infin}\int_{-\infin}^{\infin}f(t,z)e^{-j2\pi (\mu t+vz)}dt\ dz$ 

* $f(t,z)=\int_{-\infin}^{\infin}\int_{-\infin}^{\infin}F(u,v)e^{j2\pi(\mu t+vz)}d\mu\ dv$ 

* $\mu$和$v$为频率变量，涉及图像时，t和z为连续空间变量 

* 二维盒状函数的傅里叶变换：$F(u,v)=\int_{-\infin}^{\infin}\int_{-\infin}^{\infin}f(t,z)e^{-j2\pi (\mu t+vz)}dt\ dz\\=\int_{-T/2}^{T/2}\int_{-Z/2}^{Z/2}Ae^{-j2\pi (\mu t+vz)}dt\ dz=ATZ[\frac{sin(\pi\mu T)}{(\pi\mu T)}][\frac{sin(\pi vZ)}{(\pi vZ)}]$  

  ![二维盒状函数](https://ian824.gitee.io/blogpic/img/fourier-transform-basic/2Dbox.PNG) 

#### 6.4 二维取样

* 二维冲激串：$s_{\Delta T\Delta Z}(t,z)=\sum_{m=-\infin}^{\infin}\sum_{n=-\infin}^{\infin}\delta(t-m\Delta T,z-n\Delta Z)$ 

  ![二维冲激串](https://ian824.gitee.io/blogpic/img/fourier-transform-basic/2DImpulseString.PNG)

#### 6.5 二维离散傅里叶变换

* DFT：$F(u,v)=\sum_{x=0}^{M-1}\sum_{y=0}^{N-1}f(x,y)e^{-j2\pi(\mu x/M+vy/N)}$ 

* IDFT：$f(x,y)=\frac{1}{MN}\sum_{x=0}^{M-1}\sum_{y=0}^{N-1}F(u,v)e^{j2\pi(ux/M+vy/N)}$ 

* 性质：

  * 空间取样和相应频率域间隔的关系：对连续函数$f(t,z)$取样生成了一幅数字图像$f(x,y)$，它由分别在t和z方向所取的$M\times N$个样点组成，令$\Delta T$和$\Delta Z$表示样本间的间隔，那么相应离散频率域变量间的间隔分别为$\Delta \mu=\frac{1}{M\Delta T}$和$\Delta v=\frac{1}{N\Delta Z}$ 

  * 平移：

    * 用指数项乘以$f(x,y)$将使DFT的原点移到点$(u_0,v_0)$：$f(x,y)e^{j2\pi(u_0x/M+v_0y/N)}\iff F(u-u_0,v-v_0)$
    * 用负指数乘以$F(x,y)$将使$f(x,y)$的原点移到点$(x_0,y_0)$：$f(x-x_0,y-y_0)\iff F(u,v)e^{-j2\pi(ux_0/M+vy_0/N)}$  
    * 平移不影响$F(u,v)$的幅度

  * 旋转：

    * 使用极坐标$x=rcos\theta,y=rsin\theta,u=\omega cos\phi,v=\omega sin\phi$，可得到以下变换对$f(r,\theta+\theta_0)\iff F(\omega,\phi+\phi_0)$
    * 即，若$f(x,y)$旋转$\theta_0$角度，则$F(u,v)$也旋转相同的角度；反之，若$F(u,v)$旋转一个角度，$f(x,y)$也旋转相同的角度

  * 周期性：二维傅里叶变换及其反变换在$u$方向和$v$方向是无限周期的，即

    * $F(u,v)=F(u+k_1M,v)=F(u,v+k_2N)=F(u+k_1M,v+k_2N)$
    * $f(x,y)=f(x+k_1M,y)=f(x,y+k_2N)=f(x+k_1M,y+k_2N)$ 

  * 根据平移和周期性，可将傅里叶谱原点$F(0,0)$移到图像中心即点$(M/2,N/2)$处：

    * 在式子$f(x,y)e^{j2\pi(u_0x/M+v_0y/N)}\iff F(u-u_0,v-v_0)$中令$(u_0,v_0)=(M/2,N/2)$
    * 得到$f(x,y)(-1)^{x+y}\iff F(u-M/2,v-N/2)$

  * 对称性：

    ![二维傅里叶变换的对称性](https://ian824.gitee.io/blogpic/img/fourier-transform-basic/2D_DFT_sym.PNG)

#### 6.6 傅里叶谱和相角

* 二维DFT可用极坐标表示为：$F(u,v)=|F(u,v)|e^{j\phi(u,v)}$
  * 其中幅度$|F(u,v)|=[R^2(u,v)+I^2(u,v)]^{1/2}$称为傅里叶谱或频谱
  * $\phi(u,v)=arctan[\frac{I(u,v)}{R(u,v)}]$称为相角
  * $R(u,v)$和$I(u,v)$分别为$F(u,v)$的实部和虚部

#### 6.7 二维卷积

* 二维卷积：
  * $f(x,y)*h(x,y)=\sum_{m=0}^{M-1}\sum_{n=0}^{N-1}f(m,n)h(x-m,y-n),\\x=0,1,2,\cdots,M-1,y=0,1,2,\cdots,N-1$ 
* 二维卷积定理：
  * $f(x,y)*h(x,y)\iff F(u,v)H(u,v)$
  * $f(x,y)h(x,y)\iff F(u,v)*H(u,v)$ 
* 由于傅里叶变换和卷积的周期性，对两个图像进行卷积时要进行零填充：
  * $f(x,y)$和$h(x,y)$分别是大小为$A\times B$和$C\times D$的图像
  * 对$f(x,y)$进行零填充：$f_p(x,y)=\begin{cases}f(x,y),&0\leq x\leq A-1,0\leq y\leq B-1 \\ 0,& A\leq x\leq P\ or\ B\leq y\leq Q \end{cases}$ 
  * 对$h(x,y)$进行零填充：$h_p(x,y)=\begin{cases}h(x,y),&0\leq x\leq C-1,0\leq y\leq D-1 \\ 0,& C\leq x\leq P\ or\ D\leq y\leq Q \end{cases}$ 
  * 其中，$\\P\geq A+C-1,Q\geq B+D-1$ ，填充后的图像大小为$P\times Q$
  * 如果两个图像大小相同，都为$M\times N$，则要求$P\geq 2M-1,Q\geq 2N-1$ 

---

### 7. 频率域滤波基础

#### 7.1 频率域滤波步骤

* 直接进行频率域滤波：生成一个频率域的滤波函数
  1. 给定一个大小为$M\times N$的图像$f(x,y)$，令$P=2M,Q=2N$
  2. 对图像进行零填充，得到大小为$P\times Q$的填充图像$f_p(x,y)$
  3. 用$(-1)^{x+y}$乘以$f_p(x,y)$移到其变换的中心
  4. 计算$f_p(x,y)$的DFT得到$F(u,v)$
  5. 生成一个大小为$P\times Q$的频域滤波函数$H(u,v)$
  6. 两者相乘得到$G(u,v)=F(u,v)H(u,v)$
  7. 对结果进行IDFT并平移，得到滤波后的填充图像$g_p(x,y)=F^{-1}(G(u,v))(-1)^{x+y}$
  8. 从$g_p(x,y)$提取大小为$M\times N$的区域得到最终处理结果$g(x,y)$ 
* 与空间滤波对应的频域滤波
  1. 给定一个大小为$A\times B$的图像$f(x,y)$和一个大小为$C\times D$的空间滤波函数$h(x,y)$，令$P\geq A+C-1,Q\geq B+D-1$
  2. 对$f(x,y)$和$h(x,y)$分别进行零填充得到大小为$P\times Q$的$f_p(x,y)$和$h_p(x,y)$
  3. 计算图像和滤波器的DFT得到$F(u,v)$和$H(u,v)$
  4. 两者相乘得到$G(u,v)=F(u,v)H(u,v)$
  5. 进行IDFT得到滤波后的填充图像$g_p(x,y)=F^{-1}(G(u,v))$
  6. 从$g_p(x,y)$提取大小为$A\times B$的区域得到最终处理结果$g(x,y)$ 

---

### 参考

* 《数字图像处理第三版》—— 冈萨雷斯
* 傅里叶变换推导：https://www.zhihu.com/column/c_1299853366366543872
* 傅里叶分析的含义：https://www.cnblogs.com/h2zZhou/p/8405717.html
* 傅里叶变换公式的理解：https://www.bilibili.com/video/BV1pW411J7s8



