# Linux Keylogger

An educational, C-based keylogger that demonstrates how to read and interpret raw hardware input streams directly from the Linux kernel. 

Unlike standard user-space keyloggers that hook into display servers (like X11 or Wayland), this program reads directly from the `/dev/input/` character devices, allowing it to capture keystrokes at the lowest software level before they reach the desktop environment.

## Features

* **Direct Hardware Access:** Reads binary streams directly from `/dev/input/eventX`.
* **Kernel Event Parsing:** Uses the Linux kernel's native `struct input_event` (`linux/input.h`) to parse raw byte chunks into timestamps, event types, codes, and values.
* **Custom Key Mapping:** Implements a direct lookup array based on `linux/input-event-codes.h` to translate raw hardware integer codes into human-readable characters.
* **Zero-Dependency:** Written in pure C with standard POSIX libraries. Requires no external libraries or frameworks.

## Prerequisites

* A Linux-based Operating System
* GCC (GNU Compiler Collection)
* Root (`sudo`) privileges (required to read `/dev/input/` streams)

## Compilation

To compile the source code into an executable binary, run the following command in your terminal:

```bash
gcc key_logger.c -o keylogger