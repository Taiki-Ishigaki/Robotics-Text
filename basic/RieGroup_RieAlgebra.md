###### tags: `robotics`
# ロボティクスのリー群とリー代数

ロボティクスの分野で登場するリー群とリー代数のメモ
## 回転行列と角速度
$$
    R R^{\rm T} = E \\
    \dot{R} R^{\rm T} + R \dot{R}^{\rm T} = O \\
    \dot{R} = -R \dot{R}^{\rm T} R = [\omega \times] R = R [\overline{\omega} \times]
$$
ここで$R \in SO(3)$, $[\omega \times], [\overline{\omega} \times] \in so(3)$
$$
    [\omega \times] = -R \dot{R}^{\rm T} = \dot{R} R^{\rm T} \\
    [\overline{\omega} \times] = - \dot{R}^{\rm T} R = R^{\rm T}\dot{R}
$$
$\dot{R} = [\omega \times] R$より(ロドリゲスの式の導出)
$$
    R(t) = {\rm exp}([\omega \times]t) R(0)
$$
$\dot{R} = R [\overline{\omega}\times]$より
$$
    R(t) = R(0) {\rm exp}([\overline{\omega} \times]t)
$$
また$\omega$と$\overline{\omega}$の関係は
$$
    [\omega \times] = R [\overline{\omega} \times] R^{\rm T} \\
    [\overline{\omega} \times] = R^{\rm T} [\omega \times] R
$$
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