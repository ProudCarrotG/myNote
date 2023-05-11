# 线性代数

-----

## 行列式

### 排列的逆序数

-   逆序：排列中，每一个数字的前面，比这个数字大的数的**个数**，为这一个数的逆序

-   逆序数：逆序中每一个数的和

![image-20230510212920300](https://raw.githubusercontent.com/ProudCarrotG/tuChuang/main/image-20230510212920300.png)

-   通过逆序计算行列式的一项的符号

分别计算行排列的逆序数$t_1$和列排列的逆序数$t_2$，将逆序数相加得$t$，符号值为$(-1)^t$

![image-20230510213258074](https://raw.githubusercontent.com/ProudCarrotG/tuChuang/main/image-20230510213258074.png)

### 行列式的计算

#### 行列式的性质

1.   互换行(列), 要变号

![image-20230510213620551](https://raw.githubusercontent.com/ProudCarrotG/tuChuang/main/image-20230510213601347.png)这里互换了`r1`和`r2`

2.   提公因子, 可以提行的也可以提列的

![image-20230510213808198](https://raw.githubusercontent.com/ProudCarrotG/tuChuang/main/image-20230510213808198.png)

3.   倍加 可以将一行(列)中的所有元素加到另一行(列)的元素中, 行列式的值不变

![image-20230510213936835](https://raw.githubusercontent.com/ProudCarrotG/tuChuang/main/image-20230510213936835.png)

4.   拆分 对一行或一列拆分, 原行列式的值等于拆分出来的行列式的和

![image-20230510214011238](https://raw.githubusercontent.com/ProudCarrotG/tuChuang/main/image-20230510214011238.png)

5.   对应成比例, 值为零. 某一行元素的值都是另一行的元素的相同倍数, 则行列式值为0

     ![image-20230510214204232](https://raw.githubusercontent.com/ProudCarrotG/tuChuang/main/image-20230510214201464.png)

#### 计算

1.   二阶行列式

     主对角线相乘减次对角线相乘

2.   其他行列式

     1.   上三角行列式

          1.   上三角行列式的变换:通过性质,将行列式中主对角线下方的数字变为0
          2.   公式: 

          ![image-20230510214413729](https://raw.githubusercontent.com/ProudCarrotG/tuChuang/main/image-20230510214413729.png)

          3.   计算过程:

               1.   通解:

                    1.   从主对角线的第一个位置开始, 即$a_{11} -> a_{22} -> ....$

                    2.   将主对角线一个元素下的元素, 通过倍加的性质全变为0, 一次变换一个元素, 用变换元素的行减去对角线元素的行

                         1.   >   这样做的好处是可以一次变换一个元素, 并且不会影响后面元素的变换, 单过程繁杂, 一次只变换一个元素

                    3.   直到形成上三角行列式

                    4.   技巧:

                         1.   当对角线元素与下面元素不成正比关系时, 要计算分数比较困难, 所以可以通过**性质一:互换行列变号**的方式, 将合适的元素替换, 达到避免计算分数的效果
                         2.   利用性质**提公因子**的性质,可以将行列式中的数字尽可能地减小, 方便计算
                         3.   ![image-20230510220211722](https://raw.githubusercontent.com/ProudCarrotG/tuChuang/main/image-20230510220211722.png)![image-20230510220219979](https://raw.githubusercontent.com/ProudCarrotG/tuChuang/main/image-20230510220219979.png)[]()
                         4.   箭型行列式:![image-20230510220259270](https://raw.githubusercontent.com/ProudCarrotG/tuChuang/main/image-20230510220259270.png)使用列于列相减的方法化简成上三角形行列式

### 行列式的展开

1.   余子式记作$M_{ij}$:去掉$a_{ij}$所在的行与列. 求余子式时需要将行列式的值计算出来

>   $a_{ij}$为行列式的第`i`行第`j`列的元素

2.   代数余子式 $A_{ij} = (-1)^{i+j}M_{ij}$

3.   行列式展开公式

     1.   按照第`i`行展开公式
     $$
     \begin{align}
          D = a_{i1}A_{i1} + a_{i2}A_{i2}+...+a_{in}A_{in}  \tag{i=1,2,3,...n}
          \end{align}
     $$

     2.   按照第`j`列展开公式

     $$
     \begin{align}
     D = a_{1j}A_{1j} + a_{2j}A_{2j}+...+a_{nj}A_{nj} \tag{j=1,2,3,...n}
     \end{align}
     $$

4.   定理：

     1.   某行（列）元素与另一行（列）的代数余子式之积相加等于`0`

5.   技巧

     1.   算式中若包含行列式的某一行(列)的全部代数余子式$A_{ij}$时, 可以将其对应代数余子式的元素替换为其系数, 得到的新行列式的值与原式相等

        

     ![image-20230511234303153](https://raw.githubusercontent.com/ProudCarrotG/tuChuang/main/image-20230511234303153.png)![image-20230511234235268](https://raw.githubusercontent.com/ProudCarrotG/tuChuang/main/image-20230511234235268.png)

     ​	2. 算式中包含行列式的某一行(列)的全部余子式$M_{ij}$, 可以将通过公式转换成代数余子式$A_{ij}$, 然后利用技巧1计算

     ​     

6.   范德蒙行列式

![image-20230511235150117](https://raw.githubusercontent.com/ProudCarrotG/tuChuang/main/image-20230511235150117.png)
