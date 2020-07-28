###### tags: `robotics`
# ロボティクスのリー群とリー代数

ロボティクスの分野で登場するリー群とリー代数のメモ
## 回転行列$R$と角速度$\omega$
$$
    R R^{\rm T} = E \\
    \dot{R} R^{\rm T} + R \dot{R^{\rm T}} = O \\
    \dot{R} = -R \dot{R} R = [\omega \times] R = R [\overline{\omega} \times]
$$
ここで$R \in SO(3)$, $[\omega \times], [\overline{\omega} \times] \in so(3)$
$$
    [\omega \times] = -R \dot{R} \\
    [\overline{\omega} \times] = - \dot{R} R
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
    [\omega \times] = R [\overline{\omega} \times] R^{\rm T}
$$