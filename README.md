# rpi-pico-cpp-framework
My Embedded framework for C and C++ based project on the RP2040 "Pico" MCU

# Intended usasge
Cloning into a location parallel to the pico-sdk (at or near the same dir location) is recommended but not required.
It should be next tp your own embedded project, or a submodule of that project, depending on if this framework is directly compiled in or generated separately as a static lib.

# Components (whole list is to-do)

    - Filedevice (file based char device framework - serial device s and files accessed as files, eg. "/dev/ser0,115200,8n1,noflctl" (ser0 USART, baud=115200, 8N1, no-flow-control))
    - Serio (serial I/O, extentions on top of the pico SDK I/O which is not that good)
    - Serdev (extension of serial UART as a named device, using Filedevice stack)
    - gpiodev (extension of GPIO as a named device, uses ioctls for set,get)
    - tty (extension of a serial char device into a tty / console.. editing, history, etc.)
    - filedev (underlying extension of a flash device memory location into a useable file system, using hi reliability "fifo" file allocation system)
    - filedisk (adding a filesystem into the named device scope, '/' using available local flash memory)
    
