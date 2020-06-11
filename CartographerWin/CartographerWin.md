##Build Windows Cartographer

* Boost With ZLib
	 b2 -a -q -j4 address-model=64 link=static threading=multi runtime-link=shared variant=debug --with-iostreams -s ZLIB_SOURCE="D:/DevelopProj/Thirdparty/zlib-1.2.8/zlib-1.2.8"
