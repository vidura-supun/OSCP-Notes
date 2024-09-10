
1. Move the file to mobile device and execute
```cmd
adb push "E:\Cyber Labs\frida-server-16.4.0-android-x86_64\frida-server-16.4.0-android-x86_64" /data/local/tmp/frida
```

```cmd
adb shell "chmod +x /data/local/tmp/frida"
```

```cmd
adb shell "/data/local/tmp/frida &"
```


