# openssl-1.1.1g-compile-for-android
基于android-ndk-r16b编译openssl-1.1.1g支持android的armeabi、armeabi-v7a、arm64-v8a 架构ssl开发！
编译配置中做了最大化的精简配置！

编译后的静态库大小如下所示：

[root@localhost openssl-1.1.1g]# ls -lh lib/android-arm* 

lib/android-arm64-v8a:

总用量 3.5M

-rw-r--r-- 1 root root 2.8M 6月  18 18:18 libcrypto.a

-rw-r--r-- 1 root root 699K 6月  18 18:18 libssl.a

lib/android-armeabi:

总用量 2.7M

-rw-r--r-- 1 root root 2.2M 6月  18 18:18 libcrypto.a

-rw-r--r-- 1 root root 551K 6月  18 18:18 libssl.a

lib/android-armeabi-v7a:

总用量 2.7M

-rw-r--r-- 1 root root 2.2M 6月  18 18:18 libcrypto.a

-rw-r--r-- 1 root root 551K 6月  18 18:18 libssl.a


#依赖环境
  
android-ndk-r16b、make、makedepend

参考链接：https://wiki.openssl.org/index.php/Android


基础环境变量配置：#ANDROID_NDK_HOME 必须在/etc/profile添加如下配置

[root@localhost openssl-1.1.1g]# vim /etc/profile

export ANDROID_NDK_HOME=/usr/ndk/android-ndk-r16b

export PATH=$ANDROID_NDK_HOME:$PATH

[root@localhost openssl-1.1.1g]# source /etc/profile

生成Makefile.org文件

[root@localhost openssl-1.1.1g]# touch Makefile.org

[root@localhost openssl-1.1.1g]# perl -pi -e 's/install: all install_docs install_sw/install: install_docs install_sw/g' Makefile.org


armeabi编译

执行setevn-android-armeabi.sh 

[root@localhost openssl-1.1.1g]#chmod a+x setevn-android-armmeabi.sh

[root@localhost openssl-1.1.1g]#source ./setevn-android-armmeabi.sh

配置openssl生成Makefile

[root@localhost openssl-1.1.1g]# 
./Configure  no-asm no-async no-shared no-md2 no-md4 no-mdc2 no-poly1305 no-blake2 no-siphash no-sm3 no-rc2 no-rc4 no-rc5 no-idea no-aria no-bf no-cast no-camellia no-seed no-sm4 no-chacha no-ec no-dsa no-sm2 no-dso no-engine no-err no-comp no-ocsp no-cms no-ts no-srp no-cmac no-ct android-armmeabi

注：库文件默认输出在openssl根目录下

[root@localhost openssl-1.1.1g]#make depend

[root@localhost openssl-1.1.1g]#make -j8


armeabi-v7a编译

执行setevn-android-armeabi-v7a.sh 

[root@localhost openssl-1.1.1g]#chmod a+x setevn-android-armeabi-v7a.sh

[root@localhost openssl-1.1.1g]#source ./setevn-android-armeabi-v7a.sh

配置openssl生成Makefile

[root@localhost openssl-1.1.1g]# 
./Configure  no-asm no-async no-shared no-md2 no-md4 no-mdc2 no-poly1305 no-blake2 no-siphash no-sm3 no-rc2 no-rc4 no-rc5 no-idea no-aria no-bf no-cast no-camellia no-seed no-sm4 no-chacha no-ec no-dsa no-sm2 no-dso no-engine no-err no-comp no-ocsp no-cms no-ts no-srp no-cmac no-ct android-arm

注：库文件默认输出在openssl根目录下

[root@localhost openssl-1.1.1g]#make depend

[root@localhost openssl-1.1.1g]#make -j8


arm64-v8a 编译

执行setevn-android-arm64-v8a.sh 

[root@localhost openssl-1.1.1g]#chmod a+x setevn-android-arm64-v8a.sh

[root@localhost openssl-1.1.1g]#source ./setevn-android-arm64-v8a.sh

[root@localhost openssl-1.1.1g]#
./Configure no-asm no-async no-shared no-md2 no-md4 no-mdc2 no-poly1305 no-blake2 no-siphash no-sm3 no-rc2 no-rc4 no-rc5 no-idea no-aria no-bf no-cast no-camellia no-seed no-sm4 no-chacha no-ec no-dsa no-sm2 no-dso no-engine no-err no-comp no-ocsp no-cms no-ts no-srp no-cmac no-ct  android64-aarch64

[root@localhost openssl-1.1.1g]#make depend

[root@localhost openssl-1.1.1g]#make -j8

