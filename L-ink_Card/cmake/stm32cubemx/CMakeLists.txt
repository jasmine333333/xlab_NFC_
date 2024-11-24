cmake_minimum_required(VERSION 3.22)

project(stm32cubemx)
add_library(stm32cubemx INTERFACE)

# Enable CMake support for ASM and C languages
enable_language(C ASM)

target_compile_definitions(stm32cubemx INTERFACE 
	USE_HAL_DRIVER 
	STM32L051xx
    $<$<CONFIG:Debug>:DEBUG>
)

target_include_directories(stm32cubemx INTERFACE
    ../../Inc
    ../../Drivers/STM32L0xx_HAL_Driver/Inc
    ../../Drivers/STM32L0xx_HAL_Driver/Inc/Legacy
    ../../Drivers/CMSIS/Device/ST/STM32L0xx/Include
    ../../Drivers/CMSIS/Include
    ../../Drivers/BSP/Components/ST25DV
    ../../Drivers/BSP/NFC04A1
)

target_sources(stm32cubemx INTERFACE
    ../../Src/main.c
    ../../Src/gpio.c
    ../../Src/stm32l0xx_hal_exti.c
    ../../Src/usart.c
    ../../Src/custom_bus.c
    ../../Src/stm32l0xx_it.c
    ../../Src/stm32l0xx_hal_msp.c
    ../../Drivers/BSP/Components/ST25DV/st25dv_reg.c
    ../../Drivers/BSP/Components/ST25DV/st25dv.c
    ../../Drivers/BSP/NFC04A1/nfc04a1.c
    ../../Drivers/BSP/NFC04A1/nfc04a1_nfctag.c
    ../../Drivers/STM32L0xx_HAL_Driver/Src/stm32l0xx_hal_i2c.c
    ../../Drivers/STM32L0xx_HAL_Driver/Src/stm32l0xx_hal_i2c_ex.c
    ../../Drivers/STM32L0xx_HAL_Driver/Src/stm32l0xx_hal.c
    ../../Drivers/STM32L0xx_HAL_Driver/Src/stm32l0xx_hal_rcc.c
    ../../Drivers/STM32L0xx_HAL_Driver/Src/stm32l0xx_hal_rcc_ex.c
    ../../Drivers/STM32L0xx_HAL_Driver/Src/stm32l0xx_hal_flash_ramfunc.c
    ../../Drivers/STM32L0xx_HAL_Driver/Src/stm32l0xx_hal_flash.c
    ../../Drivers/STM32L0xx_HAL_Driver/Src/stm32l0xx_hal_flash_ex.c
    ../../Drivers/STM32L0xx_HAL_Driver/Src/stm32l0xx_hal_gpio.c
    ../../Drivers/STM32L0xx_HAL_Driver/Src/stm32l0xx_hal_dma.c
    ../../Drivers/STM32L0xx_HAL_Driver/Src/stm32l0xx_hal_pwr.c
    ../../Drivers/STM32L0xx_HAL_Driver/Src/stm32l0xx_hal_pwr_ex.c
    ../../Drivers/STM32L0xx_HAL_Driver/Src/stm32l0xx_hal_cortex.c
    ../../Drivers/STM32L0xx_HAL_Driver/Src/stm32l0xx_hal_tim.c
    ../../Drivers/STM32L0xx_HAL_Driver/Src/stm32l0xx_hal_tim_ex.c
    ../../Drivers/STM32L0xx_HAL_Driver/Src/stm32l0xx_hal_uart.c
    ../../Drivers/STM32L0xx_HAL_Driver/Src/stm32l0xx_hal_uart_ex.c
    ../../Src/system_stm32l0xx.c
    ../../Src/sysmem.c
    ../../Src/syscalls.c
    ../../startup_stm32l051xx.s
)

target_link_directories(stm32cubemx INTERFACE
)

target_link_libraries(stm32cubemx INTERFACE
)

# Validate that STM32CubeMX code is compatible with C standard
if(CMAKE_C_STANDARD LESS 11)
    message(ERROR "Generated code requires C11 or higher")
endif()


