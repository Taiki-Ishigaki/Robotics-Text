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

状態変数$x = [x \  \dot{x}]^T$として状態方程式は

$$
\dot{x} =
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
Ax \tag{3}
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
T^{-1} \dot{x} = T^{-1}Ax = \Lambda T^{-1} x \\
\dot{z} = \Lambda z \\
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
