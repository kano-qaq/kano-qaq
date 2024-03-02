.配置环境变量：export var_name=value
.空环境运行程序：env -i /pro_name_path
.指定环境变量运行：env -i var_name=value /pro_name_path
.作为程序输入：/pro_name_path < input_file_name
.作为程序输出：/pro_name_path > output_file_name
.ipython内运行程序：
	(1)In [1]:%alias tt /pro_name_path
	   In [2]:tt

	(2)import pwn
	   p=pwn.process(["/pro_name_path"],stdout=pwn.PIPE,stdin=pwn.PIPE)
	   p.read()

	(3)import subprocess
	   p=subprocess.Popen(["/pro_name_path"],stdout=subprocess.PIPE,stderr=subprocess.PIPE)
	   p.stdout.read()

.输入重定向
import pwn
with open("/file_path","w") as f:
	f.write("your_input")
p=pwn.process(["/pro_name_path"],stdin=open("/file_path"))

.带运行参数 指定环境变量
import glob
pwn.process(glob.glob("/pro_name_path")+["parameter"],env={"var_name":"value"})

.输出重定向
import pwn
import glob
pwn.process(glob.glob("/pro_name_path")+["parameter"],stdout=open("/file_path","w+"))

用system()/popen()运行的命令处于shell环境中。
exec()函数没有父子进程的概念，exec()函数用于替换当作正在执行的进程。
fork()函数执行时有父子进程的概念。

.用c打开二进制文件
#include<stdio.h>
#include<unistd.h>
#include<sys/types.h>
#include<sys/wait.h>
void function_name()
//execve
{
	char* argv[]={argv[0],argv[1],...,NULL};
	char* envp[]={0};
	execve("/file_path",argv,envp);
}
//other
char* argv[]={"/file_path","file_args",(char*)0};
char* envp[]={0};

execl("/file_path","file_path","file_args",(char*)0);

execv("/file_path",argv);

execle("/file_path","file_path","file_args",(char*)0,envp);


int main()
{
	int child_pid,status;
	child_pid=fork();
	if(child_pid==0)
		function_name();
	else
		waitpid(child_pid,&status,0);
	return 0;
}

.使用输入重定向
add include file
#include<stdlib.h>
#include<fcntl.h>
void function_name()
{
	char* argv[]={"/file_path","file_args",(char*)0};
	char* envp[]={0};
	int fd=open("/stdin_file_path",O_RDONLY);
	dup2(fd,STDIN_FILENO);
	close(fd);
	execve("/file_path",argv,envp);
}

.使用输出重定向
void function_name()
{
	int fd=open("/stdout_file_path",O_CREAT|O_RDWR,S_IUSER|S_IWUSR);
	dup2(fd,STDOUT_FILENO);
	close(fd);
	execve(...);
}

.dup2
实现传入文件描述符116
{
	dup2(0,116);
	execve("/file_path",0,0);
}

.使用管道符和cat命令输出程序结果
/pro_name_path | cat

.管道符和sed打印数据
/pro_name_path | sed /pwn/p
/pro_name_path | sed -e s/X/X/

.python实现管道符
//subprocess
import subporcess

p1=subprocess.Popen(["/file1_path"],stdout=subporcess.PIPE);
p2=subprocess.Popen(["/file2_path","arg0"],stdin=p1.stdout,stdout=subprocess.PIPE)
print(p2.communicate())

//pwn
import pwn
import glob

p2=pwn.process(["cat"])
p1=pwn.process(["/file1_path"],stdout=p2.stdin)
#cat | /file1_path
print(p2.readall())

.c实现管道符
//父子通信，父写，子读
int main()
{
	int fd[2];
	int ret=pipe(fd);
	if(ret==-1)
	{
		perror("pipe");
		exit(1);
	}
	pid_t pid=fork();
	if(pid>0)
	{
		//父进程-写
		close(fd[0]);
		char *p='hello\n';
		write(fd[1],p,strlen(p)+1);
		close(fd[0]);
		wait(NULL);
	}
	else if(pid==0)
	{
		//子进程-读
		close(fd[1]);
		char buf[64]={0};
		ret=read(fd[0],buf,sizeod(buf));
		close(fd[0]);
		write(STDOUT_FILEON,buf,ret);
	}
	return 0;
}

//兄弟进程通信，重定向
//ls | wc -l
int main()
{
	int fd[2];
	int ret=pipe(fd);
	if(ret==-1)
		exit(1);
	int i;
	pid_t pid,wpid;
	for(i=0;i<2;i++)
	{
		if((pid=fork())==0)
			break;
	}
	if(i==2)
	{
		close(fd[0]);
		close(fd[1]);
		wpid=wait(NULL);
		pid=wait(NULL);

	}
	else if(i==0)
	{
		close(fd[0]);
		dup2(fd[1],STDOUT_FILENO);
		execlp("ls","ls",NULL);
	}
	else if(i==1)
	{
		close(fd[1]);
		dup2(fd[0],STDIN_FILENO);
		execlp("wc","wc","-l",NULL);
	}
	return 0;
}

pwn.process(,cwd="/tmp") //改变子程序执行目录

.c改变当前目录
chdir("/path")

.命名管道
命名管道本质为文件，可以使用open()函数来作为输出/输入重定向。

.传入文件描述符
输入内容需要在文件中

.发送多个kill
p.recvuntil('PID ')
temp=p.recvuntil(')', drop=1)
pid=str(temp)
pid=pid[2:5]
p.recvuntil('order: ')
temp=p.recvuntil('\n',drop=1)

list_str=str(temp)
list_str=list_str[2:]
list_str=list_str[:len(list_str)-1] 
ser=eval(list_str)
exam=['SIGHUP','SIGINT','SIGQUIT','SIGILL','SIGTRAP','SIGABRT','SIGBUS','SIGFPE','SIGKILL','SIGUSR1','SIGSEGV','SIGUSR2','SIGPIPE','SIGALRM','SIGTERM','SIGSTKFLT','SIGCHLD','SIGCONT','SIGSTOP','SIGTSTP']
print(pid)
print('[')
for i in range(len(ser)):
    s=exam.index(ser[i])
    s+=1
    sh=['kill']
    ss='-'
    ss+=str(s)
    sh.append(ss)
    sh.append(pid) 
    print(sh)
    print(',')
print(']')

.多个计算
def format_input(input_re_value):
    input_re_value = input_re_value.replace(" ","")
    format_list = []
    for i in input_re_value:
        format_list.append(i)
    snum = 0
    while 1:
        try:
            if format_list[snum].isnumeric():
                if format_list[snum+1].isnumeric():
                    format_list[snum] = format_list[snum] + format_list[snum+1]
                    format_list.pop(snum+1)
                else:
                    snum += 1
            else:
                snum += 1
        except IndexError:
            return format_list
            break


def comput(re_value):
    while "*" in re_value or "/" in re_value:
        for i, j in enumerate(re_value):
            if j == "*":
                re_cheng = int(re_value[i - 1]) * int(re_value[i + 1])
                re_value.pop(i - 1)
                re_value.pop(i - 1)
                re_value.pop(i - 1)
                re_value.insert(i - 1, re_cheng)
                re_value.insert(0, 0)
                re_value.insert(0, 0)

            if j == "/":
                re_chu = float(re_value[i - 1]) / float(re_value[i + 1])
                re_value.pop(i - 1)
                re_value.pop(i - 1)
                re_value.pop(i - 1)
                re_value.insert(i - 1, re_chu)
                re_value.insert(0, 0)
                re_value.insert(0, 0)

    while "+" in re_value or "-" in re_value or "&" in re_value or "|" in re_value or "^" in re_value or "%" in re_value:
        for i, j in enumerate(re_value):
            if j == "+":
                re_jia = int(re_value[i - 1]) + int(re_value[i + 1])
                re_value.pop(i - 1)
                re_value.pop(i - 1)
                re_value.pop(i - 1)
                re_value.insert(i - 1, re_jia)
                re_value.insert(0, 0)
                re_value.insert(0, 0)
            if j == "-":
                re_jian = int(re_value[i - 1]) - int(re_value[i + 1])
                re_value.pop(i - 1)
                re_value.pop(i - 1)
                re_value.pop(i - 1)
                re_value.insert(i - 1, re_jian)
                re_value.insert(0, 0)
                re_value.insert(0, 0)
            if j=="%":
                re_yu=int(re_value[i-1])%int(re_value[i+1])
                re_value.pop(i - 1)
                re_value.pop(i - 1)
                re_value.pop(i - 1)
                re_value.insert(i - 1, re_yu)
                re_value.insert(0, 0)
                re_value.insert(0, 0)
            if j=="&":
                re_and=int(re_value[i-1])&int(re_value[i+1])
                re_value.pop(i - 1)
                re_value.pop(i - 1)
                re_value.pop(i - 1)
                re_value.insert(i - 1, re_and)
                re_value.insert(0, 0)
                re_value.insert(0, 0)
            if j=="|":
                re_or=int(re_value[i-1])|int(re_value[i+1])
                re_value.pop(i - 1)
                re_value.pop(i - 1)
                re_value.pop(i - 1)
                re_value.insert(i - 1, re_or)
                re_value.insert(0, 0)
                re_value.insert(0, 0)
            if j=="^":
                re_xor=int(re_value[i-1])^int(re_value[i+1])
                re_value.pop(i - 1)
                re_value.pop(i - 1)
                re_value.pop(i - 1)
                re_value.insert(i - 1, re_xor)
                re_value.insert(0, 0)
                re_value.insert(0, 0)

    return re_value[-1]

def bracket_filter(list1):
    while "(" in list1:
        i = list1.index(")")
        for m in range(i,-1,-1):
            if list1[m] == "(":
                list_new = list1[(m+1):i]
                re_res = comput(list_new)
                list1.insert(m,str(re_res))
                for item1 in range(i+1-m):
                    list1.pop(m+1)
                break
    return comput(list1)

def cal(input):
    t=format_input(input)
    r=bracket_filter(t)
    return r

for i in range(500):
    p.recvuntil("solution for: ")
    a=p.recvuntil('\n',drop=1)
    in_str=str(a)
    in_str=in_str[2:]
    in_str=in_str[:-1]
    res=cal(in_str)
    p.sendline(str(res))


