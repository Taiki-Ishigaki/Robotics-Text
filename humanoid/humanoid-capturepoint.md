###### tags: `humanoid` `robotics`
# Capture Point
## Capture Pointの導出
「ヒューマノイドが自身を停止させる為の着地点」として定義された点をCapture Pointと呼ばれ,
心・ZMPモデル
$$
    \ddot{x_{\rm G}} = \omega^2({x_{\rm G} - x_{\rm Z}}) \tag{1}
$$
の解析解から求まる．倒立振子の支持脚(ZMP)が動かない時$x_{\rm Z}(t) = x_{\rm Z}(0) = x_{{\rm Z},0}$の時,(1)式の解は
$$
    x_{\rm G}(t) = A_1 {\rm e}^{-\omega t} +  A_2 {\rm e}^{\omega t} + x_{{\rm Z},0} \ (A_1, A_2 = {\rm const})
$$
$x_{\rm G}(0) = x_{{\rm G},0}$，$\dot{x_{\rm G}(0)} = \dot{x_{{\rm G},0}}$とすると
$$
    x_{\rm G}(t) 
    = \frac{1}{2}(x_{{\rm G},0} - \frac{\dot{x_{{\rm G},0}}}{\omega} -x_{{\rm Z},0}) {\rm e}^{-\omega t} 
    + \frac{1}{2}(x_{{\rm G},0} + \frac{\dot{x_{{\rm G},0}}}{\omega} -x_{{\rm Z},0}) {\rm e}^{\omega t} 
    + x_{{\rm Z},0} \tag{2}
$$
重心位置が無限時間後に支持脚の上($x_{\rm G}(\infty) = x_{{\rm Z},0}$)に停止することを考えると，$\xi = x_{\rm G} + \frac{\dot{x_{\rm G}}}{\omega}$として(2)式は
$$
    x_{\rm G}(t)
    = (x_{{\rm G},0} - \frac{1}{2}(\xi_0 + x_{{\rm Z},0})){\rm e}^{-\omega t} 
    + \frac{1}{2}( \xi_0 - x_{{\rm Z},0}) {\rm e}^{\omega t} 
    + x_{{\rm Z},0} \tag{3}
$$
支持脚位置を$x_{{\rm Z},0} = \xi_0$とした時
$$
    x_{\rm G}(t)
    = (x_{{\rm G},0} - \xi_0){\rm e}^{-\omega t} 
    + \xi_0 \tag{4}
$$
$t \rightarrow \infty$で
$$
    x_{\rm G}(\infty) = \xi_0 \tag{5}
$$
重心位置が支持脚$\xi_0(= x_{{\rm Z},0})$の上に来る．以上からCapture Point$\xi$は
重心位置$x_{\rm G}$と重心速度$\dot{x}_{\rm G}$を用いて
$$
    \xi = x_{\rm G} + \frac{\dot{x_{\rm G}}}{\omega} \tag{6}
$$
ここでCapture Pointは重心位置，重心速度に依存し，重心の運動に従い変化することに注意する．
## Capture Pointのダイナミクス
重心・ZMPモデルについて$x_{\rm G}, \dot{x_{\rm G}}$を状態変数に取ったときの状態方程式は
$$
    \frac{d}{dt}
    \left[
        \begin{array}{cc}
        x_{\rm G} \\
        \dot{x_{\rm G}} \\
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
        x_{\rm G} \\
        \dot{x_{\rm G}} \\
        \end{array}
    \right] +
    \left[
        \begin{array}{cc}
        0 \\
        -\omega^2 \\
        \end{array}
    \right] x_{\rm Z}
    \tag{7}
$$
状態変数として$x_{\rm G}, \xi$を取ったときを考えると
$$
    \left[
        \begin{array}{cc}
        x_{\rm G} \\
        \dot{x_{\rm G}} \\
        \end{array}
    \right] =
    \left[
        \begin{array}{cc}
        1 & 0 \\
        -\omega & \omega \\
        \end{array}
    \right]
    \left[
        \begin{array}{cc}
        x_{\rm G} \\
        \xi \\
        \end{array}
    \right] =
    T 
    \left[
        \begin{array}{cc}
        x_{\rm G} \\
        \xi \\
        \end{array}
    \right] \\
        T = 
    \left[
        \begin{array}{cc}
        1 & 0 \\
        -\omega & \omega \\
        \end{array}
    \right], 
    T^{-1} =
    \left[
        \begin{array}{cc}
        1 & 0 \\
        1 & \frac{1}{\omega} \\
        \end{array}
    \right]
$$
と変換できるため(7)式は
$$
    \frac{d}{dt}
    T 
    \left[
        \begin{array}{cc}
        x_{\rm G} \\
        \xi \\
        \end{array}
    \right] =
    \left[
        \begin{array}{cc}
        0 & 1 \\
        \omega^2 & 0 \\
        \end{array}
    \right]
    T 
    \left[
        \begin{array}{cc}
        x_{\rm G} \\
        \xi \\
        \end{array}
    \right] +
    \left[
        \begin{array}{cc}
        0 \\
        -\omega^2 \\
        \end{array}
    \right] x_{\rm Z} \\
    \frac{d}{dt}
    \left[
        \begin{array}{cc}
        x_{\rm G} \\
        \xi \\
        \end{array}
    \right] =
    T^{-1}
    \left[
        \begin{array}{cc}
        0 & 1 \\
        \omega^2 & 0 \\
        \end{array}
    \right]
    T 
    \left[
        \begin{array}{cc}
        x_{\rm G} \\
        \xi \\
        \end{array}
    \right] +
    T^{-1}
    \left[
        \begin{array}{cc}
        0 \\
        -\omega^2 \\
        \end{array}
    \right] x_{\rm Z} 
$$
$$
    \frac{d}{dt}
    \left[
        \begin{array}{cc}
        x_{\rm G} \\
        \xi \\
        \end{array}
    \right] =
    \left[
        \begin{array}{cc}
        -\omega & \omega \\
        0 & \omega \\
        \end{array}
    \right]
    \left[
        \begin{array}{cc}
        x_{\rm G} \\
        \xi \\
        \end{array}
    \right] +
    \left[
        \begin{array}{cc}
        0 \\
        -\omega \\
        \end{array}
    \right] x_{\rm Z} \tag{8}
$$
(8)式の上半分の成分は
$$
    \dot{x_{\rm G}} = \omega(\xi - x_{\rm G}) \tag{9}
$$
重心がCapture Point$\xi$に向かう安定閉ループであることを示し，重心速度はCapture Pointへ向かう方向を示す．(8)式の下半分の成分は
$$
    \dot{\xi} = \omega(\xi - x_{\rm Z}) \tag{10}
$$
とCapture Pointのダイナミクスを示す．(9)式より重心はCapture Pointを追従するため，Capture Pointを安定化すれば重心も間接的に安定化される．$x_{\rm Z}$の時，(10)の解析解は
$$
    \xi(t) = B_1 {\rm e}^{\omega t} + x_{\rm Z} \ (B_1 = {\rm const})
$$
$\xi(0) = \xi_0$として
$$
    \xi(t) = (\xi_0 - x_{\rm Z}) {\rm e}^{\omega t} + x_{\rm Z} \tag{11}
$$