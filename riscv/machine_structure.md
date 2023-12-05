### 

### logic design

#### 逻辑电路基础 

-  简单的逻辑门（与或非）
- MOS管中的N沟道 与P沟道 
  1. N沟道：G极低电平，开路 
  2. P沟道 
- 非门设计，与非门设计 
- 组合逻辑电路（e.g:半加器）
- circruit with state（寄存器，触发器？）

#### 状态机 

- 累加器搭建 
  1. 寄存器是由n个1位D触发器组成的 
  2.  上升沿触发（也存在下降沿触发）

- 状态的不稳定 

  使用了累加器来做例子，具体原因为：我们知道，电路元件的输入输出是有延迟的，比如采样延迟，加法延迟，如果在采样时，由于延迟的不断累积，采到了不稳定点，就会出现状态的不稳定。 

- pipeline
  1. 加法器的最大延迟： 
  2.  

- 有限状态机  

#### 组合逻辑电路 （无记忆，可以理解为函数 ）

- 真值表 
- 简化真值表 
- 逻辑计算规律 
- 逻辑表达式和真值表的转换 

#### 组合逻辑块

- 多路复用器 

![一位多路复用器](C:\Users\chen\AppData\Roaming\Typora\typora-user-images\image-20230921132207993.png)

- 如何实现更多路的复用呢？

  1. 分层 （半决赛和总决赛的逻辑 ）

  2. 真值表转换  

-  ALU  

![ALU](C:\Users\chen\AppData\Roaming\Typora\typora-user-images\image-20230921133620457.png)

在这种简单介绍中，ALU就是一种多路复用器的实例

- 深入理解：加法器与减法器 

  1. 先考虑一位的加法：输入：a，b；输出：s0，c（进位）

  2. 高位的加法 

     ![image-20230921134634468](C:\Users\chen\AppData\Roaming\Typora\typora-user-images\image-20230921134634468.png)

​			经过级联后，就成了：

![image-20230921134737489](C:\Users\chen\AppData\Roaming\Typora\typora-user-images\image-20230921134737489.png)

溢出：cn为1时，就说明数据流失了 

减法器 ：规律：减去b就相当于加上-b，

![image-20230921141013468](C:\Users\chen\AppData\Roaming\Typora\typora-user-images\image-20230921141013468.png)

当sub选择为0时，这是一个加法器 

当sub选择为1时，这是一个减法器，b先按位取反，然后再加1

#### CPU 

由datapath和processor组成（CPU）: 

- 指令执行的5步：

  Stage 1:Instruction Fetch (IF) 

  Stage 2:Instruction Decode (ID)

  Stage 3: Execute (EX) - ALU (Arithmetic-Logic Unit)

  Stage 4:Memory Access(MEM) 

  Stage 5: Write Back to Register (WB)  

two read and one write 

![image-20230921174130139](C:\Users\chen\AppData\Roaming\Typora\typora-user-images\image-20230921174130139.png)

注意：在此处，做读操作时，clk不起作用 

- datapath for add 
- ![image-20230924195651274](C:\Users\chen\AppData\Roaming\Typora\typora-user-images\image-20230924195651274.png)

值的更新将在下一个时钟周期进行 

- datapath for sub
- ![image-20230924195712123](C:\Users\chen\AppData\Roaming\Typora\typora-user-images\image-20230924195712123.png)

只需简单修改add就可以了 ，在alu处添加一个控制单元： 

- datapath for I-type 

相比于R-type，增加了一个imm控制器（B-sel），增加了一个imm生成器 

1.  imm-gen原理：

![IMMGEN](C:\Users\chen\AppData\Roaming\Typora\typora-user-images\image-20230921193619949.png)

- datapath for load

		1. 添加了一个DMEM用于取址，又添加了一个WBSel
		 ![image-20230924200058849](C:\Users\chen\AppData\Roaming\Typora\typora-user-images\image-20230924200058849.png)

- datapath for store （s-type）

和之前一样，大部分工作可以复用 

imm_gen中的标志位需要被正确设置 

REGWEN需要被设置为0 

现在的imm_gen需要添加一个选择器 

- datapath for branch(B-format) 

添加一个branchCOMP控件 

- **datapath for jal(J-format)** 

  ![image-20230924144212880](C:\Users\chen\AppData\Roaming\Typora\typora-user-images\image-20230924144212880.png)

  ![image-20230924144054669](C:\Users\chen\AppData\Roaming\Typora\typora-user-images\image-20230924144054669.png)

- DATAPATH for U-type 

![image-20230924143900875](C:\Users\chen\AppData\Roaming\Typora\typora-user-images\image-20230924143900875.png)

![image-20230924143938835](C:\Users\chen\AppData\Roaming\Typora\typora-user-images\image-20230924143938835.png)

#### 最终设计 control logic 

CSR (CONTROL and register CSR ) 

注意：CSR是独立于前面datapath的寄存器的

有两种形式：rs 或者imm数 

一些CSR指令的例子 

![image-20230924152652737](C:\Users\chen\AppData\Roaming\Typora\typora-user-images\image-20230924152652737.png)

1. control logic的本质：一堆布尔逻辑门控制datapath 

2. instruction timing ：木桶原则 

3. control logic design：

   如图的真值表：

   ![image-20230924161624367](C:\Users\chen\AppData\Roaming\Typora\typora-user-images\image-20230924161624367.png)

 		如何实现？
   1. ROM存真值表  

   2. 组合逻辑电路：只需9位，就可以确定指令类型进行解码 

      最终方式：通过对9位instruction解码，获得相关信息，设置布尔逻辑器

