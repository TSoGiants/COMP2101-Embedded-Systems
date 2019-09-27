# COMP2101 Embedded Systems Programming

## Table of Content

* [Open Action Items](#Open-Action-Items)
* [Project Scope](#Project-Scope)
* [Miscellaneous](#Miscellaneous)

## Open Action Items

Mr. Dugie - Type up process of setting up Visual Studio Code and the Blink program for the lesson 1 worksheet.
Dr. F - Write up an introduction to microcontrollers based on the previously written slide deck.

## Project Scope

Kepler short-course on the fundamentals of microcontroller programming and architecture.

Development of this course is underway; you can follow our progress alternating Friday mornings at 9am CDT at www.tsog.tv.

The focus of this course is to teach students how to work with microcontrollers such as the AVR architecture microcontrollers found in Arduino devices. Students who have completed this course should understand the basics of microcontroller architecture and be able to create simple, practical software in a professional programming environment.

### Proposed 8-week schedule

1. General Introduction and Basic Setup
2. Introduction to Digital Inputs and Outputs
3. Introduction to Analog Inputs and PWM
4. Introduction to 7-segment LED Display and Clock Project
5. Moving the Clock Project to the LCD
6. Expanding the LCD Project pt. 1
7. Expanding the LCD Project pt. 2
8. Expanding the LCD Project pt. 3

### Week 1: General Introduction and Setup

1. Install the Arduino IDE.
    1. Take the default install settings and file locations.
2. Install Visual Studio Code.
    1. Take the default file locations.
    2. Be sure to select "Add 'Open with Code' option" whenever it is offered.
    3. It's convenient but not required to set VSC as the default editor for supported file types.
3. Before making any changes or doing anything too interesting, make sure that your Arduino board works with the Arduino IDE.
    1. Open the Arduino IDE and load the "Blink.ino" example sketch (File > Examples > Basics > Blink).
    2. Update your build environment to match your specific hardware and active port (Tools > Board and Tools > Port).
    3. Upload the sketch to the board and see whether the behavior is as expected.
4. In VSC, install the following extensions:
    1. Arduino by Microsoft
    2. C/C++ Intellisense by Microsoft
5. Open the VSC command palette (Ctrl + Shift + P) and search for "Arduino Examples". Use the dialogue that opens to find the Blink project again.
6. Use the command palette to find the "Arduino Board Configuration" dialogue. Configure VSC as you configured the Arduino IDE previously.
7. Use the command palette to find the "Arduino Upload" dialogue. The upload process can also be started with the Ctrl + Alt + U keybinding.
8. Try out the C/C++ extension by right clicking on a variable or function name, then selecting "Go to declaration" or "Go to definition". VSC should open some completely separate file. These files were installed along with the Arduino IDE.

## Miscellaneous

### Notes from first Standing Meeting (8/30/19)

Discussed the initial lesson in-depth and how it will impact the remainder of the course. Decided to focus on development in Visual Studio Code to allow students to explore the built-in libraries used by the Arduino platform.

### Notes from third Standing Meeting (9/27/19)

We'll plan on using the Elegoo Super Starter Kit UNO R3 (~$36). The kit includes everything needed for an introductory course.
