# iOS/Android Objective-C OpenGL sample

This is a sample demonstrating how to develop on Objective-C for both iOS and Android
with help of [CrystaX NDK](https://www.crystax.net/android/ndk). This is simple application
which draw rotating cube and handle screen touches. Whole code is Objective-C - no Java at all.

## Internal structure

This sample uses the shared sources between iOS and Android. For simplicity, all shared sources
are located in `common` folder (of course, OpenGL shaders are shared too; they're located in `shaders` folder).

There are some amount of platform-specific code, which is not shared between iOS and Android
(you can find it in `ios` and `android` folders); however, it's amount is small, and it's
really needed since main entry points and some platform details are **very different** between
iOS and Android.

## How to build

The only supported development hosts for this example are OS X (one can build and run this sample on both iOS and Android)
and GNU/Linux (one can build and run this sample on Android). This is done for simplicity of project files.
Since both OS X and GNU/Linux support POSIX environment and include GNU make, it's simple to write makefile for Android
project without requiring additional tools (such as Gradle).

### iOS

This is simple: just open `ios/opengl.xcodeproj` in Xcode, build and run.

### Android

To build it for Android, the following prerequisities needed:

1. [CrystaX NDK](https://www.crystax.net/android/ndk)
2. [Android SDK](http://developer.android.com/sdk/index.html)
3. [Apache ANT](http://ant.apache.org/)


Please note, however, that CrystaX NDK should be of version 10.3.1 or higher. With Homebrew, you can
check it as below:

```
brew info crystax-ndk
```

Alternatively, you can download latest daily build([darwin](https://dl.crystax.net/ndk/darwin/current/),
[linux](https://dl.crystax.net/ndk/linux/current/), [windows](https://dl.crystax.net/ndk/windows/current/))
and unpack it somewhere:

```
curl -OL https://dl.crystax.net/ndk/darwin/current/crystax-ndk-10.3.1-b799-darwin-x86_64.tar.xz
tar xf crystax-ndk-10.3.1-b799-darwin-x86_64.tar.xz
```

Note:
> I have searched and found no replacement for the android update project command.
> If you still need to build I suggest reverting to SDK Tools 25.2.5 or earlier as they removed the command in Build Tool 25.3.0
> 
> You can download them from here and replace the tools folder in your ANDROID_SDK_HOME directory
> https://dl.google.com/android/repository/tools_r25.2.5-windows.zip
> https://dl.google.com/android/repository/tools_r25.2.5-macosx.zip
> https://dl.google.com/android/repository/tools_r25.2.5-linux.zip


Now, create `anroid/local.mk` with settings pointing to your Android SDK and CrystaX NDK installations.
You can look into `android/local.mk.sample` for example.

When it's done, plug your Android device by USB, cd to `android` folder and type there:
```
make run
```

## Demo

[![Screen record](http://i.imgur.com/QVhUUfe.png)](https://youtu.be/wUxPXT_gEmA "Screen record")
