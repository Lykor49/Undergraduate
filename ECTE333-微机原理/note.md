# 微机原理 英文版

## Lecture 1 – Introduction to AVR Microcontrollers

1. Development cycle for C
- Step1: Creating Atmel Studio project: project name; project type C; select device
- Step2: Entering a C program
- Step3: Compiling the C program to produce a HEX file
- Step4: Downloading / Testing the HEX file on Atmel AVR microcontroller


## Lecture 2 - C Programming, Digital IO

### 2.1 Structure of a C program C语言程序的结构
1. C program has two main sections
- Section #include: to insert header files 插入头文件
- Section main(): code that runs when the program starts 程序启动时运行的代码

2. The role of the header file <avr/io.h> in a C program
- contains all register definitions for the selected AVR microcontroller 包含所选AVR微控制器中的所有寄存器定义

3. C comment 注释 / C instruction 指令 / C block 区块

4. Inserting assembly code into a C program 将汇编代码插入C语言程序中
- asm("assembly instructions"); 使用 asm 指令将汇编代码插入C语言程序中
- asm volatile("nop"); creates a delay of one clock cycle 创建一个一时钟周期的延迟
- volatile 用于防止编译器删除C语言指令

### 2.2 Data types and operators 数据类型和运算符
1. Data types 数据类型
char               8 bits    - 2^7 ~ 2^7 - 1 
int                16 bits   - 2^15 ~ 2^15 - 1
long int           32 bits   - 2^31 ~ 2^31 - 1
unsigned char      8 bits      0 ~ 2^8 - 1 
unsigned int       16 bits     0 ~ 2^16 - 1
unsigned long int  32 bits     0 ~ 2^32 - 1

0xA0 16进制
0b11110000 2进制
‘1’ ASCII表
2000ul 无符号的2000整数

2. C operators 运算符
- Arithmetic operators 算术运算符
- Relational operators 关系运算符
- Logical operators 逻辑运算符
- Bit-wise operators 位运算符
- Data access operators 数据访问运算符
- Miscellaneous operators 其他关系运算符

### 2.3 Flow control in C C 语言中的流控制
6 种指令类型
Conditional 条件: if-else / switch
Iterative 循环: while / for / do
goto

1. State the roles of 'break' and 'default' in the C 'switch-case' construct.
答: Use 'break' to separate different cases; Use 'default' for all other cases.

2. State the roles of 'break' / 'continue' in loop
答: The 'break' instruction inside a loop forces early termination of the loop.
The 'continue' instruction skips the subsequent instructions in the code block, and forces the execution of the next iteration.


### 2.4 C functions

### 2.5 Digital IO in ATmega16 数字IO口
ATmega16 has fours 8-bit digital IO ports
PORT A; PORT B; PORT C; PORT D
每个PORT有8个引脚, 每个IO口都可以用于输入或输出

1. Configuring for input / ouput  配置输入 / 输出设置
- Data Direction Register (DDRx) 数据方向寄存器: decides a pin is output(1) or input (0)
- Data Register (PORTx) 数据寄存器: is used to write output data to port
- Input Pins Address (PINx) 端口输入引脚: is used to read input data from port





