# LLDB [![42](https://i.imgur.com/9NXfcit.jpg)](i.imgur.com/9NXfcit.jpg)

The Low Level Debugger Rush [42 project] is a short introduction to the Low Level Debugger.

The main topics in this rush are: .lldbinit config files, python scripting for lldb, and troubleshooting methods.

---

## Description

It contains 3 directories - one for each part.

- Part I - Configuration

- Part II - Usage

- Part III - Script

#### Configuration: 00-init

Directory: `00-init`

Files: `.lldbinit` + `banner_init.py`

`.lldbinit` config file sets the Intel style disassembly syntax, changes the prompt to the login and automatically launches of a script displaying a banner of the login and to the prompt.

`banner_init.py` using the LLDB API, the script is getting the USER environment variable and injecting it. It also generates a fancy banner changing color in a random fashion.

#### Usage: 01-usage

Directory: `01-usage`

Files: `.lldbinit` + `commandes`

`commandes` is pointed by the symlink `.lldbinit` for debugging automation.

In this section, the purpose is to debug the example.cpp code using only lldb (expr, breakpoint etc.).

To compile the example.cpp:

```shell=
clang++ -Wall -g source.cpp -o example
```

Once the compilation of example.cpp is finished input the following command in lldb (lldb example):

```shell=lldb
breakpoint set --name main
process launch
```

From this breakpoint, the program will be debugged with the commands in `commandes` file.

In this example, it was required to debugg the program using as few as possible commands.

#### Script: 02-script

Directory: `02-script`

Files: `reverse.py`

`reverse.py` contains a small Python script whose purpose is to display the name of the program - set as target - in reverse. A "FT\_" prefix is added to the reversed text.

---

## Usage

- Install lldb

```shell=
brew instal lldb
```

- Make lldb read by default .lldbinit file in current repository

```shell=
printf "# Injection - Rush LLDB settings:\nsettings set target.load-cwd-lldbinit true\n" >> .lldbinit
```

- Clone repository

```shell=
git clone https://github.com/Ant0wan/Lldb.git && cd Lldb
```

- Compile the source.cpp

```shell=
clang++ -Wall -g source.cpp -o example
```

- For the next step please refer to the `Description` part above.

---

## Demo

[![DemoLLDB](https://i.imgur.com/BdVnaDy.gif)](i.imgur.com/BdVnaDy.gif)
