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







