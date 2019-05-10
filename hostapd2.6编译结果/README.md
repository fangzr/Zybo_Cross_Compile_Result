#### hostapd的移植

- 版本：2.6
- 下载：`git clone git@github.com:fangzr/hostapd.git `

##### 编译步骤

1. 解压源码包，在此路径打开终端，将上面编译好的libnl路径加入环境变量
`export PKG_CONFIG_PATH=/.../libnl-3.2.23`
2. 进入`hosdtapd-2.6/hostapd`，执行`cp defconfig .config`
3. 打开`.config`文件，完成以下修改：
- 加入以下内容（‘...’根据自己libnl、openssl源码路径修改）
```
CC=arm-linux-gnueabihf-gcc		
CFLAGS += -I/.../libnl-3.2.23/install/include/libnl3		
CFLAGS += -I/.../openssl-1.0.1g/install/include		
LIBS += -L/.../libnl-3.2.23/install/lib		
LDFLAGS += -L/.../libnl-3.2.23/install/lib		
LIBS += -L/.../openssl-1.0.1g/install/lib		
LDFLAGS += -L/.../openssl-1.0.1g/install/lib
```
- 将`CONFIG_LIBNL32=y`注释去掉，使得hostapd编译自动寻找libnl3的库

4. 保存`.congfig`，执行`make`开始编译
5. 没有错误提示情况下，在源码路径可以找到`hostapd`、`hostapd_cli`两个可执行文件，将它们全部复制到Zybo文件系统的`/bin`路径下面
