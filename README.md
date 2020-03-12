Many thanks to the shoulders of Scott Saad who's code I humbly started with. I've minimally updated this fork to partially build using the LLVM derived compiler in C++ Builder 10.3 Rio. I'd like to update it to 10.3.x or later, but I simply can't afford the $2500 (annually!!!) it would cost me to maintain a RadStudio Professional subscription. 

This fork comes with the following caveats:

1. I specifically need protobuf 2.5 to be compatible with what I'm interfacing with, so this fork has been updated to work on 2.5 (which admittedly is still comparatively old).
2. I've made changes to the project file to use the LLVM compiler (as opposed to the "Classic" Borland compiler which the base project was using).
3. Since the version of C++ Builder I have a license to does not include a functioning winnt.h (it includes the header file but good luck getting it to compile when the Clang-derived compiler doesn't support the required intrinsics), I added atomicops_internals_x86_cppbuilder.h/.cc files, using the MSVC ones as a starting point, then made slight changes to use std::atomic vs anything in winnt.h. Note it is not a full port; I only modified the function that was missing when I tried linking to the protobuf client-library I have to work with. 
4. As of now only libprotobuf is the only one working; I will re-visit with libprotobuf-lite and unit tests at a later date.
