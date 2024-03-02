
/challenge/babyrev_level17.1:     file format elf64-x86-64


Disassembly of section .init:

0000000000001000 <.init>:
    1000:   f3 0f 1e fa             endbr64 
    1004:   48 83 ec 08             sub    $0x8,%rsp
    1008:   48 8b 05 d9 2f 00 00    mov    0x2fd9(%rip),%rax        # 3fe8 <sleep@plt+0x2e78>
    100f:   48 85 c0                test   %rax,%rax
    1012:   74 02                   je     1016 <__cxa_finalize@plt-0xba>
    1014:   ff d0                   callq  *%rax
    1016:   48 83 c4 08             add    $0x8,%rsp
    101a:   c3                      retq   

Disassembly of section .plt:

0000000000001020 <.plt>:
    1020:   ff 35 52 2f 00 00       pushq  0x2f52(%rip)        # 3f78 <sleep@plt+0x2e08>
    1026:   f2 ff 25 53 2f 00 00    bnd jmpq *0x2f53(%rip)        # 3f80 <sleep@plt+0x2e10>
    102d:   0f 1f 00                nopl   (%rax)
    1030:   f3 0f 1e fa             endbr64 
    1034:   68 00 00 00 00          pushq  $0x0
    1039:   f2 e9 e1 ff ff ff       bnd jmpq 1020 <__cxa_finalize@plt-0xb0>
    103f:   90                      nop
    1040:   f3 0f 1e fa             endbr64 
    1044:   68 01 00 00 00          pushq  $0x1
    1049:   f2 e9 d1 ff ff ff       bnd jmpq 1020 <__cxa_finalize@plt-0xb0>
    104f:   90                      nop
    1050:   f3 0f 1e fa             endbr64 
    1054:   68 02 00 00 00          pushq  $0x2
    1059:   f2 e9 c1 ff ff ff       bnd jmpq 1020 <__cxa_finalize@plt-0xb0>
    105f:   90                      nop
    1060:   f3 0f 1e fa             endbr64 
    1064:   68 03 00 00 00          pushq  $0x3
    1069:   f2 e9 b1 ff ff ff       bnd jmpq 1020 <__cxa_finalize@plt-0xb0>
    106f:   90                      nop
    1070:   f3 0f 1e fa             endbr64 
    1074:   68 04 00 00 00          pushq  $0x4
    1079:   f2 e9 a1 ff ff ff       bnd jmpq 1020 <__cxa_finalize@plt-0xb0>
    107f:   90                      nop
    1080:   f3 0f 1e fa             endbr64 
    1084:   68 05 00 00 00          pushq  $0x5
    1089:   f2 e9 91 ff ff ff       bnd jmpq 1020 <__cxa_finalize@plt-0xb0>
    108f:   90                      nop
    1090:   f3 0f 1e fa             endbr64 
    1094:   68 06 00 00 00          pushq  $0x6
    1099:   f2 e9 81 ff ff ff       bnd jmpq 1020 <__cxa_finalize@plt-0xb0>
    109f:   90                      nop
    10a0:   f3 0f 1e fa             endbr64 
    10a4:   68 07 00 00 00          pushq  $0x7
    10a9:   f2 e9 71 ff ff ff       bnd jmpq 1020 <__cxa_finalize@plt-0xb0>
    10af:   90                      nop
    10b0:   f3 0f 1e fa             endbr64 
    10b4:   68 08 00 00 00          pushq  $0x8
    10b9:   f2 e9 61 ff ff ff       bnd jmpq 1020 <__cxa_finalize@plt-0xb0>
    10bf:   90                      nop
    10c0:   f3 0f 1e fa             endbr64 
    10c4:   68 09 00 00 00          pushq  $0x9
    10c9:   f2 e9 51 ff ff ff       bnd jmpq 1020 <__cxa_finalize@plt-0xb0>
    10cf:   90                      nop

Disassembly of section .plt.got:

00000000000010d0 <__cxa_finalize@plt>:
    10d0:   f3 0f 1e fa             endbr64 
    10d4:   f2 ff 25 1d 2f 00 00    bnd jmpq *0x2f1d(%rip)        # 3ff8 <sleep@plt+0x2e88>
    10db:   0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

Disassembly of section .plt.sec:

00000000000010e0 <puts@plt>:
    10e0:   f3 0f 1e fa             endbr64 
    10e4:   f2 ff 25 9d 2e 00 00    bnd jmpq *0x2e9d(%rip)        # 3f88 <sleep@plt+0x2e18>
    10eb:   0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

00000000000010f0 <write@plt>:
    10f0:   f3 0f 1e fa             endbr64 
    10f4:   f2 ff 25 95 2e 00 00    bnd jmpq *0x2e95(%rip)        # 3f90 <sleep@plt+0x2e20>
    10fb:   0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

0000000000001100 <__stack_chk_fail@plt>:
    1100:   f3 0f 1e fa             endbr64 
    1104:   f2 ff 25 8d 2e 00 00    bnd jmpq *0x2e8d(%rip)        # 3f98 <sleep@plt+0x2e28>
    110b:   0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

0000000000001110 <printf@plt>:
    1110:   f3 0f 1e fa             endbr64 
    1114:   f2 ff 25 85 2e 00 00    bnd jmpq *0x2e85(%rip)        # 3fa0 <sleep@plt+0x2e30>
    111b:   0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

0000000000001120 <read@plt>:
    1120:   f3 0f 1e fa             endbr64 
    1124:   f2 ff 25 7d 2e 00 00    bnd jmpq *0x2e7d(%rip)        # 3fa8 <sleep@plt+0x2e38>
    112b:   0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

0000000000001130 <memcpy@plt>:
    1130:   f3 0f 1e fa             endbr64 
    1134:   f2 ff 25 75 2e 00 00    bnd jmpq *0x2e75(%rip)        # 3fb0 <sleep@plt+0x2e40>
    113b:   0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

0000000000001140 <setvbuf@plt>:
    1140:   f3 0f 1e fa             endbr64 
    1144:   f2 ff 25 6d 2e 00 00    bnd jmpq *0x2e6d(%rip)        # 3fb8 <sleep@plt+0x2e48>
    114b:   0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

0000000000001150 <open@plt>:
    1150:   f3 0f 1e fa             endbr64 
    1154:   f2 ff 25 65 2e 00 00    bnd jmpq *0x2e65(%rip)        # 3fc0 <sleep@plt+0x2e50>
    115b:   0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

0000000000001160 <exit@plt>:
    1160:   f3 0f 1e fa             endbr64 
    1164:   f2 ff 25 5d 2e 00 00    bnd jmpq *0x2e5d(%rip)        # 3fc8 <sleep@plt+0x2e58>
    116b:   0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

0000000000001170 <sleep@plt>:
    1170:   f3 0f 1e fa             endbr64 
    1174:   f2 ff 25 55 2e 00 00    bnd jmpq *0x2e55(%rip)        # 3fd0 <sleep@plt+0x2e60>
    117b:   0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

Disassembly of section .text:

0000000000001180 <.text>:
    1180:   f3 0f 1e fa             endbr64 
    1184:   31 ed                   xor    %ebp,%ebp
    1186:   49 89 d1                mov    %rdx,%r9
    1189:   5e                      pop    %rsi
    118a:   48 89 e2                mov    %rsp,%rdx
    118d:   48 83 e4 f0             and    $0xfffffffffffffff0,%rsp
    1191:   50                      push   %rax
    1192:   54                      push   %rsp
    1193:   4c 8d 05 a6 0d 00 00    lea    0xda6(%rip),%r8        # 1f40 <sleep@plt+0xdd0>
    119a:   48 8d 0d 2f 0d 00 00    lea    0xd2f(%rip),%rcx        # 1ed0 <sleep@plt+0xd60>
    11a1:   48 8d 3d 4e 0a 00 00    lea    0xa4e(%rip),%rdi        # 1bf6 <sleep@plt+0xa86>
    11a8:   ff 15 32 2e 00 00       callq  *0x2e32(%rip)        # 3fe0 <sleep@plt+0x2e70>
    11ae:   f4                      hlt    
    11af:   90                      nop
    11b0:   48 8d 3d c9 31 00 00    lea    0x31c9(%rip),%rdi        # 4380 <stdout@@GLIBC_2.2.5>
    11b7:   48 8d 05 c2 31 00 00    lea    0x31c2(%rip),%rax        # 4380 <stdout@@GLIBC_2.2.5>
    11be:   48 39 f8                cmp    %rdi,%rax
    11c1:   74 15                   je     11d8 <sleep@plt+0x68>
    11c3:   48 8b 05 0e 2e 00 00    mov    0x2e0e(%rip),%rax        # 3fd8 <sleep@plt+0x2e68>
    11ca:   48 85 c0                test   %rax,%rax
    11cd:   74 09                   je     11d8 <sleep@plt+0x68>
    11cf:   ff e0                   jmpq   *%rax
    11d1:   0f 1f 80 00 00 00 00    nopl   0x0(%rax)
    11d8:   c3                      retq   
    11d9:   0f 1f 80 00 00 00 00    nopl   0x0(%rax)
    11e0:   48 8d 3d 99 31 00 00    lea    0x3199(%rip),%rdi        # 4380 <stdout@@GLIBC_2.2.5>
    11e7:   48 8d 35 92 31 00 00    lea    0x3192(%rip),%rsi        # 4380 <stdout@@GLIBC_2.2.5>
    11ee:   48 29 fe                sub    %rdi,%rsi
    11f1:   48 89 f0                mov    %rsi,%rax
    11f4:   48 c1 ee 3f             shr    $0x3f,%rsi
    11f8:   48 c1 f8 03             sar    $0x3,%rax
    11fc:   48 01 c6                add    %rax,%rsi
    11ff:   48 d1 fe                sar    %rsi
    1202:   74 14                   je     1218 <sleep@plt+0xa8>
    1204:   48 8b 05 e5 2d 00 00    mov    0x2de5(%rip),%rax        # 3ff0 <sleep@plt+0x2e80>
    120b:   48 85 c0                test   %rax,%rax
    120e:   74 08                   je     1218 <sleep@plt+0xa8>
    1210:   ff e0                   jmpq   *%rax
    1212:   66 0f 1f 44 00 00       nopw   0x0(%rax,%rax,1)
    1218:   c3                      retq   
    1219:   0f 1f 80 00 00 00 00    nopl   0x0(%rax)
    1220:   f3 0f 1e fa             endbr64 
    1224:   80 3d 5d 31 00 00 00    cmpb   $0x0,0x315d(%rip)        # 4388 <stdout@@GLIBC_2.2.5+0x8>
    122b:   75 2b                   jne    1258 <sleep@plt+0xe8>
    122d:   55                      push   %rbp
    122e:   48 83 3d c2 2d 00 00    cmpq   $0x0,0x2dc2(%rip)        # 3ff8 <sleep@plt+0x2e88>
    1235:   00 
    1236:   48 89 e5                mov    %rsp,%rbp
    1239:   74 0c                   je     1247 <sleep@plt+0xd7>
    123b:   48 8b 3d c6 2d 00 00    mov    0x2dc6(%rip),%rdi        # 4008 <sleep@plt+0x2e98>
    1242:   e8 89 fe ff ff          callq  10d0 <__cxa_finalize@plt>
    1247:   e8 64 ff ff ff          callq  11b0 <sleep@plt+0x40>
    124c:   c6 05 35 31 00 00 01    movb   $0x1,0x3135(%rip)        # 4388 <stdout@@GLIBC_2.2.5+0x8>
    1253:   5d                      pop    %rbp
    1254:   c3                      retq   
    1255:   0f 1f 00                nopl   (%rax)
    1258:   c3                      retq   
    1259:   0f 1f 80 00 00 00 00    nopl   0x0(%rax)
    1260:   f3 0f 1e fa             endbr64 
    1264:   e9 77 ff ff ff          jmpq   11e0 <sleep@plt+0x70>
    1269:   f3 0f 1e fa             endbr64

    126d:   55                      push   %rbp
    126e:   48 89 e5                mov    %rsp,%rbp
    1271:   48 83 ec 10             sub    $0x10,%rsp
    1275:   48 89 7d f8             mov    %rdi,-0x8(%rbp)
    1279:   48 8b 45 f8             mov    -0x8(%rbp),%rax
    127d:   48 89 c6                mov    %rax,%rsi
    1280:   48 8d 3d 81 0d 00 00    lea    0xd81(%rip),%rdi        # 2008 <sleep@plt+0xe98>
    1287:   b8 00 00 00 00          mov    $0x0,%eax
    128c:   e8 7f fe ff ff          callq  1110 <printf@plt>
    1291:   bf 01 00 00 00          mov    $0x1,%edi
    1296:   e8 c5 fe ff ff          callq  1160 <exit@plt>
    129b:   f3 0f 1e fa             endbr64
read_reg
    129f:   55                      push   %rbp
    12a0:   48 89 e5                mov    %rsp,%rbp
    12a3:   48 83 ec 10             sub    $0x10,%rsp
    12a7:   48 89 7d f8             mov    %rdi,-0x8(%rbp)
    12ab:   89 f0                   mov    %esi,%eax
    12ad:   88 45 f4                mov    %al,-0xc(%rbp)
    12b0:   80 7d f4 02             cmpb   $0x2,-0xc(%rbp)
    12b4:   75 0d                   jne    12c3 <sleep@plt+0x153>
    12b6:   48 8b 45 f8             mov    -0x8(%rbp),%rax
    12ba:   0f b6 80 00 04 00 00    movzbl 0x400(%rax),%eax
    12c1:   eb 7e                   jmp    1341 <sleep@plt+0x1d1>
    12c3:   80 7d f4 01             cmpb   $0x1,-0xc(%rbp)
    12c7:   75 0d                   jne    12d6 <sleep@plt+0x166>
    12c9:   48 8b 45 f8             mov    -0x8(%rbp),%rax
    12cd:   0f b6 80 01 04 00 00    movzbl 0x401(%rax),%eax
    12d4:   eb 6b                   jmp    1341 <sleep@plt+0x1d1>
    12d6:   80 7d f4 20             cmpb   $0x20,-0xc(%rbp)
    12da:   75 0d                   jne    12e9 <sleep@plt+0x179>
    12dc:   48 8b 45 f8             mov    -0x8(%rbp),%rax
    12e0:   0f b6 80 02 04 00 00    movzbl 0x402(%rax),%eax
    12e7:   eb 58                   jmp    1341 <sleep@plt+0x1d1>
    12e9:   80 7d f4 40             cmpb   $0x40,-0xc(%rbp)
    12ed:   75 0d                   jne    12fc <sleep@plt+0x18c>
    12ef:   48 8b 45 f8             mov    -0x8(%rbp),%rax
    12f3:   0f b6 80 03 04 00 00    movzbl 0x403(%rax),%eax
    12fa:   eb 45                   jmp    1341 <sleep@plt+0x1d1>
    12fc:   80 7d f4 04             cmpb   $0x4,-0xc(%rbp)
    1300:   75 0d                   jne    130f <sleep@plt+0x19f>
    1302:   48 8b 45 f8             mov    -0x8(%rbp),%rax
    1306:   0f b6 80 04 04 00 00    movzbl 0x404(%rax),%eax
    130d:   eb 32                   jmp    1341 <sleep@plt+0x1d1>
    130f:   80 7d f4 08             cmpb   $0x8,-0xc(%rbp)
    1313:   75 0d                   jne    1322 <sleep@plt+0x1b2>
    1315:   48 8b 45 f8             mov    -0x8(%rbp),%rax
    1319:   0f b6 80 05 04 00 00    movzbl 0x405(%rax),%eax
    1320:   eb 1f                   jmp    1341 <sleep@plt+0x1d1>
    1322:   80 7d f4 10             cmpb   $0x10,-0xc(%rbp)
    1326:   75 0d                   jne    1335 <sleep@plt+0x1c5>
    1328:   48 8b 45 f8             mov    -0x8(%rbp),%rax
    132c:   0f b6 80 06 04 00 00    movzbl 0x406(%rax),%eax
    1333:   eb 0c                   jmp    1341 <sleep@plt+0x1d1>
    1335:   48 8d 3d e8 0c 00 00    lea    0xce8(%rip),%rdi        # 2024 <sleep@plt+0xeb4>
    133c:   e8 28 ff ff ff          callq  1269 <sleep@plt+0xf9>
    1341:   c9                      leaveq 
    1342:   c3                      retq
write_reg
    1343:   f3 0f 1e fa             endbr64 
    1347:   55                      push   %rbp
    1348:   48 89 e5                mov    %rsp,%rbp
    134b:   48 83 ec 10             sub    $0x10,%rsp
    134f:   48 89 7d f8             mov    %rdi,-0x8(%rbp)
    1353:   89 f1                   mov    %esi,%ecx
    1355:   89 d0                   mov    %edx,%eax
    1357:   89 ca                   mov    %ecx,%edx
    1359:   88 55 f4                mov    %dl,-0xc(%rbp)
    135c:   88 45 f0                mov    %al,-0x10(%rbp)
    135f:   80 7d f4 02             cmpb   $0x2,-0xc(%rbp)
    1363:   75 13                   jne    1378 <sleep@plt+0x208>
    1365:   48 8b 45 f8             mov    -0x8(%rbp),%rax
    1369:   0f b6 55 f0             movzbl -0x10(%rbp),%edx
    136d:   88 90 00 04 00 00       mov    %dl,0x400(%rax)
    1373:   e9 90 00 00 00          jmpq   1408 <sleep@plt+0x298>
    1378:   80 7d f4 01             cmpb   $0x1,-0xc(%rbp)
    137c:   75 10                   jne    138e <sleep@plt+0x21e>
    137e:   48 8b 45 f8             mov    -0x8(%rbp),%rax
    1382:   0f b6 55 f0             movzbl -0x10(%rbp),%edx
    1386:   88 90 01 04 00 00       mov    %dl,0x401(%rax)
    138c:   eb 7a                   jmp    1408 <sleep@plt+0x298>
    138e:   80 7d f4 20             cmpb   $0x20,-0xc(%rbp)
    1392:   75 10                   jne    13a4 <sleep@plt+0x234>
    1394:   48 8b 45 f8             mov    -0x8(%rbp),%rax
    1398:   0f b6 55 f0             movzbl -0x10(%rbp),%edx
    139c:   88 90 02 04 00 00       mov    %dl,0x402(%rax)
    13a2:   eb 64                   jmp    1408 <sleep@plt+0x298>
    13a4:   80 7d f4 40             cmpb   $0x40,-0xc(%rbp)
    13a8:   75 10                   jne    13ba <sleep@plt+0x24a>
    13aa:   48 8b 45 f8             mov    -0x8(%rbp),%rax
    13ae:   0f b6 55 f0             movzbl -0x10(%rbp),%edx
    13b2:   88 90 03 04 00 00       mov    %dl,0x403(%rax)
    13b8:   eb 4e                   jmp    1408 <sleep@plt+0x298>
    13ba:   80 7d f4 04             cmpb   $0x4,-0xc(%rbp)
    13be:   75 10                   jne    13d0 <sleep@plt+0x260>
    13c0:   48 8b 45 f8             mov    -0x8(%rbp),%rax
    13c4:   0f b6 55 f0             movzbl -0x10(%rbp),%edx
    13c8:   88 90 04 04 00 00       mov    %dl,0x404(%rax)
    13ce:   eb 38                   jmp    1408 <sleep@plt+0x298>
    13d0:   80 7d f4 08             cmpb   $0x8,-0xc(%rbp)
    13d4:   75 10                   jne    13e6 <sleep@plt+0x276>
    13d6:   48 8b 45 f8             mov    -0x8(%rbp),%rax
    13da:   0f b6 55 f0             movzbl -0x10(%rbp),%edx
    13de:   88 90 05 04 00 00       mov    %dl,0x405(%rax)
    13e4:   eb 22                   jmp    1408 <sleep@plt+0x298>
    13e6:   80 7d f4 10             cmpb   $0x10,-0xc(%rbp)
    13ea:   75 10                   jne    13fc <sleep@plt+0x28c>
    13ec:   48 8b 45 f8             mov    -0x8(%rbp),%rax
    13f0:   0f b6 55 f0             movzbl -0x10(%rbp),%edx
    13f4:   88 90 06 04 00 00       mov    %dl,0x406(%rax)
    13fa:   eb 0c                   jmp    1408 <sleep@plt+0x298>
    13fc:   48 8d 3d 21 0c 00 00    lea    0xc21(%rip),%rdi        # 2024 <sleep@plt+0xeb4>
    1403:   e8 61 fe ff ff          callq  1269 <sleep@plt+0xf9>
    1408:   c9                      leaveq 
    1409:   c3                      retq
read_mem
    140a:   f3 0f 1e fa             endbr64 
    140e:   55                      push   %rbp
    140f:   48 89 e5                mov    %rsp,%rbp
    1412:   48 89 7d f8             mov    %rdi,-0x8(%rbp)
    1416:   89 f0                   mov    %esi,%eax
    1418:   88 45 f4                mov    %al,-0xc(%rbp)
    141b:   0f b6 45 f4             movzbl -0xc(%rbp),%eax
    141f:   48 8b 55 f8             mov    -0x8(%rbp),%rdx
    1423:   48 98                   cltq   
    1425:   0f b6 84 02 00 03 00    movzbl 0x300(%rdx,%rax,1),%eax
    142c:   00 
    142d:   5d                      pop    %rbp
    142e:   c3                      retq
write_mem   
    142f:   f3 0f 1e fa             endbr64
    1433:   55                      push   %rbp
    1434:   48 89 e5                mov    %rsp,%rbp
    1437:   48 89 7d f8             mov    %rdi,-0x8(%rbp)
    143b:   89 f1                   mov    %esi,%ecx
    143d:   89 d0                   mov    %edx,%eax
    143f:   89 ca                   mov    %ecx,%edx
    1441:   88 55 f4                mov    %dl,-0xc(%rbp)
    1444:   88 45 f0                mov    %al,-0x10(%rbp)
    1447:   0f b6 45 f4             movzbl -0xc(%rbp),%eax
    144b:   48 8b 55 f8             mov    -0x8(%rbp),%rdx
    144f:   48 98                   cltq   
    1451:   0f b6 4d f0             movzbl -0x10(%rbp),%ecx
    1455:   88 8c 02 00 03 00 00    mov    %cl,0x300(%rdx,%rax,1)
    145c:   90                      nop
    145d:   5d                      pop    %rbp
    145e:   c3                      retq
interpret_imm
    145f:   f3 0f 1e fa             endbr64
    1463:   55                      push   %rbp
    1464:   48 89 e5                mov    %rsp,%rbp
    1467:   48 83 ec 10             sub    $0x10,%rsp
    146b:   48 89 7d f8             mov    %rdi,-0x8(%rbp)
    146f:   48 89 75 f0             mov    %rsi,-0x10(%rbp)
    1473:   0f b6 45 f0             movzbl -0x10(%rbp),%eax
    1477:   0f b6 d0                movzbl %al,%edx
    147a:   0f b6 45 f1             movzbl -0xf(%rbp),%eax
    147e:   0f b6 c8                movzbl %al,%ecx
    1481:   48 8b 45 f8             mov    -0x8(%rbp),%rax
    1485:   89 ce                   mov    %ecx,%esi
    1487:   48 89 c7                mov    %rax,%rdi
    148a:   e8 b4 fe ff ff          callq  1343 <sleep@plt+0x1d3>
    148f:   90                      nop
    1490:   c9                      leaveq 
    1491:   c3                      retq
interpret_add
    1492:   f3 0f 1e fa             endbr64 
    1496:   55                      push   %rbp
    1497:   48 89 e5                mov    %rsp,%rbp
    149a:   53                      push   %rbx
    149b:   48 83 ec 18             sub    $0x18,%rsp
    149f:   48 89 7d e8             mov    %rdi,-0x18(%rbp)
    14a3:   48 89 75 e0             mov    %rsi,-0x20(%rbp)
    14a7:   0f b6 45 e1             movzbl -0x1f(%rbp),%eax
    14ab:   0f b6 d0                movzbl %al,%edx
    14ae:   48 8b 45 e8             mov    -0x18(%rbp),%rax
    14b2:   89 d6                   mov    %edx,%esi
    14b4:   48 89 c7                mov    %rax,%rdi
    14b7:   e8 df fd ff ff          callq  129b <sleep@plt+0x12b>
    14bc:   89 c3                   mov    %eax,%ebx
    14be:   0f b6 45 e0             movzbl -0x20(%rbp),%eax
    14c2:   0f b6 d0                movzbl %al,%edx
    14c5:   48 8b 45 e8             mov    -0x18(%rbp),%rax
    14c9:   89 d6                   mov    %edx,%esi
    14cb:   48 89 c7                mov    %rax,%rdi
    14ce:   e8 c8 fd ff ff          callq  129b <sleep@plt+0x12b>
    14d3:   01 d8                   add    %ebx,%eax
    14d5:   0f b6 d0                movzbl %al,%edx
    14d8:   0f b6 45 e1             movzbl -0x1f(%rbp),%eax
    14dc:   0f b6 c8                movzbl %al,%ecx
    14df:   48 8b 45 e8             mov    -0x18(%rbp),%rax
    14e3:   89 ce                   mov    %ecx,%esi
    14e5:   48 89 c7                mov    %rax,%rdi
    14e8:   e8 56 fe ff ff          callq  1343 <sleep@plt+0x1d3>
    14ed:   90                      nop
    14ee:   48 83 c4 18             add    $0x18,%rsp
    14f2:   5b                      pop    %rbx
    14f3:   5d                      pop    %rbp
    14f4:   c3                      retq
interpret_stk
    14f5:   f3 0f 1e fa             endbr64 
    14f9:   55                      push   %rbp
    14fa:   48 89 e5                mov    %rsp,%rbp
    14fd:   48 83 ec 10             sub    $0x10,%rsp
    1501:   48 89 7d f8             mov    %rdi,-0x8(%rbp)
    1505:   48 89 75 f0             mov    %rsi,-0x10(%rbp)
    1509:   0f b6 45 f0             movzbl -0x10(%rbp),%eax
    150d:   84 c0                   test   %al,%al
    150f:   74 4c                   je     155d <sleep@plt+0x3ed>
    1511:   48 8b 45 f8             mov    -0x8(%rbp),%rax
    1515:   0f b6 80 04 04 00 00    movzbl 0x404(%rax),%eax
    151c:   8d 50 01                lea    0x1(%rax),%edx
    151f:   48 8b 45 f8             mov    -0x8(%rbp),%rax
    1523:   88 90 04 04 00 00       mov    %dl,0x404(%rax)
    1529:   0f b6 45 f0             movzbl -0x10(%rbp),%eax
    152d:   0f b6 d0                movzbl %al,%edx
    1530:   48 8b 45 f8             mov    -0x8(%rbp),%rax
    1534:   89 d6                   mov    %edx,%esi
    1536:   48 89 c7                mov    %rax,%rdi
    1539:   e8 5d fd ff ff          callq  129b <sleep@plt+0x12b>
    153e:   0f b6 d0                movzbl %al,%edx
    1541:   48 8b 45 f8             mov    -0x8(%rbp),%rax
    1545:   0f b6 80 04 04 00 00    movzbl 0x404(%rax),%eax
    154c:   0f b6 c8                movzbl %al,%ecx
    154f:   48 8b 45 f8             mov    -0x8(%rbp),%rax
    1553:   89 ce                   mov    %ecx,%esi
    1555:   48 89 c7                mov    %rax,%rdi
    1558:   e8 d2 fe ff ff          callq  142f <sleep@plt+0x2bf>
    155d:   0f b6 45 f1             movzbl -0xf(%rbp),%eax
    1561:   84 c0                   test   %al,%al
    1563:   74 4c                   je     15b1 <sleep@plt+0x441>
    1565:   48 8b 45 f8             mov    -0x8(%rbp),%rax
    1569:   0f b6 80 04 04 00 00    movzbl 0x404(%rax),%eax
    1570:   0f b6 d0                movzbl %al,%edx
    1573:   48 8b 45 f8             mov    -0x8(%rbp),%rax
    1577:   89 d6                   mov    %edx,%esi
    1579:   48 89 c7                mov    %rax,%rdi
    157c:   e8 89 fe ff ff          callq  140a <sleep@plt+0x29a>
    1581:   0f b6 d0                movzbl %al,%edx
    1584:   0f b6 45 f1             movzbl -0xf(%rbp),%eax
    1588:   0f b6 c8                movzbl %al,%ecx
    158b:   48 8b 45 f8             mov    -0x8(%rbp),%rax
    158f:   89 ce                   mov    %ecx,%esi
    1591:   48 89 c7                mov    %rax,%rdi
    1594:   e8 aa fd ff ff          callq  1343 <sleep@plt+0x1d3>
    1599:   48 8b 45 f8             mov    -0x8(%rbp),%rax
    159d:   0f b6 80 04 04 00 00    movzbl 0x404(%rax),%eax
    15a4:   8d 50 ff                lea    -0x1(%rax),%edx
    15a7:   48 8b 45 f8             mov    -0x8(%rbp),%rax
    15ab:   88 90 04 04 00 00       mov    %dl,0x404(%rax)
    15b1:   90                      nop
    15b2:   c9                      leaveq 
    15b3:   c3                      retq
interpret_stm
    15b4:   f3 0f 1e fa             endbr64 
    15b8:   55                      push   %rbp
    15b9:   48 89 e5                mov    %rsp,%rbp
    15bc:   53                      push   %rbx
    15bd:   48 83 ec 18             sub    $0x18,%rsp
    15c1:   48 89 7d e8             mov    %rdi,-0x18(%rbp)
    15c5:   48 89 75 e0             mov    %rsi,-0x20(%rbp)
    15c9:   0f b6 45 e0             movzbl -0x20(%rbp),%eax
    15cd:   0f b6 d0                movzbl %al,%edx
    15d0:   48 8b 45 e8             mov    -0x18(%rbp),%rax
    15d4:   89 d6                   mov    %edx,%esi
    15d6:   48 89 c7                mov    %rax,%rdi
    15d9:   e8 bd fc ff ff          callq  129b <sleep@plt+0x12b>
    15de:   0f b6 d8                movzbl %al,%ebx
    15e1:   0f b6 45 e1             movzbl -0x1f(%rbp),%eax
    15e5:   0f b6 d0                movzbl %al,%edx
    15e8:   48 8b 45 e8             mov    -0x18(%rbp),%rax
    15ec:   89 d6                   mov    %edx,%esi
    15ee:   48 89 c7                mov    %rax,%rdi
    15f1:   e8 a5 fc ff ff          callq  129b <sleep@plt+0x12b>
    15f6:   0f b6 c8                movzbl %al,%ecx
    15f9:   48 8b 45 e8             mov    -0x18(%rbp),%rax
    15fd:   89 da                   mov    %ebx,%edx
    15ff:   89 ce                   mov    %ecx,%esi
    1601:   48 89 c7                mov    %rax,%rdi
    1604:   e8 26 fe ff ff          callq  142f <sleep@plt+0x2bf>
    1609:   90                      nop
    160a:   48 83 c4 18             add    $0x18,%rsp
    160e:   5b                      pop    %rbx
    160f:   5d                      pop    %rbp
    1610:   c3                      retq
interpret_ldm
    1611:   f3 0f 1e fa             endbr64 
    1615:   55                      push   %rbp
    1616:   48 89 e5                mov    %rsp,%rbp
    1619:   48 83 ec 10             sub    $0x10,%rsp
    161d:   48 89 7d f8             mov    %rdi,-0x8(%rbp)
    1621:   48 89 75 f0             mov    %rsi,-0x10(%rbp)
    1625:   0f b6 45 f0             movzbl -0x10(%rbp),%eax
    1629:   0f b6 d0                movzbl %al,%edx
    162c:   48 8b 45 f8             mov    -0x8(%rbp),%rax
    1630:   89 d6                   mov    %edx,%esi
    1632:   48 89 c7                mov    %rax,%rdi
    1635:   e8 61 fc ff ff          callq  129b <sleep@plt+0x12b>
    163a:   0f b6 d0                movzbl %al,%edx
    163d:   48 8b 45 f8             mov    -0x8(%rbp),%rax
    1641:   89 d6                   mov    %edx,%esi
    1643:   48 89 c7                mov    %rax,%rdi
    1646:   e8 bf fd ff ff          callq  140a <sleep@plt+0x29a>
    164b:   0f b6 d0                movzbl %al,%edx
    164e:   0f b6 45 f1             movzbl -0xf(%rbp),%eax
    1652:   0f b6 c8                movzbl %al,%ecx
    1655:   48 8b 45 f8             mov    -0x8(%rbp),%rax
    1659:   89 ce                   mov    %ecx,%esi
    165b:   48 89 c7                mov    %rax,%rdi
    165e:   e8 e0 fc ff ff          callq  1343 <sleep@plt+0x1d3>
    1663:   90                      nop
    1664:   c9                      leaveq 
    1665:   c3                      retq
interpret_cmp
    1666:   f3 0f 1e fa             endbr64 
    166a:   55                      push   %rbp
    166b:   48 89 e5                mov    %rsp,%rbp
    166e:   48 83 ec 20             sub    $0x20,%rsp
    1672:   48 89 7d e8             mov    %rdi,-0x18(%rbp)
    1676:   48 89 75 e0             mov    %rsi,-0x20(%rbp)
    167a:   0f b6 45 e1             movzbl -0x1f(%rbp),%eax
    167e:   0f b6 d0                movzbl %al,%edx
    1681:   48 8b 45 e8             mov    -0x18(%rbp),%rax
    1685:   89 d6                   mov    %edx,%esi
    1687:   48 89 c7                mov    %rax,%rdi
    168a:   e8 0c fc ff ff          callq  129b <sleep@plt+0x12b>
    168f:   88 45 fe                mov    %al,-0x2(%rbp)
    1692:   0f b6 45 e0             movzbl -0x20(%rbp),%eax
    1696:   0f b6 d0                movzbl %al,%edx
    1699:   48 8b 45 e8             mov    -0x18(%rbp),%rax
    169d:   89 d6                   mov    %edx,%esi
    169f:   48 89 c7                mov    %rax,%rdi
    16a2:   e8 f4 fb ff ff          callq  129b <sleep@plt+0x12b>
    16a7:   88 45 ff                mov    %al,-0x1(%rbp)
    16aa:   48 8b 45 e8             mov    -0x18(%rbp),%rax
    16ae:   c6 80 06 04 00 00 00    movb   $0x0,0x406(%rax)
    16b5:   0f b6 45 fe             movzbl -0x2(%rbp),%eax
    16b9:   3a 45 ff                cmp    -0x1(%rbp),%al
    16bc:   73 1a                   jae    16d8 <sleep@plt+0x568>
    16be:   48 8b 45 e8             mov    -0x18(%rbp),%rax
    16c2:   0f b6 80 06 04 00 00    movzbl 0x406(%rax),%eax
    16c9:   83 c8 08                or     $0x8,%eax
    16cc:   89 c2                   mov    %eax,%edx
    16ce:   48 8b 45 e8             mov    -0x18(%rbp),%rax
    16d2:   88 90 06 04 00 00       mov    %dl,0x406(%rax)
    16d8:   0f b6 45 fe             movzbl -0x2(%rbp),%eax
    16dc:   3a 45 ff                cmp    -0x1(%rbp),%al
    16df:   76 1a                   jbe    16fb <sleep@plt+0x58b>
    16e1:   48 8b 45 e8             mov    -0x18(%rbp),%rax
    16e5:   0f b6 80 06 04 00 00    movzbl 0x406(%rax),%eax
    16ec:   83 c8 04                or     $0x4,%eax
    16ef:   89 c2                   mov    %eax,%edx
    16f1:   48 8b 45 e8             mov    -0x18(%rbp),%rax
    16f5:   88 90 06 04 00 00       mov    %dl,0x406(%rax)
    16fb:   0f b6 45 fe             movzbl -0x2(%rbp),%eax
    16ff:   3a 45 ff                cmp    -0x1(%rbp),%al
    1702:   75 1a                   jne    171e <sleep@plt+0x5ae>
    1704:   48 8b 45 e8             mov    -0x18(%rbp),%rax
    1708:   0f b6 80 06 04 00 00    movzbl 0x406(%rax),%eax
    170f:   83 c8 01                or     $0x1,%eax
    1712:   89 c2                   mov    %eax,%edx
    1714:   48 8b 45 e8             mov    -0x18(%rbp),%rax
    1718:   88 90 06 04 00 00       mov    %dl,0x406(%rax)
    171e:   0f b6 45 fe             movzbl -0x2(%rbp),%eax
    1722:   3a 45 ff                cmp    -0x1(%rbp),%al
    1725:   74 1a                   je     1741 <sleep@plt+0x5d1>
    1727:   48 8b 45 e8             mov    -0x18(%rbp),%rax
    172b:   0f b6 80 06 04 00 00    movzbl 0x406(%rax),%eax
    1732:   83 c8 02                or     $0x2,%eax
    1735:   89 c2                   mov    %eax,%edx
    1737:   48 8b 45 e8             mov    -0x18(%rbp),%rax
    173b:   88 90 06 04 00 00       mov    %dl,0x406(%rax)
    1741:   80 7d fe 00             cmpb   $0x0,-0x2(%rbp)
    1745:   75 20                   jne    1767 <sleep@plt+0x5f7>
    1747:   80 7d ff 00             cmpb   $0x0,-0x1(%rbp)
    174b:   75 1a                   jne    1767 <sleep@plt+0x5f7>
    174d:   48 8b 45 e8             mov    -0x18(%rbp),%rax
    1751:   0f b6 80 06 04 00 00    movzbl 0x406(%rax),%eax
    1758:   83 c8 10                or     $0x10,%eax
    175b:   89 c2                   mov    %eax,%edx
    175d:   48 8b 45 e8             mov    -0x18(%rbp),%rax
    1761:   88 90 06 04 00 00       mov    %dl,0x406(%rax)
    1767:   90                      nop
    1768:   c9                      leaveq 
    1769:   c3                      retq
interpret_jmp
    176a:   f3 0f 1e fa             endbr64 
    176e:   55                      push   %rbp
    176f:   48 89 e5                mov    %rsp,%rbp
    1772:   48 83 ec 10             sub    $0x10,%rsp
    1776:   48 89 7d f8             mov    %rdi,-0x8(%rbp)
    177a:   48 89 75 f0             mov    %rsi,-0x10(%rbp)
    177e:   0f b6 45 f1             movzbl -0xf(%rbp),%eax
    1782:   84 c0                   test   %al,%al
    1784:   74 15                   je     179b <sleep@plt+0x62b>
    1786:   0f b6 55 f1             movzbl -0xf(%rbp),%edx
    178a:   48 8b 45 f8             mov    -0x8(%rbp),%rax
    178e:   0f b6 80 06 04 00 00    movzbl 0x406(%rax),%eax
    1795:   21 d0                   and    %edx,%eax
    1797:   84 c0                   test   %al,%al
    1799:   74 1f                   je     17ba <sleep@plt+0x64a>
    179b:   0f b6 45 f0             movzbl -0x10(%rbp),%eax
    179f:   0f b6 d0                movzbl %al,%edx
    17a2:   48 8b 45 f8             mov    -0x8(%rbp),%rax
    17a6:   89 d6                   mov    %edx,%esi
    17a8:   48 89 c7                mov    %rax,%rdi
    17ab:   e8 eb fa ff ff          callq  129b <sleep@plt+0x12b>
    17b0:   48 8b 55 f8             mov    -0x8(%rbp),%rdx
    17b4:   88 82 05 04 00 00       mov    %al,0x405(%rdx)
    17ba:   90                      nop
    17bb:   c9                      leaveq 
    17bc:   c3                      retq
interpret_sys
    17bd:   f3 0f 1e fa             endbr64 
    17c1:   55                      push   %rbp
    17c2:   48 89 e5                mov    %rsp,%rbp
    17c5:   48 83 ec 30             sub    $0x30,%rsp
    17c9:   48 89 7d d8             mov    %rdi,-0x28(%rbp)
    17cd:   48 89 75 d0             mov    %rsi,-0x30(%rbp)
    17d1:   0f b6 45 d1             movzbl -0x2f(%rbp),%eax
    17d5:   0f b6 c0                movzbl %al,%eax
    17d8:   83 e0 02                and    $0x2,%eax
    17db:   85 c0                   test   %eax,%eax
    17dd:   74 5f                   je     183e <sleep@plt+0x6ce>
    17df:   48 8b 45 d8             mov    -0x28(%rbp),%rax
    17e3:   0f b6 80 02 04 00 00    movzbl 0x402(%rax),%eax
    17ea:   0f b6 d0                movzbl %al,%edx
    17ed:   48 8b 45 d8             mov    -0x28(%rbp),%rax
    17f1:   0f b6 80 01 04 00 00    movzbl 0x401(%rax),%eax
    17f8:   0f b6 c0                movzbl %al,%eax
    17fb:   48 8b 4d d8             mov    -0x28(%rbp),%rcx
    17ff:   48 8d b1 00 03 00 00    lea    0x300(%rcx),%rsi
    1806:   48 8b 4d d8             mov    -0x28(%rbp),%rcx
    180a:   0f b6 89 00 04 00 00    movzbl 0x400(%rcx),%ecx
    1811:   0f b6 c9                movzbl %cl,%ecx
    1814:   48 01 f1                add    %rsi,%rcx
    1817:   89 c6                   mov    %eax,%esi
    1819:   48 89 cf                mov    %rcx,%rdi
    181c:   b8 00 00 00 00          mov    $0x0,%eax
    1821:   e8 2a f9 ff ff          callq  1150 <open@plt>
    1826:   0f b6 d0                movzbl %al,%edx
    1829:   0f b6 45 d0             movzbl -0x30(%rbp),%eax
    182d:   0f b6 c8                movzbl %al,%ecx
    1830:   48 8b 45 d8             mov    -0x28(%rbp),%rax
    1834:   89 ce                   mov    %ecx,%esi
    1836:   48 89 c7                mov    %rax,%rdi
    1839:   e8 05 fb ff ff          callq  1343 <sleep@plt+0x1d3>
    183e:   0f b6 45 d1             movzbl -0x2f(%rbp),%eax
    1842:   0f b6 c0                movzbl %al,%eax
    1845:   83 e0 20                and    $0x20,%eax
    1848:   85 c0                   test   %eax,%eax
    184a:   0f 84 89 00 00 00       je     18d9 <sleep@plt+0x769>
    1850:   48 8b 45 d8             mov    -0x28(%rbp),%rax
    1854:   0f b6 80 01 04 00 00    movzbl 0x401(%rax),%eax
    185b:   0f b6 c0                movzbl %al,%eax
    185e:   ba 00 01 00 00          mov    $0x100,%edx
    1863:   29 c2                   sub    %eax,%edx
    1865:   89 d0                   mov    %edx,%eax
    1867:   48 63 d0                movslq %eax,%rdx
    186a:   48 89 d0                mov    %rdx,%rax
    186d:   48 01 c0                add    %rax,%rax
    1870:   48 01 c2                add    %rax,%rdx
    1873:   48 8b 45 d8             mov    -0x28(%rbp),%rax
    1877:   0f b6 80 02 04 00 00    movzbl 0x402(%rax),%eax
    187e:   0f b6 c0                movzbl %al,%eax
    1881:   48 39 c2                cmp    %rax,%rdx
    1884:   48 0f 46 c2             cmovbe %rdx,%rax
    1888:   48 89 c1                mov    %rax,%rcx
    188b:   48 8b 75 d8             mov    -0x28(%rbp),%rsi
    188f:   48 8b 45 d8             mov    -0x28(%rbp),%rax
    1893:   0f b6 80 01 04 00 00    movzbl 0x401(%rax),%eax
    189a:   0f b6 d0                movzbl %al,%edx
    189d:   48 89 d0                mov    %rdx,%rax
    18a0:   48 01 c0                add    %rax,%rax
    18a3:   48 01 d0                add    %rdx,%rax
    18a6:   48 01 c6                add    %rax,%rsi
    18a9:   48 8b 45 d8             mov    -0x28(%rbp),%rax
    18ad:   0f b6 80 00 04 00 00    movzbl 0x400(%rax),%eax
    18b4:   0f b6 c0                movzbl %al,%eax
    18b7:   48 89 ca                mov    %rcx,%rdx
    18ba:   89 c7                   mov    %eax,%edi
    18bc:   e8 5f f8 ff ff          callq  1120 <read@plt>
    18c1:   0f b6 d0                movzbl %al,%edx
    18c4:   0f b6 45 d0             movzbl -0x30(%rbp),%eax
    18c8:   0f b6 c8                movzbl %al,%ecx
    18cb:   48 8b 45 d8             mov    -0x28(%rbp),%rax
    18cf:   89 ce                   mov    %ecx,%esi
    18d1:   48 89 c7                mov    %rax,%rdi
    18d4:   e8 6a fa ff ff          callq  1343 <sleep@plt+0x1d3>
    18d9:   0f b6 45 d1             movzbl -0x2f(%rbp),%eax
    18dd:   0f b6 c0                movzbl %al,%eax
    18e0:   83 e0 08                and    $0x8,%eax
    18e3:   85 c0                   test   %eax,%eax
    18e5:   0f 84 8a 00 00 00       je     1975 <sleep@plt+0x805>
    18eb:   48 8b 45 d8             mov    -0x28(%rbp),%rax
    18ef:   48 8d 90 00 03 00 00    lea    0x300(%rax),%rdx
    18f6:   48 8b 45 d8             mov    -0x28(%rbp),%rax
    18fa:   0f b6 80 01 04 00 00    movzbl 0x401(%rax),%eax
    1901:   0f b6 c0                movzbl %al,%eax
    1904:   48 01 d0                add    %rdx,%rax
    1907:   48 89 45 f0             mov    %rax,-0x10(%rbp)
    190b:   48 8b 45 d8             mov    -0x28(%rbp),%rax
    190f:   0f b6 80 01 04 00 00    movzbl 0x401(%rax),%eax
    1916:   0f b6 c0                movzbl %al,%eax
    1919:   ba 00 01 00 00          mov    $0x100,%edx
    191e:   29 c2                   sub    %eax,%edx
    1920:   89 d0                   mov    %edx,%eax
    1922:   48 63 d0                movslq %eax,%rdx
    1925:   48 8b 45 d8             mov    -0x28(%rbp),%rax
    1929:   0f b6 80 02 04 00 00    movzbl 0x402(%rax),%eax
    1930:   0f b6 c0                movzbl %al,%eax
    1933:   48 39 c2                cmp    %rax,%rdx
    1936:   48 0f 46 c2             cmovbe %rdx,%rax
    193a:   88 45 ee                mov    %al,-0x12(%rbp)
    193d:   0f b6 55 ee             movzbl -0x12(%rbp),%edx
    1941:   48 8b 45 d8             mov    -0x28(%rbp),%rax
    1945:   0f b6 80 00 04 00 00    movzbl 0x400(%rax),%eax
    194c:   0f b6 c0                movzbl %al,%eax
    194f:   48 8b 4d f0             mov    -0x10(%rbp),%rcx
    1953:   48 89 ce                mov    %rcx,%rsi
    1956:   89 c7                   mov    %eax,%edi
    1958:   e8 c3 f7 ff ff          callq  1120 <read@plt>
    195d:   0f b6 d0                movzbl %al,%edx
    1960:   0f b6 45 d0             movzbl -0x30(%rbp),%eax
    1964:   0f b6 c8                movzbl %al,%ecx
    1967:   48 8b 45 d8             mov    -0x28(%rbp),%rax
    196b:   89 ce                   mov    %ecx,%esi
    196d:   48 89 c7                mov    %rax,%rdi
    1970:   e8 ce f9 ff ff          callq  1343 <sleep@plt+0x1d3>
    1975:   0f b6 45 d1             movzbl -0x2f(%rbp),%eax
    1979:   0f b6 c0                movzbl %al,%eax
    197c:   83 e0 10                and    $0x10,%eax
    197f:   85 c0                   test   %eax,%eax
    1981:   0f 84 8a 00 00 00       je     1a11 <sleep@plt+0x8a1>
    1987:   48 8b 45 d8             mov    -0x28(%rbp),%rax
    198b:   48 8d 90 00 03 00 00    lea    0x300(%rax),%rdx
    1992:   48 8b 45 d8             mov    -0x28(%rbp),%rax
    1996:   0f b6 80 01 04 00 00    movzbl 0x401(%rax),%eax
    199d:   0f b6 c0                movzbl %al,%eax
    19a0:   48 01 d0                add    %rdx,%rax
    19a3:   48 89 45 f8             mov    %rax,-0x8(%rbp)
    19a7:   48 8b 45 d8             mov    -0x28(%rbp),%rax
    19ab:   0f b6 80 01 04 00 00    movzbl 0x401(%rax),%eax
    19b2:   0f b6 c0                movzbl %al,%eax
    19b5:   ba 00 01 00 00          mov    $0x100,%edx
    19ba:   29 c2                   sub    %eax,%edx
    19bc:   89 d0                   mov    %edx,%eax
    19be:   48 63 d0                movslq %eax,%rdx
    19c1:   48 8b 45 d8             mov    -0x28(%rbp),%rax
    19c5:   0f b6 80 02 04 00 00    movzbl 0x402(%rax),%eax
    19cc:   0f b6 c0                movzbl %al,%eax
    19cf:   48 39 c2                cmp    %rax,%rdx
    19d2:   48 0f 46 c2             cmovbe %rdx,%rax
    19d6:   88 45 ef                mov    %al,-0x11(%rbp)
    19d9:   0f b6 55 ef             movzbl -0x11(%rbp),%edx
    19dd:   48 8b 45 d8             mov    -0x28(%rbp),%rax
    19e1:   0f b6 80 00 04 00 00    movzbl 0x400(%rax),%eax
    19e8:   0f b6 c0                movzbl %al,%eax
    19eb:   48 8b 4d f8             mov    -0x8(%rbp),%rcx
    19ef:   48 89 ce                mov    %rcx,%rsi
    19f2:   89 c7                   mov    %eax,%edi
    19f4:   e8 f7 f6 ff ff          callq  10f0 <write@plt>
    19f9:   0f b6 d0                movzbl %al,%edx
    19fc:   0f b6 45 d0             movzbl -0x30(%rbp),%eax
    1a00:   0f b6 c8                movzbl %al,%ecx
    1a03:   48 8b 45 d8             mov    -0x28(%rbp),%rax
    1a07:   89 ce                   mov    %ecx,%esi
    1a09:   48 89 c7                mov    %rax,%rdi
    1a0c:   e8 32 f9 ff ff          callq  1343 <sleep@plt+0x1d3>
    1a11:   0f b6 45 d1             movzbl -0x2f(%rbp),%eax
    1a15:   0f b6 c0                movzbl %al,%eax
    1a18:   83 e0 04                and    $0x4,%eax
    1a1b:   85 c0                   test   %eax,%eax
    1a1d:   74 2d                   je     1a4c <sleep@plt+0x8dc>
    1a1f:   48 8b 45 d8             mov    -0x28(%rbp),%rax
    1a23:   0f b6 80 00 04 00 00    movzbl 0x400(%rax),%eax
    1a2a:   0f b6 c0                movzbl %al,%eax
    1a2d:   89 c7                   mov    %eax,%edi
    1a2f:   e8 3c f7 ff ff          callq  1170 <sleep@plt>
    1a34:   0f b6 d0                movzbl %al,%edx
    1a37:   0f b6 45 d0             movzbl -0x30(%rbp),%eax
    1a3b:   0f b6 c8                movzbl %al,%ecx
    1a3e:   48 8b 45 d8             mov    -0x28(%rbp),%rax
    1a42:   89 ce                   mov    %ecx,%esi
    1a44:   48 89 c7                mov    %rax,%rdi
    1a47:   e8 f7 f8 ff ff          callq  1343 <sleep@plt+0x1d3>
    1a4c:   0f b6 45 d1             movzbl -0x2f(%rbp),%eax
    1a50:   0f b6 c0                movzbl %al,%eax
    1a53:   83 e0 01                and    $0x1,%eax
    1a56:   85 c0                   test   %eax,%eax
    1a58:   74 15                   je     1a6f <sleep@plt+0x8ff>
    1a5a:   48 8b 45 d8             mov    -0x28(%rbp),%rax
    1a5e:   0f b6 80 00 04 00 00    movzbl 0x400(%rax),%eax
    1a65:   0f b6 c0                movzbl %al,%eax
    1a68:   89 c7                   mov    %eax,%edi
    1a6a:   e8 f1 f6 ff ff          callq  1160 <exit@plt>
    1a6f:   90                      nop
    1a70:   c9                      leaveq 
    1a71:   c3                      retq
#interpret_instruction
    1a72:   f3 0f 1e fa             endbr64 
    1a76:   55                      push   %rbp
    1a77:   48 89 e5                mov    %rsp,%rbp
    1a7a:   48 83 ec 10             sub    $0x10,%rsp
    1a7e:   48 89 7d f8             mov    %rdi,-0x8(%rbp)
    1a82:   48 89 75 f0             mov    %rsi,-0x10(%rbp)
    1a86:   0f b6 45 f2             movzbl -0xe(%rbp),%eax
    1a8a:   84 c0                   test   %al,%al
    1a8c:   79 10                   jns    1a9e <sleep@plt+0x92e>
    1a8e:   48 8b 45 f8             mov    -0x8(%rbp),%rax
    1a92:   48 8b 75 f0             mov    -0x10(%rbp),%rsi
    1a96:   48 89 c7                mov    %rax,%rdi
    1a99:   e8 c1 f9 ff ff          callq  145f <interpret_imm>
    1a9e:   0f b6 45 f2             movzbl -0xe(%rbp),%eax
    1aa2:   0f b6 c0                movzbl %al,%eax
    1aa5:   83 e0 10                and    $0x10,%eax
    1aa8:   85 c0                   test   %eax,%eax
    1aaa:   74 10                   je     1abc <sleep@plt+0x94c>
    1aac:   48 8b 45 f8             mov    -0x8(%rbp),%rax
    1ab0:   48 8b 75 f0             mov    -0x10(%rbp),%rsi
    1ab4:   48 89 c7                mov    %rax,%rdi
    1ab7:   e8 d6 f9 ff ff          callq  1492 <interpret_add>
    1abc:   0f b6 45 f2             movzbl -0xe(%rbp),%eax
    1ac0:   0f b6 c0                movzbl %al,%eax
    1ac3:   83 e0 08                and    $0x8,%eax
    1ac6:   85 c0                   test   %eax,%eax
    1ac8:   74 10                   je     1ada <sleep@plt+0x96a>
    1aca:   48 8b 45 f8             mov    -0x8(%rbp),%rax
    1ace:   48 8b 75 f0             mov    -0x10(%rbp),%rsi
    1ad2:   48 89 c7                mov    %rax,%rdi
    1ad5:   e8 1b fa ff ff          callq  14f5 <interpret_stk>
    1ada:   0f b6 45 f2             movzbl -0xe(%rbp),%eax
    1ade:   0f b6 c0                movzbl %al,%eax
    1ae1:   83 e0 20                and    $0x20,%eax
    1ae4:   85 c0                   test   %eax,%eax
    1ae6:   74 10                   je     1af8 <sleep@plt+0x988>
    1ae8:   48 8b 45 f8             mov    -0x8(%rbp),%rax
    1aec:   48 8b 75 f0             mov    -0x10(%rbp),%rsi
    1af0:   48 89 c7                mov    %rax,%rdi
    1af3:   e8 bc fa ff ff          callq  15b4 <interpret_stm>
    1af8:   0f b6 45 f2             movzbl -0xe(%rbp),%eax
    1afc:   0f b6 c0                movzbl %al,%eax
    1aff:   83 e0 01                and    $0x1,%eax
    1b02:   85 c0                   test   %eax,%eax
    1b04:   74 10                   je     1b16 <sleep@plt+0x9a6>
    1b06:   48 8b 45 f8             mov    -0x8(%rbp),%rax
    1b0a:   48 8b 75 f0             mov    -0x10(%rbp),%rsi
    1b0e:   48 89 c7                mov    %rax,%rdi
    1b11:   e8 fb fa ff ff          callq  1611 <interpret_ldm>
    1b16:   0f b6 45 f2             movzbl -0xe(%rbp),%eax
    1b1a:   0f b6 c0                movzbl %al,%eax
    1b1d:   83 e0 40                and    $0x40,%eax
    1b20:   85 c0                   test   %eax,%eax
    1b22:   74 10                   je     1b34 <sleep@plt+0x9c4>
    1b24:   48 8b 45 f8             mov    -0x8(%rbp),%rax
    1b28:   48 8b 75 f0             mov    -0x10(%rbp),%rsi
    1b2c:   48 89 c7                mov    %rax,%rdi
    1b2f:   e8 32 fb ff ff          callq  1666 <interpret_cmp>
    1b34:   0f b6 45 f2             movzbl -0xe(%rbp),%eax
    1b38:   0f b6 c0                movzbl %al,%eax
    1b3b:   83 e0 02                and    $0x2,%eax
    1b3e:   85 c0                   test   %eax,%eax
    1b40:   74 10                   je     1b52 <sleep@plt+0x9e2>
    1b42:   48 8b 45 f8             mov    -0x8(%rbp),%rax
    1b46:   48 8b 75 f0             mov    -0x10(%rbp),%rsi
    1b4a:   48 89 c7                mov    %rax,%rdi
    1b4d:   e8 18 fc ff ff          callq  176a <interpret_jmp>
    1b52:   0f b6 45 f2             movzbl -0xe(%rbp),%eax
    1b56:   0f b6 c0                movzbl %al,%eax
    1b59:   83 e0 04                and    $0x4,%eax
    1b5c:   85 c0                   test   %eax,%eax
    1b5e:   74 10                   je     1b70 <sleep@plt+0xa00>
    1b60:   48 8b 45 f8             mov    -0x8(%rbp),%rax
    1b64:   48 8b 75 f0             mov    -0x10(%rbp),%rsi
    1b68:   48 89 c7                mov    %rax,%rdi
    1b6b:   e8 4d fc ff ff          callq  17bd <interpret_sys>
    1b70:   90                      nop
    1b71:   c9                      leaveq 
    1b72:   c3                      retq
#interpret_loop
    1b73:   f3 0f 1e fa             endbr64 
    1b77:   55                      push   %rbp
    1b78:   48 89 e5                mov    %rsp,%rbp
    1b7b:   48 83 ec 20             sub    $0x20,%rsp
    1b7f:   48 89 7d e8             mov    %rdi,-0x18(%rbp)
    1b83:   48 8d 3d ae 04 00 00    lea    0x4ae(%rip),%rdi        # 2038 <sleep@plt+0xec8>
    1b8a:   e8 51 f5 ff ff          callq  10e0 <puts@plt>
    1b8f:   48 8b 45 e8             mov    -0x18(%rbp),%rax
    1b93:   0f b6 80 05 04 00 00    movzbl 0x405(%rax),%eax
    1b9a:   8d 48 01                lea    0x1(%rax),%ecx
    1b9d:   48 8b 55 e8             mov    -0x18(%rbp),%rdx
    1ba1:   88 8a 05 04 00 00       mov    %cl,0x405(%rdx)
    1ba7:   0f b6 c0                movzbl %al,%eax
    1baa:   48 8b 4d e8             mov    -0x18(%rbp),%rcx
    1bae:   48 63 d0                movslq %eax,%rdx
    1bb1:   48 89 d0                mov    %rdx,%rax
    1bb4:   48 01 c0                add    %rax,%rax
    1bb7:   48 01 d0                add    %rdx,%rax
    1bba:   48 01 c8                add    %rcx,%rax
    1bbd:   0f b7 10                movzwl (%rax),%edx
    1bc0:   66 89 55 fd             mov    %dx,-0x3(%rbp)
    1bc4:   0f b6 40 02             movzbl 0x2(%rax),%eax
    1bc8:   88 45 ff                mov    %al,-0x1(%rbp)
    1bcb:   48 8b 45 e8             mov    -0x18(%rbp),%rax
    1bcf:   0f b6 55 fd             movzbl -0x3(%rbp),%edx
    1bd3:   0f b6 4d fe             movzbl -0x2(%rbp),%ecx
    1bd7:   48 c1 e1 08             shl    $0x8,%rcx
    1bdb:   48 09 d1                or     %rdx,%rcx
    1bde:   0f b6 55 ff             movzbl -0x1(%rbp),%edx
    1be2:   48 c1 e2 10             shl    $0x10,%rdx
    1be6:   48 09 ca                or     %rcx,%rdx
    1be9:   48 89 d6                mov    %rdx,%rsi
    1bec:   48 89 c7                mov    %rax,%rdi
    1bef:   e8 7e fe ff ff          callq  1a72 <sleep@plt+0x902>
    1bf4:   eb 99                   jmp    1b8f <sleep@plt+0xa1f>
#main
    1bf6:   f3 0f 1e fa             endbr64 
    1bfa:   55                      push   %rbp
    1bfb:   48 89 e5                mov    %rsp,%rbp
    1bfe:   48 81 ec 20 04 00 00    sub    $0x420,%rsp
    1c05:   89 bd ec fb ff ff       mov    %edi,-0x414(%rbp)
    1c0b:   48 89 b5 e0 fb ff ff    mov    %rsi,-0x420(%rbp)
    1c12:   64 48 8b 04 25 28 00    mov    %fs:0x28,%rax
    1c19:   00 00 
    1c1b:   48 89 45 f8             mov    %rax,-0x8(%rbp)
    1c1f:   31 c0                   xor    %eax,%eax
    1c21:   48 8b 85 e0 fb ff ff    mov    -0x420(%rbp),%rax
    1c28:   48 8b 00                mov    (%rax),%rax
    1c2b:   48 89 c6                mov    %rax,%rsi
    1c2e:   48 8d 3d 2d 04 00 00    lea    0x42d(%rip),%rdi        # 2062 <sleep@plt+0xef2>
    1c35:   b8 00 00 00 00          mov    $0x0,%eax
    1c3a:   e8 d1 f4 ff ff          callq  1110 <printf@plt>
    1c3f:   48 8d 3d 32 04 00 00    lea    0x432(%rip),%rdi        # 2078 <sleep@plt+0xf08>
    1c46:   e8 95 f4 ff ff          callq  10e0 <puts@plt>
    1c4b:   48 8d 3d 76 04 00 00    lea    0x476(%rip),%rdi        # 20c8 <sleep@plt+0xf58>
    1c52:   e8 89 f4 ff ff          callq  10e0 <puts@plt>
    1c57:   48 8d 3d b2 04 00 00    lea    0x4b2(%rip),%rdi        # 2110 <sleep@plt+0xfa0>
    1c5e:   e8 7d f4 ff ff          callq  10e0 <puts@plt>
    1c63:   48 8d 3d f6 04 00 00    lea    0x4f6(%rip),%rdi        # 2160 <sleep@plt+0xff0>
    1c6a:   e8 71 f4 ff ff          callq  10e0 <puts@plt>
    1c6f:   48 8d 3d 3a 05 00 00    lea    0x53a(%rip),%rdi        # 21b0 <sleep@plt+0x1040>
    1c76:   e8 65 f4 ff ff          callq  10e0 <puts@plt>
    1c7b:   48 8d 3d 6b 05 00 00    lea    0x56b(%rip),%rdi        # 21ed <sleep@plt+0x107d>
    1c82:   e8 59 f4 ff ff          callq  10e0 <puts@plt>
    1c87:   48 8d 3d 6a 05 00 00    lea    0x56a(%rip),%rdi        # 21f8 <sleep@plt+0x1088>
    1c8e:   e8 4d f4 ff ff          callq  10e0 <puts@plt>
    1c93:   48 8d 3d ae 05 00 00    lea    0x5ae(%rip),%rdi        # 2248 <sleep@plt+0x10d8>
    1c9a:   e8 41 f4 ff ff          callq  10e0 <puts@plt>
    1c9f:   48 8b 05 da 26 00 00    mov    0x26da(%rip),%rax        # 4380 <stdout@@GLIBC_2.2.5>
    1ca6:   b9 01 00 00 00          mov    $0x1,%ecx
    1cab:   ba 02 00 00 00          mov    $0x2,%edx
    1cb0:   be 00 00 00 00          mov    $0x0,%esi
    1cb5:   48 89 c7                mov    %rax,%rdi
    1cb8:   e8 83 f4 ff ff          callq  1140 <setvbuf@plt>
    1cbd:   48 8d 95 f0 fb ff ff    lea    -0x410(%rbp),%rdx
    1cc4:   b8 00 00 00 00          mov    $0x0,%eax
    1cc9:   b9 80 00 00 00          mov    $0x80,%ecx
    1cce:   48 89 d7                mov    %rdx,%rdi
    1cd1:   f3 48 ab                rep stos %rax,%es:(%rdi)
    1cd4:   48 89 fa                mov    %rdi,%rdx
    1cd7:   89 02                   mov    %eax,(%rdx)
    1cd9:   48 83 c2 04             add    $0x4,%rdx
    1cdd:   66 89 02                mov    %ax,(%rdx)
    1ce0:   48 83 c2 02             add    $0x2,%rdx
    1ce4:   88 02                   mov    %al,(%rdx)
    1ce6:   48 83 c2 01             add    $0x1,%rdx
    1cea:   8b 05 74 25 00 00       mov    0x2574(%rip),%eax        # 4264 <sleep@plt+0x30f4>
    1cf0:   89 c2                   mov    %eax,%edx
    1cf2:   48 8d 85 f0 fb ff ff    lea    -0x410(%rbp),%rax
    1cf9:   48 8d 35 20 23 00 00    lea    0x2320(%rip),%rsi        # 4020 <sleep@plt+0x2eb0>
    1d00:   48 89 c7                mov    %rax,%rdi
    1d03:   e8 28 f4 ff ff          callq  1130 <memcpy@plt>
    1d08:   48 8b 05 71 25 00 00    mov    0x2571(%rip),%rax        # 4280 <sleep@plt+0x3110>
    1d0f:   48 8b 15 72 25 00 00    mov    0x2572(%rip),%rdx        # 4288 <sleep@plt+0x3118>
    1d16:   48 89 85 f0 fe ff ff    mov    %rax,-0x110(%rbp)
    1d1d:   48 89 95 f8 fe ff ff    mov    %rdx,-0x108(%rbp)
    1d24:   48 8b 05 65 25 00 00    mov    0x2565(%rip),%rax        # 4290 <sleep@plt+0x3120>
    1d2b:   48 8b 15 66 25 00 00    mov    0x2566(%rip),%rdx        # 4298 <sleep@plt+0x3128>
    1d32:   48 89 85 00 ff ff ff    mov    %rax,-0x100(%rbp)
    1d39:   48 89 95 08 ff ff ff    mov    %rdx,-0xf8(%rbp)
    1d40:   48 8b 05 59 25 00 00    mov    0x2559(%rip),%rax        # 42a0 <sleep@plt+0x3130>
    1d47:   48 8b 15 5a 25 00 00    mov    0x255a(%rip),%rdx        # 42a8 <sleep@plt+0x3138>
    1d4e:   48 89 85 10 ff ff ff    mov    %rax,-0xf0(%rbp)
    1d55:   48 89 95 18 ff ff ff    mov    %rdx,-0xe8(%rbp)
    1d5c:   48 8b 05 4d 25 00 00    mov    0x254d(%rip),%rax        # 42b0 <sleep@plt+0x3140>
    1d63:   48 8b 15 4e 25 00 00    mov    0x254e(%rip),%rdx        # 42b8 <sleep@plt+0x3148>
    1d6a:   48 89 85 20 ff ff ff    mov    %rax,-0xe0(%rbp)
    1d71:   48 89 95 28 ff ff ff    mov    %rdx,-0xd8(%rbp)
    1d78:   48 8b 05 41 25 00 00    mov    0x2541(%rip),%rax        # 42c0 <sleep@plt+0x3150>
    1d7f:   48 8b 15 42 25 00 00    mov    0x2542(%rip),%rdx        # 42c8 <sleep@plt+0x3158>
    1d86:   48 89 85 30 ff ff ff    mov    %rax,-0xd0(%rbp)
    1d8d:   48 89 95 38 ff ff ff    mov    %rdx,-0xc8(%rbp)
    1d94:   48 8b 05 35 25 00 00    mov    0x2535(%rip),%rax        # 42d0 <sleep@plt+0x3160>
    1d9b:   48 8b 15 36 25 00 00    mov    0x2536(%rip),%rdx        # 42d8 <sleep@plt+0x3168>
    1da2:   48 89 85 40 ff ff ff    mov    %rax,-0xc0(%rbp)
    1da9:   48 89 95 48 ff ff ff    mov    %rdx,-0xb8(%rbp)
    1db0:   48 8b 05 29 25 00 00    mov    0x2529(%rip),%rax        # 42e0 <sleep@plt+0x3170>
    1db7:   48 8b 15 2a 25 00 00    mov    0x252a(%rip),%rdx        # 42e8 <sleep@plt+0x3178>
    1dbe:   48 89 85 50 ff ff ff    mov    %rax,-0xb0(%rbp)
    1dc5:   48 89 95 58 ff ff ff    mov    %rdx,-0xa8(%rbp)
    1dcc:   48 8b 05 1d 25 00 00    mov    0x251d(%rip),%rax        # 42f0 <sleep@plt+0x3180>
    1dd3:   48 8b 15 1e 25 00 00    mov    0x251e(%rip),%rdx        # 42f8 <sleep@plt+0x3188>
    1dda:   48 89 85 60 ff ff ff    mov    %rax,-0xa0(%rbp)
    1de1:   48 89 95 68 ff ff ff    mov    %rdx,-0x98(%rbp)
    1de8:   48 8b 05 11 25 00 00    mov    0x2511(%rip),%rax        # 4300 <sleep@plt+0x3190>
    1def:   48 8b 15 12 25 00 00    mov    0x2512(%rip),%rdx        # 4308 <sleep@plt+0x3198>
    1df6:   48 89 85 70 ff ff ff    mov    %rax,-0x90(%rbp)
    1dfd:   48 89 95 78 ff ff ff    mov    %rdx,-0x88(%rbp)
    1e04:   48 8b 05 05 25 00 00    mov    0x2505(%rip),%rax        # 4310 <sleep@plt+0x31a0>
    1e0b:   48 8b 15 06 25 00 00    mov    0x2506(%rip),%rdx        # 4318 <sleep@plt+0x31a8>
    1e12:   48 89 45 80             mov    %rax,-0x80(%rbp)
    1e16:   48 89 55 88             mov    %rdx,-0x78(%rbp)
    1e1a:   48 8b 05 ff 24 00 00    mov    0x24ff(%rip),%rax        # 4320 <sleep@plt+0x31b0>
    1e21:   48 8b 15 00 25 00 00    mov    0x2500(%rip),%rdx        # 4328 <sleep@plt+0x31b8>
    1e28:   48 89 45 90             mov    %rax,-0x70(%rbp)
    1e2c:   48 89 55 98             mov    %rdx,-0x68(%rbp)
    1e30:   48 8b 05 f9 24 00 00    mov    0x24f9(%rip),%rax        # 4330 <sleep@plt+0x31c0>
    1e37:   48 8b 15 fa 24 00 00    mov    0x24fa(%rip),%rdx        # 4338 <sleep@plt+0x31c8>
    1e3e:   48 89 45 a0             mov    %rax,-0x60(%rbp)
    1e42:   48 89 55 a8             mov    %rdx,-0x58(%rbp)
    1e46:   48 8b 05 f3 24 00 00    mov    0x24f3(%rip),%rax        # 4340 <sleep@plt+0x31d0>
    1e4d:   48 8b 15 f4 24 00 00    mov    0x24f4(%rip),%rdx        # 4348 <sleep@plt+0x31d8>
    1e54:   48 89 45 b0             mov    %rax,-0x50(%rbp)
    1e58:   48 89 55 b8             mov    %rdx,-0x48(%rbp)
    1e5c:   48 8b 05 ed 24 00 00    mov    0x24ed(%rip),%rax        # 4350 <sleep@plt+0x31e0>
    1e63:   48 8b 15 ee 24 00 00    mov    0x24ee(%rip),%rdx        # 4358 <sleep@plt+0x31e8>
    1e6a:   48 89 45 c0             mov    %rax,-0x40(%rbp)
    1e6e:   48 89 55 c8             mov    %rdx,-0x38(%rbp)
    1e72:   48 8b 05 e7 24 00 00    mov    0x24e7(%rip),%rax        # 4360 <sleep@plt+0x31f0>
    1e79:   48 8b 15 e8 24 00 00    mov    0x24e8(%rip),%rdx        # 4368 <sleep@plt+0x31f8>
    1e80:   48 89 45 d0             mov    %rax,-0x30(%rbp)
    1e84:   48 89 55 d8             mov    %rdx,-0x28(%rbp)
    1e88:   48 8b 05 e1 24 00 00    mov    0x24e1(%rip),%rax        # 4370 <sleep@plt+0x3200>
    1e8f:   48 8b 15 e2 24 00 00    mov    0x24e2(%rip),%rdx        # 4378 <sleep@plt+0x3208>
    1e96:   48 89 45 e0             mov    %rax,-0x20(%rbp)
    1e9a:   48 89 55 e8             mov    %rdx,-0x18(%rbp)
    1e9e:   48 8d 85 f0 fb ff ff    lea    -0x410(%rbp),%rax
    1ea5:   48 89 c7                mov    %rax,%rdi
    1ea8:   e8 c6 fc ff ff          callq  1b73 <sleep@plt+0xa03>
    1ead:   b8 00 00 00 00          mov    $0x0,%eax
    1eb2:   48 8b 4d f8             mov    -0x8(%rbp),%rcx
    1eb6:   64 48 33 0c 25 28 00    xor    %fs:0x28,%rcx
    1ebd:   00 00 
    1ebf:   74 05                   je     1ec6 <sleep@plt+0xd56>
    1ec1:   e8 3a f2 ff ff          callq  1100 <__stack_chk_fail@plt>
    1ec6:   c9                      leaveq 
    1ec7:   c3                      retq

    1ec8:   0f 1f 84 00 00 00 00    nopl   0x0(%rax,%rax,1)
    1ecf:   00 
    1ed0:   f3 0f 1e fa             endbr64 
    1ed4:   41 57                   push   %r15
    1ed6:   4c 8d 3d 93 1e 00 00    lea    0x1e93(%rip),%r15        # 3d70 <sleep@plt+0x2c00>
    1edd:   41 56                   push   %r14
    1edf:   49 89 d6                mov    %rdx,%r14
    1ee2:   41 55                   push   %r13
    1ee4:   49 89 f5                mov    %rsi,%r13
    1ee7:   41 54                   push   %r12
    1ee9:   41 89 fc                mov    %edi,%r12d
    1eec:   55                      push   %rbp
    1eed:   48 8d 2d 84 1e 00 00    lea    0x1e84(%rip),%rbp        # 3d78 <sleep@plt+0x2c08>
    1ef4:   53                      push   %rbx
    1ef5:   4c 29 fd                sub    %r15,%rbp
    1ef8:   48 83 ec 08             sub    $0x8,%rsp
    1efc:   e8 ff f0 ff ff          callq  1000 <__cxa_finalize@plt-0xd0>
    1f01:   48 c1 fd 03             sar    $0x3,%rbp
    1f05:   74 1f                   je     1f26 <sleep@plt+0xdb6>
    1f07:   31 db                   xor    %ebx,%ebx
    1f09:   0f 1f 80 00 00 00 00    nopl   0x0(%rax)
    1f10:   4c 89 f2                mov    %r14,%rdx
    1f13:   4c 89 ee                mov    %r13,%rsi
    1f16:   44 89 e7                mov    %r12d,%edi
    1f19:   41 ff 14 df             callq  *(%r15,%rbx,8)
    1f1d:   48 83 c3 01             add    $0x1,%rbx
    1f21:   48 39 dd                cmp    %rbx,%rbp
    1f24:   75 ea                   jne    1f10 <sleep@plt+0xda0>
    1f26:   48 83 c4 08             add    $0x8,%rsp
    1f2a:   5b                      pop    %rbx
    1f2b:   5d                      pop    %rbp
    1f2c:   41 5c                   pop    %r12
    1f2e:   41 5d                   pop    %r13
    1f30:   41 5e                   pop    %r14
    1f32:   41 5f                   pop    %r15
    1f34:   c3                      retq   
    1f35:   66 66 2e 0f 1f 84 00    data16 nopw %cs:0x0(%rax,%rax,1)
    1f3c:   00 00 00 00 
    1f40:   f3 0f 1e fa             endbr64 
    1f44:   c3                      retq   

Disassembly of section .fini:

0000000000001f48 <.fini>:
    1f48:   f3 0f 1e fa             endbr64 
    1f4c:   48 83 ec 08             sub    $0x8,%rsp
    1f50:   48 83 c4 08             add    $0x8,%rsp
    1f54:   c3                      retq   

