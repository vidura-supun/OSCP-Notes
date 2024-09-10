#mobile #MITM 

🔴 Always test the proxy from AVD settings

For OSes lower than Nougurt(7)

```powershell
mv cacert.der cacert.cer
```

```powershell
adb push cacert.cer /sdcard/
```

1. Navigate to **Settings->Security->More Security->Encryption & credentials->....->SDK_gphone64**
2. Install it

For OSes higher than Nougurt

[[Rooting the devices]]

1. Start as writable
```cmd 
E:\Android\sdk\emulator\emulator.exe -list-avds
```

```cmd
E:\Android\sdk\emulator\emulator.exe -avd Pixel_5_API_33 -writable-system
```

2.  Prep the directories

```cmd
adb root
```

```cmd
adb shell avbctl disable-verification
```

```cmd
adb reboot
```

```cmd
adb root
```

```cmd
adb remount
```

3. Prep the certificate

```bash
openssl x509 -inform DER -in burpcert.der -out burpcert.pem  
```

```bash
openssl x509 -inform PEM -subject_hash_old -in burpcert.pem |head -1
```

4. Copy the certificate 

```cmd
 adb push C:\Users\Vidura\Downloads\9a5ba575.0 /sdcard/
```

```cmd
adb shell "mv /sdcard/9a5ba575.0 /system/etc/security/cacerts/"
```

```cmd
adb shell "chmod 644 /system/etc/security/cacerts/9a5ba575.0"
```

```cmd
adb reboot
```

4. Test

```powershell
adb shell "ls /system/etc/security/cacerts/" | Select-String 9a5ba575
```
