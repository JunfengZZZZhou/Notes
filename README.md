# 笔记
====
## 1、pyinstaller 打包 qt5 OSError:[WinError6]句柄无效
    使用python3.7 qt5 时， 如果只是-F 没问题，但是会出现控制台；加上-w（-noconsole）之后，闪退。将问题print到文件发现在 QThread 里面的调用Google语音识别的一句话出现 OSError:[WinError6]句柄无效 的问题。找遍网络，大部分人是在subprocess里面出现的，解决方法无法转移到这个上面。最后发现，取消-F，只-w的话，问题解决。虽然不是一个文件，但是问题不大。
