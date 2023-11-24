# VSC_BuildConfigurations
This is just a simple method for me and those who are interested in some unconventional ways of building C/C++ projects. It works by abusing the "launch" and "tasks" configurations stored in the settings.json and tasks.json files. These files can be stored globally in your VSC user directory for easy access from any of your projects or they can be stored in a ".vscode" directory in your project within "launch.json" and "tasks.json" files for a neater and project specific configuration.
- "launch"-configuration: Creates a debugable workspace by giving it a displayable name, specifying a workspace, some use definitions, a debugger, the executable and most importantly, specifying a "preLaunchTask". This task is being executed and waited for before launching anything else and I use it to compile the code into an executable.
- "task"-configuration: Executes a command and is identified by the label. Those labels make changes extremely difficult and I hate it. Tasks can also rely on other task with the "dependsOn" option. I can't remember if the order of the listed tasks is preserved, but you could always daisy chain the tasks with the "dependsOn" option.

## Compilers and Debuggers
MinGW is used for Windows in these configurations, but the commands should work with any GCCcompilers on other systems.
You need the compilers locally on your machine. Windows users need to set up their system variables propery, this can be tested by entering the command "gcc --version" into their terminal of choice. If the directory to the compiler is set up properly in PATH, the command should work from everywhere on your computer.
The configurations need to be able to use the GCC Commands from everywhere on your computer.

The paths in settings.json and tasks.json need to be set to your local minGW directory manually.

For further instructions follow this guide:
- Windows:	https://code.visualstudio.com/docs/cpp/config-mingw
- Linux:		https://code.visualstudio.com/docs/cpp/config-linux

## Possible Improvements
A standarized file structure and better handeling of object files could be implemented... but at that point you could just use CMake (I hate this thing) and makefiles.

## Minimal Working Setup
You can just create a single source file and use a "Single File" launch option in the debug tab of VSC. This should compile the file you currently have in focus and start debugging the executable. 
If you want to understand a launch option, you would:
1. read the name and fail to interpret any meaning
2. check out the workspace it specifies
3. check out the executable it looks for
4. follow the "preLaunchTask" being executed
5. follow the chain of "dependsOn"-tasks
6. work your way back up the chain of "dependsOn"-tasks
7. and finally verify, that the arguments, label names and the name of the output files are not matching (most common mistakes)
8. (optional) check if debug symbols are generated, since VSC basically always launches a debugger, even if you don't have breakpoints

## Workflow
I usually only use this as a way to compile and execute my code via a button click inside of VSC and to avoid dealing with cmake. But this setup can probably definitely deal with any other programming language, since VSC can sometimes even create debug configurations automatically (e.g. for python).
The other launch options I implemented usually have some arbitrary requirements on the directory structure. Debugging was rarely used but could definitely come in handy. This setup has scored quite a few points over time:
- It is as light-weight as VSC can get, since it only relies on VSC executing some commands in the console for you. You can even configure it to use other terminals installed on your system (at least if I remember correctly).
- Has proven to be reliable and even extremely useful when it came to supporting me in my first beginner vulkan project with about 5000 lines of code. I doubt, that bigger projects would encounter any unexpected problems.
- It came in really handy when I needed some basic debugging-features for helping other students on random computers that are badly configured or only offer CodeBlocks (...I also hate this, but even more).

Have fun torturing yourself with this and please ignore my random test configurations. As of the time of writing this, I have switched from using VSC to using Neovim.
I can only recommend this only if you need something that you can come back to if you are stuck with machines that you don't really want to configure or if you want to abuse the "launch debug" button of VSC. The computers in my university or those of my friends, usually only have VSC and some heavy, greasy IDE like CodeBlocks or Visual Studio installed, so this is the easiest method for me.
