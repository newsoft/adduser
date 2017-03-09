# adduser

Programmatically creates a 'local admin' Windows user. Requires admin rights. The created user is hardcoded to the following:

Login: `audit`
Password: `Test123456789!` (this should be good enough to fit most password policies)

This standalone piece code can run in many contexts:
- As a command-line EXE.
- As a DLL (the user will be created on DLL load). This is useful to exploit "DLL Preloading" issues.
- As a DLL, through `rundll32.exe adduser.dll,CreateAdminUser`. This is useful to bypass mandatory code signing applied to EXE files only.
