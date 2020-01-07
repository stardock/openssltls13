# openssltls13
Openssl with TLS1.3 enabled


wget https://www.openssl.org/source/openssl-1.1.1d.tar.gz  
tar xzf openssl-1.1.1d.tar.gz  
mv openssl-1.1.1d openssl  
git clone https://github.com/hakasenyang/openssl-patch.git  
cd openssl  
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




https://blog.sometimesnaive.org/article/78.html  
https://blog.sometimesnaive.org/article/64  
https://imququ.com/post/optimize-ssl-ciphers-with-boringssl.html  
http://nginx.org/download/  


OpenSSL Dev issue???  
https://trac.nginx.org/nginx/ticket/1670  
https://trac.nginx.org/nginx/ticket/1529  
https://ftp.openssl.org/source/old/1.1.1/  

https://github.com/openssl/openssl/issues/7562  

