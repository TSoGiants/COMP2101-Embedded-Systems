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
* ~~Complete writing lesson #1.~~

### Dr. F

* Write up an introduction to microcontrollers based on the previously written slide deck.
* Still needs to write up an introduction to microcontrollers based on the previously written slide deck.
* Finish introduction to microcontrollers, purchase Elegoo kit, and begin writing lesson #2 based off the SBEE embedded systems worksheets.

## Project Scope

The focus of this course is to teach students how to work with microcontrollers such as the AVR architecture microcontrollers found in Arduino devices. Students who have completed this course should understand the basics of microcontroller architecture and be able to create simple, practical software in a professional programming environment.

### Lesson 1: General Introduction and Setup

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

Right click on the `delay` portion of the second `delay(milliseconds)` function call and select "Go to Definition" to go to the .c or .cpp file where the function is defined. Copy the content of this function, go back to Blink.ino, delete the second call to `delay(ms)`, and replace it with the copied code snippet. Try uploading the new Blink.ino file.

Even though the code from the function definition is "the same" as the function, the logic has to change slightly because the context has changed. Work through this problem on your own and compare your solution to [ours](#Lesson-1-Code-Examples) when you're done.

### Lesson 2: Digital Inputs and Outputs

#### Further Activities for Lesson 2

### Lesson 3: Analog Inputs and PWM

#### Further Activities for Lesson 3

### Lesson 4: Seven-Segment LED Display

#### Further Activities for Lesson 4

### Lesson 5: Liquid Crystal Display

#### Further Activities for Lesson 5

### Lesson 6: LCD continued

#### Further Activities for Lesson 6

### Lesson 7: Monitoring Analog Sensors with the LCD

#### Further Activities for Lesson 7

### Lesson 8: Monitoring Digital Sensors with the LCD

#### Further Activities for Lesson 8

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

### Lesson 1 Code Examples

```c
// the loop function runs over and over again forever
void loop() {
  uint32_t dly_ms = 1000, start = 0;
  digitalWrite(LED_BUILTIN, HIGH);   // turn the LED on (HIGH is the voltage level)
  delay(dly_ms);                     // wait for a second
  digitalWrite(LED_BUILTIN, LOW);    // turn the LED off by making the voltage LOW

  start = micros();                  // Get the system time in microseconds (us)
  while(dly_ms * 1000 > micros() - start)
  { /* While the delay is greater than the time passed since checking micros() */
    yield();                         // Let the processor handle other tasks
  }
}
```
