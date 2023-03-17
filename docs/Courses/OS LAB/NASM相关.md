# 基本用法
nasm -f \<format\>\<filename> \[-o \<output\>\]
默认格式为纯二进制bin，可以用-f指定为elf等

# 关键字$ and \$\$
- 显式标号
```
code_start:
	mov ax, 0
```
$指本行，\$\$指本section
```
code_start:
	jmp $
	;等价于jmp code_start
```

# 逻辑分段section
```
section data 
	var dd 0 
section code 
	jmp start
```
用于规划程序，与segment有区别，最后取决于nasm的物理规划

# vstart=xxx修饰
影响编译器安排地址，在规划代码时按照xxx为起点开始。
加载器需要保证程序被正确加载到相应位置（与编译无关）


















