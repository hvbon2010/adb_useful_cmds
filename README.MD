# Introduction
In Android, we will use the adb and fastboot tools in very much, so I summarized to use them effectively.

# Abstract
## ADB
Android Debug Bridge (adb) is a versatile command-line tool that lets you communicate with a device. The adb command facilitates a variety of device actions, such as installing and debugging apps, and it provides access to a Unix shell that you can use to run a variety of commands on a device. It is a client-server program that includes three components:

- `A client`, which sends commands. The client runs on your development machine. You can invoke a client from a command-line terminal by issuing an adb command.

- `A daemon (adbd)`, which runs commands on a device. The daemon runs as a background process on each device.

- `A server`, which manages communication between the client and the daemon. The server runs as a background process on your development machine.

https://developer.android.com/studio/command-line/adb

## Fastboot
Fastboot is Flashing tool for android device, include fastboot in bootloader mode and fastbootd in user space.

https://source.android.com/setup/build/running

https://source.android.com/devices/bootloader/fastbootd

