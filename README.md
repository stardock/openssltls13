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

openssl ciphers -s -tls1_3  


Reference:  
https://www.openssl.org/source/ (Package source)  
https://blog.csdn.net/mrpre/article/details/78575481 (Path to build)  
https://github.com/openssl/openssl/issues/8838 (List Ciphers)  
https://www.jianshu.com/p/aa3f7c4d3a10 (Test TLS)  
https://www.cnblogs.com/xyb930826/p/6077348.html (Bug fix)  
https://zhih.me/make-your-website-support-tls1-3/ (Patch to openssl)  


