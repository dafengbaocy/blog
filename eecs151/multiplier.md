## basic

二进制乘法的基本逻辑其实和正常的十进制加法没什么区别，无非是进制数发生了改变 

![image-20231016102352986](C:\Users\chen\AppData\Roaming\Typora\typora-user-images\image-20231016102352986.png)

最正常的思路自然是把加法的思路代入乘法：

从个位开始，一位一位往上×，配合一个移位寄存器

![image-20231016102511010](C:\Users\chen\AppData\Roaming\Typora\typora-user-images\image-20231016102511010.png)

## 并行化 

如何并行化？简单思路就是把乘法的逻辑直接照搬就是并行化（每一行都可以并行化，只需要留意进位就可以了）

![image-20231016102818581](C:\Users\chen\AppData\Roaming\Typora\typora-user-images\image-20231016102818581.png)

但是，这个critical path还是有点长：全加器的个数就是他的critical path

### carry-save

所谓的carry-save，就是前文提到的进位保留与否问题，如果说之前的进位只是，wire，那么现在的进位就是reg了

好处是，我们不用管进位问题了，直接在最后在算进位就可以了

![image-20231016103902924](D:\code\web\blog\eecs151\img\image-20231016103902924.png)

![image-20231016104114084](D:\code\web\blog\eecs151\img\image-20231016104114084.png)

![image-20231016104438494](D:\code\web\blog\eecs151\img\image-20231016104438494.png)

### wallace tree 

你最终在哪里添加你的进位部分与sum部分是完全无所谓的，只要你把他添加了就可以，这就意味着，计算的顺序是可以被打乱的，因此，我门可以把原有的乘法样式进行改变 

![image-20231016104814733](D:\code\web\blog\eecs151\img\image-20231016104814733.png)

最终的电路逻辑图如图所示 

![image-20231016104910687](D:\code\web\blog\eecs151\img\image-20231016104910687.png)

## booth-recording

动机：我们平时做二进制乘法时，如果multipiler的某一位有一个0，那么其中的一行其实是完全可以省略的，现在就有这样的问题：如果能每次计算两位，那么计算量就能大大减小

![image-20231016105321803](D:\code\web\blog\eecs151\img\image-20231016105321803.png)

![image-20231016105405700](D:\code\web\blog\eecs151\img\image-20231016105405700.png)

## 有符号乘法 

因为由补码的规则，最高位是负号权重，因此，×出的最后一位的应该是－，而且需要进行符号位的扩展

![image-20231016112119761](D:\code\web\blog\eecs151\img\image-20231016112119761.png)

如此，会出现非常多的符号位

![image-20231016112349918](D:\code\web\blog\eecs151\img\image-20231016112349918.png)

如何解决？

只要在每个符号位加上一个1，就可以使原来的1全部消失 

![image-20231016112625759](D:\code\web\blog\eecs151\img\image-20231016112625759.png)