# C-libUsage
一些开源库的使用方法介绍和实例

常用依赖包：
```sh
brew install glog # 安装到了 /usr/local/Cellar/glog/0.3.5_3
brew install libevent # 安装到了 /usr/local/Cellar/libevent/2.1.8
brew install gcc make cmake
brew install boost # 安装到了 /usr/local/Cellar/boost/1.66.0
# 将 gtest 安装到根目录下
git clone https://github.com/google/googletest.git
cd googletest/googletest && mkdir bld && cd bld
cmake .. && make -j
cp -a ../include/gtest ~/include
cp -a *.a ~/lib
cd ../../googlemock && mkdir bld && cd bld
cmake .. && make -j
cp -a ../include/gmock ~/include
cp -a *.a ~/lib
```

## 基于C++11 的高性能网络服务器 evpp
项目简介： evpp 是一个基于 libevent 开发的现代化 C++11 高性能网络服务器，自带 TCP/UDP/HTTP 等协议的异步非阻塞式的服务器和客户端库，具有如下特性：
现代版的 C++11接口
非阻塞异步接口都是 C++11 的 functional/bind 形式的回调仿函数（不是 libevent 中的C风格的函数指针）
CPU 多核友好和线程安全
非阻塞纯异步多线程 TCP 服务器/客户端
非阻塞纯异步多线程 HTTP 服务器/客户端
非阻塞纯异步多线程 UDP 服务器
支持多进程模式
优秀的跨平台特性和高性能（继承自 libevent 的优点）
已经经过详尽的测试，并已经用于生产环境，每天承载数万亿次的网络通信
非常容易安装和集成，evpp 能够很容易就打包出 deb/rpm/tar.gz 等格式的安装包
项目地址：
https://gitee.com/zieckey/evpp

读后感：看起来挺好用的，但是编译过不了，等编译没问题了再看吧。

### 代码下载和安装
```sh
git clone https://github.com/Qihoo360/evpp
cd evpp && git submodule update --init --recursive
mkdir -p build && cd build
cmake -DCMAKE_BUILD_TYPE=Debug ..
make -j4 && make test #编译有错放弃！开源工程做得不够兼容。
# server_status.h:28:9: error: multiple conversions from switch condition type 'const std::atomic<Status>' to an integral or enumeration type
```


## 简洁易用的 C++11 网络库 handy [亲测可用]
项目简介： 本项目是一个简洁易用的 C++11网络库，主要特性如下所示：
支持单机千万并发连接
多平台支持
支持优雅退出
高性能
支持半同步半异步处理
openssl 支持
protobuf 支持
udp 支持
项目地址： https://gitee.com/yedf/handy
拉取过来： https://gitee.com/heliangHIT/handy

编译安装：`make` (不建议安装 `make install`， 当成库用就可以了)
编码测试（含命令）：[./demo/handy/main.cpp](./demo/handy/main.cpp)
用后感：使用方法挺简单的，用起来很方便很不错。


## JSON for Modern C++ [亲测可用]
JSON for Modern C++ 是一个由德国大牛 nlohmann 编写的在 C++ 下使用的 JSON 库。
具有以下特点
直观的语法
整个代码由一个头文件组成 json.hpp，没有子项目，没有依赖关系，没有复杂的构建系统，使用起来非常方便
使用 C++ 11 标准编写
使用 json 像使用 STL 容器一样
STL 和 json 容器之间可以相互转换
严谨的测试：所有类都经过严格的单元测试，覆盖了 100％ 的代码，包括所有特殊的行为。此外，还检查了 Valgrind 是否有内存泄漏。为了保持高质量，该项目遵循核心基础设施倡议(CII)的最佳实践
项目地址： https://github.com/nlohmann/json
fork项目地址： https://github.com/HeLiangHIT/json

编译安装：这个工程的使用只需要一个头文件，无需编译和安装！非常简单，下面的命令是编译测试代码而已。
```
mkdir build && cd build
cmake .. && cmake --build .
```
还有很多高级的用法参考readme。
编码测试（含命令）：[./demo/json/main.cpp](./demo/json/main.cpp)
用后感：没有比这个更好用的c++json库了！只需要头文件就可以了！




