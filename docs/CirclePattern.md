Circle Pattern:

对于曲面间的共形映射，共形可以通过如下方式来解释：对于每个点其周边的圆域映射到曲面的圆域中。也就是每个点的小圆盘映射到一个同样的一个小圆盘中。这样就可以得到一种逼近共形映射的方式：通过保持三角网格圆盘的一致性。

首先想到的自然是每个顶点赋予一个圆盘，通过映射保持每个点的圆盘，从而逼近一个共形映射。但是这个方法只考虑到曲面的拓扑特征（点之间的连接）并没有考虑到曲面的几何特征。如果要考虑到曲面的几何特征的话，将每个三角面作为一个基本的元素。通过保持每个三角面的外接圆来拟合三角面。三角面的外接圆之间要保持交角不变。这样就能将求映射转化为一个最小化凸能量的问题

![image-20241129195848620](C:\Users\LGX_MATE_BOOK\AppData\Roaming\Typora\typora-user-images\image-20241129195848620.png)

Thurston提出的一个CirclePacking的猜想,离散化的共形性质可以通过Circle Packing的方式来实现

![image-20241129200603745](C:\Users\LGX_MATE_BOOK\AppData\Roaming\Typora\typora-user-images\image-20241129200603745.png)

不过纯粹的Circle Packing方法只是考虑到网格的组合性质（只是当作一个Graph来看）而没有考虑其几何性质

Circle Patterns主要考虑几何性质

![image-20241129201850514](C:\Users\LGX_MATE_BOOK\AppData\Roaming\Typora\typora-user-images\image-20241129201850514.png)

对于此种表示法，Bokeko等人最近也将其转化为求一个凸能量的最小值

![image-20241129202001225](C:\Users\LGX_MATE_BOOK\AppData\Roaming\Typora\typora-user-images\image-20241129202001225.png)

![image-20241129202409478](C:\Users\LGX_MATE_BOOK\AppData\Roaming\Typora\typora-user-images\image-20241129202409478.png)

这个工作也主要是基于Bokeno的

![image-20241129205735996](C:\Users\LGX_MATE_BOOK\AppData\Roaming\Typora\typora-user-images\image-20241129205735996.png)





相关工作：

![image-20241129203043390](C:\Users\LGX_MATE_BOOK\AppData\Roaming\Typora\typora-user-images\image-20241129203043390.png)

conformal 特性保证了Circle交角的不变性，在欧式几何中三角形是基本的building block，但是对于conformal geometry，则building block就是圆了。

![image-20241129204217964](C:\Users\LGX_MATE_BOOK\AppData\Roaming\Typora\typora-user-images\image-20241129204217964.png)

![image-20241129203251062](C:\Users\LGX_MATE_BOOK\AppData\Roaming\Typora\typora-user-images\image-20241129203251062.png)

一个Circle Patterns求解的问题即可分解为求解Coherent Angle System问题

![image-20241201134719394](C:\Users\LGX_MATE_BOOK\AppData\Roaming\Typora\typora-user-images\image-20241201134719394.png)、



用Circle Patterns来求共形映射需要做两阶段的非线性优化，第一阶段求Coherent Angle System，第二阶段基于theta_e通过能量最小化求radii

第一个优化问题

![image-20241201132302957](C:\Users\LGX_MATE_BOOK\AppData\Roaming\Typora\typora-user-images\image-20241201132302957.png)

第二个优化：S(1o)是半径的对数值

![image-20241201134811707](C:\Users\LGX_MATE_BOOK\AppData\Roaming\Typora\typora-user-images\image-20241201134811707.png)