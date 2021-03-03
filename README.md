# 笔记

## 1、pyinstaller 打包 qt5 OSError:[WinError6]句柄无效
    使用python3.7 qt5 时， 如果只是-F 没问题，但是会出现控制台；加上-w（-noconsole）之后，闪退。将问题print到文件发现在 QThread 里面的调用Google语音识别的一句话出现 OSError:[WinError6]句柄无效 的问题。找遍网络，大部分人是在subprocess里面出现的，解决方法无法转移到这个上面。最后发现，取消-F，只-w的话，问题解决。虽然不是一个文件，但是问题不大。

## 2、python import 自己写的文件时报错
    从网上看来得方法。建立一个__init__.py文件， 里面写上：
    import os, sys; sys.path.append(os.path.dirname(os.path.realpath(__file__)))
    解决问题。

## 3、如何创建相对路径快捷方式
    首先建立一个快捷方式
    打开改快捷方式的属性
    设置“目标”为：%windir%\system32\cmd.exe /c start your_relpath\app.exe [your_args]
    或者 设置“目标”为： %SystemRoot%\explorer.exe "your_relpath\app.exe [your_args]"

## 4、关于python打包之后，相对路径快捷方式得到的路径不正确的问题
    sys.path[0]在Python脚本文件中返回的是文件夹的路径E:\test（脚本路径为E:\test\updater.py），而通过py2exe打包后的exe文件返回的却是该exe的路径E:\test\updater.exe（exe程序路径为E:\test\updater.exe），为了兼容这两种方式写了一个函数用于获取当前路径：

    def getpwd():
        pwd = sys.path[0]
        if os.path.isfile(pwd):
            pwd = os.path.dirname(pwd)
        return pwd
    来自https://groups.google.com/forum/#!topic/python-cn/_NW0NJvpNrU
    
    注：如果使用%SystemRoot%\explorer.exe "your_relpath\app.exe [your_args]"创建快捷方式， 则程序内部建立文件需都改为绝对路径。
 
## 5、clion 项目启动后无法找到header
    在cmakelist里面加入
    include_directories("/usr/include/eigen") 
    build
    然后去掉这句
    build
    好了
