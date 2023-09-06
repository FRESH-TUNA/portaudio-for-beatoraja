# PortAudio for beatoraja
This forked project helps to provide portaudio support to beatoraja in MACOS and LINUX.

Thanks to Phil Burk!

## HOW TO?
### Install portaudio in OS(current stable version: 19.7.0)
```
# In MACOS using homebrew package manager
brew install portaudio
```

### Build portaudio java binded library for Beatoraja.
On MacOS, you may need to tell CMAKE where to look for stdio.h.

```
export SDKROOT=$(xcrun --sdk macosx --show-sdk-path)
```

This should work on Linux and Mac. 
In macos, Xcode is may be required.

```

# clone this project and move to root directory of project
cd portaudio-for-beatoraja

# This commend may be depends on your linux platform.
export LIBRARY_PATH=$LIBRARY_PATH:/usr/local/lib

cmake .
make install

# builded library result
ls -l libjportaudio.dylib
```

You might need to use "sudo make install".

If you have jni.h not found error, you should modify two files.
- [./src/main/jni/com_portaudio_PortAudio.h](./src/main/jni/com_portaudio_PortAudio.h), 
- [./src/main/jni/com_portaudio_BlockingStream.h](./src/main/jni/com_portaudio_BlockingStream.h).

```c

# before
#include <jni.h>

# after
#include "<your-jdk-path>/Contents/Home/include/jni.h"
```

<your-jdk-path> is depends on your jdk installed path.
My jdk path is /Library/Java/JavaVirtualMachines/liberica-jdk-18-full.jdk

### Move builded library to Beatoraja
Just copy libjportaudio.dylib file to root folder of beatoraja!
And have a fun with portaudio audio option!
