# COMP2101 Embedded Systems Programming

Kepler short-course on the fundamentals of microcontroller programming and architecture.

Development of this course is underway; you can follow our progress alternating Friday mornings at 9am CDT at www.tsog.tv.

## Table of Content

* [Action Items](#Action-Items)
* [Project Scope](#Project-Scope)
* [Miscellaneous](#Miscellaneous)

## Action Items

### Mr. Dugie

* ~~Type up process of setting up Visual Studio Code and the Blink program for the lesson 1 worksheet.~~
* ~~Evaluate available Arduino kits to find a good match for our course objectives.~~
* Complete writing lesson #1.

### Dr. F

* Write up an introduction to microcontrollers based on the previously written slide deck.
* Still needs to write up an introduction to microcontrollers based on the previously written slide deck.
* Finish introduction to microcontrollers, purchase Elegoo kit, and begin writing lesson #2 based off the SBEE embedded systems worksheets.

## Project Scope

The focus of this course is to teach students how to work with microcontrollers such as the AVR architecture microcontrollers found in Arduino devices. Students who have completed this course should understand the basics of microcontroller architecture and be able to create simple, practical software in a professional programming environment.

### Lesson 1: General Introduction and Setup

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

#### Independent Project Suggestions for Lesson 1

### Lesson 2: Digital Inputs and Outputs

#### Independent Project Suggestions for Lesson 2

### Lesson 3: Analog Inputs and PWM

#### Independent Project Suggestions for Lesson 3

### Lesson 4: Seven-Segment LED Display

#### Independent Project Suggestions for Lesson 4

### Lesson 5: Liquid Crystal Display

#### Independent Project Suggestions for Lesson 5

### Lesson 6: LCD continued

#### Independent Project Suggestions for Lesson 6

### Lesson 7: Monitoring Analog Sensors with the LCD

#### Independent Project Suggestions for Lesson 7

### Lesson 8: Monitoring Digital Sensors with the LCD

#### Independent Project Suggestions for Lesson 8

## Miscellaneous

### Notes from Standing Meeting (8/30/19)

Discussed the initial lesson in-depth and how it will impact the remainder of the course. Decided to focus on development in Visual Studio Code to allow students to explore the built-in libraries used by the Arduino platform.

### Notes from Standing Meeting (9/13/19)

Discussed an overall project plan for the students to complete throughout the course. Decided that the format of a 3-week mini-project, followed by a longer 5-week project would be applicable to this course. Looked through a number of Arduino starter-kits on Amazon.com, but did not select one that would be the "ideal" fit for the course. Concluded that the course should be written around components available in common kits, rather than trying to find a kit or package that fits a given curriculum.

### Notes from Standing Meeting (9/27/19)

Dr. F floated the idea of building our own PCB / kit for the course, but Mr. Dugie found a good kit from a reputable manufacturer (Elegoo) that should have the contents, price point, and longevity that we need for this class: https://www.amazon.com/ELEGOO-Project-Tutorial-Controller-Projects/dp/B01D8KOZF4 Basing our discussion around this kit, we decided upon the following tentative lesson schedule:

1) General intro to IDE / blink / basics
2) Digital input (buttons and leds)
3) Analog input and output (tri color LED and potentiometer)
4) Setting up the 7 segment display (single digit 0-9)
5) Two-line LCD display, part 1
6) Two-line LCD display, part 2
7) Analog sensors
8) Digital sensors
