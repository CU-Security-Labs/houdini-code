# Houdini

Houdini is a framework for reproducible container security testing.

## Requirements

To use Houdini, you need:

- A Linux kernel
- A filesystem

We recommend using [Buildroot](https://buildroot.org/) to create both the kernel and the filesystem for a clean, reproducible environment.

## Getting Started

1. **Set up Buildroot**  
   Download and configure Buildroot to generate a minimal Linux system. Make sure to include packages Houdini needs (Python, Docker).

2. **Build the Kernel and Filesystem**  
   Run Buildroot to compile the kernel and generate the root filesystem. Example:

   ```bash
   make menuconfig   # Configure your system
   make              # Build kernel and filesystem
   
3. **Configure Houdini VM**  
   Go into `utilities/buildroot_manager.py`. In the function argument of `start_vm`, enter the paths of the kernel and the drive (root filesystem). Buildroot will generate both for you.

   Example:

   ```python
   from utilities.buildroot_manager import start_vm

   kernel_path = "/path/to/buildroot/output/images/bzImage"
   drive_path = "/path/to/buildroot/output/images/rootfs.ext2"

   start_vm(kernel=kernel_path, drive=drive_path)
