
cmake_minimum_required(VERSION 3.0)

add_library(ll
  src/stm32f1xx_ll_utils.c
  src/stm32f1xx_ll_usb.c
  src/stm32f1xx_ll_usart.c
  src/stm32f1xx_ll_tim.c
  src/stm32f1xx_ll_spi.c
  src/stm32f1xx_ll_sdmmc.c
  src/stm32f1xx_ll_rtc.c
  src/stm32f1xx_ll_rcc.c
  src/stm32f1xx_ll_pwr.c
  src/stm32f1xx_ll_i2c.c
  src/stm32f1xx_ll_gpio.c
  src/stm32f1xx_ll_fsmc.c
  src/stm32f1xx_ll_exti.c
  src/stm32f1xx_ll_dma.c
  src/stm32f1xx_ll_dac.c
  src/stm32f1xx_ll_crc.c
  src/stm32f1xx_ll_adc.c)

target_include_directories(ll PUBLIC inc)

set(STM32_DEVICE_GROUP "STM32F103xB" CACHE STRING
 "Chip configuration as defined in stm32f1xx.h (default value for the bluepill)")

target_compile_definitions(ll PUBLIC ${STM32_DEVICE_GROUP})
target_compile_definitions(ll PUBLIC "USE_FULL_LL_DRIVER")
target_include_directories(ll PUBLIC CMSIS/Device/ST/STM32F1xx/Include)

target_include_directories(ll PUBLIC CMSIS/Include)
target_compile_options(ll PUBLIC
  -mthumb
  -mcpu=cortex-m3
  -mfloat-abi=soft
  -mlittle-endian)
