# PicoCTF GDB Test Drive

One of the biggest issues in solving reverse engineering challenges is to understand what the program is designed to do. If the program stops running as soon as you execute it, it is difficult to analyze its functionality without viewing the source code. Debugging tools like GDB let you run the program one step at a time and pause at a specific location to investigate its functionality. This tutorial will walk you through the PicoCTF GDB Test Drive challenge. 

### In this tutorial, you’ll 

- Learn how to install GDB
- Learn how to use GDB to solve the GDB Test Drive PicoCTF challenge

You will use the following commands: 
* `mkdir` - Create a new directory
* `cd` - Change working directory
* `wget` - Download file via HTTP and HTTPS. 
* `chmod` - Change mode. Change permission



## Installing GDB

1. Open a Terminal. 

2. Download GDB If it is not already installed. 
```
sudo apt install gdb
```
3. Use `mkdir` to create a new folder **gdb_test_drive**, and use `cd` to navigate to the folder. 
```
mkdir gdb_test_drive && cd gdb_test_drive
```
4. Open the [GDB Test Drive challenge](https://play.picoctf.org/practice/challenge/273?page=1&search=GDB). On the popup, right click on the Binary link and copy the URL.

5. Use `wget` command with the URL you just copied in the previous step and download the file. 
```
wget https://artifacts.picoctf.net/c/86/gdbme
```
6. Use `chmod` command with the `+x`, followed by the file name to make the file executable.  
```
chmod +x gdbme
```
7. Execute the program and check its functionality.
```
./gdbme
```
The program doesn't do anything. It immediately goes to sleep. `CTRL + C` to quit the program.

<img src="https://github.com/tRumiBe/picoCTF/blob/main/images/3.png" width="400" height="82">

8. This time, run the program using GDB. 
```
gdb gdbme
```
![GDB](https://github.com/tRumiBe/picoCTF/blob/main/images/1.png)

9. View the assembly instructions using the following code.
```
layout asm
```
You can see the sleep function at **<main+99>**. Sleep function pauses execution. It suggests the program pauses at this location.  

![GDB layout assembly](https://github.com/tRumiBe/picoCTF/blob/main/images/6.png)

10. Set a breakpoint at **<main+99>**. The program will pause at this location. 
```
break *(main+99)
```
11. Start running the program by using `run` command. 
```
run
```
The program stops at sleep function.
![Sleep function](https://github.com/tRumiBe/picoCTF/blob/main/images/5.png)


12.  Use `jump` command to skip to the next function, which is **<main+104>**.
```
jump *(main+104)
```

You will get the flag. 
