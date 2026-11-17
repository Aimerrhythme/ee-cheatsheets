# 相量与复数运算（Phasors and Complex Arithmetic）

> 用复数表示同频正弦量的幅值与相位，把微分方程变成代数运算。

## 核心公式
$$ u(t)=\sqrt{2}\,U\sin(\omega t+\varphi)\;\Longleftrightarrow\;\dot U=U\angle\varphi=U e^{j\varphi} $$

$$ \dot U = a+jb,\quad U=\sqrt{a^2+b^2},\quad \varphi=\arctan\frac{b}{a}\ (\text{注意象限}) $$

$$ a=U\cos\varphi,\quad b=U\sin\varphi $$

乘除用极坐标，加减用直角坐标：

$$ \dot A\dot B=AB\angle(\varphi_A+\varphi_B),\quad \frac{\dot A}{\dot B}=\frac{A}{B}\angle(\varphi_A-\varphi_B) $$

元件阻抗与导纳：

$$ Z_R=R,\quad Z_L=j\omega L,\quad Z_C=\frac{1}{j\omega C}=-j\frac{1}{\omega C},\quad \dot U=Z\dot I $$

复功率：

$$ \tilde S=\dot U\dot I^{*}=P+jQ,\quad S=UI,\quad P=UI\cos\varphi,\quad Q=UI\sin\varphi $$

常用旋转因子：

$$ j=e^{j90^\circ},\quad a=e^{j120^\circ},\quad 1+a+a^2=0 $$

## 典型数值 / 量纲
| 量 | 典型值 | 单位 |
|----|--------|------|
| 工频角频率 $\omega$（50 Hz） | 314.16 | $\mathrm{rad/s}$ |
| 相量模（有效值）与幅值 | $U_m=\sqrt{2}U$ | $\mathrm{V}$ |
| 220 V 相电压相量 | $220\angle 0^\circ$ | $\mathrm{V}$ |
| 线电压（星形） | $\sqrt{3}\,U_p\angle30^\circ$ | $\mathrm{V}$ |
| 1 mH 在 50 Hz 的感抗 | 0.314 | $\Omega$ |
| 100 μF 在 50 Hz 的容抗 | −j31.8 | $\Omega$ |
| 滞后 / 超前 | $\varphi_i<\varphi_u$ 为感性 | — |

## 课堂提示
- 相量只适用于**同频**正弦稳态；不同频率要在时域叠加。
- 求角度用 atan2：第二、三象限需 $\pm180^\circ$ 修正。
- 感性电流滞后电压，口诀“电感滞后、电容超前”（ELI the ICE man）。
- 有效值相量与幅值相量不要混用，复功率里电流要取共轭。

## 相关工具
- [ee-lab-toolkit/tools/...](https://github.com/Aimerrhythme/ee-lab-toolkit)
