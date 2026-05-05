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
2次元均質弾性体で、紙面垂直方向(z軸)方向のみに変位が存在するantiplane問題を考える。変位の非ゼロ成分 \( u_z = u(x,y,t) \) の支配方程式は

$$ \rho \frac{\partial^2 u}{\partial t^2} - \mu (\frac{\partial^2 u}{\partial x^2} + \frac{\partial^2 u}{\partial y^2}) = 0 \hspace{5mm} \text{on} \hspace{2mm} \Omega $$

*  \( \rho \): 密度,  \( \mu \): shear modulus, \( \Omega \): 空間領域
<!-- \( \Omega = \{(x,y) | [-\infty, \infty] \times [-\infty, \infty]\}\) -->

\( y = 0\) 平面上に位置する断層でのすべり \( \delta(x,t)\) / すべり速度 \(V(x,t)\)を既知とすると、断層面での変位不連続は境界条件
$$ u|_{y = +0} - u|_{y = -0} = \delta(x, t) $$
$$ \dot{u}|_{y = +0} - \dot{u}|_{y = -0} = V(x, t) $$
として表現される。また断層にかかるトラクションの釣り合い条件により、断層面上の接線応力 \( \tau = \sigma_{yz} = \tau^0 + \mu \; \partial u_z / \partial y\)
の連続性が境界条件として課される:
$$ \tau(y = +0) = \tau(y = -0) $$


### スペクトル法による解法
断層座標(x軸)・および時間方向に対してフーリエ変換を導入する:
$$ u(x, y, t) = \int_{-\infty}^\infty \int_{-\infty}^\infty \hat{u}(\omega, y, k) e^{i(kx-\omega t)} d \omega dk  $$
支配方程式は、S波速度 \( c = \sqrt{\mu / \rho} \) を用いて
$$ \frac{\partial^2 \hat{u}}{\partial y^2} = (k^2 - \frac{\omega^2}{c^2})\hat{u} $$
もしくは \( \alpha = \sqrt{1 - \omega^2 / (k^2 c^2)}\)を用いて
$$ \frac{\partial^2 \hat{u}}{\partial y^2} = k^2 \alpha^2 \hat{u} $$
となり、その解は、\( y \rightarrow \pm \infty \)で解が発散しないことに留意して、
$$ 
\hat{u}(k, y, \omega) =  \left \{
\begin{aligned}
& U^+(k, \omega) e^{- |k| \alpha y} \hspace{3mm} (y > 0)\\
& U^-(k, \omega) e^{|k| \alpha y} \hspace{6mm} (y < 0)
\end{aligned}
\right.
$$
応力連続の境界条件 
$$ \frac{\partial \hat{u}}{\partial y}|_{y=+0} = \frac{\partial \hat{u}}{\partial y}|_{y=-0} $$
より
$$ U^+(k, \omega) = - U^-(k, \omega) $$
であり、変位不連続の境界条件より
$$
\begin{aligned} 
\hat{\delta}(k, \omega) &= \hat{u}|_{y = +0} - \hat{u}|_{y = -0} = U^+ - U^- = 2U^+
\end{aligned}
$$
のため、偏微分方程式の解は周波数空間で
$$ 
\hat{u}(k, y, \omega) =  \left \{
\begin{aligned}
& + \frac{\hat{\delta}}{2} e^{- |k| \alpha y} \hspace{3mm} (y > 0)\\
& - \frac{\hat{\delta}}{2} e^{|k| \alpha y} \hspace{6mm} (y < 0)
\end{aligned}
\right.
$$
と表される。

### 応力と極限
上記の解を用いると、周波数空間での応力の表記を得る:
$$ 
\hat{\tau} - \hat{\tau}^0 = \mu \frac{\partial \hat{u}}{\partial y}|_{y=0} = - \frac{\mu|k|}{2} \alpha(k, \omega) \hat{\delta}(k, \omega)
$$  

#### 高周波数極限: Radiation damping
波動伝播にかかる時間に比べて十分短い時間スケールでの応力変化を考える。これは \( \omega / (k c) \rightarrow \infty \)の極限を考えればよく、この極限で
\( \alpha(k, \omega) \approx - i \omega / (|k| c) \)となるためその応力変化は、
$$ \hat{\tau} - \hat{\tau}^0 \approx  - \frac{\mu}{2c} (- i\omega  \hat{\delta}) = - \frac{\mu}{2c} \hat{V}$$
この十分短いスケールで即時的に起きる応力変化はRadiation dampingと呼ばれる (Rice, 1993)。

#### 低周波数極限: 静的解
波動伝播にかかる時間に比べて十分長い時間スケールでの応力変化を考える。これは \( \omega / (k c) \rightarrow 0 \)の極限を考えればよく、
\( \alpha(k, \omega) \approx 1\)を用いると応力変化は、
$$ \hat{\tau} - \hat{\tau}^0  = - \frac{\mu|k|}{2} \hat{\delta} $$  
これは波動方程式の代わりに、慣性項を無視した静的な弾性体の釣り合いの式
$$ \mu (\frac{\partial^2 u}{\partial x^2} + \frac{\partial^2 u}{\partial y^2}) = 0 \hspace{5mm} \text{on} \hspace{2mm} \Omega $$
を支配方程式とした際の解と一致し、静的解 (Static solution)と呼ばれる。
$$ \frac{\mu |k|}{2} \hat{\delta} = \frac{\mu}{2 \pi}(- i \pi \text{sgn}(k)) \times (i k \hat{\delta}) $$
であり、\( 1 / x \)のフーリエ変換が\(- i \pi \text{sgn}(k)\)であることを用いると、静的応力効果は実空間で
$$ \tau(x,t) = \tau^0(x) - \frac{\mu}{2 \pi} \int_{\Sigma} \frac{\partial \delta(\xi) / \partial \xi}{x - \xi} d\xi $$  
と表される (参照: Segall 2010, p111-113)。

### 境界積分法による数値計算
断層におけるすべり発展を数値的に計算する際には、時刻tにおける応力をその前のすべり履歴から計算する必要がある。上記の表式では時間周波数領域における解を求めたが、数値計算に利用するためには実時間領域に変換する必要がある。
周波数空間における動的な応力効果は、radiation damping (即時効果)を陽的に分離して、
$$ \hat{\tau} = \hat{\tau}^0 - \frac{\mu}{2c} \hat{V} + \hat{f} $$
とかける。ここで
$$ \hat{f} = - \frac{\mu|k|}{2} \{\alpha + \frac{i\omega}{c}\} \hat{\delta} $$

#### スペクトル境界積分法
この項を実時間方向に逆変換した式はPerrin et al. (1995)で導出されており、1次の第1種ベッセル関数\( J_1(x)\)を用いて
$$ f(k, t) = - \frac{\mu |k|}{2} \int_0^t \frac{J_1(|k|ct')}{t'} \delta(k,t-t') dt'$$
と表される (displacement representation)。
この表式に部分積分を行うことにより、静的応力変化を分離したvelocity representation
$$ f(k, t) = - \frac{\mu |k|}{2} \delta(k, t) + \int_0^t W(|k|ct') V(k,t-t') dt'$$
を得る。ただし \( W(p) = \int_p^\infty [J_1(\xi) / \xi] d\xi, W(0) = 1 \) 
この表式を用いた断層計算はスペクトル境界積分要素法　(Spectral Boundary Integral Element Method: SBIEM)と呼ばれ、地震サイクルのモデリングなどに用いられている(e.g., Lapusta et al., 2000)。

#### 準動的近似
Velocity representationを用いた際、右辺の時間畳み込み項が計算のボトルネックとなるが、この項を無視し静的変化とradiation dampingのみを考慮した
$$ \tau(x,t) = \tau_0 - \frac{\mu}{2c} V -\frac{\mu}{2 \pi} \int_{\Sigma} \frac{\partial \delta(\xi) / \partial \xi}{x - \xi} d\xi $$ 
という近似がしばしば用いられる。これを準動的近似 (Quasi-dynamic approximation)と呼ぶ。

#### 境界積分法
\( \hat{f} \)を時空間両方で逆変換した形はCochard and Madariaga (1994)で導出されており、
$$ 
\begin{aligned}
\tau(x,t) = & \tau_0 - \frac{\mu}{2c} V(x,t) \\
& - \frac{\mu}{2 \pi} \int_{\Sigma} \int_0^{t - \frac{|x-\xi|}{c}} \frac{\sqrt{(t-t')^2-(x-\xi)^2 / c^2}}{(t-t')(x - \xi)} \frac{\partial V(\xi, t')}{\partial \xi} dt' d\xi 
\end{aligned}
$$ 
と表記される。右辺の積分は、causality coneと呼ばれる情報が弾性波に伝播可能な時空間領域 ((x,t)を頂点とする傾きcの三角形)で行われる。


### 参考文献

1. Perrin, Gilles, James R. Rice, and Gutuan Zheng. 1995. “Self-Healing Slip Pulse on a Frictional Surface.” Journal of the Mechanics and Physics of Solids 43 (9): 1461–95.
2. Geubelle, Philippe H., and James R. Rice. 1995. “A Spectral Method for Three-Dimensional Elastodynamic Fracture Problems.” Journal of the Mechanics and Physics of Solids 43 (11): 1791–1824.
3. Segall, Paul. 2010. Earthquake and Volcano Deformation. Princeton University Press.
4. Cochard, Alain, and Raúl Madariaga. 1994. “Dynamic Faulting under Rate-Dependent Friction.” Pure and Applied Geophysics 142 (3): 419–45.
5. Lapusta, Nadia, James R. Rice, Yehuda Ben-Zion, and Gutuan Zheng. 2000. “Elastodynamic Analysis for Slow Tectonic Loading with Spontaneous Rupture Episodes on Faults with Rate- and State-Dependent Friction.” Journal of Geophysical Research: Solid Earth, October. https://doi.org/10.1029/2000JB900250.


