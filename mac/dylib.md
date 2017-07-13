# Build dylib on Mac os x


Use build process from the source of `libnet` for instance.

### 1. Find the top source direction with `.configure`

```
./configure --prefix=<where you want to install>
```

### 2. check if `Makefile` here

```
make
make install
```

### 3. Done! Generally the the `install_name` of `libnet.dylib` will be set 
   properly.


## Write a dylib

```
gcc -dynamiclib foo.c -o libfoo.dylib
gcc main.c -L. -lfoo -o main
```

To specify a `install_name` of a dylib, use `-install_name` in `gcc`
```
gcc -dynamiclib foo.c -install_name  -o libfoo.dylib

```

The `install_name` of dylib will be write in `main`


## otool

### `otool -L <executable>`

Check all the dylib linked in `main`, where the
`install_name` of a dylib is the path where `main` links the dylib.

```
otool -L main
```

### `otool -D <dylib>`

Check the `install_name` of a dylib

```
otool -D libfoo.dylib
```

### `install_name_tool -id <new name> <dylib>`

Change the `install_name_tool` of `libfoo.dylib` to `../libfoo.dylib`

```
install_name_tool -id ../libfoo.dylib libfoo.dylib 
```

### `install_name_tool -change <old value> <new value> <executable>`

Change the path where executable find the dylib 

```
install_name_tool -change ../libfoo.dylib ../../libfoo.dylib main
```

NOTE: One more method, if `install_name` of a dylib is not corret, setting
      the environment variable `$DYLD_LIBRARY_PATH` to the path where the
      dylib is can let executable find the dylib successfully. More info can
      see `man dyld`.

> More info see `mac/dylib`.


## libnet Compling from source

```
brew install automake libtool doxygen libdnet
```

Use the method above `configure, make, make install` with 
`libnet-1.2-rc3.tar.gz` (recommand)

Or use the method show in `BUILD-FROM-GIT.txt`

