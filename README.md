"c:\Program Files\Amazon Corretto\jdk17.0.14_7\bin\java.exe" -classpath "C:\basjx\uiautomatorviewer-gradle\build\install\uiautomatorviewer-gradle\lib\uiautomatorviewer-gradle.jar;C:\basjx\uiautomatorviewer-gradle\build\install\uiautomatorviewer-gradle\lib\ddmlib-31.5.1.jar;C:\basjx\uiautomatorviewer-gradle\build\install\uiautomatorviewer-gradle\lib\org.eclipse.core.commands-3.11.0.jar;C:\basjx\uiautomatorviewer-gradle\build\install\uiautomatorviewer-gradle\lib\org.eclipse.equinox.common-3.18.0.jar;C:\basjx\uiautomatorviewer-gradle\build\install\uiautomatorviewer-gradle\lib\org.eclipse.jface-3.30.0.jar;C:\basjx\uiautomatorviewer-gradle\build\install\uiautomatorviewer-gradle\lib\org.eclipse.osgi-3.18.400.jar;C:\basjx\uiautomatorviewer-gradle\build\install\uiautomatorviewer-gradle\lib\org.eclipse.swt-3.124.0.jar;C:\basjx\uiautomatorviewer-gradle\build\install\uiautomatorviewer-gradle\lib\org.eclipse.swt.win32.win32.x86_64-3.124.0.jar;C:\basjx\uiautomatorviewer-gradle\build\install\uiautomatorviewer-gradle\lib\common-31.5.1.jar;C:\basjx\uiautomatorviewer-gradle\build\install\uiautomatorviewer-gradle\lib\protobuf-java-3.22.3.jar;C:\basjx\uiautomatorviewer-gradle\build\install\uiautomatorviewer-gradle\lib\kxml2-2.3.0.jar;C:\basjx\uiautomatorviewer-gradle\build\install\uiautomatorviewer-gradle\lib\kotlin-stdlib-jdk8-1.9.20.jar;C:\basjx\uiautomatorviewer-gradle\build\install\uiautomatorviewer-gradle\lib\kotlin-stdlib-jdk7-1.9.20.jar;C:\basjx\uiautomatorviewer-gradle\build\install\uiautomatorviewer-gradle\lib\kotlin-stdlib-1.9.20.jar;C:\basjx\uiautomatorviewer-gradle\build\install\uiautomatorviewer-gradle\lib\annotations-23.0.0.jar;C:\basjx\uiautomatorviewer-gradle\build\install\uiautomatorviewer-gradle\lib\annotations-31.5.1.jar;C:\basjx\uiautomatorviewer-gradle\build\install\uiautomatorviewer-gradle\lib\guava-32.0.1-jre.jar;C:\basjx\uiautomatorviewer-gradle\build\install\uiautomatorviewer-gradle\lib\jna-platform-5.6.0.jar;C:\basjx\uiautomatorviewer-gradle\build\install\uiautomatorviewer-gradle\lib\failureaccess-1.0.1.jar;C:\basjx\uiautomatorviewer-gradle\build\install\uiautomatorviewer-gradle\lib\listenablefuture-9999.0-empty-to-avoid-conflict-with-guava.jar;C:\basjx\uiautomatorviewer-gradle\build\install\uiautomatorviewer-gradle\lib\jsr305-3.0.2.jar;C:\basjx\uiautomatorviewer-gradle\build\install\uiautomatorviewer-gradle\lib\checker-qual-3.33.0.jar;C:\basjx\uiautomatorviewer-gradle\build\install\uiautomatorviewer-gradle\lib\error_prone_annotations-2.18.0.jar;C:\basjx\uiautomatorviewer-gradle\build\install\uiautomatorviewer-gradle\lib\j2objc-annotations-2.8.jar;C:\basjx\uiautomatorviewer-gradle\build\install\uiautomatorviewer-gradle\lib\jna-5.6.0.jar" com.android.uiautomator.UiAutomatorViewer

![Screenshot](MainScreen.png)

### Verifying this code against the SDK sources ###
1. **Verifying that this repository is actually based on the original viewer sources**: This repository is based on https://android.googlesource.com/platform/tools/swt/+/1ad1e59667a2b7ea4c0c90e3bfb76c39c5a96fb3/uiautomatorviewer/ .
The [initial commit - da94b667bbdc007d2bdf74d300932eb3dc75256e](https://github.com/TarCV/uiautomatorviewer-gradle/tree/da94b667bbdc007d2bdf74d300932eb3dc75256e) is exactly that directory.
Therefore, you can [download that source](https://android.googlesource.com/platform/tools/swt/+archive/1ad1e59667a2b7ea4c0c90e3bfb76c39c5a96fb3/uiautomatorviewer.tar.gz) and compare it against [the sources in that initial commit](https://github.com/TarCV/uiautomatorviewer-gradle/archive/da94b667bbdc007d2bdf74d300932eb3dc75256e.zip).<br/>There should be no differences except in timestamps.
2. **Reviewing changes**: Some changes were made to those original sources to fix building on the latest Java/OS/etc., update libraries, and for convenience. These changes can be reviewed by [comparing the current main with the initial commit](https://github.com/TarCV/uiautomatorviewer-gradle/compare/da94b667bbdc007d2bdf74d300932eb3dc75256e...main).

### Running on Windows, Linux ###
You can run the app as is on these OSes, just make sure Android Debug Bridge is available.
```bash
./gradlew installDist
./build/install/uiautomatorviewer-gradle/bin/uiautomatorviewer-gradle
```

### Running on Mac ###
Launch the app passing `-XstartOnFirstThread` JVM argument, otherwise it will immediately crash. For example:
```bash
./gradlew installDist
JAVA_OPTS=-XstartOnFirstThread ./build/install/uiautomatorviewer-gradle/bin/uiautomatorviewer-gradle
```
(Unfortunately, this option is not supported on Linux, so it cannot be added to the shell wrapper script)

Also make sure Android Debug Bridge is available.
