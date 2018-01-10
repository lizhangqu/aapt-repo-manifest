# aapt-repo-manifest

查看cmake构建脚本请转移至项目 [https://github.com/lizhangqu/aapt-cmake-buildscript](https://github.com/lizhangqu/aapt-cmake-buildscript)

## for mac

创建大小写敏感磁盘

```
hdiutil create -volname "aapt" -type SPARSE -fs 'Case-sensitive Journaled HFS+' -size 10g aapt.dmg
```

挂载

```
hdiutil attach aapt.dmg.sparseimage -mountpoint /Volumes/aapt
```

卸载

```
hdiutil detach /Volumes/aapt
```

## for linux(Ubuntu 16.0.4)

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install openjdk-8-jdk
sudo apt-get install cmake
sudo apt-get install clang
sudo apt-get install git-core gnupg flex bison gperf build-essential zip curl zlib1g-dev gcc-multilib g++-multilib libc6-dev-i386 lib32ncurses5-dev x11proto-core-dev libx11-dev lib32z-dev ccache libgl1-mesa-dev libxml2-utils xsltproc unzip
```

## for windows(Ubuntu 16.0.4下使用MinGw进行交叉编译)

当前windows可执行文件和动态库的版本只能在linux(Ubuntu 16.0.4)上进行交叉编译产生，需要安装MinGw

```
sudo apt-get install mingw-w64
```

安装完成后，mingw-gcc和mingw-g++默认使用的线程模型是win32的，但是我们需要使用posix的线程模型，因此分别执行以下命令，将工具链指向带-posix后缀的工具链

```
sudo update-alternatives --config x86_64-w64-mingw32-gcc
