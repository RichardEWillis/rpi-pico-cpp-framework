# rpi-pico-cpp-framework
My Embedded framework for C and C++ based project on the RP2040 "Pico" MCU

# Intended usage
Cloning into a location parallel to the pico-sdk (at or near the same dir location) is recommended but not required.
It should be next tp your own embedded project, or a submodule of that project, depending on if this framework is directly compiled in or generated separately as a static lib.

# Components (whole list is to-do)

* Filedevice (file based char device framework - serial device s and files accessed as files, eg. "/dev/ser0,115200,8n1,noflctl" (ser0 USART, baud=115200, 8N1, no-flow-control))
* Serio (serial I/O, extentions on top of the pico SDK I/O which is not that good)
* Serdev (extension of serial UART as a named device, using Filedevice stack)
* gpiodev (extension of GPIO as a named device, uses ioctls for set,get)
* tty (extension of a serial char device into a tty / console.. editing, history, etc.)
* filedev (underlying extension of a flash device memory location into a useable file system, using hi reliability "fifo" file allocation system)
* filedisk (adding a filesystem into the named device scope, '/' using available local flash memory)
* Service (base class for creating a generic service)
* STMachine (base and other classes to create a C++ based state machine)
* StateService (base class for a state machine base service)

# Directory Structure

## cppfw/ 
Exportable headers are all here in this directory, so this location will contain all info needed to compile in the framewaork source (or libs) and integrate them into application code. Do not include headers from any other directory.

## common
Will contain common internal headers are source code. Some enxternal source may also be here but APIs are exposed only in cppfw/

## devbase
The C++ base classes for creating a device stack, including registration of derived types and enumerations.

## chardev
Character stream based device classes. Will include special classes as well such as gpiodev which really only uses ioctl calls for its operation.

## filedev
C++ classes defining a simple named filesystem based off of some raw flash sectors made available on the target. Flash hardware info will be imported in the form of defines that are setup in the main project or some BSP structure.

## libs
Generated static libraries are created here, for linking into the main project.
