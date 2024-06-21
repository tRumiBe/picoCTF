# PicoCTF GDB Test Drive

One of the biggest issues in solving reverse engineering challenges is to understand what the program is designed to do. If the program stops running as soon as you execute it, it is difficult to analyze its functionality without viewing the source code. Debugging tools like GDB let you run the program one step at a time and pause at a specific step to investigate its functionality. This tutorial will walk you through the PicoCTF GDB Test Drive challenge. 

### In this tutorial, you’ll 

- Learn how to install GDB
- Learn how to use GDB to solve the GDB Test Drive PicoCTF challenge

You will use the following commands. 
`mkdir` `cd` `wget` `chmod` `gdb` 


## Installing GDB

1. Open a Terminal. 

2. Download GDB If it is not already installed. 
```
sudo apt install gdb
```
3. Use `mkdir` command  to create a new folder **gdb_test_drive**, and navigate to the folder by typing `cd`. 
```
mkdir gdb_test_drive && cd gdb_test_drive
```
4. Open the [GDB Test Drive challenge](https://play.picoctf.org/practice/challenge/273?page=1&search=GDB), and right click on the binary file to copy the download link.

5. Use wget command and paste the link you copied in the previous step. 
```
wget https://artifacts.picoctf.net/c/86/gdbme
```
6. Use `chmod` command with the `+x` to make gdbme executable so that GDB can run it. 
```
chmod +x gdbme
```
7. Before running with GDB, execute gdbme. This helps to examine the program’s functionality. 
```
./gdbme
```
8. Gdbme immediately goes to sleep. `CTRL + C` to quit the program.

9. View the assembly instructions the program executes.  
```
layout asm
```
You can see the sleep function at **<main+99>**. Sleep function pause execution. It suggests the program pause at this location.  

===== Graphic ======

10. Set the breakpoint at **<main+99>**. You can pause the program by setting up breakpoints at a specific location. 
```
break *(main+99)
```
11. Start running the program by using `run` command. 
```
run
```

12. The program stops at sleep function. Use `jump` command to skip to the next function, which is **<main+104>**.
```
jump *(main+104)
```

You will get the flag. 
