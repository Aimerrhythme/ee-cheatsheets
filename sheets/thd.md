# 谐波与 THD（Harmonics and THD）

> 谐波是周期量中频率为基波整数倍的正弦分量；总谐波畸变率 THD 用谐波有效值的方和根与基波有效值之比，表示波形偏离正弦的程度。

## 核心公式

$h$ 次谐波频率 $f_h = h f_1$（$h = 2, 3, \ldots$）。非整数倍为间谐波；IEEE 519 的 THD 与 TDD 不计间谐波，一般计到 50 次。$V_h$ 为该次有效值：

$$
v(t) = V_0 + \sum_{h=1}^{\infty} \sqrt{2}\, V_h \cos(h\omega_1 t + \varphi_h)
$$

无直流时，有效值与 THD（公式里用比值，不是百分数）以及电压、电流 THD 为：

$$
V_{\mathrm{rms}} = \sqrt{\sum_{h=1}^{H} V_h^2} = V_1\sqrt{1 + \mathrm{THD}_V^2}
$$

$$
\mathrm{THD}_V = \frac{\sqrt{\sum_{h=2}^{H} V_h^2}}{V_1},\quad
\mathrm{THD}_I = \frac{\sqrt{\sum_{h=2}^{H} I_h^2}}{I_1}
$$

电流限值用总需量畸变 TDD。$I_L$ 是 PCC 处基波最大需量电流（2014：前 12 个月各月最大需量的平均）：

$$
\mathrm{TDD} = \frac{\sqrt{\sum_{h=2}^{H} I_h^2}}{I_L} = \mathrm{THD}_I \cdot \frac{I_1}{I_L}
$$

电压近似正弦时，位移因数 $\mathrm{DPF} = \cos\varphi_1$，畸变因数与真功率因数为：

$$
\mathrm{DF} = \frac{I_1}{I_{\mathrm{rms}}} = \frac{1}{\sqrt{1 + \mathrm{THD}_I^2}},\quad
\mathrm{PF} = \frac{P}{S} = \mathrm{DPF} \cdot \mathrm{DF}
$$

$p$ 脉波整流器的特征谐波为 $h = kp \pm 1$（$k = 1, 2, \ldots$）。六脉波即 $6k \pm 1$（5、7、11、13…），理想大电感时 $I_h \approx I_1/h$，故 $I_5/I_1 = 1/5$、$I_7/I_1 = 1/7$。十二脉波为 $12k \pm 1$，理论上消去 5、7 次。

## 典型数值 / 量纲

电压限值取自 IEEE 519-2014 表 1（PCC，线对中性点，相对额定基波电压）。公开转述的 2022 表 1 数值相同。$>161\,\mathrm{kV}$ 且畸变来自 HVDC、并在未来用户接入点已衰减时，THD 可到 2.0%。

| PCC 电压 $V$ | 单次谐波 | THD |
|---|---|---|
| $V \le 1.0\,\mathrm{kV}$ | 5.0% | 8.0% |
| $1\,\mathrm{kV} < V \le 69\,\mathrm{kV}$ | 3.0% | 5.0% |
| $69\,\mathrm{kV} < V \le 161\,\mathrm{kV}$ | 1.5% | 2.5% |
| $V > 161\,\mathrm{kV}$ | 1.0% | 1.5% |

120 V–69 kV 电流限值取自 2014 表 2（奇次，占 $I_L$ 的 %）。2022 公开转述中下表数字未改。69–161 kV 的 TDD 为 2.5%–10%；$>161\,\mathrm{kV}$ 为 1.5%–3.75%。分档端点以原文为准。周 95% 的 10 min 值不超过表值；日 99% 的 3 s 值，电压可到 1.5 倍、电流可到 2.0 倍，电流另有周 99% 的 1.5 倍。

| $I_{SC}/I_L$ | $3 \le h < 11$ | $11 \le h < 17$ | $17 \le h < 23$ | $23 \le h < 35$ | $35 \le h \le 50$ | TDD |
|---|---|---|---|---|---|---|
| $<20$ | 4.0 | 2.0 | 1.5 | 0.6 | 0.3 | 5.0 |
| $20<50$ | 7.0 | 3.5 | 2.5 | 1.0 | 0.5 | 8.0 |
| $50<100$ | 10.0 | 4.5 | 4.0 | 1.5 | 0.7 | 12.0 |
| $100<1000$ | 12.0 | 5.5 | 5.0 | 2.0 | 1.0 | 15.0 |
| $>1000$ | 15.0 | 7.0 | 6.0 | 2.5 | 1.4 | 20.0 |

## 课堂提示

- THD 的分母是基波有效值，不是总有效值。表内是百分数，代入 $\sqrt{1 + \mathrm{THD}^2}$ 前先除以 100。
- 电流是否超标看 TDD，不看测量瞬间的 $\mathrm{THD}_I$。轻载 $I_1 \ll I_L$ 时 THD 可以很大而 TDD 仍合格；满载时二者接近。
- 限值只用于 PCC，不要套到单台设备端子或厂内母线。半波整流产生的直流分量不允许。电压、电流都畸变时 $P = \sum V_h I_h \cos\varphi_h$，不能只用 $\cos\varphi_1$。
- 2014：偶次谐波为上表奇次限值的 25%。2022 的红线说明与多份公开转述改为：2、4、6 次取表列限值的 50%，更高偶次与奇次相同；偶次注脚以标准原文为准。三相桥的特征谐波是 $6k \pm 1$，3 次及三倍频主要来自单相负荷。

## 相关工具

- [IEEE 519-2022](https://standards.ieee.org/ieee/519/10677/) — 谐波限值原文（电压 THD 与电流 TDD）
- [Total harmonic distortion（Wikipedia）](https://en.wikipedia.org/wiki/Total_harmonic_distortion) — THD 定义与有效值关系
