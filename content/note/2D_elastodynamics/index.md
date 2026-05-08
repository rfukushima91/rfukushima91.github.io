---
title: 2次元動弾性antiplaneクラックの解
summary: 
date: 2026-05-04

# Featured image
# Place an image named `featured.jpg/png` in this page's folder and customize its options here.
# image:
#   caption: 'Image credit: [**Unsplash**](https://unsplash.com)'

authors:
  - admin

# tags:
#   - Elasticity
#   - Hugo Blox
#   - Markdown

# content_meta:
#   trending: true
---
<script type="text/javascript" async src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/3.2.2/es5/tex-mml-chtml.min.js">
</script>
<script type="text/x-mathjax-config">
 MathJax.Hub.Config({
 tex2jax: {
 inlineMath = [['\(', '\)'], ['$', '$']]
 displayMath: [ ['$$','$$'], ["\\[","\\]"] ]
 }
 });
</script>

<!--
Figure:
\tau(x, t) = \tau_0 - \frac{\mu}{2 \pi} \int_{\Sigma} \frac{\partial \delta(\xi) / \partial \xi}{x - \xi} d\xi - \frac{\mu}{2 c} V + g(x, t) -->

2次元均質弾性体内に埋め込まれたantiplane断層における応力を解きます。ゴールは、断層面上の応力をすべり・すべり速度の関数として表し、静的応力変化 (static stress drop) / すべり速度による即時応力変化 (radiation damping) / すべり履歴に依存する動的な応力変化の項に分離することです。主にPerrin et al. (1995), およびGeubelle and Rice (1995)の議論に基づいています。

### 問題設定
2次元均質弾性体で、紙面垂直方向(z軸)方向のみに変位が存在するantiplane問題を考えます。変位の非ゼロ成分 \( u_z = u(x,y,t) \) の支配方程式は以下で表されます。

$$ \rho \frac{\partial^2 u}{\partial t^2} - \mu (\frac{\partial^2 u}{\partial x^2} + \frac{\partial^2 u}{\partial y^2}) = 0 \hspace{5mm} \text{on} \hspace{2mm} \Omega $$

*  \( \rho \): 密度,  \( \mu \): shear modulus, \( \Omega \): 空間領域
<!-- \( \Omega = \{(x,y) | [-\infty, \infty] \times [-\infty, \infty]\}\) -->

ここで、\( y = 0\) 平面上に位置する断層でのすべり時間発展 \( \delta(x,t)\) を境界条件として課します。断層面での変位不連続は境界条件
$$ u|_{y = +0} - u|_{y = -0} = \delta(x, t) $$
<!-- $$ \dot{u}|_{y = +0} - \dot{u}|_{y = -0} = V(x, t) $$ -->
として表現されます。また断層にかかるトラクションの釣り合い条件により、断層面上の接線応力 \( \tau = \sigma_{yz} = \tau^0 + \mu \; \partial u_z / \partial y\)
の連続性が境界条件として課されます:
$$ \tau(y = +0) = \tau(y = -0) $$


### スペクトル法による解法
偏微分方程式を解くため、断層にそった空間方向(x軸)に対しフーリエ変換・時間方向に対してラプラス変換を導入します：
$$ \hat{U}(k, y, s) = \int_{-\infty}^\infty \int_0^\infty u(x, y, t) e^{-ikx-st} ds dk  $$
<!-- $$ u(x, y, t) = \int_{-\infty}^\infty \int_{-\infty}^\infty \hat{u}(\omega, y, k) e^{i(kx-\omega t)} d \omega dk  $$ -->
このとき支配方程式は、S波速度 \( c = \sqrt{\mu / \rho} \) として
$$ \frac{\partial^2 \hat{U}}{\partial y^2} = (k^2 + \frac{s^2}{c^2})\hat{U} $$
となります。これは\( y \)についての2階微分方程式であり、\( y \rightarrow \pm \infty \)で解が発散しないことに留意すると、一般解は
$$ 
\hat{U}(k, y, s) =  \left \{
\begin{aligned}
& U^+(k, s) e^{- |k| \alpha y} \hspace{3mm} (y > 0)\\
& U^-(k, s) e^{|k| \alpha y} \hspace{6mm} (y < 0)
\end{aligned}
\right.
$$

$$  \alpha = \sqrt{1 + s^2 / (k^2 c^2)} $$

となり、境界条件を満たすように\(U^+, U^-\)を選べば欲しい解が得られます。

応力連続の境界条件は
$$ 
\begin{aligned}
\frac{\partial \hat{u}}{\partial y}|_{y=+0} &= \frac{\partial \hat{u}}{\partial y}|_{y=-0} \\
\Rightarrow U^+(k, s) &= - U^-(k, s) 
\end{aligned}
$$
変位不連続の境界条件は、\(\delta (x,t)\) をラプラス・フーリエ変換した
$$ \hat{D}(k, s) = \int_{-\infty}^\infty \int_0^\infty \delta(x, t) e^{-ikx-st} ds dk  $$
を用いて
$$
\begin{aligned} 
\hat{D}(k, s) &= \hat{u}|_{y = +0} - \hat{u}|_{y = -0} = U^+ - U^- = 2U^+
\end{aligned}
$$

と表されるため、最終的に周波数空間での波動分方程式の解
$$ 
\hat{U}(k, y, s) =  \left \{
\begin{aligned}
& + \frac{\hat{D}}{2} e^{- |k| \alpha y} \hspace{3mm} (y > 0)\\
& - \frac{\hat{D}}{2} e^{|k| \alpha y} \hspace{6mm} (y < 0)
\end{aligned}
\right.
$$
を得ます。

### 応力と極限
上記の解を用いると、周波数領域で応力は以下のように表されます:
$$ 　\hat{T}(k,s) - \hat{T}^0(k,s) = \mu \frac{\partial \hat{u}}{\partial y}|_{y=0} = - \frac{\mu|k|}{2} \alpha(k, s) \hat{D}(k, s)　$$  ここで\(\hat{T}, \hat{T}^0\)は応力: \(\tau\)と初期応力: \(\tau^0\)を周波数領域に変換したものです。

#### 高周波数極限: Radiation damping
波動伝播にかかる時間に比べて十分短い時間スケールでのすべりに対する応力応答を考えます。上の標識で\( s / (|k| c) \rightarrow \infty \)の極限を考えると \( \alpha(k,s) \approx  s / (|k| c) \)となり、
$$ \hat{T} - \hat{T}^0 \approx  - \frac{\mu}{2c} (s  \hat{D}) $$ 　時間・空間領域に変換すると、
$$ \tau(x,t) = \tau^0(x) - \frac{\mu}{2c} \dot{\delta}(x,t)$$
これは、断層がすべっている際、応力化がすべり速度に比例して即時的に変化することを示しています。この十分短いスケールでの応力変化はRadiation dampingと呼ばれます (Rice, 1993)。

#### 低周波数極限: 静的解
もう一方の極限として、\( s / (|k| c) \rightarrow 0 \)の極限をとると、
\( \alpha(k,s) \approx 1\)となり、応力は、
$$ \hat{T}(k,s) - \hat{T}^0(k,s)  = - \frac{\mu|k|}{2} \hat{D}(k,s) $$  もしくは時間領域に逆ラプラス変換して
$$ \hat{\tau}(k,t) - \hat{\tau}^0 (k,t) = - \frac{\mu|k|}{2} \hat{\delta}(k,t) $$
となります。
この極限では波動伝播にかかる時間に比べて十分長い時間スケールに着目しており、上式は弾性波が伝わり切った後の地中の応力状態を示しています。つまり、この解は波動方程式において慣性項を無視した静的な弾性体の釣り合いの式
$$ \mu (\frac{\partial^2 u}{\partial x^2} + \frac{\partial^2 u}{\partial y^2}) = 0 \hspace{5mm} \text{on} \hspace{2mm} \Omega $$
を支配方程式とした際の解であり、静的解 (Static solution)と呼ばれます。

この逆フーリエ変換は、
$$ \frac{\mu |k|}{2} \hat{\delta(k)} = \frac{\mu}{2 \pi}(- i \pi \text{sgn}(k)) \times (i k \hat{\delta}) $$
と分解できること、および\( 1 / x \)のフーリエ変換が\(- i \pi \text{sgn}(k)\)であることを用いると計算でき、最終的に静的応力降下は
$$ \tau(x,t) = \tau^0(x) - \frac{\mu}{2 \pi} \int_{\Sigma} \frac{\partial \delta(\xi) / \partial \xi}{x - \xi} d\xi $$  
と表されます (参照: Segall 2010, p111-113)。

### 境界積分法による数値計算
断層におけるすべり発展を数値的に計算する際には、時刻tにおける応力をその前のすべり履歴から計算します。上記の表式では周波数領域 \(s\)における解を求めましたが、数値的に時間発展を計算するには時間領域に逆ラプラス変換を行う必要性があります。

スタート地点として、radiation damping (即時効果)を陽的に分離した表現:
$$ \tau(x,t) = \tau^0 - \frac{\mu}{2c} \dot{\delta}(x,t) + f(x,t) $$
を考えます。周波数領域での解を用いると、
$$ 　\hat{T}(k,s) = \hat{T}^0 - \frac{\mu}{2c} (s  \hat{D}) - \frac{\mu|k|}{2} (\alpha - \frac{s}{|k|c}) \hat{D}　$$ 
となり、\(f(x,t)\)の周波数領域での表現
$$ \hat{F}(k,s) = - \frac{\mu|k|}{2} \{\sqrt{1 + s^2/(k^2c^2)} - \frac{s}{|k|c}\} \hat{D}(k,s) $$
を得ます。
<!-- ここでの目的はこの\(\hat{F}\)をラプラス逆変換することにより、時間領域での表現\(\hat{f}(k,t)\) or \(f(x,t)\)を得ることです。 -->

#### スペクトル境界積分法
スペクトル境界積分要素法　(Spectral Boundary Integral Element Method: SBIEM)では、有限個の離散波長に対し\(\hat{f}(k,t)\)を評価し、数値的に空間方向の逆フーリエ変換を行うことにより断層の応力を評価します。この手法は断層の摩擦則と組み合わせることにより、地震サイクルのシミュレーションなどに用いられています (e.g., Lapusta et al., 2000)。ここでは\(\hat{F}\)をラプラス逆変換することにより、時間領域での表現\(\hat{f}(k,t)\)を導出します

$$ M(s) = \sqrt{1 + s^2/(k^2c^2)} - \frac{s}{|k|c} $$
とした際、このラプラス逆変換\(m(t)\)が見つかれば、
$$ \hat{f}(k,t) = - \frac{\mu |k|}{2} \int_0^t m(t') \hat{\delta}(k,t-t') dt' $$
と時間畳み込みによる表現を得ます。\( b = |k|c \) とし、
$$ 
\begin{align}
M(s) &= \sqrt{1 + s^2/b^2} - \frac{s}{b}  \\
&= \frac{1 + s^2/ b^2 - (s/b)\sqrt{1 + s^2/b^2}}{\sqrt{1 + s^2/b^2}} \\
&= \frac{1}{2} [\frac{(\sqrt{1 + s^2/b^2} - s/b)^2}{\sqrt{1 + s^2/b^2}} + \frac{1}{\sqrt{1 + s^2/b^2}}]
\end{align}
$$
と変形しておくと、n次の第一種ベッセル関数\( J_n(t)\)のラプラス変換
$$ \mathcal{L}[J_n(t)] = \frac{(\sqrt{1 + s^2} - s)^n}{\sqrt{1 + s^2}}$$
が適用できます。\( \mathcal{L}^{-1} [F(s)] = f(t)\) の時\( \mathcal{L}^{-1} [F(s/b)] = b f(bt)\)より、
$$  \mathcal{L}^{-1}[M(s)] = \frac{b}{2} [J_0(bt) + J_2(bt)]$$
さらにベッセル関数の漸化式 $$ J_{n-1}(t) + J_{n+1}(t) = 2 \frac{J_n(t)}{t} $$
を用いて、\( \mathcal{L}^{-1} [F(s)] = \frac{J_1(|k|ct)}{t} \)となり、
$$ \hat{f}(k, t) = - \frac{\mu |k|}{2} \int_0^t \frac{J_1(|k|ct')}{t'} \hat{\delta}(k,t-t') dt'$$
を得ます。(diplacement representation)

また、
$$ W(p) = \int_p^\infty [J_1(\xi) / \xi] d\xi, W(0) = 1 $$
を定義すると、\(- dW / dp = J_1(p) / p\) より、
$$ \begin{align}
\hat{f}(k, t) =& - \frac{\mu |k|}{2} \int_0^t - \frac{dW(|k|ct')}{dt'} \hat{\delta}(k,t-t') d t' \\
=& - \frac{\mu |k|}{2} [- W(|k|ct') \hat{\delta}(t-t')]_0^t \\
& - \frac{\mu |k|}{2} \int_0^t W(k|c|t') \frac{d}{dt'} \hat{\delta}(k,t-t') dt' \\
\end{align}
$$
と部分積分でき、最終的に静的応力変化を分離した
$$ \hat{f}(k,t) = - \frac{\mu |k|}{2} \hat{\delta}(k, t) + \frac{\mu |k|}{2} \int_0^t W(k|c|t') \hat{\dot{\delta}}(k,t-t') dt' $$
を得られます (velocity representation)。


#### 準動的近似
Velocity representationを用いた際、右辺の時間畳み込み項が計算のボトルネックとなります。主に地震サイクルの計算で、計算量削減のために、この畳み込み項を無視した
$$ \tau(x,t) = \tau_0 - \frac{\mu}{2c} V -\frac{\mu}{2 \pi} \int_{\Sigma} \frac{\partial \delta(\xi) / \partial \xi}{x - \xi} d\xi $$ 
という近似がしばしば用いられます。これを準動的近似 (Quasi-dynamic approximation)と呼びます。

#### 境界積分法
\( \hat{F}(k,s) \)を時空間両方で逆変換した形はCochard and Madariaga (1994)で導出されており、
$$ 
\begin{aligned}
\tau(x,t) = & \tau_0 - \frac{\mu}{2c} \dot{\delta}(x,t) \\
& - \frac{\mu}{2 \pi} \int_{\Sigma} \int_0^{t - \frac{|x-\xi|}{c}} \frac{\sqrt{(t-t')^2-(x-\xi)^2 / c^2}}{(t-t')(x - \xi)} \frac{\partial \dot{\delta}(\xi, t')}{\partial \xi} dt' d\xi 
\end{aligned}
$$ 
と表記される。右辺の積分は、causality coneと呼ばれる情報が弾性波に伝播可能な時空間領域 ((x,t)を頂点とする傾きcの三角形)で行われる。


### 参考文献

1. Perrin, Gilles, James R. Rice, and Gutuan Zheng. 1995. “Self-Healing Slip Pulse on a Frictional Surface.” Journal of the Mechanics and Physics of Solids 43 (9): 1461–95.
2. Geubelle, Philippe H., and James R. Rice. 1995. “A Spectral Method for Three-Dimensional Elastodynamic Fracture Problems.” Journal of the Mechanics and Physics of Solids 43 (11): 1791–1824.
3. Segall, Paul. 2010. Earthquake and Volcano Deformation. Princeton University Press.
4. Lapusta, Nadia, James R. Rice, Yehuda Ben-Zion, and Gutuan Zheng. 2000. “Elastodynamic Analysis for Slow Tectonic Loading with Spontaneous Rupture Episodes on Faults with Rate- and State-Dependent Friction.” Journal of Geophysical Research: Solid Earth, October. https://doi.org/10.1029/2000JB900250.
5. Cochard, Alain, and Raúl Madariaga. 1994. “Dynamic Faulting under Rate-Dependent Friction.” Pure and Applied Geophysics 142 (3): 419–45.

