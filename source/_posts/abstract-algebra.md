---
title: 抽象代数笔记
subtitle: 群、环、域
date: 2019-11-24 23:24:56
tags: 
 - 抽象代数
categories: 
 - 数学
---

# 抽象代数笔记
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
1.G有单位元e<sub>L</sub>，$\forall$a$\in$G，e<sub>L</sub>a=a
2.$\forall$a$\in$G，有左逆元a^-1^，a^-1^a=e<sub>L</sub>
>**证明**：
>①证 aa^-1^=e<sub>L</sub>
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
$\Delta$. o(e)=1
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
    $ \because ( a b ) ^ { m n } = a ^ { m n } b ^ { m n } = 1$
$\therefore k | m n$
$\therefore ( a b ) ^ { k m } = b ^ { k m } = 1 \therefore n | k m$
$\because ( n , m ) = 1 \quad \therefore n | k$
同理$m | k \quad \therefore n m | k$
$\therefore o ( a b ) = k = m n$

### 例题
* $H \leqslant G \Leftrightarrow \forall a , b \in H , a b \in H$
    >$\Rightarrow $:由定义可知
$\Leftarrow: \forall a , b \in H , a b \in H \Rightarrow a H = H$
$\therefore$H为半群
$\because$G中消去律成立
$\therefore$H中消去律也成立
$\therefore$H是群
* G是偶数阶群，证明G中存在二阶元
    >先证大于2的元素个数为偶数个
设$o(a)=n\geq 3,则o(a^{-1})=n，且a^{-1}\neq a$
$\because$有一个单位元，G有偶数个元素
$\therefore$至少有一个二阶元
* $\forall a , b \in G , o(ab) = o ( b a )$
    >**证明**:设$o( a b ) = n \quad则 ( ab ) ^ { n } = e$
$( a b ) ^ { n } = \underbrace { a ^ { ( b a ) } ( b a ) \cdots ( b a ) } _ { n - 1 } = a ( b a ) ^ { n - 1 } b = e$
$\therefore o(ba)|n \quad即o(ba)|o(ab)$
$\therefore ( b a ) ^ { n - 1 } = a ^ { - 1 } b ^ { - 1 } \quad ( b a ) ^ { n } = e$
$\therefore o ( ab ) | o ( b a ) \quad \therefore o ( a b ) = o ( b a )$
* $a\in G,o(a)=n,则o(a^{m})=n/(m,n)$
    >证能互相整除
设$o \left( a ^ { n } \right) = k , \quad ( m , n ) = d$
令$m = r d , n = s d , \quad n / ( m , n ) = s$
①.$( a ^ { m } ) ^ { s } = a ^ { m s } = a ^ { n r } = e \quad \therefore k | s$
②.$ \left( a ^ { m } \right) ^ { k } = a ^ { m k } = e \quad \therefore n | m k$
$\therefore \operatorname { s | k } \quad\therefore ( r , s ) = 1 \quad \therefore s | k$
$\therefore k = s$
---
## 生成元，同构