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
## 参考文献
[[1] 水戸部和久，矢島克知，那須康雄："ゼロモーメント点の操作による歩行ロボットの制御"，日本ロボット学会誌，Vol.18，No.3，pp.359–365，2000.](https://www.jstage.jst.go.jp/article/jrsj1983/18/3/18_3_359/_article/-char/ja/)