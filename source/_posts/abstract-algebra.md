---
title: 抽象代数笔记
subtitle: 群、环、域
date: 2019-11-24 23:24:56
comments: true
tags: 
 - 抽象代数
categories: 
 - 数学
top_img: /images/math.jpg
cover: /images/math.jpg
---

# 群、环、域
## 群
### 群的定义
#### 半群
>* 满足结合律
#### 含幺半群
>* 满足结合律
>* 有单位元
#### 群 
>* 满足结合律 
>* 有单位元
>* 有逆元
#### Abel群（可换群）
>* 满足结合律 
>* 有单位元
>* 有逆元
>* 满足交换律
#### 关系 
>半群$\rightarrow$含幺半群$\rightarrow$群$\rightarrow$Abel群
#### 举例
>* 群:(Z,+)
>* Abel群:(Q,+),(R,+),(C,+)
### 群的阶
>群G的元素个数 |G| 称为群G的阶
### 群的运算
* 可换群中的运算称为加法，可换群又叫加群
* 加群的单位元叫零元，逆元叫负元
* 当ab=ba时,(ab)^n^=a^n^b^n^
### 单位元
**若存在e<sub>L</sub>=e<sub>R</sub>=e,单位元唯一**
>**证明**：(证 e<sub>L</sub>=e<sub>L</sub>e<sub>R</sub>=e<sub>R</sub>)
>设有e<sub>1</sub>,e<sub>2</sub>,则e<sub>1</sub>=e<sub>1</sub>e<sub>2</sub>=e<sub>2</sub>
### 逆元
* **若存在a<sub>L</sub>^-1^=a<sub>R</sub>^-1^，则a<sub>L</sub>^-1^=a<sub>R</sub>^-1^=a^-1^,且逆元唯一**
  >**证明**：a<sub>L</sub>^-1^=a<sub>L</sub>^-1^(aa<sub>R</sub>^-1^)=a<sub>R</sub>^-1^
$\exists$ a<sub>1</sub>^-1^,a<sub>2</sub>^-1^,则a<sub>1</sub>^-1^=a<sub>1</sub>^-1^aa<sub>2</sub>^-1^=a<sub>2</sub>^-1^
* **性质**：
    >* (a^-1^)^-1^=a
    >* a,b可逆，则ab可逆，(ab)^-1^=b^-1^a^-1^
    >* a可逆则a^n^可逆，(a^n^)^-1^=(a^-1^)^n^=a^-n^
### 例题
**半群(G,$\cdot$)是群的充要条件:**
1.G有左单位元e<sub>L</sub>，$\forall$a$\in$G，e<sub>L</sub>a=a
2.$\forall$a$\in$G，有左逆元a^-1^，a^-1^a=e<sub>L</sub>
>**证明**：
>①证左逆元也是右逆元
> aa^-1^=e<sub>L</sub>aa^-1^=(a^-1^)^-1^a^-1^aa^-1^=(a^-1^)^-1^e<sub>L</sub>a^-1^=(a^-1^)^-1^a^-1^=e<sub>L</sub>
>②证左单位元也是右单位元：
$\forall$a$\in$G,ae<sub>L</sub>=a(a^-1^a)=(aa^-1^)a=e<sub>L</sub>a
>③$\because$ e<sub>L</sub>为单位元
$\therefore$ a^-1^为逆元
---

## 子群
### 表示
>子群：S$\leq$G 真子群：S<G
### 子群运算
A,B为G的非空子集，g$\in$G
>AB={ab | a$\in$A，b$\in$B}
>A^-1^={a^-1^ | a$\in$A}
>gA={ga | g$\in$A}
### 平凡子群
单位子群{e}和群自身为所有群都有的子群，这两个群称为平凡子群
$\Delta$.单群：只有两个子群，单位子群和自身
### 几个命题
>* S$\leq$G$\iff$$\forall$a,b$\in$S,a^-1^$\in$S$\iff$$\forall$a,b$\in$S,ab^-1^$\in$S
>>**证明**：(i)$\Rightarrow$(ii) 由子群定义可知
>(ii)$\Rightarrow$(iii) $\forall$a,b$\in$S,b^-1^$\in$S &emsp;$\therefore$ab^-1^$\in$S
>(iii)$\Rightarrow$(i) aa^-1^=e$\in$S(单位元),ea^-1^=a^-1^$\in$S(逆元)
>由b^-1^$\in$S,ab=a(b^-1^)^-1^$\in$S &emsp;运算对S封闭
>* H$\leq$G,则H的单位元为G的单位元
>* H<sub>1</sub>,H<sub>2</sub>$\leq$G$\Rightarrow$H<sub>1</sub>$\bigcap$H<sub>2</sub>$\leq$G
>* H<sub>1</sub>,H<sub>2</sub>$\leq$G,则H<sub>1</sub>$\bigcup$H<sub>2</sub>$\leq$G$\iff$H<sub>1</sub>$\subseteq$H<sub>2</sub>或H<sub>2</sub>$\subseteq$H<sub>1</sub>
>* H<sub>1</sub>,H<sub>2</sub>$\leq$G,则H<sub>1</sub>H<sub>2</sub>$\leq$G$\iff$H<sub>1</sub>H<sub>2</sub>=H<sub>2</sub>H<sub>1</sub>
>>**证明**：$\Rightarrow$：$\forall$ab$\in$H<sub>1</sub>H<sub>2</sub>，(ab)^-1^$\in$H<sub>1</sub>H<sub>2</sub>
>设(ab)^-1^=a<sub>1</sub>b<sub>1</sub>
$\therefore$ ab=(a<sub>1</sub>b<sub>1</sub>)^-1^=b<sub>1</sub>^-1^a<sub>1</sub>^-1^$\in$H<sub>2</sub>H<sub>1</sub>
$\therefore$ H<sub>1</sub>H<sub>2</sub>$\subseteq$H<sub>2</sub>H<sub>1</sub>
同理可得H<sub>2</sub>H<sub>1</sub>$\subseteq$H<sub>1</sub>H<sub>2</sub>
$\therefore$ H<sub>1</sub>H<sub>2</sub>=H<sub>2</sub>H<sub>1</sub>
$\Leftarrow$：$\forall$a<sub>1</sub>b<sub>1</sub>,a<sub>2</sub>b<sub>2</sub>，(a<sub>1</sub>b<sub>1</sub>)(a<sub>2</sub>b<sub>2</sub>)^-1^
=$a _ { 1 } b _ { 1 } b _ { 2 } ^ { - 1 } a _ { 2 } ^ { - 1 }$=$a _ { 1 } b'a _ { 2 } ^ { - 1 }$=$a _ { 1 } a' b''=a''b''$
$\therefore$$H_{1}H_{2}$$\leq$G
### 元素的阶
* a$\in$G,使a^n^=e成立的最小正整数n为a的阶，记o(a)
$\Delta. o(e)=1$
* a$\in$G，则a^m^=1$\iff$o(a) | m
  >$\Rightarrow$：设$o ( a ) = n ,则 m = p n + r , 0 \leq r < n$
$\therefore a ^ { m } = a ^ { p n + r } = a ^ { r } = 1$
$\because n是使 a ^ { m } = 1$的最小正整数
$\therefore r = 0 \quad 即m = p n \quad$
$\therefore n|m$
$\Leftarrow: n = o ( a ) | m \Rightarrow m = k n \Rightarrow a ^ { m } = a ^ { k n } = \left( a ^ { n } \right) ^ { k } = 1$
* 有限群每一个元素的阶都有限
* G为群,$a , b \in G ,o ( a ) = m , o ( b ) = n，若 ( m , n ) = 1 ,a b = b a,则o ( a b ) = m n$
    >**证明**：设$o ( a b ) = k$
    $\because ( a b ) ^ { m n } = a ^ { m n } b ^ { m n } = 1$
$\therefore k | m n$
$\therefore ( a b ) ^ { k m } = b ^ { k m } = 1 \therefore n | k m$
$\because ( n , m ) = 1 \quad \therefore n | k$
同理$m | k \quad \therefore n m | k$
$\therefore o ( a b ) = k = m n$

### 例题
* $H \leqslant G \Leftrightarrow \forall a , b \in H , a b \in H$
    >$\Rightarrow$:由定义可知
$\Leftarrow: \forall a , b \in H , a b \in H \Rightarrow a H = H$
$\therefore$H为半群
$\because$G中消去律成立
$\therefore$H中消去律也成立
$\therefore$H是群
* G是偶数阶群，证明G中存在二阶元
    >先证大于2的元素个数为偶数个
设$o(a)=n\geq 3$,则$o(a^{-1})=n$，且$a^{-1}\neq a$
$\because$有一个单位元，G有偶数个元素
$\therefore$至少有一个二阶元
* $\forall a , b \in G , o(ab) = o ( b a )$
    >**证明**:设$o( a b ) = n \quad$则$( ab ) ^ { n } = e$
$( a b ) ^ { n } = \underbrace { a ( b a ) \cdots ( b a ) } _ { n - 1 } = a ( b a ) ^ { n - 1 } b = e$
$\therefore b( b a ) ^ { n}=b,( b a ) ^ { n}b=b$
$\therefore ( b a ) ^ { n } = e$
$\therefore o ( ab ) | o ( b a ) \quad$同理$o ( ba ) | o ( ab ) \quad$
$\therefore o ( a b ) = o ( b a )$
* $a\in G,o(a)=n,则o(a^{m})=n/(m,n)$
    >证能互相整除
设$o\left( a ^ { m } \right) = k , \quad ( m , n ) = d$
令$m = r d , n = s d , \quad n / ( m , n ) = s$
①.$( a ^ { m } ) ^ { s } = a ^ { m s } = a ^ { n r } = e \quad \therefore k | s$
②.$\left( a ^ { m } \right) ^ { k } = a ^ { m k } = e \quad \therefore n | m k$
$\therefore \operatorname { s | k } \quad\therefore ( r , s ) = 1 \quad \therefore s | k$
$\therefore k = s$
---
## 生成元，同构
### 生成元
$a \in G ,\quad$ 令$H = \left\{ a ^ { k } | k \in Z \right\}$，此子群为由 $a$ 生成的循环子群$<a>$，则$a$为H的生成元
### 同构
对群 $( G , \cdot ) , \quad \left( G ^ { \prime } , \circ \right)$，若存在双射$f$从G到G'，$f ( a \cdot b ) = f ( a ) \circ f ( b ) ( \forall a , b \in G )$
则称$f$为G的同构
### 命题
* $\left( Z, + \right)$的生成元为1或-1
* $\left( Z _ { n } , + \right)$的生成元为$\bar { a } , ( a , n ) = 1$
    >**证明**：设$z _ { n } = \langle \bar { a } \rangle \quad \because \bar{1}\in Z _ { n }$
$\therefore$必有$k,k\bar{a}=\bar{1}  \Leftrightarrow \exists p \in Z , \quad k a + p n = 1$
$\Leftrightarrow( a , n)  = 1$
* （$Q,+$）与（$Q^{*},\cdot$）不同构
    >**证明**：设（Q,+）与（Q^*^,$\cdot$）同构
    设$f(a)=2$  ，则$f(a)=f(\frac{a}{2}+\frac{a}{2})=f(\frac{a}{2})f(\frac{a}{2})=\sqrt{2} \notin Q^{*}$
* 循环群的子群仍是循环群，且
    (1)$(Z,+)$的全部子群为$H_{m}=\langle m \rangle ,m=0,1,2,$…
    (2)$(Z_{n},+)$的全部子群为$\langle \bar{0}\rangle$和$\lang \bar{d} \rangle,d|n$
    >**证明**：(1)设$H \leqslant Z ,$若$H \neq \{ 0 \} ,$令$M = \{ x | x \in H , x > 0 \}$
$\because x \in H \quad \therefore x \in H \quad \therefore M \neq \phi$
由自然数集的良序性可知，$M$存在最小元$m$
$\therefore \forall x \in M , \quad x=p m + r , \quad \therefore 0 \leq r < m , r = x - p m \in M$
由$M$最小性得$r = 0 \quad \therefore M = \left\{ k m | k \in Z ^ { + } \right\}$
$\therefore H = \{ k m | k \in Z \} = \langle m \rangle$
(2) 令$Z _ { n } = \left\{ \bar { 0} , \bar {1} , \right.$$\cdots$$,\overline { n - 1 } \},$设$H \leqslant Z ,$且$H \neq \{ \overline { 0 } \}$
令$M = \{ k | \bar { k } \in H \backslash \{ \overline { 0 } \} , k < n \} ,M \neq \phi$是自然数的子集，且由最小元$d$
$\forall x \in M , x = p d + r , 0 \leq r < d , \bar { r } = \bar { x } - p \bar { d } \in H$
$\because d$为最小元$\quad \therefore r =0$
$\therefore M = \{ kd | k > 0 \} , H = \{ k \bar{d} | k = 0,1,2 , \cdots \}$
由$d$最小$\Rightarrow \exists m \in z ^ { + } , m d = n$
$\therefore H = \{ \overline { 0 } , \bar { d } , \bar { 2d }  , \cdots , \bar{(m - 1)d} \rangle,d|n$

---
## 陪集
### 几个定价命题
* $aH = H \Leftrightarrow a\in H$
    >$\Leftarrow$:由定义可知
$\Rightarrow: e \in H , \quad \exists h ^ { \prime } \in H , \quad a h ^ { \prime } = e$
* $b \in a H \Leftrightarrow a H = b H$
    >$\Rightarrow: b \in a H  \therefore \exist h ^ { \prime } \in H \quad b = a h ^ { \prime }$
$b H = a h ^ { \prime } H = a H$
$\Leftarrow: e \in H \quad$ be $\in aH$
* $a H = b H \Leftrightarrow a ^ { - 1 } b \in H \left( H a = H b \Leftrightarrow b a ^ { - 1 }\in H \right)$
    >$\Rightarrow: H = a ^ { - 1 } b H \quad \therefore a ^ { - 1 } b \in H$
$\Leftarrow a ^ { - 1 } b \in H \quad \exists h \in H \quad a ^ { - 1 } b = h \quad b = a h \in a H$
### 子群指数
$H \leq G$,$H$在$G$中的左（右）陪集个数，用$[ G: H ]$表示
### 拉格朗日定理
$H \leq G , | G | = | H | [G:H]$
* G为有限群，$H\leq G,$则$|H| | |G|$
* 当$|G| < \infty$时，$\forall a \in G,o ( a ) | | G |$
* 若$| G | = p$(素数)，则$G = C _ { p}$，即素数阶群必为循环群
    >**证明**:$\forall a \in G , a \neq e$，由$( 2 ): \circ ( a ) | | a | = P$
$\because o ( a ) > 1 \quad \therefore o ( a ) = p$
$\therefore G=\langle a \rangle$
### 命题
* $A = \{ a H|a \in G \}$构成划分
* $| A B | = \frac { | A | |B | } { | A \cap B | }$
* $A \leqslant G , B \leqslant G , \exists g , h \in G , A g = B h ,$则$ A = B$
    >**证明**:$A \subseteq B ,$由于$Ag=Bh$
    $\therefore g = b h, \quad \forall a \in A,abh=ag=b_{1}h$
$\therefore a = b_{1} b ^ { - 1 } \in B$

---
## 正规子群和商群
### 正规子群
$H \leqslant G, \forall g \in G , \quad g H = H g ,$则称H为G的正规子群，记为$H \unlhd G$
### 性质
$\forall a \in G , a H = H a \Leftrightarrow \forall a \in G , \forall h \in H , a h a ^ { - 1 } \in H$
$\Leftrightarrow \forall a \in G , a H a ^ { - 1 } \subseteq H \Leftrightarrow \forall a \in G , aHa ^ { - 1 } = H$
>$\begin{aligned} 1 \Rightarrow 2 &: \forall a \in G , \forall h \in H , a h \in H a \Rightarrow a h = h_{1} a \\ & \Rightarrow a h a ^ { - 1 } = h_{1} \in H \\ 2 \Rightarrow 3 &:  a ha^{-1} \Rightarrow a H a ^ { - 1 } \subseteq H \end{aligned}$
$3 \Rightarrow 4: \forall a \in G, aHa^{-1}$ $\subseteq H$
$\because a ^ { - 1 } \in G \quad \therefore a ^ { - 1 } H \left( a ^ { - 1 } \right)^{-1} = a ^ { - 1 } H a\subseteq H$
$\forall h \in H , a ^ { - 1 } h a = h_{1}\in H$
$\therefore h = a h a ^ { - 1 } \in aHa ^ { - 1 }$
$\therefore H \subseteq a H a ^ { - 1 } \quad \therefore H = a H a ^ { - 1 }$
>$4\Rightarrow 1: a H a ^ { - 1 } \Rightarrow \left( a H a ^ { - 1 } \right) a = H a \Rightarrow aH=Ha$
### 商群
$H \unlhd G,G / H = \{ a H | a \in G \} = \{ H a | a \in G \},G/H$关于子集乘法构成的群称为G关于H的商群
### 命题
* 指数为2的子群为正规子群
    >**证明**:$H \leqslant G , \quad [ G: H ] = 2$
取$G \in G$ \ $H \quad$ 则$aH \cap H = \phi$
$G = H U a H = H U H a \quad$
$\therefore a H = a$ \ $H= H a$
$\therefore H \unlhd G$
* $A \unlhd G , B \unlhd G ,$则$A \cap B \unlhd G , A B \unlhd G$
    >**证明**:
    $(1)\forall h \in A \cap B , g \in G$
    $\because h \in A , A \unlhd G$
$\therefore ghg ^ { - 1 } \in A$
$\because h \in B , B \unlhd G \quad \therefore g h g ^ { - 1 } \in B$
$\therefore g h g ^ { - 1 } \in A \cap B \quad \therefore A \cap B \unlhd G$
$(2)$先证$A B \leqslant G \quad$
由于$A\unlhd G \quad \therefore A B = B A\quad \therefore A B \leq G$(由子群性质可得)
再证$A B\unlhd G: \forall g \in G , a b \in A B$
$g a b g ^ { - 1 } = \left( g a g ^ { - 1 } \right) \left( gbg ^ { - 1 } \right) = a_{1} b_{1} \in A B$
$\therefore A B \unlhd G$
* $A \unlhd G , B \leq G ,$则$A \cap B \unlhd B , A B \leqslant G$
    >$(1)\forall h \in A \cap B , b \in B$
$\because h \in A , b \in G  \quad: b h b ^ { - 1 } \in A$
$\because h \in B \quad \therefore b h b ^ { - 1 } \in B \quad \therefore b h b ^ { - 1 } \in A \cap B$
$\therefore A \cap B \unlhd B$
$(2)A \unlhd G \quad \therefore A B = B A \quad \therefore A B \leqslant G$
---
## 群的同态
### 定义
两个群 $(G,\cdot )(G',\circ )$，若存在$f:G \rightarrow G'$,$\forall a,b \in G,f(a \cdot b)=f(a) \circ f(b)$，则称$f$是$G$到$G'$的一个同态，表示为$G \stackrel{f}{\sim } G'$
如果$f$为单射，则称为单同态，$f$为满射，则称为满同态，$f$为双射，则称为同构，同构记为$G \cong G'$

### 同态基本定理
* **核：**$G \stackrel{f}{\sim } G'$，$K = \left\{ a | a \in G , f ( a ) = e' \right\} = f ^ { - 1 } \left( e'\right)$，$K$是同态$f$的核，记为$Kerf$
* $K$是群
* $K\unlhd G$
* $\forall a ^ { \prime } \in Im f ,$若$f ( a ) = a ^ { \prime } ,$则$f ^ { - 1 } \left( a ^ { \prime } \right) = a k$ 
* $G / K \cong  G'$
    >**证明**:
    $G / K = \{ gK | g \in G \} \quad \sigma : g K \rightarrow f ( g ) \quad  (G / K \rightarrow G')$
    $\forall g_{1} , g _ { 2 } \in G,\quad$设$g _ { 1 } K = g _ { 2 } K$
    则$g _ { 1 } ^ { - 1 } g _ { 2 } \in K \Leftrightarrow f \left( g _ { 1 } ^ { - 1 } g_{2} \right) =e'$
    $\Leftrightarrow f \left( g _ { 1 } \right) = f \left( g _ { 2 } \right)$
    $\therefore \sigma$为单射
    $\forall b \in G ^ { \prime } , \exists a \in G , f ( a ) = b$
    $\therefore a k \in G / K \quad \sigma ( a k ) = f ( a ) = b$
    $\therefore \sigma$为满射
    $\sigma \left( g _{1}k g _ { 2 } k \right) = \sigma \left( g_{1} g_{2} k \right) = f \left( g _ { 1 } g _ { 2 } \right)$
    $=f \left( g_ { 1 } \right) f ( g_{2} ) = \sigma \left( g_ { 1 } k \right) \sigma ( g_{2}k )$
    $\therefore \sigma$为同构 
* $G \stackrel{f}{\sim } G'$，$\varphi$是$G$到$G/K$的自然同态，$\exist G/K$到$G'$的同构$\sigma$使$f=\sigma \varphi$
    >$\sigma : g K \rightarrow f ( g )$
    $\forall x\in G$，$(\sigma \varphi)(x)=\sigma(\varphi(x))=\sigma(xK)=f(x)$
    $\therefore \sigma \varphi=f$


---
## 环
### 定义
* $A$是非空集合，$(A,+)$为可换群，$(A,\cdot)$为半群，且满足加法和乘法的分配率，则称$(A,+,\cdot)$为环
* 若对乘法可换，则称可换环
### 零因子
$ab=0,a\neq0,b\neq0,a$为零因子，b为右零因子
### 整环
无零因子的可换环
### 除环
至少有两个元素：单位元和逆元，$A^{*}=A\backslash\{0\}$构成乘法群
### 域
* 可换的除环或乘法构成群的整环
* 最简单的域：$\{ 0,1 \}$
* 环无零因子的充分必要条件是乘法消去律成立
* 有限的无零因子环是除环（满足消去律，乘法成群）
* 有限整环是域（同时为除环和整环）
---
## 子环
* **子环性质:**
  * $S\subseteq A,\forall a,b \in S,a-b \in S,ab \in S \Leftrightarrow S$为$A$的子环
  * $S_{1},S_{2}$为$A$子环$\Rightarrow S_{1}\cap S_{2}$为$A$子环
* **左理想、右理想：** 相当于群的陪集
* **理想：** 相当于正规子群
* **商环：**$A$为环，$I$为$A$的理想，$A$作为加群关于$I$的商群$A/I=\{a+I|a\in A\}$
---
## 环的同构与同态
环$A$和$A'$，有$f:A\rightarrow A'$，$\forall a,b \in A$，$f(a+b)=f(a)+f(b)$，$f(ab)=f(a)\circ f(b)$，称$f$为同态，若$f$为单射，称单同态，若$f$为满射，称满同态，若$f$为双射，称同构

---