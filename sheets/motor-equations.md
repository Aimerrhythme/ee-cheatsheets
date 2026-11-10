# 电机基本方程（Motor Basic Equations：DC / Induction）

> 用电压平衡、电磁转矩与机械运动三类方程描述电机：直流电机关系线性直观，异步电机则以转差率 $s$ 联系转子侧各量。

## 核心公式

**直流电机**（他励，稳态）：

$$ E_a = C_e\,\Phi\,n = K_e\,\omega,\qquad T_{em} = C_T\,\Phi\,I_a = K_t\,I_a $$

$$ U = E_a + I_a R_a \;\Rightarrow\; n = \frac{U}{C_e\Phi} - \frac{R_a}{C_e C_T\Phi^2}\,T_{em} $$

机械运动方程与功率关系：

$$ J\frac{\mathrm{d}\omega}{\mathrm{d}t} = T_{em} - T_L - B\,\omega,\qquad P_{em} = E_a I_a = T_{em}\,\omega $$

**三相异步电机**（稳态）：

$$ n_1 = \frac{60 f_1}{p},\qquad s = \frac{n_1 - n}{n_1},\qquad n = (1-s)\,n_1 $$

$$ P_{em} = 3 I_2'^2\,\frac{R_2'}{s}(1-s),\qquad T_{em} = \frac{P_{em}}{\Omega} = \frac{3\,p}{2\pi f_1}\cdot\frac{U_1^2\,R_2'/s}{\left(R_1 + R_2'/s\right)^2 + \left(X_1 + X_2'\right)^2} $$

最大转矩及其转差率（忽略 $R_1$ 时）：

$$ s_m \approx \frac{R_2'}{X_1 + X_2'},\qquad T_{max} \approx \frac{3\,p\,U_1^2}{4\pi f_1 \left(X_1 + X_2'\right)} $$

功率分配：$P_{Cu2} = s\,P_{M}$，其中 $P_{M}$ 为电磁功率（气隙传递功率）。

## 典型数值 / 量纲

| 量 | 典型值 | 单位 |
|----|--------|------|
| 工频同步转速（$f_1=50\,\mathrm{Hz}$）$p=1,2,3,4$ | 3000 / 1500 / 1000 / 750 | r/min |
| 异步机额定转差率 $s_N$ | 约 0.01 ~ 0.06（小机组偏大） | — |
| 异步机 $T_{max}/T_N$ | 约 1.8 ~ 2.5 | — |
| 异步机直接起动电流 $I_{st}/I_N$ | 约 5 ~ 7 | — |
| 直流电机 $R_a$ 压降占比 | 额定时约 $(3\sim 8)\%\,U_N$ | — |
| 转矩单位 | $\mathrm{N\cdot m}$；$T=9.55\,P/n$（$P$ 为 W，$n$ 为 r/min） | N·m |

## 课堂提示

- 直流机三个常数别混：$E_a\propto n$、$T\propto I_a$；$C_T = \dfrac{60}{2\pi}C_e \approx 9.55\,C_e$，用 SI 制 $K_e = K_t$ 数值相同。
- 直流机改变 $U$ 是"平移"机械特性（斜率不变），串电阻 $R_a$ 是"变斜"，弱磁（减小 $\Phi$）升速但降低转矩能力。
- 异步机 $s=1$ 为起动，$s\to0$ 为空载；$T_{max}$ 与 $U_1^2$ 成正比，与 $R_2'$ 无关，而 $s_m$ 与 $R_2'$ 成正比（绕线机串电阻改善起动的依据）。
- 电压下降 10% 时转矩约降为 $0.9^2=81\%$，易误判电机"带不动"；转子铜耗 $P_{Cu2}=sP_M$ 说明低速运行效率差。
- 符号带 $'$ 的参数表示已折算到定子侧，做题时先确认是否已折算。

## 相关工具

- [ee-lab-toolkit/tools/motor-torque-speed](https://github.com/Aimerrhythme/ee-lab-toolkit/tree/main/tools/motor-torque-speed)：电机转矩-转速特性演示（Matlab + Python）
- [ee-lab-toolkit/tools/pid-step-compare](https://github.com/Aimerrhythme/ee-lab-toolkit/tree/main/tools/pid-step-compare)：转速环 PID 阶跃响应对比
- [速查表：标幺值](per-unit.md)
- [Induction motor（Wikipedia）](https://en.wikipedia.org/wiki/Induction_motor)
- [DC motor（Wikipedia）](https://en.wikipedia.org/wiki/DC_motor)
