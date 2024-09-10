#exploit #code

#### 64 bit windows

```bash
x86_64-w64-mingw32-gcc shell.c -o shell.exe
```

#### 32 bit Windows

```bash
i686-w64-mingw32-gcc shell.c -o shell.exe
```

### Statically link the library

```bash
i686-w64-mingw32-gcc 42341.c -o syncbreeze_exploit.exe -lws2_32
```
