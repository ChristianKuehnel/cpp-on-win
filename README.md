
# Developing C++ on Windows 

This tutorial will walk you through installing and configuring widely used
C++ development tools on Windows.

## Tool Overview
We will be using these tools as they are widely used in open source development:
* [Cmake](https://cmake.org/) - as build management system
* [Ninja](https://ninja-build.org/) - as build system actually doing the building
* [LLVM](http://llvm.org/) - as compiler (clang) , linker (lld), debugger (lldb), 
  language server (clangd)
* [git](https://git-scm.com/) - as version control tool (e.g. to work on Github)

While not really required, I would recommend using an integrated development 
environment. IMHO this makes using all these tools much easier. In this tutorial,
we'll be using [Visual Studio Code](https://code.visualstudio.com/) from Microsoft (short VSCode). 
While not 100% open source, it has hughe ecosystem of extensions available and 
also works across many operating systems and languages.

## Installation
To make installation as easy as possible, we'll be using Chocolately as package 
manager. It will then install the tools we need: 

1. Install chocolately https://chocolatey.org/install using admin rights.

1. In a Powershell *with admin rights* run:
```choco install -y cmake ninja llvm git vscode git```
to install the tools we will need, the argument `-y` tells it to assume `yes`
on all questions during the installation. 

That's it.


## Configuring VSCode
Now that we have all the tools installed, we need to configure them. We will do
this by configuring a first project to see if everything is working.

1. Start Visual Studio Code and install these extensions:
   * [clangd](https://marketplace.visualstudio.com/items?itemName=llvm-vs-code-extensions.vscode-clangd), 
     the C++ language server from LLVM.
   * [CMake Tools](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cmake-tools), 
     to configure the builds from within VSCode
1. Disable the C++ Intellisense extension, it will interfere with clangd. 
  If there is a pop-up, decline it, even if VSCode keeps asking you over and 
  over again. We'll be using `clangd` instead.
1. On the "Welcome" screen of Vistual Studio Code select "clone repository..." 
  and enter `https://github.com/jameskbride/cmake-hello-world` as URL. Then pick
  a local folder where you want to store that project.
1. Allow Cmake to configure the project. When asked to select a "Kit" choose 
   "Clang". This will select clang & Co as your toolchain for this project.
1. To run something in VSCode, hit `<CTRL> + <SHITFT> + <p>`. This will open the 
   "Command Palette". Use the Command Palette to run the followingn commands:
   1. Run `> CMake: configure` to configure the build environment. The Terminal 
      will show you the log output of the CMake commands. If you see 
      `Generating done` in the log, the configure step was successful.
   1. Run `> Cmake: build` (or hit `<F7>`) to build the project. Again you will see
      the log output of the compilation in the Terminal. If your system is be using
      Ninja as builder, `The build completed with exitcode 0.` means that the build
      was successful.
   1. Run `> CMake: run without Debugging` (or hit `<shift> + <F5>`). This will run
      your program in the Terminal and show you the console output. If you see the
      output `Hello, world!` you program was run successfully.

That's it. You just downloaded a project from Github, configured CMake, compiled
and linked the project and were able to run the resulting program.


## TODO: Running the debugger

## TODO: Unit testing 
using GTest
