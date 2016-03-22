This project demonstrates an issue regarding Xcode 7.3 and
linking an OS X CLI target using Swift. 

If `-ObjC` is passed as a linker flag, linking will fail with
errors like:

```
duplicate symbol _OBJC_CLASS_$__SwiftNativeNSError in:
    /Applications/Xcode-7.3.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/lib/swift_static/macosx/libswiftRuntime.a(ErrorObject.mm.o)
    /Applications/Xcode-7.3.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/lib/swift_static/macosx/libswiftCore.a(ErrorObject.mm.o)
```

Linking works fine if `-ObjC` is not being passed.

See also <http://www.openradar.me/25289652>

----

@below here

My first step was to check if the -objc flag is still needed, and apparently it is not. The flag was used to load all symbols from ObjC static libs, and Xcode 7.3 seems to be using lObjCLib for that. What is your application of the -objc flag?

