## 笔记

### 从 c 源码到可执行二进制

- gcc hello_world.c -E -o hello_world.i 预处理：加入头文件，替换宏。
- gcc hello_world.c -S -c hello_world.s 编译：包含预处理，将 C 程序转换成汇编程序。
- gcc hello_world.c -c hello_world.o 汇编：包含预处理和编译，将汇编程序转换成可链接的二进制程序。
- gcc hello_world.c -o hello_world 链接：包含以上所有操作，将可链接的二进制程序和其它别的库链接在一起，形成可执行的程序文件。

### dump 文件

`objdump -d hello_world >> hello_world.dump` 可以反汇编的二进制文件，得到`hello_world.dump`。

- 第一列为地址
- 第二列为十六进制，表示真正装入机器中的代码数据
- 第三列是对应的汇编代码
- 第四列是相关代码的注释

## 思考

为了实现 C 语言中函数的调用和返回功能，CPU 实现了函数调用和返回指令，即上图汇编代码中的“call”，“ret”指令，请你思考一下：call 和 ret 指令在逻辑上执行的操作是怎样的呢？

`call`: 实际上就是跳转到某个内存地址并执行相应的程序
`ret`: 从某个内存地址返回到进入之前的内存地址
