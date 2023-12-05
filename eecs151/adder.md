## 单位全加器 

​	通过真值表，可以轻松构建逻辑组合电路

但引入两个新的参数：P和G

P和G的作用：

```
纹波进位加法器必须等待在获得结果之前要计算每个位对的进位。
而且P和G只与A和B有关
```

![image-20231016092849183](C:\Users\chen\AppData\Roaming\Typora\typora-user-images\image-20231016092849183.png)

## 纹波进位加法器 

![image-20231016093833608](C:\Users\chen\AppData\Roaming\Typora\typora-user-images\image-20231016093833608.png)

花费时间较长，因为关键路径永远是全加器的个数 

### 进位旁路加法器 

改进：当所有P=1时，即A和B仅有一位为1，那么C0和最终仅为就会一样 

![image-20231016094154756](C:\Users\chen\AppData\Roaming\Typora\typora-user-images\image-20231016094154756.png)

如果分进位数将其进行组合，那么：除了初始化和最终的结束阶段，中间对P的检查是可以并行化的，但是，时间复杂度仍然是O（n）线性复杂度

![image-20231016094240848](C:\Users\chen\AppData\Roaming\Typora\typora-user-images\image-20231016094240848.png)

## Carry-Lookahead Adder 

基本思想：如果我们将单位全加器的进位的逻辑表达式拆开来看：我们发现：进位其实一直都只与初始进位有关，中间的进位可以理解为一些wire，由c0生成。

![image-20231016094917812](C:\Users\chen\AppData\Roaming\Typora\typora-user-images\image-20231016094917812.png)

在进一步地，因为我们其实并不关心中间的进位是什么，所以，我们只需要算出最后的进位即可，由上图的递推表达式可以发现，

![image-20231016095923251](C:\Users\chen\AppData\Roaming\Typora\typora-user-images\image-20231016095923251.png)

最终可以将所有的P,Q综合起来 

![image-20231016095442728](C:\Users\chen\AppData\Roaming\Typora\typora-user-images\image-20231016095442728.png)

此外，由数学归纳法： 

![image-20231016095430362](C:\Users\chen\AppData\Roaming\Typora\typora-user-images\image-20231016095430362.png)

为了进一步提升并行化程度，可以采用树形结构 

![image-20231016095854352](C:\Users\chen\AppData\Roaming\Typora\typora-user-images\image-20231016095854352.png)

![image-20231016101726993](C:\Users\chen\AppData\Roaming\Typora\typora-user-images\image-20231016101726993.png)

这样的树形结够只是理想构思，因为sum位还没计算呢，真正的应用型往往更为复杂 

![image-20231016101833852](C:\Users\chen\AppData\Roaming\Typora\typora-user-images\image-20231016101833852.png)

![image-20231016101844559](C:\Users\chen\AppData\Roaming\Typora\typora-user-images\image-20231016101844559.png)