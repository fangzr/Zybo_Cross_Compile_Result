### 关于文件夹内容
- 内核文件含mt7601u驱动和rt2800驱动
- 设备树是编译内核步骤生成的，添加了别的PL部分情况下，必须自己用SDK生成dtb的替代！
- debian文件系统下载[linaro-jessie-developer-20161117-32.tar.gz](http://releases.linaro.org/debian/images/developer-armhf/17.02/linaro-jessie-developer-20161117-32.tar.gz "linaro-jessie-developer-20161117-32.tar.gz")

### 使用方法
 1. 三个文件放在SD卡FAT32分区即可
 
 2. 文件系统解压到EXT4分区：
 `sudo tar xf linaro-jessie-developer-20161117-32.tar.gz --strip-components=1 -C <path>/ROOT_FS/`
 
 3. 直接拖拽复制文件没有权限使用以下命令(不怕麻烦也可以root下的指令对文件操作)：
 ```
 sudo chmod 777 EXT4分区路径
 sudo chown -R 非root用户 EXT4分区路径
 ```
 
 4. 参考教程：[https://github.com/SDU-Embedded/linux_zynq/wiki/Installing-Linux-on-the-ZYBO](https://github.com/SDU-Embedded/linux_zynq/wiki/Installing-Linux-on-the-ZYBO)
