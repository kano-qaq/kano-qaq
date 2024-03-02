level5 gdb script

commands
	silent
	set $a=*(unsigned long long*)($rbp-0x18)
	printf "val:%llx\n",$a
	continue
end
continue

level6

from pwn import *

p=process(["/challenge/embryogdb_level6"])
p.sendline("r")
p.sendline("b*main+686")
p.sendline("commands")
p.sendline("silent")
p.sendline("if($rax!=$rdx)")
p.sendline("set $rdx=*(unsigned long long*)($rbp-0x18)")
p.sendline("end")
p.sendline("continue")
p.sendline("end")
p.sendline("continue")
for i in range(0x40):
    p.sendlineafter("Random value:","1234")
p.interactive()

level 7
call (void)win()
直接执行函数
