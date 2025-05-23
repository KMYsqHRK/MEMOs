# 薄膜の圧力計算理論

## 1. 薄膜流れの基礎概念

薄膜流れは流体力学の重要な領域で、二つの表面の間に挟まれた非常に薄い流体層の挙動を扱います。この理論は「潤滑理論」(Lubrication Theory)とも呼ばれ、次のような特徴を持ちます：

- 流体層の厚さは他の二次元（長さと幅）に比べて非常に小さい
- 粘性力が支配的である
- 慣性力は通常無視できる
- 圧力は膜厚方向にほぼ一定

## 2. レイノルズ方程式

薄膜内の圧力分布を支配する方程式はレイノルズ方程式と呼ばれます。これはナビエ・ストークス方程式を薄膜の条件下で簡略化したものです。

### 2.1 一般形式

二次元の場合、レイノルズ方程式は以下のように表されます：

$$\frac{\partial}{\partial x}\left(\frac{h^3}{\mu}\frac{\partial p}{\partial x}\right) + \frac{\partial}{\partial y}\left(\frac{h^3}{\mu}\frac{\partial p}{\partial y}\right) = 6U\frac{\partial h}{\partial x} + 12\frac{\partial h}{\partial t}$$

ここで：
- $p$ は圧力
- $h$ は膜厚
- $\mu$ は流体の粘度
- $U$ は表面のすべり速度
- $t$ は時間

### 2.2 定常状態の場合

定常状態（時間変化なし）では、式は次のように簡略化されます：

$$\frac{\partial}{\partial x}\left(\frac{h^3}{\mu}\frac{\partial p}{\partial x}\right) + \frac{\partial}{\partial y}\left(\frac{h^3}{\mu}\frac{\partial p}{\partial y}\right) = 6U\frac{\partial h}{\partial x}$$

### 2.3 等粘度・等膜厚の場合

膜厚が一定で粘度も一定の場合、さらに簡略化され：

$$\frac{h^3}{12\mu}\left(\frac{\partial^2 p}{\partial x^2} + \frac{\partial^2 p}{\partial y^2}\right) = 0$$

これはラプラス方程式の形となります：

$$\nabla^2 p = 0$$

## 3. 境界条件

レイノルズ方程式を解くには適切な境界条件が必要です：

### 3.1 ディリクレ境界条件
領域の境界上で圧力が既知：
$$p = p_0 \quad \text{on} \quad \Gamma_D$$

### 3.2 ノイマン境界条件
圧力勾配が既知：
$$\frac{\partial p}{\partial n} = q_0 \quad \text{on} \quad \Gamma_N$$

### 3.3 キャビテーション条件
流体が気化する臨界圧力以下にならないという条件：
$$p \geq p_{cav}$$

## 4. 数値解法

実際の問題ではレイノルズ方程式の解析解を得ることは難しく、数値解法が用いられます：

### 4.1 有限差分法
最も単純な方法で、領域を格子状に分割し、微分を差分近似で置き換えます。

### 4.2 有限要素法
複雑な形状に適応でき、変分原理に基づいて解を求めます。

### 4.3 境界要素法
境界上の積分方程式に基づく手法で、境界のみを離散化するため、計算効率が良い場合があります。グリーン関数（影響関数）を利用し：

$$p(x,y) = \int_{\Gamma} G(x,y;x',y') q(x',y') d\Gamma - \int_{\Gamma} \frac{\partial G}{\partial n}(x,y;x',y') p(x',y') d\Gamma$$

ここで $G$ はグリーン関数で、2次元の場合：

$$G(x,y;x',y') = -\frac{1}{2\pi}\ln(r)$$

ただし $r = \sqrt{(x-x')^2 + (y-y')^2}$ です。

## 5. 実際の応用

薄膜圧力の計算は以下のような分野で重要です：

- 流体軸受の設計と最適化
- 硬質ディスクドライブのヘッド浮上解析
- マイクロ流体デバイス
- 生体内関節の潤滑解析

## 6. 計算例と解の特徴

典型的な解の特徴として：

- 収束部での圧力上昇
- 拡大部での圧力低下（キャビテーションのリスク）
- 速度の増加による圧力上昇
- 膜厚減少による圧力上昇（ただし極端に薄くなると境界層効果が現れる）

これらの特性を理解することで、流体膜の動的挙動や負荷支持能力を予測し、様々なシステムの設計に活用できます。