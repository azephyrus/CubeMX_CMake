cmake_minimum_required(VERSION 3.22)

project(stm32cubemx)
add_library(stm32cubemx INTERFACE)

# Enable CMake support for ASM and C languages
enable_language(C ASM)

target_compile_definitions(stm32cubemx INTERFACE
    STM32F10X_MD
    $<$<CONFIG:Debug>:DEBUG>
)

target_include_directories(stm32cubemx INTERFACE
    ../../Core/Inc
    ../../Peripherals/Inc
    ../../STM32F10x_StdPeriph_Driver/inc
)

target_sources(stm32cubemx INTERFACE
    ../../Core/Src/main.c
    ../../Core/Src/core_cm3.c
    ../../Core/Src/system_stm32f10x.c
    ../../startup_stm32f103xb.s
    ../../STM32F10x_StdPeriph_Driver/src/misc.c
    ../../STM32F10x_StdPeriph_Driver/src/stm32f10x_adc.c
    ../../STM32F10x_StdPeriph_Driver/src/stm32f10x_bkp.c
    ../../STM32F10x_StdPeriph_Driver/src/stm32f10x_can.c
    ../../STM32F10x_StdPeriph_Driver/src/stm32f10x_cec.c
    ../../STM32F10x_StdPeriph_Driver/src/stm32f10x_crc.c
    ../../STM32F10x_StdPeriph_Driver/src/stm32f10x_dac.c
    ../../STM32F10x_StdPeriph_Driver/src/stm32f10x_dbgmcu.c
    ../../STM32F10x_StdPeriph_Driver/src/stm32f10x_dma.c
    ../../STM32F10x_StdPeriph_Driver/src/stm32f10x_exti.c
    ../../STM32F10x_StdPeriph_Driver/src/stm32f10x_flash.c
    ../../STM32F10x_StdPeriph_Driver/src/stm32f10x_fsmc.c
    ../../STM32F10x_StdPeriph_Driver/src/stm32f10x_gpio.c
    ../../STM32F10x_StdPeriph_Driver/src/stm32f10x_i2c.c
    ../../STM32F10x_StdPeriph_Driver/src/stm32f10x_iwdg.c
    ../../STM32F10x_StdPeriph_Driver/src/stm32f10x_pwr.c
    ../../STM32F10x_StdPeriph_Driver/src/stm32f10x_rcc.c
    ../../STM32F10x_StdPeriph_Driver/src/stm32f10x_rtc.c
    ../../STM32F10x_StdPeriph_Driver/src/stm32f10x_sdio.c
    ../../STM32F10x_StdPeriph_Driver/src/stm32f10x_spi.c
    ../../STM32F10x_StdPeriph_Driver/src/stm32f10x_tim.c
    ../../STM32F10x_StdPeriph_Driver/src/stm32f10x_usart.c
    ../../STM32F10x_StdPeriph_Driver/src/stm32f10x_wwdg.c
    ../../Core/Src/Delay.c
)

target_link_directories(stm32cubemx INTERFACE
)

target_link_libraries(stm32cubemx INTERFACE
)

# Validate that STM32CubeMX code is compatible with C standard
if(CMAKE_C_STANDARD LESS 11)
    message(ERROR "Generated code requires C11 or higher")
endif()


