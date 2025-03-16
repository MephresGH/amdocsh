# AMD Shell Overclocking Utility


### INTRODUCTION
AMDOCSH is an overclocking script written in Bash.
It overclocks currently installed graphics cards compatible with the "amdgpu" kernel driver.
The script's purpose is to be a basic replacement for most desktop overclocking utilities for AMD GPUs.
AMDOCSH works by giving direct access to multiple options from the amdgpu (and modesetting) driver options.
Settings taken from the user's input will be put into two smaller scripts.
Those then get installed into the /bin/ folder and enabled + executed via systemd by default.
This script can be managed like a regular systemd service.
AMDOCSH is currently capable of:

- Overclocking/Underclocking core and memory
- Increasing/Decreasing of maximum power draw
- Undervolting/Overvolting
- Setting persistent clock profiles for memory and core
- Setting of custom fan speeds
- Resetting all amdgpu-related options to factory settings


### INSTALLATION
Installation can either be done automatically (via a systemd service), or manual installation
so that amdocsh can be run after your desktop environment/window manager of choice.
The latter approach will be much more complicated, though.


### DEPENDENCIES
The following pieces of software are required to run AMDOCSH:


- GNU coreutils
- systemd
- xf86-video-amdgpu (optional)
- xf86-video-modesetting (recommended, default)


### TROUBLESHOOTING
If the script returns errors, check for the following:

- All dependencies are installed and function properly
- Kernel Mode Setting (KMS) is enabled and active
- Directories accessed through AMDOCSH are valid (different conditions can cause location variances)
- Re-run the program to fix potential issues and address common errors

To see all amdgpu-related driver options and functions, you can view the documentation:
https://www.kernel.org/doc/html/v4.20/gpu/amdgpu.html


### NOTE OF INTEREST
KMS is highly recommended for AMDOCSH to function.
Having KMS disabled can result in the script exiting to avoid writing into the user's root directory.
As of currently, running amdocsh's start script does not set a static VRAM clock speed and other parameters
for some cards when running it once, thus causing flickering and potential crashes under certain loads.
A temporary solution here is running the start script multiple times in a row
(2 times seems to work), be it manually or via a basic for loop.
Finally: this software does not come with any warranty, safety measures or any other form of protection.
I provide access to all of these options as-is for personal use.
I do not take any responsibility for any hardware-related issues you might cause with this script.
For more information, see the applied license.
Basic debug information can also be found in /tmp/amdocsh.log when using the systemd startup service.
