# Compilaion-Xilinx-Library-for-QuestaSim
Tested on:
OS: Windows 10 64x
Xilinx ISE Design Suite 14.7 64x
Mentor Graphics QuestaSim 10.9c 64x

Add to environment variable your Xilinx & Questasim path. 
For example:

*C:\Xilinx\14.7\ISE_DS\ISE\bin\nt64*

*C:\questasim64_10.7c\win64*

You may change **-arch** for FPGA family you use and **-lib** (whatever Xilinx library you want to compile) in *questasim.src*

in *compile_lib.bat* we have **-dir C:/questasim64_10.7c/xilinx** - this is directory for your precompiled library. 
I prefer place libs in questasim directory but you may place it wherever you want.

And the last one:
After execution *compile_lib.bat* whithout any errors, 
in the dir (from where bat file was executed) you will find *modelsim.ini* (basically he just add Xilinx libraries)
you can use it two ways:
1. Add Xilinx lib path to main questasim *modelsim.ini* file (for example **C:\questasim64_10.7c\modelsim.ini**) like that:
```
[Library]
other libraries
...
; Xilinx library
secureip = $MODEL_TECH/../xilinx/secureip
unisim = $MODEL_TECH/../xilinx/unisim
unimacro = $MODEL_TECH/../xilinx/unimacro
unisims_ver = $MODEL_TECH/../xilinx/unisims_ver
unimacro_ver = $MODEL_TECH/../xilinx/unimacro_ver
simprim = $MODEL_TECH/../xilinx/simprim
simprims_ver = $MODEL_TECH/../xilinx/simprims_ver
xilinxcorelib = $MODEL_TECH/../xilinx/xilinxcorelib
xilinxcorelib_ver = $MODEL_TECH/../xilinx/xilinxcorelib_ver
```
2. Or use it in the testbenches directly
test.tcl:
```
set XILINX $env(XILINX)
setenv MODELSIM path_to_your_script/modelsim.ini
```

