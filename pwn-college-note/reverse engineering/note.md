#####################
Yan85

esi   reg

edx   imm_value

初始化寄存器:b c a

a(储存返回值)
b(地址寄存器)
c(次数寄存器)
d()
s(执行push,+1/执行pop,-1)
i(rip)
f(标志寄存器)

指令:
IMM  reg(esi)=val(edx)
SYS  
STM  addr_reg(esi)=val(edx)
ADD  reg1(esi),reg2(edx)
LDM  reg(esi)=addr_reg(edx)
STK  reg NONE==pop reg
STK  NONE reg==push reg
STK  reg1 reg2==push reg2;pop reg1

函数偏移:
IMM 0x2e7
ADD 0x31c
STM 0x43b
LDM 0x49a
SYS 0x64a
CMP 0x4f1


#####################
level 9
通过输入patch 条件跳转

level 10
patch jne to je

level 11.0
patch double jne to je

level 11.1
patch jne
patch jmp address

level 12.0/level 12.1
Yan 85架构
from pwn import *

context.log_level="debug"

p=process(["/challenge/babyrev_level12.0"])

payload=b'\x39\xf3\x53\xa6\x91\xc0'
p.sendline(payload)

p.interactive()

level 13.0/level 13.1
多了CMP指令

level 14.0
from pwn import *

#context.log_level="debug"

p=process(["/challenge/babyrev_level14.0"])
desstr="30febc4e9e5006eb9c6f9bf9"
addstr="7b917106806731d8d8c7bd56"
t1=bytearray.fromhex(desstr)
t2=bytearray.fromhex(addstr)

t3=list(t1)
t4=list(t2)
in_list=[]
for i in range(len(t3)):
    v1=0x100+t3[i]
    v2=v1-t4[i]
    v2=v2&0xff
    in_list.append(hex(v2))
in_str=""
for i in range(len(in_list)):
    t_str=str(in_list[i])
    print(t_str[2:])
    in_str+=(t_str[2:])
print(in_str)

payload=bytearray.fromhex(in_str)
p.sendline(payload)

p.interactive()

level 15.0
from pwn import *

#context.log_level="debug"

p=process(["/challenge/babyrev_level15.0"])
desstr="29ae478c7f18"
addstr="733f0ab06ae0"
t1=bytearray.fromhex(desstr)
t2=bytearray.fromhex(addstr)

t3=list(t1)
t4=list(t2)
in_list=[]
for i in range(len(t3)):
    v1=t3[i]
    v2=v1+t4[i]
    v2=v2&0xff
    in_list.append(hex(v2))
in_str=""
for i in range(len(in_list)):
    t_str=str(in_list[i])
    print(t_str[2:])
    in_str+=(t_str[2:])
print(in_str)

payload=bytearray.fromhex(in_str)
p.sendline(payload)

p.interactive()

level 16.1
虚拟机形式
vmcode 2 asm python script:

    a="02b902010201010200010800011000010010010008010002020901023002027a08020c1002022004012001200002a301020010081020021620102002028620102014020108040408024320012000024f20012000025220012000025220012000024520012000024320012000025420012000022120012000022020012000025920012000026f20012000027520012000027220012000022020012000026620012000026c20012000026120012000026720012000023a20012000020a20012000021410020102202020022f20028010402010026620028110402010026c2002821040201002612002831040201002672002841040201002002002851040201002800202000820200402000804040802ff10020002042002202010020008040408020010042010020102202020020002200002010200010800011000020108040408024b20012000024520012000025920012000023a20012000022020012000020510020102202020010010010008010002010200010800011000023008020e10020002202010010010010008010002020201020108040408024920012000024e20012000024320012000024f20012000025220012000025220012000024520012000024320012000025420012000022120012000020a20012000020b1002010220202002010220000204100204100802ff2004200204200801020001080080020280080808080201000801000202b72010200102ff2004201002002008201002a52010200101102001000102b320027810402010022920027910402010020220027a1040201002e320027b10402010026a20027c10402010023d20027d10402010027420027e10402010026f20027f10402010023a2002801040201002182002811040201002c02002821040201002bc20028310402010028420028410402010022c20028510402010026601"
    code=[]
    for i in range(0,len(a),6):
        print(i,a[i:i+6])
        code.append(a[i:i+6])
    '''
    a:0x02
    b:0x08
    c:0x10
    d:0x20
    i:0x01
    '''

    def val_t_reg(val_str):
        val=int(val_str,16)
        res=""
        if val==0x02:
            res+="a"
        elif val==0x08:
            res+="b"
        elif val==0x10:
            res+="c"
        elif val==0x20:
            res+="d"
        elif val==0x01:
            res+="i"

        return res

    for i in range(len(code)):
        asm=""
        #imm
        if(code[i][0:2])=="02":
            #print("imm")
            imm_val="0x"+code[i][2:4]
            reg=val_t_reg("0x"+code[i][4:6])
            asm+="imm "+reg+" "+imm_val
            print(asm)
        #add
        if(code[i][0:2])=="04":
            #print("add")
            add_reg=val_t_reg("0x"+code[i][4:6])
            reg=val_t_reg("0x"+code[i][2:4])
            asm+="add "+add_reg+" "+reg
            print(asm)
        #stk
        if(code[i][0:2])=="01":
            #print("stk")
            if(code[i][2:4]=="00"):
                #pop
                reg=val_t_reg("0x"+code[i][4:6])
                asm+="pop "+reg
            else:
                #push
                reg=val_t_reg("0x"+code[i][2:4])
                asm+="push "+reg
            print(asm)
        #stm
        if(code[i][0:2])=="40":
            #print("stm")
            add_reg=val_t_reg("0x"+code[i][4:6])
            reg=val_t_reg("0x"+code[i][2:4])
            asm+="stm *"+add_reg+" = "+reg
            print(asm)
        #ldm
        if(code[i][0:2])=="80":
            add_reg=val_t_reg("0x"+code[i][4:6])
            reg=val_t_reg("0x"+code[i][2:4])
            asm+="ldm "+reg+" = *"+add_reg
            print(asm)
            #print("ldm")
        #cmp
        if(code[i][0:2])=="08":
            #print("cmp")
            reg1=val_t_reg(code[i][2:4])
            reg2=val_t_reg(code[i][4:6])
            asm+="cmp "+reg2+" "+reg1
            print(asm)
        #jmp
        if(code[i][0:2])=="10":
            #print("jmp")
            reg=val_t_reg(code[i][2:4])
            stat="0x"+code[i][4:6]
            asm+="jmp "+stat+" "+reg
            print(asm)
        #sys
        if(code[i][0:2])=="20":
            #print("sys")
            reg=val_t_reg(code[i][2:4])
            stat="0x"+code[i][4:6]
            asm+="sys "+stat+" "+reg
            print(asm)

还需要根据实际gdb来获取对比的值。

level 17.1

    a="7b0180ac20802001200108019701801c2080010280401004c20280000180400204000180040110ff20800002804002104008040001800401100020804020100102804010040002800001040200080100082000083002804a2080020101200110010220310280c920800201012001100102203202801120800201012001100102203302808d20800201012001100102203402809c2080020101200110010220350280a52080020101200110010220360280d92080020101200110010220370280102080020101200110010220380280c42080020101200110010220390280ca20800201012001100102203a0280c720800201012001100102203b0280c320800201012001100102203c02804320800201012001100102203d0280f920800201012001100102203e02806420800201012001100102203f0280c12080020101200110010220400280cc2080020101200110010220410280bf2080020101200110010220420280302080020101200110010220430280e720800201012001100102204402802320800201012001100102200020080001080002089f0880200210200110ff40804002104001100200080100080202010101010102400001080002089d4080400202ff40804020100040804020408b4080400202204008000808300280820180152080024080084010400008890880002080204040044080400102bb4080400c02bd01800520800102804010040200080100082000083001801b2080000280400804002008000108000208190880b301800a2080010280401004010280000104"
    code=[]
    for i in range(0,len(a),6):
        #print(i,a[i:i+6])
        code.append(a[i:i+6])
    '''
    a:0x02
    b:0x01
    c:0x20
    d:0x40
    s:0x04
    i:0x08
    '''
    op_code1=4
    op_code2=6

    reg1_1=0
    reg1_2=2

    reg2_1=2
    reg2_2=4

    def val_t_reg(val_str):
        val=int(val_str,16)
        res=""
        if val==0x02:
            res+="a"
        elif val==0x01:
            res+="b"
        elif val==0x20:
            res+="c"
        elif val==0x40:
            res+="d"
        elif val==0x08:
            res+="i"
        elif val==0x04:
            res+="s"

        return res

    for i in range(len(code)):
        asm=""
        #imm
        if(code[i][op_code1:op_code2])=="80":
            #print("imm")
            imm_val="0x"+code[i][reg1_1:reg1_2]
            reg=val_t_reg("0x"+code[i][reg2_1:reg2_2])
            asm+="imm "+reg+" "+imm_val
            print(asm)
        #add
        if(code[i][op_code1:op_code2])=="10":
            #print("add")
            add_reg=val_t_reg("0x"+code[i][reg2_1:reg2_2])
            reg=val_t_reg("0x"+code[i][reg1_1:reg1_2])
            asm+="add "+add_reg+" "+reg
            print(asm)
        #stk
        if(code[i][op_code1:op_code2])=="08":
            #print("stk")
            if(code[i][reg1_1:reg1_2]=="00"):
                #pop
                reg=val_t_reg("0x"+code[i][reg2_1:reg2_2])
                asm+="pop "+reg
            else:
                #push
                reg=val_t_reg("0x"+code[i][reg1_1:reg1_2])
                asm+="push "+reg
            print(asm)
        #stm
        if(code[i][op_code1:op_code2])=="20":
            #print("stm")
            add_reg=val_t_reg("0x"+code[i][reg2_1:reg2_2])
            reg=val_t_reg("0x"+code[i][reg1_1:reg1_2])
            asm+="stm *"+add_reg+" = "+reg
            print(asm)
        #ldm
        if(code[i][op_code1:op_code2])=="01":
            add_reg=val_t_reg("0x"+code[i][reg1_1:reg1_2])
            reg=val_t_reg("0x"+code[i][reg2_1:reg2_2])
            asm+="ldm "+reg+" = *"+add_reg
            print(asm)
            #print("ldm")
        #cmp
        if(code[i][op_code1:op_code2])=="40":
            #print("cmp")
            reg1=val_t_reg(code[i][reg2_1:reg2_2])
            reg2=val_t_reg(code[i][reg1_1:reg1_2])
            asm+="cmp "+reg2+" "+reg1
            print(asm)
        #jmp
        if(code[i][op_code1:op_code2])=="02":
            #print("jmp")
            reg=val_t_reg(code[i][reg1_1:reg1_2])
            stat="0x"+code[i][reg2_1:reg2_2]
            asm+="jmp "+stat+" "+reg
            print(asm)
        #sys
        if(code[i][op_code1:op_code2])=="04":
            #print("sys")
            reg=val_t_reg(code[i][reg1_1:reg1_2])
            stat="0x"+code[i][reg2_1:reg2_2]
            asm+="sys "+stat+" "+reg
            print(asm)


from pwn import *

#context.log_level="debug"

p=process(["/challenge/babyrev_level17.1"])
desstr="f7db3b90cf1a16ff9bf60a58fd3d79f41276b135a1"
addstr="4ac9118d9ca5d910c4cac7c343f964c1ccbf30e723"

t1=bytearray.fromhex(desstr)
t2=bytearray.fromhex(addstr)

t3=list(t1)
t4=list(t2)
in_list=[]
for i in range(len(t3)):
    v1=0x100+t3[i]
    v2=v1-t4[i]
    v2=v2&0xff
    in_list.append(hex(v2))
in_str=""
for i in range(len(in_list)):
    t_str=str(in_list[i])
    print(t_str[2:])
    in_str+=(t_str[2:])
print(in_str)
in_str="ad122a0333753defd72c4395ba44153346b7814e7e"

payload=bytearray.fromhex(in_str)
p.sendline(payload)

p.interactive()

可根据read_register来确定寄存器的代表值。
字符串输出不再把字符压入栈中，使用字符串的地址。

level 18
orw_1:
imm a 0xc2  "/flag" offset
imm b 0x00
sys 0x02 d  #open
imm b 0x00
add b 
imm c 0xff
imm a 0x00
add a d
sys 0x08 d  #read
imm b 0x00
add b 
imm c 0x00
add c d
imm a 0x01
sys 0x10 d  #write

orw_2:
imm d 0x2f
imm c 0x80
stm *c = d
imm d 0x66
imm c 0x81
stm *c = d
imm d 0x6c
imm c 0x82
stm *c = d
imm d 0x61
imm c 0x83
stm *c = d
imm d 0x67
imm c 0x84
stm *c = d
imm d 0x00
imm c 0x85
stm *c = d
imm a 0x80
imm b 0x00
sys 0x04 d  #open
imm b 0x00
add b s
imm c 0xff
imm a 0x00
add a d
sys 0x10 d  #read
imm b 0x00
add b s
imm c 0x00
add c d
imm a 0x01
sys 0x20 d  #write
把汇编指令转为二进制码即可

level 19.0
fuzz出需要的信息

level 19.1
