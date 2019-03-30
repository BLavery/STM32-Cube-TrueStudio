# STM32-Cube-TrueStudio
Simplest STM32 programming using Cube and TrueStudio


## SUMMARY ONLY

Using cheap STM32 boards with free software, C/C++ code, ST's CubeMX configurator, Eclipse IDE, and CubeProgrammer.

Boards used:
 - STM32F030F4P6
 - STM32F103 BluePill
 - STM32F407VG
 
After trialing several eclipse versions, I settled on ST/Atollic/TrueStudio as current support, free, easiest to integrate with Cube.

CubeMX generates HAL-based setup code in C, not C++. TrueStudio/Eclipse can be adjusted to allow C++ for user code.
C code suits F030, as C++ code is too big for limited flash space.
C++ or C/C++ mix work very happily with the other boards.

Knocking together user C and C++ code for ...

 - serial printf, 
 - oled display, 
 - small tft display, 
 - some GPIO primitives that have an arduino ready-to-go feel, 
 - and millis() micros() sleep() and delayMicroseconds()
 
... is not too difficult, and from there we can "talk" to our board easily, and do trivial control. 

And we can use Cube to repeatedly change chip or pin options, without messing our user code.
 
**We now have the working basics in place.** 

But for bigger control, we will need to start doing some more serious coding/cutting/porting/debugging because ready-to-use libraries (a la arduino) are not just waiting somewhere!
 
# SETUP: VERY BARE OUTLINE:

*This info is from memory only, from investigations of several months ago. There are doubtless lots of further steps and tips you will have to discover for yourself for now.*


You will need a STlink device.

Create a folder for your project "workspace" in your user area. (eg .../brian/stm32projects would do for me.)
You are going to use this folder for each project:
 - Cubemx to write startup and config files.
 - TrueStudio to author and compile your projects
 - CubeProgrammer to flash your MCU from

Register with www.st.com.
Logged in to www.st.com, do a browser search for "stm32 cubemx"
Download stm32cubemx, install and start.
"Install/remove embedded packages" - Install for F0 F1 F4, or your own choice for your board families.
You have the option to choose the folder for this "repository". See Help-Updater Settings.

Still on www.st.com, find and download stm32Programmer. Install.
Plug in your STlink and start the programmer. 
Try to connect to STlink with programmer. 
You will likely be asked to do a Firmware Upgrade for the STlink.
You can attach your STM32 board to 4 wires of SWD. Don't have anything else powering the STM32.
The programmer should be able (via STlink) to connect to and identify the board.

Download TrueStudio (now sponsored by ST) from https://atollic.com/truestudio/
Install.

Time to start up.
Run CubeMX. "Start my project from MCU selector". Pick your MCU.
CubeMX is a whole world in itself. However once you get used to it, ten minutes should get you initially set up for a new project. You can easily revisit to make changes. The following is inadequate info for setting up. Find documentation or HOWTO info from online.

4 tabs. Start with Pinout and Config. Work your way through all options needed.
Ensure RCC selects clock crystals used on your board. 
Tab2: Clock config. Ensure your crystals (LSE HSE) are active. 
Adjust settings to get full clock speed at right side indicators, with no errors. Use the "resolve" if needed.
Tab3: Project Manager. Project location, the folder you created above. Give a project name. 
Toolchain TrueStudio, structure Basic.
All ready? "Generate Code" at top right.

TrueStudio possibly self starts. If not, start and "Import" what you just wrote to your workspace.
Go for broke? With your project now open, "Project - Build Project"
Get the Console tab low centre, and you should see a line per compile step, or errors if any.
You want a "Build finished" with no errors.

Start CubeProgrammer.
Check you connect to your board.
"Open File". In your workspace, in your projectname folder, find the .elf image.
Click Download. Your board has been flashed. Shame it doesn't have code to show anything.
But your IDE system works.

So go back to the main.c in your project, add a line or two of C to turn on a LED.
(You will need to consult the HAL document for your MCU family from ST.)
Put your code between a suitable pair of USER CODE BEGIN and USER CODE END comments. 
That way, CubeMX will not erase your code lines next Generate Code action.
 
**MORE DETAIL?  SORRY, STILL COMING. MIGHT BE A WHILE**
