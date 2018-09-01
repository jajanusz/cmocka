cmocka
======

cmocka is an elegant unit testing framework for C with support for mock
objects. It only requires the standard C library, works on a range of computing
platforms (including embedded) and with different compilers.

For information about how to use the cmocka unit testing framework see
doc/index.html or https://api.cmocka.org/.

Compiling
---------

To compile the cmocka library and example applications run, create a build dir,
and in the build dir call 'cmake /path/to/cmocka' followed by 'make'. On
Windows you can use the cmake gui. More details can be found in the INSTALL file.

Compiling for embedded
----------------------

Example of compiling just static libs for embedded:
```
# From the root of cmocka project
mkdir build && cd build
cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_C_COMPILER=<your_compiler> -DWITH_STATIC_LIB=ON -DWITH_SHARED_LIB=OFF -DWITH_EXAMPLES=OFF -DCMAKE_INSTALL_PREFIX=/path/to/cmocka/for/platform ..
make
make install
```
It will comile and install lib/ and include/ dirs at /path/to/cmocka/for/platform.

Website
-------

https://cmocka.org
