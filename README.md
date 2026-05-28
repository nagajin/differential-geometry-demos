# 微分幾何 教材デモ集 / Differential Geometry Demos

曲面の幾何をブラウザ上でインタラクティブに観察するための教材デモ集です。外部ライブラリ・ビルド・サーバを一切必要とせず、各デモは単一の HTML ファイルだけで動作します。

> Interactive, dependency-free web demos for differential geometry — each one a single self-contained HTML file.

## ▶ ライブデモ

- **デモ一覧**: https://nagajin.github.io/differential-geometry-demos/
- **測地線と Gauss–Bonnet の定理**: https://nagajin.github.io/differential-geometry-demos/gauss-bonnet.html

## 収録デモ

### 測地線と Gauss–Bonnet の定理 (`gauss-bonnet.html`)

パラメトリック曲面 $X(u,v)$ の上に測地線三角形を描き、局所 Gauss–Bonnet の定理

$$\iint_T K\, dA = \Big(\theta_A+\theta_B+\theta_C\Big) - \pi$$

が成り立つことを数値的に検証します（辺が測地線なので測地的曲率の寄与は 0）。

- **収録曲面**: 球面 ($K>0$)・トーラス ($K$ 混在)・鞍面 ($K<0$)・擬球面 ($K=-1$)・円柱 ($K=0$)
- **2 モード**: 測地線三角形 / 測地線シュート（曲面上の「まっすぐな線」を観察）
- 頂点 A·B·C はドラッグで移動、ガウス曲率 $K$ を色表示、測地線は前面=実線・背面=破線
- 内角の和と曲率積分を同時に表示し、一致を確認できます

#### 数値解法
- 第一・第二基本形式 $E,F,G,\ L,M,N$ と Christoffel 記号、ガウス曲率 $K=(LN-M^2)/(EG-F^2)$ をすべて差分で算出
- 測地線方程式 $\ddot u^k + \Gamma^k_{ij}\,\dot u^i \dot u^j = 0$ を 4 次 Runge–Kutta 法で積分
- 2 点を結ぶ測地線は最接近シューティング法（粗いスキャン → 黄金分割探索）で求解
- 内角は計量内積で測定、$\iint_T K\,dA$ は $(u,v)$ 領域のグリッド数値積分

各曲面で角度超過 $\Sigma\theta-\pi$ と曲率積分 $\iint K\,dA$ が数値誤差の範囲で一致します（球面で過剰、鞍面で不足、円柱でちょうど $\pi$）。

## 関連

平均曲率流シミュレータ: https://github.com/nagajin/mean-curvature-flow

## ライセンス

MIT License
