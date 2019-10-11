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
* ~~Complete drafting lesson #1.~~
* Complete drafting lesson #2.
* Complete drafting lesson #3.
* Complete drafting lesson #4.
* Complete drafting lesson #5.
* Complete drafting lesson #6.
* Complete drafting lesson #7.
* Complete drafting lesson #8.
* Review completed lessons and example snippets, adding context and related technical information where possible.

### Dr. F

* Write up an introduction to microcontrollers based on the previously written slide deck.
* Still needs to write up an introduction to microcontrollers based on the previously written slide deck.
* Finish introduction to microcontrollers, purchase Elegoo kit, and begin writing lesson #2 based off the SBEE embedded systems worksheets.

## Project Scope

The focus of this course is to teach students how to work with microcontrollers such as the AVR architecture microcontrollers found in Arduino devices. Students who have completed this course should understand the basics of microcontroller architecture and be able to create simple, practical software in a professional programming environment.

### Lesson 1: General Introduction and Setup

In this lesson, we will prepare a helpful development environment and compile our first project. This will include minimally technical explanations of memory addresses, volatile and non-volatile memory, and data types and modifiers.

1. [Install](https://www.arduino.cc/en/Main/Software) the Arduino IDE and associated support files.
    1. Get the Windows installer instead of the .zip file or the app.
    2. In the "Select components to install" menu, the "Create Desktop shortcut" component is optional but all others should be selected.
    3. Install to the default destination folder.
2. [Install](https://code.visualstudio.com/Download) Visual Studio Code.
    1. Accept the license agreement.
    2. Install to the default destination folder.
    3. Accept the default start menu folder.
    4. In the "Additional Tasks" menu, check that the "Open with Code" action will be added to the file context menu and directory context menu, that Code will be registered as an editor for supported file types, and that Code will be added to PATH.
3. Before making any changes or doing anything too interesting, make sure that your Arduino board works with the Arduino IDE.
    1. Open the Arduino IDE and load the "Blink.ino" example sketch (File > Examples > Basics > Blink).
    2. Update your build environment to match your specific hardware and active port (Tools > Board and Tools > Port). We are going to be using the Genuino Uno for these projects.
    3. Upload the sketch (Ctrl + u) to the board and see whether the behavior is as expected. Try changing the value of the `delay(milliseconds)` function to see how the behavior of the board changes.
    4. Once you're satisfied that the board is working, close the Arduino IDE.
4. In Code, install the following extensions (Ctrl + Shift + X):
    1. Arduino by Microsoft
    2. C/C++ by Microsoft
5. Open the Code command palette (Ctrl + Shift + P) and search for "Arduino Examples". Use the dialogue that opens to find the Blink project again, and open the Blink.ino file.
6. Use the command palette to find the "Arduino Board Configuration" and "Select Serial Port" dialogues. Configure Code as you configured the Arduino IDE previously.
7. Use the command palette to find the "Arduino Upload" dialogue. The upload process can also be started with the Ctrl + Alt + U keybinding.

One of the best reasons to use Code instead of the Arduino IDE is the choice of extensions offered by Code. You may have already noticed the more readable syntax highlighting, but other tools are even more valuable than that. Right now, your Blink.ino file has only two functions: `void setup()` and `void loop()`. However, the usual convention for C and C++ is to have an `int main()` function in a main.c or main.cpp file that will always start the project. So what's happening here?

Right click on the `setup` portion of `void setup()` and select "Go to Declaration" from the resulting menu. This will cause Code to search for the header file where the `setup()` function was first declared. Since we used the default install locations, this file is going to be at `C:\Program Files (x86)\Arduino\hardware\arduino\avr\cores\arduino\Arduino.h`. By right clicking and going directly to the header file, we saved a lot of time that otherwise would have been spent searching!

Next, right click on the tab at the top of the Code interface that says "Arduino.h" and select "Reveal in Explorer". This will open a new Windows explorer window in the project directory for Arduino.h. Once the window is open, type "main" and your file selector should jump down to main.cpp. Open this file and find the `int main(void)` function it contains. You should now be able to see how the `setup()` and `loop()` functions are related to each other as well as how the actual loop is managed.

#### Further Activities for Lesson 1

##### Configure the Local Build Environment

When building your Blink.ino project, you may see the following message:

```console
[Warning] Output path is not specified. Unable to reuse previously compiled files. Upload could be slow. See README.
```

If so, you could take the following steps:

1. Reveal Blink.ino in the Windows Explorer.
2. Open the .vscode directory, and then the arduino.json file.
3. Add the following line at the end of your .json file:

    ```json
    "output": "../build"
    ```

4. Make sure that all lines in this file except the last have a comma at the end. JSON files aren't code files, but they require specific syntax to be interpreted correctly.

##### Replace a Function Call and Debug the Resulting Problems

Right click on the `delay` portion of the second `delay(ms)` function call and select "Go to Definition" to go to the .c or .cpp file where the function is defined. Copy the content of this function, go back to Blink.ino, delete the second call to `delay(ms)`, and replace it with the copied code snippet. Try uploading the new Blink.ino file.

Because the context is different, copying code from a function declaration to replace a function call will usually result in an error. Fix Blink.ino on your own by studying the source file you copied from and checking the build output for compile errors. If you have time, do the same thing with the second `digitalWrite` call. Compare your solution to [ours](#Lesson-1-Code-Examples) when you're done.

### Lesson 2: Introduction to Wiring, Digital Inputs, and Digital Outputs

In this lesson, we will introduce basic components such as push buttons and LEDs. This will include discussion of wiring, nodes, currents and charge carriers, and cathodes and anodes.

1. From your starter kit, remove the large breadboard, the small breadboard the jumper wires, the packet of LEDs, and the five push buttons. From the packet of LEDs, remove one of each type of LED (white, blue, green, yellow, red, tricolor). The tricolor LEDs appear similar to the white LEDs but have four legs instead of two.
2. Both the large breadboard and the small breadboard have a layer of adhesive foam on their undersides. The adhesive is good for only a few uses, especially if left in place for quite a while, but it can be used to anchor a breadboard to a surface after a circuit has been completed. This is useful for some projects. The foam backing is easily deformed, and is usually easy to manipulate. Peel away a corner of the non-adhesive film from the bottom of the smaller breadboard, then peel away a corner of the foam to reveal the conductive inserts that allow solderless breadboards to conduct electricity. These inserts can be pried out from the breadboard with a pin or mechanical pencil. Once you are done examining the smaller breadboard, undo your changes as best as you can and set it back inside the box. We will not be using it much.
3. Place one push button onto your large breadboard
    * Examine the button. You will see that it has four legs, and is longer in one direction than the other. Each "side" of the button has two legs that are facing the same direction. These legs that face the same direction are electronically separated by a very large resistance, such that the flow of charge carriers between them is equal to or very close to zero. These legs are said to be in an "open circuit" state. The legs that are located directly across from and are facing away from each other are separated by a very small resistance, such that the flow of charge carriers between them is unrestricted or very close to unrestricted. These legs are said to be in a "closed circuit" or "short circuit" state. When the button is pushed, two pieces of conductor inside the button are forced to touch. This shorts the two nodes together, bypassing the large resistance and allowing charge carriers to flow freely from any of the legs to any other.
4. We will now begin wiring our breadboard. Using your jumper wires, connect the two red rails of your breadboard together. Next, do the same with the two blue rails. By convention, the red rail is the highest voltage node ("supply") and uses red wires while the blue rail is the lowest voltage supply ("ground") and uses black wires. Staying with convention can help others understand your circuit more quickly, but is not required. Use more jumper wires to connect your supply rail to a 3.3V port of your controller board and your ground rail to a GND port of your controller board.
5. Take one of your single color LEDs, and see that one of the legs is shorter than the other. Insert the short leg of the LED into the ground rail of our circuit board, and insert the long leg into one of the rows that has been connected to a button.
6. Take one of your 220Ω resistors and connect it from the supply rail of your breadboard to the same row as the longer LED leg. The LED should light up! Using a smaller resistor will allow higher current, which will result in a brighter LED. Using a larger resistor will do the opposite and result in a dimmer LED. Each LED is likely to have a different level of brightness for a certain amount of current, but allowing too much current to flow through the LED will damage it very quickly. If any of your LEDs become damaged and no longer lights up, set it aside or throw it away. It cannot be repaired.
7. Remove the resistor from the row with the LED's longer leg and instead connect it to the other leg of the button that is on the same side of the breadboard. Push the button to turn the LED back on.

We have demonstrated the basic physical principles and component behaviors that we will be relying on, so let's move on to the coding!

#### Further Activities for Lesson 2

### Lesson 3: Introduction to Analog-Digital Conversion (ADC), Pulse Width Modulation (PWM) and True Analog Outputs

Draft deadline: 20 October 2019

#### Further Activities for Lesson 3

### Lesson 4: The Seven-Segment LED Display

Draft deadline: 20 October 2019

#### Further Activities for Lesson 4

### Lesson 5: The Liquid Crystal Display (LCD)

Draft deadline: 27 October 2019

#### Further Activities for Lesson 5

### Lesson 6: The LCD continued

Draft deadline: 27 October 2019

#### Further Activities for Lesson 6

### Lesson 7: Monitoring Analog Sensors with the LCD

Draft deadline: 27 October 2019

#### Further Activities for Lesson 7

### Lesson 8: Monitoring Digital Sensors with the LCD

Draft deadline: 3 November 2019

#### Further Activities for Lesson 8

## Miscellaneous

### Notes from Standing Meeting (8/30/19)

Discussed the initial lesson in-depth and how it will impact the remainder of the course. Decided to focus on development in Visual Studio Code to allow students to explore the built-in libraries used by the Arduino platform.

### Notes from Standing Meeting (9/13/19)

Discussed an overall project plan for the students to complete throughout the course. Decided that the format of a 3-week mini-project, followed by a longer 5-week project would be applicable to this course. Looked through a number of Arduino starter-kits on Amazon.com, but did not select one that would be the "ideal" fit for the course. Concluded that the course should be written around components available in common kits, rather than trying to find a kit or package that fits a given curriculum.

### Notes from Standing Meeting (9/27/19)

Dr. F floated the idea of building our own PCB / kit for the course, but Mr. Dugie found [a good kit from a reputable manufacturer (Elegoo)](https://www.amazon.com/ELEGOO-Project-Tutorial-Controller-Projects/dp/B01D8KOZF4) that should have the contents, price point, and longevity that we need for this class. Basing our discussion around this kit, we decided upon the following tentative lesson schedule:

1) General intro to IDE / blink / basics
2) Digital input (buttons and leds)
3) Analog input and output (tri color LED and potentiometer)
4) Setting up the 7 segment display (single digit 0-9)
5) Two-line LCD display, part 1
6) Two-line LCD display, part 2
7) Analog sensors
8) Digital sensors

### Lesson 1 Code Examples

```c
// the loop function runs over and over again forever
#define DLY_MS (uint32_t)1000
void loop() {
    uint32_t start;
    uint8_t pin = LED_BUILTIN, bit;
    volatile uint8_t *out;

    digitalWrite(pin, HIGH);  // turn the LED on (HIGH is the voltage level)
    delay(DLY_MS);            // wait for the specified amount of time

    out = portOutputRegister(       /* Get the address mapped to the state of the pin.      */
          digitalPinToPort(pin)     /* For more information about our controller, see       */
    );                              /* https://www.microchip.com/wwwproducts/en/ATMEGA328P  */
    bit = digitalPinToBitMask(pin); // Get the position of the pin on the register
    *out &= ~bit;                   // Set the pin's bit on the register's byte to 0

    start = micros();   // Get the system time in microseconds (us)
    while(DLY_MS * 1000 > micros() - start) 
    { /* While the delay is greater than the time passed since checking micros() */
        yield();        // Let the controller handle other tasks
    }
}
```
