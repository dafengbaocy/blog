![image-20231016114050764](D:\code\web\blog\eecs151\img\image-20231016114050764.png)

## CORE

由上一节学到的锁存器的强化状态的方法，将锁存器的值放在1中得到5Tcell 

![image-20231016114236822](D:\code\web\blog\eecs151\img\image-20231016114236822.png)

但是：

1. 存取晶体管必须能够压倒反馈；因此必须很大
2.  较容易写入 0，较难写入 1 (Vdd-Vth)

解决：在另一边加入输入的反，6Tcell

![image-20231016114815694](D:\code\web\blog\eecs151\img\image-20231016114815694.png)

### 读写操作 

![image-20231016114856847](D:\code\web\blog\eecs151\img\image-20231016114856847.png)

sram的晶体管大小的选择 

![image-20231016114953088](D:\code\web\blog\eecs151\img\image-20231016114953088.png)

写入操作 

![image-20231016115018910](D:\code\web\blog\eecs151\img\image-20231016115018910.png)

## mem decoder 

就是多路复用器 

![image-20231016115120390](D:\code\web\blog\eecs151\img\image-20231016115120390.png)

但是造一个256位的多路复用器开销较大，因此，一般采用树形结构的二路复用器，

![image-20231016115209409](D:\code\web\blog\eecs151\img\image-20231016115209409.png)