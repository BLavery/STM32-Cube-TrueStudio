# STM32-Cube-TrueStudio
Simplest STM32 programming using Cube and TrueStudio


## SUMMARY ONLY

Using STM32 boards with free software, C/C++ code, ST's CubeMX configurator, Eclipse IDE, and CubeProgrammer.

Boards used:
 - STM32F030F4P6
 - STM32F103 BluePill
 - STM32F407VG
 
After trialing several eclipse versions, I settled on ST/Atollic/TrueStudio as current support, free, easiest to integrate with Cube.

Cube generates C setup code, not C++. TrueStudio/Eclipse can be adjusted to allow C++ for user code.
C code suits F030, as C++ code is too big for limited flash space.
C++ or C/C++ mix work very happily with the other boards.

Knocking together user C++ code for ...

 - serial printf, 
 - oled display, 
 - small tft display, 
 - some GPIO primitives that have an arduino ready-to-go feel, 
 - and millis() micros() sleep() and delayMicroseconds()
 
... is not too difficult, and from there we can "talk" to our board easily, and do trivial control. 

And we can use Cube to repeatedly change chip or pin options, without messing our user code.
 
**We now have the working basics in place.** 

But for bigger control, we will need to start doing some more serious coding/cutting/porting/debugging because ready-to-use libraries (a la arduino) are not just waiting somewhere!
 
**MORE DETAIL?  SORRY, STILL COMING.**
