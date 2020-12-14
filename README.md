
# tools 

## Overview
We will be using these tools as they are widely used in open source development:
* Cmake - as build system
* Ninja - as builder
* clang - as compiler 
* git - as version control tool (e.g. to work on Github)

While not really required, I would recommend using an integrated development 
environment. IMHO this makes using all these tools much easier. In this tutorial,
we'll be using *Visual Studio Code* from Microsoft. While not 100% open source,
it has hughe ecosystem of extensions available and also works across many
operating systems.

# installing the tools
To make installation as easy as possible, we'll be using Chocolately as package 
manager. It will then install the tools we need: 
1. Install chocolately https://chocolatey.org/install using admin rights.
1. In a Powershell *with admin rights* run:
```choco install -y cmake ninja llvm git vscode git```
to install the tools we will need, the argument `-y` tells it to assume `yes`
on all questions during the installation. 

That's it.


# configuring VisualSudio Code
* Disable the C++ Intellisense extension, it will interfere with clangd. Even 
  if VSCode keeps asking you over and over again.
* Start Visual Studio Code and install these extensions:
  * clangd - The C++ language server from LLVM.
  * cmake - To configure the builds
* On the "Welcome" screen of Vistual Studio Code select "clone repository..." 
  and enter `https://github.com/jameskbride/cmake-hello-world` as URL. Then pick
  a local folder where you want to store that project.
* Allow Cmake to configure the project
  * When asked to select a "Kit" choose "Clang". This will select the compiler.
* To run something in VSCode, hit `<CTRL> + <SHITFT> + <p>`. This will open the 
  command bar. Use the command bar to run the followingn commands:
* Run `> CMake: configure` to configure the build environment. The Terminal 
  will show you the log output of the CMake commands. If you see 
  `Generating done` in the log, the configure step was successful.
* Run `> Cmake: build` (or hit `<F7>`) to build the project. Again you will see
  the log output of the compilation in the Terminal. If your system is be using
  Ninja as builder, `The build completed with exitcode 0.` means that the build
  was successful.
* Run `> CMake: run without Dibugging` (or hit `<shift> + <F5>`). This will run
  your program in the Terminal and show you the console output. If you see the
  output `Hello, world!` you program was run successfully.

That's it. You just downloaded a project from Github, configured CMake, compiled
and linked the project and were able to run the resulting program.


# TODO debugger