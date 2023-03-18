# CPU and memory contents

- xp /nuf \[phy_addr\]显示物理地址内容
 n 显示的单元数
 u 每个显示单元的大小： b 1字节； h 2字节； w 4字节；g 8字节。
 f 显示格式： x 按照十六进制显示；d 十进制显示；u 按照无符号十进制显示；o 按照八进制显示；t 按照二进制显示；c 按照字符显示；s 按照 ASCIIz 显示；i 按照 instr 显示。
- x /nuf \[line_addr\] 显示线性地址的内容
- setpmem \[phy_addr\] \[size\] \[val\] 设置以物理内存 phy_addr 为起始，连续 size 个字节的内容为 val。
- r|reg|regs|registers 显示 8 个通用寄存器的值+eflags 寄存器+eip 寄存器。
- print-stack \[num\] 显示堆栈，num 默认为 16，表示打印的栈条目数。
- info
 info break - show information about current breakpoint status
 info cpu - show dump of all cpu registers
 info idt - show interrupt descriptor table
 info ivt - show interrupt vector table
 info gdt - show global descriptor table
 info tss - show current task state segment
 info tab - show page tables
 info eflags - show decoded EFLAGS register
 info symbols \[string\] - list symbols whose prefix is string
 info device - show list of devices supported by this command
 info device \[string\] - show state of device specified in string
 info device \[string\] \[string\] - show state of device with options
- sreg 显示所有段寄存器的值。
- dreg 显示所有调试寄存器的值。
- creg 显示所有控制寄存器的值。
- page line_addr 显示线性地址到物理地址间的映射。

# Execution control

- c|cont|continue，向下持续执行。
- s|step \[count\] 执行 count 条指令，count 是指定单步执行的指令数，count 默认为 1。若遇到函数调用，则会进入函数中去执行。
- p|n|next 执行 1 条指令，若待执行的指令是函数调用，不管函数内有多少指令，把整个函数当作一个整体来执行。

# Breakpoint management

- vb|vbreak \[seg：off\] 以虚拟地址添加断点。
- lb|lbreak \[addr\] 以线性地址添加断点。
- pb|pbreak|b|break \[addr\] 以物理地址添加断点。
- sb \[delta\] 再执行 delta 条指令程序就中断。
- sba \[time\] CPU 从运行开始，执行第 time 条指令时中断。
- watch r|read \[phy_addr\] 设置读断点，如果物理地址 phy_addr 有读操作则停止运行。
- watch w|write \[phy_addr\] 设置写断点，如果物理地址 phy_addr 有写操作则停止运行。
- watch 显示所有读写断点。  
- unwatch \[phy_addr\] 清除在此地址上的读写断点，不指定清除所有。
- blist 显示所有断点信息，功能等同于 info b。
- bpd|bpe \[n\] 禁用断点（break point disable）/启用断点（break point enable），n 是断点号。
- d|del|delete \[n\] 删除某断点。

# Debugger control

- q|quit|exit 退出调试。
- set \[regname\] = expr 指定寄存器的值。
- set u on|off 停止执行时自动反汇编。
- show mode 每次 CPU 变换模式时提示。
- show int 每次有中断时就提示，细分为softint、extint 和 iret。
