# test

### Linux实现socks终端代理、全局代理
`https://cloud.tencent.com/developer/article/1852590`

git clone --recurse-submodules https://github.com/project-chip/connectedhomeip.git -b v1.1-branch

### arm版本lighting-app编译
gn gen out --args='target_cpu="arm64" target_os="linux"'

apt-get install g++-aarch64-linux-gnu gcc-aarch64-linux-gnu

#### 交叉编译ssl
wget https://www.openssl.org/source/old/1.1.1/openssl-1.1.1f.tar.gz
tar xzf openssl-1.1.1f.tar.gz
cd openssl-1.1.1f
./Configure linux-aarch64 --prefix=/usr/local/include/aarch64-linux-gnu/ssl --cross-compile-prefix=aarch64-linux-gnu- no-shared
make
make install

#### 交叉编译glib-2.0
wget https://download.gnome.org/sources/glib/2.64/glib-2.64.6.tar.xz
cd glib-2.64.6

https://docs.gtk.org/glib/cross-compiling.html

vim cross_file.txt
```
[host_machine]
system = 'linux'
cpu_family = 'aarch64'
cpu = 'aarch64'
endian = 'little'

[properties]
c_args = []
c_link_args = []
libelf = 'disabled'

[binaries]
c = 'aarch64-linux-gnu-gcc'
cpp = 'aarch64-linux-gnu-g++'
ar = 'aarch64-linux-gnu-ar'
ld = 'aarch64-linux-gnu-ld'
objcopy = 'aarch64-linux-gnu-objcopy'
strip = 'aarch64-linux-gnu-strip'
pkgconfig = 'aarch64-linux-gnu-pkg-config'
windres = 'aarch64-linux-gnu-windres'
```
然后执行以下命令：
```
meson setup --cross-file cross_file.txt builddir
```
