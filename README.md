# ETW-Patch
<a href="https://t.me/pulzetools"><img src="https://img.shields.io/badge/Join%20my%20Telegram%20group-2CA5E0?style=for-the-badge&logo=telegram&labelColor=db44ad&color=5e2775"></a>

- This repository contains code that demonstrates how to patch the ```EtwEventWrite``` function from the ```ntdll.dll``` library on Windows using CGO. This technique modifies the behavior of ```EtwEventWrite``` by injecting custom assembly code that replaces the beginning of the function.

## How it works?
- Uses Windows API functions ```(GetModuleHandleA, GetProcAddress, VirtualProtect)``` to locate and modify the EtwEventWrite function in memory.

- Defines a byte sequence ```(0x33, 0xC0, 0xC3)``` that represents the assembly instructions ```(XOR EAX, EAX; RET)``` used to replace the beginning of the EtwEventWrite function. This effectively nullifies the function's effect, making it return immediately without performing its intended actions.
