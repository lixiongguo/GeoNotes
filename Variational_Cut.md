对于拓扑复杂的曲面如果要进行展平那么就需要用分割线对其进行分割，即使是拓扑圆盘的曲面如果想要尽可能扭曲小的摊平到平面上也是需要分割线对其进行分割的。求一个最优分割线的过程也就是一个典型的几何优化过程。

![image-20240823191520150](C:\Users\LGX_MATE_BOOK\AppData\Roaming\Typora\typora-user-images\image-20240823191520150.png)

为了更好进行建模，先考虑在连续域上的曲面模型然后再进行离散化得到三角网格的模型。

从连续域的微分几何理论出发，对于一条特定的曲线$\gamma$，n为其法线，可以通过迭代这样一个流来迭代求得其扭曲

$$
\frac{d}{dt}\gamma =(\frac{\part u}{\part n})^2n\\
其中u是曲面经过\gamma切割线切开后，再进行共形展开所得到的共形因子\\
可以用Yamabe方程\Delta u = -K求得,其中K是曲面的高斯曲率
$$
注意到不需要真的显示地将曲面展平，对于共形映射，只要有共形因子就可以表达映射（通过Yamabe方程）

如果只是单纯要求distortion最小的话，直接让曲线长度不断增加就可以，但是这样肯定不是我们想要的，所以增加一个对长度的惩罚项，要求长度尽可能小，面积扭曲尽可能小，这与经典的等周问题(isoperimeteric problem)是相关联的

该方法基于连续域的，并用形状导数（shape derivatives）来进行优化

![img](file:///C:\Users\LGX_MATE_BOOK\Documents\Tencent Files\474015788\nt_qq\nt_data\Pic\2024-07\Ori\e6b0bedd818d5060bf520bea8a95770a.png)

![img](file:///C:\Users\LGX_MATE_BOOK\Documents\Tencent Files\474015788\nt_qq\nt_data\Pic\2024-07\Ori\5f05e292a919d545f7ea17432bc8c8ff.png)

该最优化的constrain是Yamabe方程，应用Dirichlet能量来度量面积扭曲（area distortion），并且增加长度的正则项

![img](file:///C:\Users\LGX_MATE_BOOK\Documents\Tencent Files\474015788\nt_qq\nt_data\Pic\2024-07\Ori\facb05712da13777aa04a50a95d20ad0.png)

![img](file:///C:\Users\LGX_MATE_BOOK\Documents\Tencent Files\474015788\nt_qq\nt_data\Pic\2024-07\Ori\345baa55783404a5f94aa83350565816.png)

**Shape Optimization**

如何求解上面的最优化呢，应用 Shape优化方法

关于shape Derivative

![img](file:///C:\Users\LGX_MATE_BOOK\Documents\Tencent Files\474015788\nt_qq\nt_data\Pic\2024-07\Ori\3b7be85e0d6fc8e5326e65b086bcad41.png)

![img](file:///C:\Users\LGX_MATE_BOOK\Documents\Tencent Files\474015788\nt_qq\nt_data\Pic\2024-07\Ori\4886a099eb0c3a02b51b92df325259b5.png)

应用Lagrange乘子法

![img](file:///C:\Users\LGX_MATE_BOOK\Documents\Tencent Files\474015788\nt_qq\nt_data\Pic\2024-07\Ori\32a3c0947914e4d06bdf9d16521c9283.png)

进一步得到shape derivative

![img](file:///C:\Users\LGX_MATE_BOOK\Documents\Tencent Files\474015788\nt_qq\nt_data\Pic\2024-07\Ori\e3bd041997a822b43e58fdc856e95b01.png)

Dirichlet能量的Shape Derivative

![img](file:///C:\Users\LGX_MATE_BOOK\Documents\Tencent Files\474015788\nt_qq\nt_data\Pic\2024-07\Ori\01b1ce316d745b475fbdff93b2dc8834.png)

从而获取到梯度流

![img](file:///C:\Users\LGX_MATE_BOOK\Documents\Tencent Files\474015788\nt_qq\nt_data\Pic\2024-07\Ori\7508a9031ac45ffacc660da6497720ec.png![img](file:///C:\Users\LGX_MATE_BOOK\Documents\Tencent Files\474015788\nt_qq\nt_data\Pic\2024-07\Ori\fb991427a43b8951663f3a910f63c2b0.png)

通过隐式函数来进行表达

![img](file:///C:\Users\LGX_MATE_BOOK\Documents\Tencent Files\474015788\nt_qq\nt_data\Pic\2024-07\Ori\c64a1dc9212d85ddaffc47746c4df767.png)

![img](file:///C:\Users\LGX_MATE_BOOK\Documents\Tencent Files\474015788\nt_qq\nt_data\Pic\2024-07\Ori\13272d14c2c4154c1a8a253e97b525fc.png)

**离散化**

