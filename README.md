# test

### Linux实现socks终端代理、全局代理
`https://cloud.tencent.com/developer/article/1852590`

### arm版本lighting-app编译
gn gen out --args='target_cpu="arm64" target_os="linux"'

apt-get install g++-aarch64-linux-gnu gcc-aarch64-linux-gnu

wget https://www.openssl.org/source/old/1.1.1/openssl-1.1.1f.tar.gz
tar xzf openssl-1.1.1f.tar.gz
cd openssl-1.1.1f
./Configure linux-aarch64 --prefix=/usr/local/include/aarch64-linux-gnu/ssl --cross-compile-prefix=aarch64-linux-gnu- no-shared
make
make install

