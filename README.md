# my_math

#### 原始开源库链接
https://gitee.com/jasonakzhang/my_math

#### 介绍
查表法实现数学库中的常见函数。包含sin，cos，tan，asin，acos，atan，atan2，sqrt，pow。(sqrt，pow不是查表法)
在适中的表下以适中的效率实现适中精度，如生成的表步长为0.0001时，表文件大小为615KB，计算精度最差为小数后7位。在不严谨测试下，计算时间比math.h略长，在(1<<30)次随机值计算中查表法多了0.02秒。

#### 软件架构
c语言编写，没啥架构，新手都看得懂。本实现方法绝非最优。以下是有关程序实现的说明。
开方考虑到实际有时数据会很大，故暂不考虑用查表法，直接用牛顿逼近法。次方考虑到实际不会有负次幂，故没有做负次幂的功能。二分法查表是用于反三角函数查表使用。所有表都只有0到pi/2，通过对称性和诱导公式就可以求其它定义域的值。cos用诱导公式转为sin，可以节省cos_table的空间，asin和acos同理。tan的表和sin的表不同，虽然能用诱导公式转换为sin和cos表示，但atan需要tan表，且atan2用得多，故单独开一个tan表保证效率。

#### 安装教程
1. 将my_math.c和my_math.h放入工程中。
2. 使用create_math_table生成查找表my_math_table.h，把表文件放入工程中。在运行my_math_create.exe后会输入一个步长值，这个值越小精度越高，但同时占用的空间也就越大，请根据实际情况设定步长。这里预先编译好了Windows平台的exe文件可以直接运行，如果您是其他平台，可以通过create_math_table.c编译运行。请保持输入的步长值和my_math.h中的TABLE_STEP一致。

#### 使用说明
1. 在工程中包含my_math.h，即可使用其中声明的函数，使用方法与math.h一致。例如想计算sin(value)，就可以用sin_lookup(value)。

#### 参与贡献
1.  我
2.  各路AI
3.  各开源项目

#### 特技
1.  没啥特技

#### 其它，都是和程序无关的话
本工程开发背景：
鄙人是臭打智能车的，打的越野，用的英飞凌TC芯片，在优化时程序时发现如果上了双精度浮点的话fpu就用不了，也就是数学函数都失效了没法计算，但双精度对于我们比较重要，毕竟单精度浮点连经纬度都没法稳定表示，在师兄和各群友的建议下还是编写一个自己的数学库方便用。当时正值新年放假前夕，刚好写个数学库也不用单片机待在身边，怕新年假期闲得无聊，就把写数学库这个任务放在新年假期搞咯。之前看说什么git是程序员的标配，就学了一下，学完了得有东西练手呀，唉正好和这个小项目结合一下，既能熟练git的使用，又能深入对工程的理解，还能推进一下小车的进度。

