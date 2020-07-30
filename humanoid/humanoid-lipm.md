###### tags: `humanoid` `robotics` 
# 線形倒立振子

## 倒立振子モデル

地面に自由関節で固定された長さ$l$の棒に質点(重さ:$m$)倒立振子を考える(簡単のため同一平面上を動く時を考える). 振子の傾きを$\theta$として，倒立振子の運動方程式は，

$$
(m l^2)\ddot{\theta} = mg \sin\theta \ l
$$

$0 \simeq \theta$のとき$\sin\theta \simeq \theta$となり，

$$
\ddot{\theta} = \omega^2 \theta \quad  \omega := \sqrt{\frac{g}{l}}\tag{1}
$$


質点の水平方向の位置を$x$として，$x = l \sin\theta \simeq l\theta$ なので(1)式より

$$
\ddot{x} = \omega^2 x \tag{2}
$$
と質点の水平運動を表す微分方程式が与えられる.(2)式の解は$x(0)=x_0$，$\dot{x}(0)=\dot{x}_0$として

$$ 
x(t) = \frac{1}{2}(x_0 + \frac{\dot{x}_0}{\omega}) e^{\omega t} + \frac{1}{2}(x_0 - \frac{\dot{x}_0}{\omega}) e^{-\omega t} \\
 = x_0 {\rm cosh}(\omega t) + \frac{\dot{x}_0}{\omega} {\rm sinh}(\omega t)
$$

状態変数$X = [x \ \dot{x}]^T$として状態方程式は

$$
\dot{X} =
\left[
    \begin{array}{cc}
    \dot{x} \\
    \ddot{x} \\
    \end{array}
\right] =
\left[
    \begin{array}{cc}
    0 & 1 \\
    \omega^2 & 0 \\
    \end{array}
\right]
\left[
    \begin{array}{cc}
    x \\
    \dot{x} \\
    \end{array}
\right] =
AX \tag{3}
$$

## モデルの解析

状態遷移行列$A$の固有値，固有ベクトルを求めシステムの性質を調べる

$$
det(\lambda E - A ) = 0 \\
\left|
    \begin{array}{cc}
    \lambda & -1 \\
    -\omega^2 & \lambda \\
    \end{array}
\right|
= \lambda^2 - \omega^2 = (\lambda - \omega) (\lambda + \omega) = 0 \\
\lambda = \omega, -\omega
$$

固有値は$\lambda = \omega, -\omega$で固有ベクトルは

$\lambda = -\omega < 0$ のとき（安定モード）
$$a_1 = [1, -\omega]^T$$

$\lambda = \omega > 0$ のとき（不安定モード）
$$a_2 = [1, \omega]^T$$

行列$A$の固有値分解は

$$
A = T \Lambda T^{-1}
= \frac{1}{2}
\left[
    \begin{array}{cc}
    1 & 1 \\
    -\omega & \omega \\
    \end{array}
\right]
\left[
    \begin{array}{cc}
    -\omega & 0 \\
    0 & \omega \\
    \end{array}
\right]
\left[
    \begin{array}{cc}
    1 & -1/\omega \\
    1 &  1/\omega \\
    \end{array}
\right]
$$

$T$を用いて状態変数を変換して$z = T^{-1}x$，(3)式を同値変換すると
$$
T^{-1} \dot{X} = T^{-1}AX = \Lambda T^{-1} X \\
\dot{Z} = \Lambda Z \\
\left[
    \begin{array}{cc}
    \dot{z_1} \\
    \dot{z_2} \\
    \end{array}
\right] =
\left[
    \begin{array}{cc}
    -\omega & 0 \\
    0 & \omega \\
    \end{array}
\right]
\left[
    \begin{array}{cc}
    z_1 \\
    z_2 \\
    \end{array}
\right]
$$
ここで$z_1 = x - \frac{\dot{x}}{\omega}$は安定モード，$z_2 = x + \frac{\dot{x}}{\omega}$は不安定モードを示す．

## 軌道エネルギー

(2)式の両辺に$\dot{x}$をかけると

$$
    \dot{x} \ddot{x} = \omega^2 \dot{x} x \\
    \dot{x} \ddot{x} - \omega^2 \dot{x} x = 0 \\
    \frac{\rm d}{{\rm d}t}(\frac{1}{2}(\dot{x}^2 - \omega^2 x^2)) = 0
$$

$E = \frac{1}{2}(\dot{x}^2 - \omega^2 x^2)$とすると
$$
    \frac{\rm d}{{\rm d}t}E = 0
$$
となるため，$E$は時間によらず変化しない値であり，軌道エネルギーと呼ぶ

### 軌道エネルギーを用いた計算例

初期状態$X_0 = [x_0\ \dot{x}_0]^{\rm T}$として，質点が目標速度$\dot{x}_d$となる位置$x_1$を求める．

各時点での軌道エネルギーは
$$
    E_0 = \frac{1}{2}(\dot{x}_0^2 - \omega^2 x_0^2) \\
    E_1 = \frac{1}{2}(\dot{x}_d^2 - \omega^2 x_1^2) \\
$$
時間によらず軌道エネルギーは変化しないので，
$$
    E_0 = E_1 \\
    \frac{1}{2}(\dot{x}_0^2 - \omega^2 x_0^2) = \frac{1}{2}(\dot{x}_d^2 - \omega^2 x_1^2) \\
    \dot{x}_0^2 - \omega^2 x_0^2 = \dot{x}_d^2 - \omega^2 x_1^2 \\
    x_1 = \pm \sqrt{ \frac{\omega^2x_0^2 -(\dot{x}_0^2 - \dot{x}_d^2)}{\omega^2}}
$$

## $\dot{X} = AX$の位相平面図

$\omega = 1$のときの$\dot{X}=AX$の位相平面図を示す.

![lipm_phase_portrait](https://i.imgur.com/t3wlf0X.png)

ここで，軌道エネルギー$E = \frac{1}{2}(\dot{x}^2 - \omega^2 x^2)$の符号によって図の領域を区切ることができる．

例えば$x < 0$，$\dot{x} > 0$の第二象限に状態が置かれているときに，$E > 0$であれば$x=0$を超えることができるが，$E < 0$であると$x=0$を超えることができない．
