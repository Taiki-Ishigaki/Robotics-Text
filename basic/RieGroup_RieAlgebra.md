###### tags: `robotics`
# ロボティクスのリー群とリー代数

ロボティクスの分野で登場するリー群とリー代数のメモ
## 回転行列と角速度
回転行列$R$と角速度ベクトルの関係は，回転行列の性質から
$$
    R R^{\rm T} = E \\
    \dot{R} R^{\rm T} + R \dot{R}^{\rm T} = O \\
    \dot{R} = -R \dot{R}^{\rm T} R = [\omega \times] R = R [\overline{\omega} \times]
$$
のように導かれる． $\omega$は絶対座標系から見た角速度，$\overline{\omega}$は物体座標系からみた角速度を表し
$$
    [\omega \times] = -R \dot{R}^{\rm T} = \dot{R} R^{\rm T} \\
    [\overline{\omega} \times] = - \dot{R}^{\rm T} R = R^{\rm T}\dot{R}
$$
$\omega$と$\overline{\omega}$の関係は
$$
    [\omega \times] = R [\overline{\omega} \times] R^{\rm T} \\
    [\overline{\omega} \times] = R^{\rm T} [\omega \times] R
$$
### リー群 $SO(3)$
回転行列$R$の集合$G$は群として以下のような性質を持つ

1. $R$は行列積について閉じている
$$
    R_1 R_2 \in G　(R_1, R_2 \in G )
$$
2. 行列積は結合法則を満たし
$$
    (R_1 R_2) R_3 = R_1 (R_2 R_3)
$$
3. 単位元$E \in G$が存在し
$$
    R_1 E = E R_1 = R_1
$$
4. 逆元$R_1^{-1}$が存在する
$$
    R_1 R_1^{-1} = R_1^{-1} R_1 = E
$$

回転行列は群で，なめらかな構造を持つことからリー群に分類される．回転行列$R$の集合は特殊直交群(special orthogonal group)に属し，その集合は$SO(3)$と表され，以下を満たす．
$$
    R^{\rm T} = R^{-1}, {\rm det}(R) = 1
$$

### $\omega$ と $\overline{\omega}$の変換
任意のベクトル$q,p$について，$x = Rp$として
$$
    [(R q)\times] R p = R ([q \times] p) \\
    [(R q)\times] x = R [q \times] R^{\rm T} x \\
    [(R q)\times] = R [q \times] R^{\rm T}
$$
となるため，$q = \overline{\omega}$とすると$Rq = \omega$となる.これをリー群の随伴表現${\rm Ad}_R = R$を用いて
$$
    {\rm Ad}_R\overline{\omega} = \omega
$$
$\omega$から$\overline{\omega}$への変換を行うことができる．また同様に
$$
    [(R^{\rm T} q)\times] = R^{\rm T} [q \times] R
$$
と${\rm Ad}_{R^{-1}}=R^{\rm T}$をもちいて
$$
    {\rm Ad}_{R^{-1}}\omega = \overline{\omega}
$$
${\rm Ad}_{R}$と${\rm Ad}_{R^{-1}}$の間に双対の関係がある？(Adjoint, Coadjoint, dual)

### リー代数
角速度ベクトル$\omega, \overline{\omega}$は回転運動の接ベクトルとなる．

$[\omega \times],[\overline{\omega}\times]$の集合$g$はリー代数で，ベクトルとしてスカラ倍と和について閉じている
$$
    a [\omega \times] \in g \ ([\omega \times] \in g , a \in \mathbb{R}) \\
    [\omega_1 \times] + [\omega_2 \times] \in g \ ([\omega_1 \times], [\omega_2 \times] \in g)
$$
また以下の交換子積と呼ばれる演算についても閉じている．
$$
    [[\omega_1 \times], [\omega_2 \times]] = [\omega_1 \times] [\omega_2 \times] - [\omega_2 \times] [\omega_1 \times] \in g \\
    ([\omega_1 \times], [\omega_2 \times] \in g)
$$
これは$[\omega \times]$の交代行列の性質$[\omega \times]^{\rm T} = - [\omega \times]$を満たしている
$$
    [[\omega_1 \times], [\omega_2 \times]]^{\rm T} = ([\omega_1 \times] [\omega_2 \times])^{\rm T} - ([\omega_2 \times] [\omega_1 \times])^{\rm T} \\
    = [\omega_2 \times] [\omega_1 \times] - [\omega_1 \times] [\omega_2 \times]
    = -[[\omega_1 \times], [\omega_2 \times]] 
$$
行列積については閉じていないことに注意
$$
    [\omega_1 \times] [\omega_2 \times] \notin g \\
    ([\omega_1 \times] [\omega_2 \times])^{\rm T} = [\omega_2 \times][\omega_1 \times] \neq -[\omega_1 \times] [\omega_2 \times]
$$
### 行列微分方程式
$\dot{R} = [\omega \times] R$より(ロドリゲスの式の導出へつながる)
$$
    R(t) = {\rm exp}([\omega \times]t) R(0)
$$
$\dot{R} = R [\overline{\omega}\times]$より
$$
    R(t) = R(0) {\rm exp}([\overline{\omega} \times]t)
$$