# VSCode_and_STM32_LL

There is a [good article by Cristian Dobre](https://hbfsrobotics.com/blog/configuring-vs-code-arm-development-stm32cubemx) which explains in details how to setup VSCode for STM32 environment.

In my case the stlink/v2 debugger was not working with the last version of [Texane’s ST-Link Tools](https://github.com/stlink-org/stlink/releases). But I found that it is working well with the version v1.5.1. The binary files you can find in this repository and simply put them into your "C:\VSARM\stlink\".

If you generate your project from STM32Cube-MX using peripheral Low Layer (LL) driver then you need to change the setting "USE_HAL_DRIVER" to "USE_FULL_LL_DRIVER" in the c_cpp_properties.json file.

All .json configuration files in ./vscode are made for stm32f303 MCU and you can use them as example for setting your project.
