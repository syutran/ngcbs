# ngcbs 山东农信新一代综合业务系统安装及运行维护


***
### HOSTNAME 问题需要修改的文件
```
/etc/sysconfig/network
/etc/hosts
```
临时修改可用 
```
# hostname dtnshy_11
```
*** 
### TRAMS AGENT 安装
将  trams_agent_setup.tar 上传到服务器 /usr/trams 目录
```
# tar xvf trams_agent_setup.tar
# ./trams_setup.sh

------------- Agent Installation Menu -------------
0. Quit to OS
1. Install TRAMS agent
2. Reinstall OS scripts
3. Reinstall database scripts
4. Re-Config TRAMS agent
5. Uninstall TRAMS agent
6. Create Installation Package (Only for developer)
7. Start TRAMS service
8. Stop TRAMS service
9. Current TRAMS service status
10.View all the configuration
11.TCP monitor sub-menu(For Redhat, AIX, SunOS, HP-UX)
Please select(0~11):

1－安装，7－启动，

```
生成 /etc/trams_profile 文件，``
```
# the trams working path
TRAMS_WORKPATH /usr/trams
# the listening port for trams working service
WRK_PORT 39900
# the trams temporary data path
DATAPATH /usr/trams/data
# the log filename of trams service 
LOGFILE /usr/trams/log/trams.log
# the maximum size (KB) of trams log file 
LOGSIZE 1024
# ethernet name
ETHERNET eth0
```
***
### 需要单独安装的包
#### Ksh
为什么要安装KSH，可能为了统一使用~/.profile
```
yum install ksh
or
rpm -ivh ksh-20120801-33.el6.i686.rpm
```
ksh 的执行顺序
***
### 文件传输ESBFTS（摸索的）
NGCBS的文件传输并不使用系统的FTP ，自带的ftp_exe就是proftpd的老版本，由ngcbs用户在启动文件传输时启动，所以不要另外再安装proftpd 这个也不影响系统的vsftpd的运行 使用的端口10200不一样。
ftp_exe 不执行，需要安装 libpam.so.0 --yum install libpam.so.0
***

