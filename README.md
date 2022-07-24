# Embedded-Systems-Lab1
Assignment provided by Embedded Systems (ECGR 3101)
This project was performed using a board EK-TM4C123GXL and Energia IDE

Objective
This project has multiple learning objectives.  After completing the lab, students will be able to use the GPIO peripheral for both inputs (switches) and outputs (LEDs).  Second, the lab explicitly requires the students to find some additional software needed and incorporate that into the project.  Third, this lab will expose students to the SysTick peripheral and how to use polling to create time delays.

Procedure
From Resource Explorer  search for information about our board EK-TM4C123GXL.

Using the resulting tree (inside the Explorer panel), find the example 'blinky", (Software>TM4C ARM Cortex  M4F>Examples>blinky)and click on "blinky".

Using the icons in the upper right corner, use the "Import to IDE" get a local copy of the project.  Then use the "Install" icon to create a project that you can edit.

Rename "blinky" to "lab2".  (Click on "blinky" and then "File>Rename".)

Strip out all the blinky code and update the include directives to have these header files:
#include <stdint.h>
#include <stdbool.h>
#include "inc/hw_types.h"
#include "inc/hw_memmap.h"
#include "inc/hw_nvic.h"
#include "driverlib/gpio.h"
#include "driverlib/sysctl.h"
#include "driverlib/systick.h"
#include "buttons.h"

Copy the buttons.h and buttons.c into your project directory; forexample:
-cp -i ~/ti/.../examples/boards/ek-tm4c123gxl/drivers/buttons.[ch] .
   

Now you are ready to begin: Review the requirements below and plan out the software needed for this project.  No extra hardware circuit is needed for this lab.  

HINT1:  Create two functions: "main()" and "mydelay()".

HINT2: how will you alternate the two colors?

HINT3:  Where do you check for debounce in the design? set the clock frequency to 80 MHz
-enable the port for the red and green LEDs
-(wait for it to be ready)
-set the GPIO direction

In the second part of main(),
-set up the switchs (using calls to button.c)
-set SysTick RELOAD value for a 0.2 s delay
-enable the SysTick peripheral

In the last part of main(),
-create a while(1) do-forever loop
-turn off all of the LEDs
-turn on the current LED color
-delay for 4 seconds
-turn off the current LED color
-delay for 4 seconds

In mydelay(), you will need to get into the low-level details to poll the SysTick peripheral.
-using HWREG macro to transfer the reload register value to the count register
-create a loop to count a 4 second delay based 0.2 second delay created by SysTick
-use HWREG macro to check the COUNT flag in the SysTick control register
-Last hint:  here's where you want to check button_poll and use the BUTTON_PRESSED macro.

Requirements
-Code is formatted correctly (proper indentation, descriptive names, no magic numbers, appopriate comments
-explicitly set the clock frequency to 80 MHz
-add (and use) button.c and button.h to debounce switches
-SW1 turns LED red, SW2 turns LED green
-complete on-(4s)delay or off-(4s)delay cycle before switching colors
-before deadline, upload code, and the check-off sheet to Canvas

Criteria
-Clock frequency is set to 80 MHz
-texttt{button.c} and \texttt{button.h} are used to debounce switches
-SW1 turns LED red, SW2 turns LED green
-Complete on-(4s)delay or off-(4s)delay cycle before switching colors
