# openssltls13
Openssl with TLS1.3 enabled


wget https://www.openssl.org/source/openssl-1.1.1d.tar.gz  
tar xzf openssl-1.1.1d.tar.gz  
mv openssl-1.1.1d openssl  
git clone https://github.com/hakasenyang/openssl-patch.git
cd /usr/src/openssl 
patch -p1 < ../openssl-patch/openssl-equal-1.1.1_ciphers.patch
patch -p1 < ../openssl-patch/openssl-1.1.1-chacha_draft.patch

./config --prefix=/usr --libdir=lib64 enable-tls1_3
make  
make install  




Reference:
https://blog.csdn.net/mrpre/article/details/78575481 (Path to build)  
https://github.com/openssl/openssl/issues/8838 (List Ciphers)  




