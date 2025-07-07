# Protonify
Protonify your Ubuntu desktop to enable double-click running of exe and msi files through proton-9.4, pre-setup.

USE AT YOUR OWN RISK.

Installation: Intended and tested on Ubuntu 24.04 LTS. (Proton 9.4 squashed)

**Step 0:**
Download source/all .sh to one folder.

**Step 1:**

First ensure all files are able to be executed.

Open folder in terminal and use: 

chmod +x *.sh

or 

chmod +x installer_1.sh installer_2.sh proton_dependencies.sh proton_g_init.sh proton_wrapper.sh proton_wrapper_replace.sh

**Step 2:**

WARNING: May break desktop due to package changes, I reinstall ubuntu-desktop afterwards (lazy of me). (I only use this on fresh installs) 
(If you want you can see which packages I quick included cause this and remove them from the installers)

./installer_1.sh
./installer_2.sh

Done. (self-tested this updated script once) [I use this for myself, I shared it because why not, let me know if it does not work for you]

May require restart after completed. (90% sure you must install Steam as well, but possibly not)

In some cases double-click itself may not target the file with proton, in which case there should be an option (Run windows file) available from the .desktop
This might never happen to you, but I use nemo and sometimes file-roller is what it defaults to, even though I don't have it set to fileroller.

About:
Integrates all exe/msi installs/file-data into a single compat /home/yourusername/Windows/ allowing you to achieve a more stable set of installed windows files.
For example: .Net 4/5/6/7/8 etc, etc. all in one installed environment.

WARNING 2: Depending on what you run and how you exit, it will not close protons environment. (Check your processes and such to close if need be)

Enjoy.



**Extended Description:**

AI Generated (Gemini): to those that hate AI ;) you're welcome, I included this part, this way, on purpose.

The provided Bash scripts are designed to set up and configure Proton for running Windows applications on a Linux system. They automate the process of installing necessary dependencies, downloading and extracting the Proton core, and integrating Proton with the desktop environment for easy execution of Windows files. These scripts appear to be part of a project named "Protonify," likely hosted on GitHub, which aims to simplify the use of Proton.

Here's a breakdown of each script's function:

* **`proton_dependencies.sh`**: This script installs the essential runtime dependencies required for Proton to function. It uses `apt` to install packages like `curl`, `wget`, `fuse`, `python3`, `mesa-vulkan-drivers`, various `libvulkan`, `libgl`, `libx` libraries, `libgtk-3-0t64`, `libdbus-1-3`, `libasound2t64`, `libpulse0`, and `cabextract`. It temporarily disables `set -e` to allow non-critical package installation failures to not halt the entire script.
* **`proton_g_init.sh`**: This script handles the initial setup of the Proton core. It first checks for and installs `megatools` (for `megadl`) and `squashfs-tools` (for `unsquashfs`). It then downloads a Proton SquashFS file (`proton.sqfs`) from a specified MEGA URL, verifies its integrity using a SHA256 hash, and extracts its contents into the `$HOME/Proton` directory.
* **`proton_wrapper.sh`**: This is the core wrapper script responsible for launching Windows applications using Proton. It sets several environment variables, including `STEAM_COMPAT_DATA_PATH` and `STEAM_COMPAT_CLIENT_INSTALL_PATH`. It checks for the existence of the Proton binary and the provided file path. Based on the file extension (`.msi`, `.bat`, `.lnk`, or `.exe`), it uses Proton to run the corresponding file type (e.g., `msiexec` for MSI, `cmd` for BAT, `winepath` for LNK).
* **`proton_wrapper_replace.sh`**: This script's purpose is to replace the `wrapperinit.sh` script, located in `$HOME/Proton`, with the custom `proton_wrapper.sh` script. It ensures the `$HOME/Proton` directory exists and sets the custom script as executable.
* **`installer_1.sh`**: This script acts as an orchestrator for the initial installation steps. It sequentially runs `proton_dependencies.sh`, `proton_g_init.sh`, and `proton_wrapper_replace.sh`. It ensures that if any of these sub-scripts fail, the entire installation process is halted.
* **`installer_2.sh`**: This script completes the Proton setup by installing additional development dependencies necessary for compiling related tools (like `python3`, `git`, `make`, `cmake`, `g++`, `clang`, various `libdev` packages, and `wine64`/`wine32`). It then creates a `.desktop` file (`Proton.desktop`) in `~/.local/share/applications` to allow running Windows executables directly from the file manager. It sets this `.desktop` file as executable, makes the `wrapperinit.sh` executable, and updates the desktop database. Finally, it sets Proton as the default application for `.exe` and `.msi` file types using `xdg-mime`.

The scripts collectively provide a comprehensive solution for setting up a Proton environment, downloading the Proton core, handling dependencies, and integrating it with the desktop for running Windows applications. The GitHub repository "https://github.com/Partakithware/Protonify" is likely the source of these scripts and serves as a project dedicated to simplifying Proton installation and usage for Linux users.








