这里主要针对的是2D平面变形（2D Plane deformation）,将这种变形可以视为一个复变换，那样调和映射就是有比较好的性质

![img](file:///C:\Users\LGX_MATE_BOOK\Documents\Tencent Files\474015788\nt_qq\nt_data\Pic\2024-07\Ori\360c8766d0f6f980badece4d00bf5688.png)

所以本文的主要目的就是构造这样一个复调和映射，由于调和函数可以分解为两个全纯函数

![img](file:///C:\Users\LGX_MATE_BOOK\Documents\Tencent Files\474015788\nt_qq\nt_data\Pic\2024-07\Ori\a64421cfb96400951c0f67e0e3e153c7.png)

![img](file:///C:\Users\LGX_MATE_BOOK\Documents\Tencent Files\474015788\nt_qq\nt_data\Pic\2024-07\Ori\6f5200395fa7e87dee063795e2743fd1.png)

f的distortion可以用如下两个奇异值表达

![img](file:///C:\Users\LGX_MATE_BOOK\Documents\Tencent Files\474015788\nt_qq\nt_data\Pic\2024-07\Ori\5c3c0db1f38b109f29b11b9f4824eebe.png)

我们的目的是bound映射的distortion，这等价于如下定义

![img](file:///C:\Users\LGX_MATE_BOOK\Documents\Tencent Files\474015788\nt_qq\nt_data\Pic\2024-07\Ori\f231ccc7bffedbdec98b9caf1bf7aea1.png)

上面的表达式隐含了f是单射

![img](file:///C:\Users\LGX_MATE_BOOK\Documents\Tencent Files\474015788\nt_qq\nt_data\Pic\2024-07\Ori\f4a85edaca221323970edc5649db5685.png)

由于对于Harmonic映射，边界值全部决定了映射的形态，原文中证明下面的表达式可以等价于上面的证明

![img](file:///C:\Users\LGX_MATE_BOOK\Documents\Tencent Files\474015788\nt_qq\nt_data\Pic\2024-07\Ori\b98fee24c117fb0284f3ab415f980db8.png)

离散化：利用离散Cauchy变换，可以将全纯函数表达如下，所以目标就是求解分解后的phi psy系数

![img](file:///C:\Users\LGX_MATE_BOOK\Documents\Tencent Files\474015788\nt_qq\nt_data\Pic\2024-07\Ori\8d811f776a8b1e8e2b1bce5830dab417.png)

![img](file:///C:\Users\LGX_MATE_BOOK\Documents\Tencent Files\474015788\nt_qq\nt_data\Pic\2024-07\Ori\3a6790957e6d7b629835c4caa83e112a.png)



为了做求解，需要做凸化处理

![img](file:///C:\Users\LGX_MATE_BOOK\Documents\Tencent Files\474015788\nt_qq\nt_data\Pic\2024-07\Ori\38c5ca4e8f15c07a5b041a5d4cf15470.png)

各constrain条件的凸化如下

![img](file:///C:\Users\LGX_MATE_BOOK\Documents\Tencent Files\474015788\nt_qq\nt_data\Pic\2024-07\Ori\9b062984c64bdd1b037318455ae05fb4.png)

![img](file:///C:\Users\LGX_MATE_BOOK\Documents\Tencent Files\474015788\nt_qq\nt_data\Pic\2024-07\Ori\8d49f1cbf2ec77ed963e208d90962fa2.png)

剩下的5a条件

![img](file:///C:\Users\LGX_MATE_BOOK\Documents\Tencent Files\474015788\nt_qq\nt_data\Pic\2024-07\Ori\d1ca188dec43a5ae81c60cc000421ead.png)

![img](file:///C:\Users\LGX_MATE_BOOK\Documents\Tencent Files\474015788\nt_qq\nt_data\Pic\2024-07\Ori\8331088796c930577bf49e0077dd6bac.png)

用ARAP做regularization，由于ARAP能量也是非凸的，所以做如下凸化

![img](file:///C:\Users\LGX_MATE_BOOK\Documents\Tencent Files\474015788\nt_qq\nt_data\Pic\2024-07\Ori\830c77382dcc51312e52a70d2f9e52be.png)



综合上面凸化的结果，利用Active Set方法，则可以得到如下表达式

（注意这里采样了三个集合 M，A, B）

![img](file:///C:\Users\LGX_MATE_BOOK\Documents\Tencent Files\474015788\nt_qq\nt_data\Pic\2024-07\Ori\3978f83c5a46da54e36cf65b40a32e12.png)

离散化后的能量

![img](file:///C:\Users\LGX_MATE_BOOK\Documents\Tencent Files\474015788\nt_qq\nt_data\Pic\2024-07\Ori\3d821f78efd5a974e202679066cf15d1.png)

对于conformal Mapping可以更进一步简化

![img](file:///C:\Users\LGX_MATE_BOOK\Documents\Tencent Files\474015788\nt_qq\nt_data\Pic\2024-07\Ori\31bc9f3fc15b53201d2be6cee54ecb30.png)

计算细节

![img](file:///C:\Users\LGX_MATE_BOOK\Documents\Tencent Files\474015788\nt_qq\nt_data\Pic\2024-07\Ori\5b46740096272510318004b9e18226da.png)

另外注意到的是这里用到了三个active set，这三个set如何添加

![img](file:///C:\Users\LGX_MATE_BOOK\Documents\Tencent Files\474015788\nt_qq\nt_data\Pic\2024-07\Ori\815ab12449ac6fe0bb5b94fb5d98df44.png)

上面的优化这是针对边界上的个别的点，为了能推广到整个边界上（注意利用Thereom 4的定义）

![img](file:///C:\Users\LGX_MATE_BOOK\Documents\Tencent Files\474015788\nt_qq\nt_data\Pic\2024-07\Ori\3d488c2281c1da5eb875c978f3bf49ea.png)

利用之前uniform采样的B集，如何计算各最值

![img](file:///C:\Users\LGX_MATE_BOOK\Documents\Tencent Files\474015788\nt_qq\nt_data\Pic\2024-07\Ori\0727a8e7112236a51dc4f82c385cfba1.png)

利用Lipschitz性，转化为两个端点值和Liphischitz常数的表达

![img](file:///C:\Users\LGX_MATE_BOOK\Documents\Tencent Files\474015788\nt_qq\nt_data\Pic\2024-07\Ori\7cfa5e20ccc6041b5476e8064e9ad597.png)

如何计算Liphsthiz常数

![img](file:///C:\Users\LGX_MATE_BOOK\Documents\Tencent Files\474015788\nt_qq\nt_data\Pic\2024-07\Ori\7b73ae66c1f199857e7ba022857d5e7d.png)

![img](file:///C:\Users\LGX_MATE_BOOK\Documents\Tencent Files\474015788\nt_qq\nt_data\Pic\2024-07\Ori\155fc608f007641a5ceb2206b9216c2a.png)