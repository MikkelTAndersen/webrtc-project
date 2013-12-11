webrtc-project
==============

Wraps the webrtc repository and includes the required project files needed to build with gyp


More information can be found at the original [webrtc source].
Google provides [webrtc git source] project that the camfire webrtc repository actually pulls from.

# Instructions
`gclient sync`

     GYP_DEFINES="libjingle_java=1 build_with_libjingle=1 build_with_chromium=0 target_arch=x64 java_home=/Library/Java/JavaVirtualMachines/jdk1.7.0_17.jdk/Contents/Home" gclient runhooks --force

`ninja -C out/Debug libjingle_peerconnection_jar`

After compilation you will have a system object file and a jar. You need to install the .so file and then place the jar in your project.
Using osx you need to rename the .so file to .jnilib. For example:

    cp /Users/jonathan/code/active/libjingle/trunk/out/Debug/jingle_peerconnection_so.so /usr/lib/java/libjingle_peerconnection_so.jnilib

# Requirements

* gyp

* depot_tools

# Additional Notes

The gclient configuration was generated with the following command:

`gclient config http://webrtc.googlecode.com/svn/trunk/ --name trunk`

This repository links to the webrtc git projects. The main webrtc project is a svn project that uses gyp. I had to be
a little bit tricky to get things to work. I referenced the instructions for [devtools save].



[webrtc git source]: https://chromium.googlesource.com/external/webrtc
[webrtc source]: https://code.google.com/p/webrtc/ 
[devtools save]: https://code.google.com/p/devtools-save/wiki/BuildingDevToolsSave

