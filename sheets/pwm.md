# PWM 与 SPWM（Pulse-Width Modulation / Sinusoidal PWM）

> 用固定开关周期内导通时间的长短（占空比）来控制输出电压的平均值；SPWM 让占空比按正弦规律变化，从而在输出中得到正弦基波。

## 核心公式

占空比与平均电压（以 Buck 为例）：

$$ D = \frac{t_{on}}{T_s},\quad V_o = D\,V_{in} $$

调制比（幅值调制比）与载波比（频率调制比）：

$$ m_a = \frac{\hat V_{r}}{\hat V_{tri}},\qquad m_f = \frac{f_{s}}{f_1} $$

线性区（$m_a \le 1$）输出基波幅值：

$$ \hat V_{AN,1} = m_a\,\frac{V_{dc}}{2}\ \ (\text{半桥/单相桥臂}),\qquad \hat V_{o,1} = m_a\,V_{dc}\ \ (\text{单相全桥}) $$

三相 SPWM 线电压基波有效值：

$$ V_{LL,1} = \frac{\sqrt{3}}{2\sqrt{2}}\,m_a V_{dc} \approx 0.612\,m_a V_{dc} $$

方波（$m_a \to$ 很大）基波极限与扩展线性区：

$$ \hat V_{AN,1}^{\max} = \frac{4}{\pi}\cdot\frac{V_{dc}}{2},\qquad m_a^{\max}\big|_{\text{三次谐波注入 / SVPWM}} = \frac{2}{\sqrt{3}} \approx 1.155 $$

谐波位置（边带）：

$$ h = j\,m_f \pm k,\quad \text{如 } m_f,\ m_f \pm 2,\ 2m_f \pm 1,\ \dots $$

## 典型数值 / 量纲

| 量 | 典型值 | 单位 |
|----|--------|------|
| 调制比 $m_a$（线性区） | 0 ~ 1（注入/SVPWM 可到 1.155） | — |
| 载波比 $m_f$（小功率同步调制） | 奇数且为 3 的倍数，如 9、15、21 | — |
| 开关频率 $f_s$：IGBT | 2 ~ 20 | kHz |
| 开关频率 $f_s$：Si MOSFET / SiC | 20 ~ 数百 | kHz |
| 死区时间（IGBT 桥臂） | 约 0.5 ~ 3 | μs |
| $\hat V_{AN,1}$ 方波 / 线性区上限之比 | $4/\pi \approx 1.273$ | — |

## 课堂提示

- 分清两个"比"：$m_a$ 管幅值（基波多大），$m_f$ 管频率（谐波离基波多远）。$m_f$ 越大，滤波越容易，但开关损耗越大。
- 半桥基波幅值是 $m_a V_{dc}/2$，全桥是 $m_a V_{dc}$；三相线电压还要再乘 $\sqrt{3}$，有效值别忘了除以 $\sqrt{2}$。
- $m_a > 1$ 进入过调制：基波不再与 $m_a$ 成正比，低次谐波重新出现。三相取 $m_f$ 为 3 的倍数，可使线电压中载波整数倍处的三倍频谐波相互抵消。
- 死区防止上下管直通，但会造成输出电压损失和低次谐波畸变，小 $m_a$ 时更明显。

## 相关工具

- [ee-lab-toolkit/tools/pwm-waveform](https://github.com/Aimerrhythme/ee-lab-toolkit/tree/main/tools/pwm-waveform)：PWM 波形与调制比/载波比演示（Matlab + Python）
- [ee-lab-toolkit/tools/fft-thd](https://github.com/Aimerrhythme/ee-lab-toolkit/tree/main/tools/fft-thd)：对 SPWM 输出做 FFT，观察 $m_f$ 边带与 THD
- [速查表：谐波与 THD](thd.md)
- [Pulse-width modulation（Wikipedia）](https://en.wikipedia.org/wiki/Pulse-width_modulation)
