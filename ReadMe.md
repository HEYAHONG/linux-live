# [原版说明](README)

# [许可](DOC/LICENSE)

# 说明

Linux Live一般指无需安装，可直接运行的Linux运行方式，类似于Windows PE的运行方式，一般安装在USB存储设备上，不影响原有硬盘系统。

此工具可将正在运行的Linux系统打包成Linux Live系统。

此工具可支持以下运行模式：

- Live(纯内存)模式：所有文件都在内存中。通常适用于从网络启动。现在PC的内存越来越大（如8G、16G、32G），此方式用于将系统完全加载至内存提高速度。需要在内核启动参数中添加`toram`。
- 传统Live模式：文件仍然保存在存储介质（如USB存储介质）上，新创建的文件/修改的文件保存在内存中，重启后修改的设置失效。此模式下不能添加其它模式需要的内核启动参数。
- Live(持久存储)模式:此模式与传统Live模式的区别在于，对系统的修改将被保存在存储介质（如USB存储介质）上。需要在内核启动参数中添加`perch`。

# 使用步骤

## 前期准备

- 安装需要打包的软件。
- 清理系统中不需要的文件（如对于Debian系而言的apt缓存）。
- 下载本源代码（推荐下载至根目录，这样本源代码就不会被打包至Linux Live中）。

## 打包

- 修改[config](config)，根据自己的需要定制设置。注意：此文件不仅在打包时使用，也会打包在Linux Live系统中，因此，对变量的使用要考虑不同的环境。
- 运行build脚本。
- 根据build脚本的提示生成最终的文件(iso镜像文件/zip文件)。

## 使用

- 见最终打包文件的[readme.txt](bootinfo.txt).
- 其核心为vmlinuz与initrfs.img文件，这两个文件可用于第一阶段的加载,第一阶段加载完成后，可通过多种方式(如网络启动)加载打包的系统。

# 脚本说明

- [build](build):打包当前系统。
- [configure](configure):生成适合当前系统的推荐配置（默认文件名为config.tmp,用户可自行选择是否替换原config），现适用于ubuntu(24.04及更新版本)。
