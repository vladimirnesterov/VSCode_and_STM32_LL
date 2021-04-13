# VSCode and STM32 with LL drivers

There is a [good article by Cristian Dobre](https://hbfsrobotics.com/blog/configuring-vs-code-arm-development-stm32cubemx) that explains in details how to setup VSCode for STM32 environment.

In my case the STLink-v2 debugger was not working with the last version of [Texane’s ST-Link Tools](https://github.com/stlink-org/stlink/releases). But I found that it is working well with the version v1.5.1. The binary files you can find in this repository and simply put them into your "C:\VSARM\stlink\".

Direct link to mingw installer for win64 is [here](https://sourceforge.net/projects/mingw-w64/files/Toolchains%20targetting%20Win32/Personal%20Builds/mingw-builds/installer/mingw-w64-install.exe/download).

If you generate your project from STM32Cube-MX using peripheral Low Layer (LL) driver then you need to change the setting **"USE_HAL_DRIVER"** to **"USE_FULL_LL_DRIVER"** in the c_cpp_properties.json file.

All .json configuration files in ./vscode are made for stm32f303 MCU and you can use them as example for setting your project.

The files are based on the examples provided in the article mentioned above. With some changes that helped me to get it work. For example the task for "clean" was added in the **tasks.json** file:

```json
{
        "label": "Make Clean",
        "type": "shell",
        "command": "make -j4 clean", 
        "windows": {
            "command": "del",
            "args": [
                "build/*"
            ]
        },
        "options": {
            "cwd": "${workspaceRoot}"
        },
        "group": {
            "kind": "build",
            "isDefault": true
        },
        "problemMatcher": []
    },
``` 
