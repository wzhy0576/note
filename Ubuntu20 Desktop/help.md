### ubuntu18.04、20.04 磁盘分区并挂载到home下(更换home的挂载分区)

https://blog.csdn.net/u011932817/article/details/102878605



### Git for Linux

https://zhuanlan.zhihu.com/p/137578868

config user :

https://blog.csdn.net/seamanj/article/details/50682542



### Typora for Linux

https://typora.io/#linux



### ubuntu apt-get指令的autoclean,clean,autoremove的区别

https://blog.csdn.net/ever_peng/article/details/79387745



### How to Install Windows 10 in a Virtual Machine

https://www.extremetech.com/computing/198427-how-to-install-windows-10-in-a-virtual-machine



### ubuntu20.04开机进入引导菜单选择界面

https://jingyan.baidu.com/article/00a07f38941a67c3d028dcc6.html



### GTK+3.0 Quick Start

https://developer.gnome.org/gtk3/stable

https://www.cnblogs.com/niocai/archive/2011/07/15/2107472.html



### Use GTK+3.0 in Clion

```sh
sudo apt install libgtk3.0-dev
pkg-config --cflags gtk+-3.0
pkg-config --libs gtk+-3.0
```

CMakeLists.txt

```cmake
cmake_minimum_required(VERSION 3.17)
project(demo C)

set(CMAKE_C_STANDARD 99)
find_package(PkgConfig REQUIRED)
pkg_check_modules(GTK3 REQUIRED gtk+-3.0)

include_directories(${GTK3_INCLUDE_DIRS})
link_directories(${GTK3_LIBRARY_DIRS})

add_definitions(${GTK3_CFLAGS_OTHER})
add_executable(demo main.c)
target_link_libraries(demo ${GTK3_LIBRARIES})
```

header

```c
#include <gtk/gtk.h>
```

