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
    
