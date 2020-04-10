# ヒューマノイドの運動方程式
浮遊リンク系の運動方程式は以下のように与えられる  

\begin{align}
    \left[
        \begin{array}{cc}
        \boldsymbol{H_0} & \boldsymbol{H_{0\theta}} \\
        \boldsymbol{H_{0\theta}}^{\rm{T}} & \boldsymbol{H_\theta}
        \end{array}
    \right]
    \left[
        \begin{array}{cc}
        \boldsymbol{\ddot{q}_0} \\
        \boldsymbol{\ddot{q}_{\theta}}
        \end{array}
    \right]
    +
    \left[
        \begin{array}{cc}
        \boldsymbol{b_0} \\
        \boldsymbol{b_{\theta}}
        \end{array}
    \right]
    =
    \left[
        \begin{array}{cc}
        0 \\
        \boldsymbol{\tau_{\theta}}
        \end{array}
    \right]
\end{align}