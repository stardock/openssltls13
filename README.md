# openssltls13
Openssl with TLS1.3 enabled

## 前言  

* 必须执行次教程才可以编译运行后面的nginx  
* 推荐使用宝塔面板  
* 请每次执行一条，遇到错误请停下来排错  

## 克隆 OpenSSL

* 这里用的是 1.1.1 稳定版的源码  
```  
cd
wget https://github.com/openssl/openssl/archive/OpenSSL_1_1_1.tar.gz   
tar xzvf OpenSSL_1_1_1.tar.gz  
mv openssl-OpenSSL_1_1_1 openssl  
```  

## 给 OpenSSL 打补丁  

* 补丁来自：https://github.com/hakasenyang/openssl-patch  
* 此补丁的目的是让 OpenSSL 支持 TLS1.3 的 23,26,28 草案，以及 Final 版标准  
```  
cd 
git clone -b openssl-1.1.1 https://github.com/stardock/openssl-patch  
cd openssl   
patch -p1 < ../openssl-patch/openssl-equal-1.1.1_ciphers.patch  
patch -p1 < ../openssl-patch/openssl-1.1.1-chacha_draft.patch  
```  

## 编译安装
```  
./config  
make  
make install  
```  

查看编译结果  

[root@vml6xnph ~]# which openssl
/usr/local/bin/openssl

重新登录putty  

cd apps  
openssl version             #若出现报错参考下面链接(Bug Fix)  
openssl ciphers -v | grep TLSv1.3 | column -t  

```
[root@vml6xnph apps]# ./openssl ciphers -v | grep TLSv1.3 | column -t
TLS_AES_256_GCM_SHA384        TLSv1.3  Kx=any  Au=any  Enc=AESGCM(256)             Mac=AEAD
TLS_CHACHA20_POLY1305_SHA256  TLSv1.3  Kx=any  Au=any  Enc=CHACHA20/POLY1305(256)  Mac=AEAD
TLS_AES_128_GCM_SHA256        TLSv1.3  Kx=any  Au=any  Enc=AESGCM(128)             Mac=AEAD
```



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
https://www.sinosky.org/compile-nginx-with-a-custom-openssl-library.html  
让Nginx快速支持TLS1.3协议  
https://www.jianshu.com/p/aa3f7c4d3a10  
https://zhih.me/make-your-website-support-tls1-3/  
