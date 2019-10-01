## compile and install
All of the steps can be found all over the net;
## Learn
When starting to learn the code, we can find that like in arch/arm64/kernel directory, it's difficult to read the code directly because of a lot of macros, Thus we need to pretreat the code, which mean there should be three steps to do before the reading.
### Download the cross-compile tools 
Because the arm platform is so slow that we compile its directories on windows/linux, while in this way, we have to use codesourcery tools.
For arm64, we can download aarch64-linux-gnu- to do the cross compile.
```shell
sudo apt-cache search aarch64 ##find the suitable version of tools for arm64 for your computer.
sudo apt-get install gcc-aarch64-linux-gnu ##for example
sudo apt-get install gcc7-aarch64-linux-gnu ##for example
```
### Use Makefile to ensure the -I of gcc when compile the ***.c
Using V=1, the command will set up .cmd to store every command for every output.
```shell
make ARCH=arm64 CROSS_COMPILE=aarch64-linux-gnu- -j8 V=1
```
Thus we can do what we want. For example, change the "-o arch/arm/kernel/sys.c arch/arm/kernel/sys.o" into "-E arch/arm/kernel/sys.c arch/arm/kernel/sys.i"

![](/home/zhuyuanming/Pictures/asm646.png)
![](/home/zhuyuanming/Pictures/asm647.png)

Then cat the sys.i, we can get the sys_call_table.

![](/home/zhuyuanming/Pictures/asm648.png)




