# openssl-1.1.1g-compile-for-android
编译openssl-1.1.1g支持android的armeabi、armeabi-v7a、arm64-v8a主流CPU架构的ssl开发



#依赖环境
  
NDK、openssl-1.1.1g源码、Make、makedepend

参考链接：https://wiki.openssl.org/index.php/Android


基础环境变量配置：#ANDROID_NDK_HOME 必须在/etc/profile配置

export ANDROID_NDK_HOME=/usr/ndk/android-ndk-r16b

export PATH=$ANDROID_NDK_HOME:$PATH

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


armv7a编译

执行setevn-android-armv7a.sh 

[root@localhost openssl-1.1.1g]#chmod a+x setevn-android-armv7a.sh

[root@localhost openssl-1.1.1g]#source ./setevn-android-armv7a.sh

配置openssl生成Makefile

[root@localhost openssl-1.1.1g]# 
./Configure  no-asm no-async no-shared no-md2 no-md4 no-mdc2 no-poly1305 no-blake2 no-siphash no-sm3 no-rc2 no-rc4 no-rc5 no-idea no-aria no-bf no-cast no-camellia no-seed no-sm4 no-chacha no-ec no-dsa no-sm2 no-dso no-engine no-err no-comp no-ocsp no-cms no-ts no-srp no-cmac no-ct android-arm

注：库文件默认输出在openssl根目录下

[root@localhost openssl-1.1.1g]#make depend

[root@localhost openssl-1.1.1g]#make -j8


arm64-v8a 编译

执行setevn-android-arm64.sh 

[root@localhost openssl-1.1.1g]#chmod a+x setevn-android-arm64.sh

[root@localhost openssl-1.1.1g]#source ./setevn-android-arm64.sh

[root@localhost openssl-1.1.1g]#
./Configure no-asm no-async no-shared no-md2 no-md4 no-mdc2 no-poly1305 no-blake2 no-siphash no-sm3 no-rc2 no-rc4 no-rc5 no-idea no-aria no-bf no-cast no-camellia no-seed no-sm4 no-chacha no-ec no-dsa no-sm2 no-dso no-engine no-err no-comp no-ocsp no-cms no-ts no-srp no-cmac no-ct  android64-aarch64

[root@localhost openssl-1.1.1g]#make depend

[root@localhost openssl-1.1.1g]#make -j8

