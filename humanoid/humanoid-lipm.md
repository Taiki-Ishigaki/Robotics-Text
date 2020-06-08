###### tags: `humanoid` `robotics` 
# 線形倒立振り子

## 線形倒立振子の運動方程式

地面にfree jointで固定された長さ$h$の棒に質点(重さ:$m$)倒立振子を考える(簡単のため同一平面上を動く時を考える). 振子の傾きを$\theta$として，倒立振子の運動方程式は，

$$
(m h^2)\ddot{\theta} = mg \sin\theta \ h
$$

$0 \simeq \theta$のとき，$\sin\theta \simeq \theta$とすることができるので

$$
\ddot{\theta} = \omega^2 \sin\theta \quad  \omega := \sqrt{\frac{g}{h}}\tag{1}
$$

重心位置$x_G$として，$x_G = h \sin\theta \simeq h\theta$なので(1)式は

$$
\ddot{x_G} = \omega x_G \tag{2}
$$
となり線形倒立振り子の運動方程式が求まる.
状態変数$x = [x_G \dot{x_G}]^T$として状態方程式は

$$
\dot{x} =
\left[
    \begin{array}{cc}
    \dot{x_G} \\
    \ddot{x_G} \\
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
    x_G \\
    \dot{x_G} \\
    \end{array}
\right] =
Ax \tag{3}
$$

## 運動方程式の解析

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

$\lambda = -\omega < 0$ のとき（不安定モード）
$$a_1 = [1, -\omega]^T$$

$\lambda = \omega > 0$ のとき（安定モード）
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

$T$を用いて状態変数を変換して$z = T^{-1}x$，(3)式の同値変換をすると
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
ここで$z_1 = x_G - \frac{\dot{x_G}}{\omega}$は不安定モード，$z_2 = x_G + \frac{\dot{x_G}}{\omega}$は安定モードを示す．
