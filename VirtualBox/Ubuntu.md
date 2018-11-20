##Virtualbox Ubuntu 共享文件夹
* 在VirtualBox中选择设备-共享文件夹-共享文件夹  名字命名为UbuntuShared 只勾选固定分配
* 在Ubuntu虚拟机中，打开终端，获取root权限，输入以下命令： mkdir /mnt/UbuntuShared
* 挂载目录建立好以后，我们开始执行挂载操作 mount -t vboxsf UbuntuShared /mnt/UbuntuShare

##解决 Virtualbox 共享文件夹 cannot create symlink error 问题
* VBoxManage setextradata YOURVMNAME VBoxInternal2/SharedFoldersEnableSymlinksCreate/YOURSHAREFOLDERNAME 1
 	其中：YOURVMNAME为虚拟机中ubuntu系统的名称
	YOURSHAREFOLDERNAME 为共享的目录名称
* 以管理者身份运行” VirtualBox　即可
