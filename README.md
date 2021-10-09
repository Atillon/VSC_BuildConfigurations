# VSC_BuildConfigurations

This is just a simple method for me and those who are interested in some unconventional ways of building C/C++ projects.

#-----COMPILER-----#
MinGW is used for Windows in these configurations, but the commands should work with any GCCcompilers on other systems.
You need the compilers locally on your machine. Windows users need to set up their system variables propery, this can be tested by entering the command "gcc --version" into their terminal of choice. If the directory to the compiler is set up properly in PATH, the command should work from everywhere on your computer.
The configurations need to be able to use the GCC Commands from everywhere on your computer.

For further instructions follow this guide:
-Windows:	https://code.visualstudio.com/docs/cpp/config-mingw
-Linux:		https://code.visualstudio.com/docs/cpp/config-linux

#-----CONFIGURATION-----#
The paths in settings.json and tasks.json need to be set to your local minGW directory manually.