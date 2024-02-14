# SYSTEM REQUIREMENTS

Please be sure that your system meets these minimum software prerequisits
before running Scarab. Below are the packages that we use to run Scarab.
Other versions of the same software may work, but have not been tested.

Scarab relies on the following software packages:

## Required Packages
* [Intel PIN (see below)](#tested-intel-pin-versions)
* g++ 7.3.1
* gcc 7.3.1
* Clang 5.0.1
* Python 3.6.3
* [Intel XED 12.01](https://github.com/intelxed/xed/releases) (included as a git submodule)

## Tested Intel PIN versions:
* [PIN-Play 3.5](https://software.intel.com/en-us/articles/program-recordreplay-toolkit)
* [PIN 3.15](https://www.intel.com/content/www/us/en/developer/articles/tool/pin-a-binary-instrumentation-tool-downloads.html)

Note: Our checkpoint creater scripts only work with PIN-Play currently (due to a despendency with their simpoint scripts).

## Required Python Packages
See `$SCARAB_ROOT/bin/requirements.txt`

## How to Setup Scarab
1. Git clone the scarab repository and cd into scarab
2. Get the submodules using:
```git submodule update --init```
3. Go into src/dep/xed and run:
```./mfile.py```
4. Copy PIN 3.15 (for linux) onto the machine
5. Disable yama if you’re on Ubuntu (check the PIN 3.15 readme)
6. In the scarab folder, get all the python packages from requirements.txt
    (You may have to install numpy 1.24.0 if the make command fails)
7. Go to scarab/src/pin/pin_lib/decoder.cc. Go to line 140 and add an “&” before “opcode”.
8. Downgrade to gcc 9.5.0
9. Set PIN_ROOT to the path of the folder that contains pin.exe and run “make” in scarab/src:
```export PIN_ROOT="/path/to/folder/containing/pin"```

Step 9 is required every time you reboot your machine.

##### E.g. Install with pip:
```
cd $SCARAB_ROOT/bin
pip3 install -r requirements.txt
```

# Other Useful Packages

## If Running GTest
* GTest 1.6

## If Using Power Model
* Perl 5 v5.16.3
* [McPAT v1.0](http://www.hpl.hp.com/research/mcpat/)
* [CACTI 6.5](http://www.hpl.hp.com/research/cacti/)

Note: Lower or higher versions of the above software may work, but have not been tested.
