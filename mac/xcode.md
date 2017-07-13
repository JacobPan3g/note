# Xcode

1. Default xcode

`xcode-select -p` show the default xcode in mac os x
`sudo xcode-select -switch /Applications/Xcode.app` to change the default.
If there are more than one xcode installed in mac os x, the second one will be named "xcode 2". Sometimes, it'll raise some errors because the " "(space) in the name. 

For instance, to build libnet, I followed the `BUILD-FROM-GIT.txt` at the top of project. Because my default xcode is named "xcode 2", it throw an error as
`/bin/sh: /Applications/Xcode: No such file or directory`. After I switched to "xcode" using the cmd above, the build process success.
