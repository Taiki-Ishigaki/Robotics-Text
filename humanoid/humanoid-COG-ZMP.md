###### tags: `humanoid` `robotics` 
# 重心・ZMPモデル
線形倒立振子に対してZMPを制御入力とした重心・ZMPモデル[1]について述べる

## 重心の動力学
$$
    m \ddot{p_G} = f_Z - mg \\
    \dot{L} = \tau_Z - (p_G - p_Z) \times f_Z
$$

## 重心・ZMPモデル
$f_Z$を消去して
$$
    \dot{L} = \tau_Z - (p_G - p_Z) \times (m \ddot{p}_G + mg)
$$
両辺に$n_Z$の外積をとって$，n_Z \times \tau_Z = 0$であることを用いて
$$
    n_Z \times \dot{L} = n_Z \times \tau_Z - n_Z \times (p_G - p_Z) \times (m \ddot{p}_G + mg) \\
    n_Z \times \dot{L} + n_Z \times (p_G - p_Z) \times (m \ddot{p}_G + mg) =0 \\
    n_Z \times \dot{L} + (n_Z \cdot (m\ddot{p}_G + mg))(p_G - p_Z) - (n_Z  \cdot (p_G - p_Z))(m\ddot{p}_G + mg) = 0 \\
    m(\ddot{p}_G + g) = m\frac{n_Z \cdot (\ddot{p}_G + g)}{n_Z  \cdot (p_G - p_Z)}(p_G - p_Z) + \frac{n_Z \times \dot{L}}{n_Z  \cdot (p_G - p_Z)}
$$
ZMPは
$$
    p_Z = p_G - \frac{n_Z  \cdot (p_G - p_Z)}{n_Z \cdot (\ddot{p}_G + g)} (\ddot{p}_G + g) + \frac{n_Z \times \dot{L}}{m(n_Z \cdot (\ddot{p}_G + g))}
$$

すべての接触点が同一平面上にあるとき，$n_Z = [0\ 0\ 1]^{\rm T}$として

$$
\left[
    \begin{array}{ccc}
    {\ddot{p}_G}_x \\
    {\ddot{p}_G}_y \\
    {\ddot{p}_G}_z
    \end{array}
\right] 
= \omega^2
\left[
    \begin{array}{lll}
    ({p_G}_x - {p_Z}_x) - \frac{\dot{L}_y}{m({\ddot{p}_G}_z + g_z)}\\
    ({p_G}_y - {p_Z}_y) + \frac{\dot{L}_x}{m({\ddot{p}_G}_z + g_z)}\\
    ({p_G}_z - {p_Z}_z)
    \end{array}
\right]
+
\left[
    \begin{array}{ccc}
    g_x \\
    g_y \\
    g_z
    \end{array}
\right] \\
\omega = \sqrt{\frac{{\ddot{p}_G}_z + g_z}{{p_G}_z - {p_Z}_z}}
$$


## 参考文献
[[1] 水戸部和久，矢島克知，那須康雄："ゼロモーメント点の操作による歩行ロボットの制御"，日本ロボット学会誌，Vol.18，No.3，pp.359–365，2000.](https://www.jstage.jst.go.jp/article/jrsj1983/18/3/18_3_359/_article/-char/ja/)