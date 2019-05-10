#### wireless tools工具移植
##### 介绍

Wireless tools for Linux是一个Linux命令行工具包，用来设置支持Linux Wireless Extension的无线设备。
| 命令     | 功能                            |
|----------|-------------------------------|
| iwconfig | 设置基本无线参数                |
| iwlist   | 扫描、列出频率，比特率，密钥等     |
| iwspy    | 获取每个节点链接的质量          |
| iwpriv   | 操作WirelessExtensions 特定驱动 |
| ifrename | 基于各种静态标准命名接口        |

- 版本 ：29

- 官网介绍：https://hewlettpackard.github.io/wireless-tools/Tools.html

- 源码下载地址 ： https://hewlettpackard.github.io/wireless-tools/wireless_tools.29.tar.gz

##### 编译步骤
1. 进入wireless_tools.29目录
2. 修改Makefile

`vim Makefile`

3. 修改位置如下：

``` Makefile
CC = arm-linux-gnueabihf-gcc
AR = arm-linux-gnueabihf-ar
RANLIB=arm-linux-gnueabihf-ranlib
```
> ***Note:*** 
>1. 确认 ～/.bashrc添加了一下内容
`export PATH=$PATH:/opt/Xilinx/SDK/2017.4/gnu/aarch32/lin/gcc-arm-linux-gnueabi/bin/`
`export CROSS_COMPILE=arm-linux-gnueabihf-`
>2. 否则执行 `source /opt/Xilinx/Vivado/2017.4/settings64.sh`

---
3. 输入`make`开始编译

4. 将生成的工具`ifrename, iwconfig, iwevent, iwgetid, iwlist, iwpriv, iwspy`可执行文件拷贝到根文件系统目录/bin目录
5. 将`iwlib.so、libiw.so.29`动态库文件放在开发板/lib文件夹
6. 在开发板终端输入`iwlist`等命令查看是否移植成功

```
root@Zybo:~# iwlist                                                             
Usage: iwlist [interface] scanning [essid NNN] [last]                           
              [interface] frequency                                             
              [interface] channel                                               
              [interface] bitrate                                               
              [interface] rate                                                  
              [interface] encryption                                            
              [interface] keys                                                  
              [interface] power                                                 
              [interface] txpower                                               
              [interface] retry                                                 
              [interface] ap                                                    
              [interface] accesspoints                                          
              [interface] peers                                                 
              [interface] event                                                 
              [interface] auth                                                  
              [interface] wpakeys                                               
              [interface] genie                                                 
              [interface] modulation  
```
