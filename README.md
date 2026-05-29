# 微分幾何 教材デモ集 / Differential Geometry Demos

曲面の幾何とベクトル解析を、ブラウザ上でインタラクティブに観察するための教材デモ集です。外部ライブラリ・ビルド・サーバを一切必要とせず、各デモは**単一の HTML ファイル**だけで動作します（描画は HTML Canvas 2D API）。

> Interactive, dependency-free web demos for differential geometry and vector calculus — each one a single self-contained HTML file.

## ▶ ライブデモ

**デモ一覧:** https://nagajin.github.io/differential-geometry-demos/

| デモ | 内容 | リンク |
|---|---|---|
| 曲面の曲率ビジュアライザ | ガウス曲率・平均曲率・主曲率と主方向 | [curvature-visualizer.html](https://nagajin.github.io/differential-geometry-demos/curvature-visualizer.html) |
| 測地線と Gauss–Bonnet の定理 | 測地線三角形と $\iint K\,dA=\Sigma\theta-\pi$ | [gauss-bonnet.html](https://nagajin.github.io/differential-geometry-demos/gauss-bonnet.html) |
| Theorema Egregium（驚異の定理） | カテノイド↔ヘリコイドの等長変形 | [theorema-egregium.html](https://nagajin.github.io/differential-geometry-demos/theorema-egregium.html) |
| 3大積分定理ビジュアライザ | グリーン・ストークス・ガウス発散 | [integral-theorems.html](https://nagajin.github.io/differential-geometry-demos/integral-theorems.html) |

## 収録デモ

### 1. 曲面の曲率ビジュアライザ (`curvature-visualizer.html`)

パラメトリック曲面 $X(u,v)$ のガウス曲率 $K$・平均曲率 $H$・主曲率 $k_1,k_2$ を色で表示し、主曲率方向（曲率線）の場を重ね描きします。

- **収録曲面**: 球面・楕円体・トーラス・鞍面・猿の鞍・カテノイド ($H=0$)
- 表示する量を $K$ / $H$ / $k_1$ / $k_2$ で切替、曲面をクリックすると点の曲率と種類（楕円点／双曲点／放物点／臍点）を表示
- 形状作用素 $S=\mathrm{I}^{-1}\mathrm{I\!I}$ の固有値が主曲率、固有ベクトルが主方向。符号は「凸＝正」（球面で $H>0$）に統一

### 2. 測地線と Gauss–Bonnet の定理 (`gauss-bonnet.html`)

パラメトリック曲面の上に測地線三角形を描き、局所 Gauss–Bonnet の定理

$$\iint_T K\, dA = \big(\theta_A+\theta_B+\theta_C\big) - \pi$$

が成り立つことを数値的に検証します（辺が測地線なので測地的曲率の寄与は 0）。

- **収録曲面**: 球面 ($K>0$)・トーラス ($K$ 混在)・鞍面 ($K<0$)・擬球面 ($K=-1$)・円柱 ($K=0$)
- **2 モード**: 測地線三角形 / 測地線シュート（曲面上の「まっすぐな線」を観察）
- 頂点 A·B·C はドラッグで移動。内角の和（角度超過）と曲率積分を同時に表示し一致を確認
- 測地線は測地線方程式を 4 次 Runge–Kutta で積分、2 点連結は最接近シューティング法

### 3. Theorema Egregium（驚異の定理） (`theorema-egregium.html`)

カテノイドとヘリコイドの**局所等長変形**（associated family）をアニメーションし、ガウスの驚異の定理を可視化します。

- 変形中、ガウス曲率 $K$ と第一基本形式 $\mathrm{I}=(E,F,G)$ は**不変**（内在量）、第二基本形式 $\mathrm{I\!I}=(L,M,N)$ と曲面の形は**変化**（外在量）
- 組合せ $LN-M^2$ が不変なので $K=(LN-M^2)/(EG-F^2)$ も不変。追跡点でこれらを実時間計測
- 途中もすべて極小曲面 ($H=0$)

### 4. 3大積分定理ビジュアライザ (`integral-theorems.html`)

グリーン・ストークス・ガウスの発散定理を、**左辺（境界での積分）と右辺（rot / div の内部積分）を数値計算して一致**させて確かめます。

- **グリーン** (2D): $\oint_{\partial D}(P\,dx+Q\,dy)=\iint_D(\partial_x Q-\partial_y P)\,dA$
- **ストークス** (3D): $\oint_{\partial S}\mathbf{F}\cdot d\mathbf{r}=\iint_S(\operatorname{rot}\mathbf{F})\cdot\mathbf{n}\,dA$（半球↔平面円板で**曲面に依らない**ことを確認）
- **ガウス発散** (3D): $\oiint_{\partial V}\mathbf{F}\cdot\mathbf{n}\,dA=\iiint_V(\operatorname{div}\mathbf{F})\,dV$
- 場（回転場／動径場／混合場／変化場）・領域・サイズを切替、場の矢印と被積分量を可視化
- いずれも一般化ストークスの定理 $\int_{\partial\Omega}\omega=\int_\Omega d\omega$ の特別な場合として提示

## 数値解法（共通方針）

- 第一・第二基本形式、Christoffel 記号、$K$・$H$・$\operatorname{rot}$・$\operatorname{div}$ などの微分量はすべて**有限差分**で算出
- 常微分方程式（測地線など）は **4 次 Runge–Kutta 法**で積分
- 各定理は**左辺と右辺を独立に数値計算**し、数値誤差の範囲で一致することを表示

数学的背景は東京理科大学 小池直之先生の講義・研究にもとづいています。

## 関連

平均曲率流シミュレータ（曲線短縮流・曲面の平均曲率流）: https://github.com/nagajin/mean-curvature-flow

## ライセンス

MIT License
