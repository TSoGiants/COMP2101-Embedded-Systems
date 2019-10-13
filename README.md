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
* Pull educational information to the front of each lesson.
* ~~Draft lesson #1.~~
* ~~Draft lesson #2.~~
* Draft lesson #3.
* Draft lesson #4.
* Draft lesson #5.
* Draft lesson #6.
* Draft lesson #7.
* Draft lesson #8.
* Review completed lessons, example code snippets. Add context and related technical information when useful.

### Dr. F

* Write up an introduction to microcontrollers based on the previously written slide deck.
* Still needs to write up an introduction to microcontrollers based on the previously written slide deck.
* Finish introduction to microcontrollers, purchase Elegoo kit, and begin writing lesson #2 based off the SBEE embedded systems worksheets.
* Review completed lessons, example code snippets. Add context and related technical information when useful.

## Project Scope

The focus of this course is to teach students how to work with microcontrollers such as the AVR architecture microcontrollers found in Arduino devices. Students who have completed this course should understand the basics of microcontroller architecture and be able to create simple, practical software in a professional programming environment.

## Topics Covered

* [Lesson 1](#Lesson-1): Development environments, data types, variable addresses and values, compiler keywords.
* [Lesson 2](#Lesson-2): Wiring, nodes, currents & charge carriers, anodes & cathodes, digital inputs & outputs, if statements & logical expressions.
* [Lesson 3](#Lesson-3): Analog-digital conversion, pulse width modulation
* [Lesson 4](#Lesson-4): No topics explained. New components & project work.
* [Lesson 5](#Lesson-5): No topics explained. New components & project work.
* [Lesson 6](#Lesson-6): Nothing new - continuing work on lesson 5's project
* [Lesson 7](#Lesson-7): No topics explained. New components & project work.
* [Lesson 8](#Lesson-8): No topics explained. New components & project work.

## Topics Yet to Be Explained

* Preprocessor macros, compilation process, architecture

### Lesson 1: General Introduction and Setup

In this lesson, we will prepare a helpful development environment and compile our first project. This will include explanations of variable types, variable addresses, and compiler keywords.

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
    3. Upload the sketch (`Ctrl + U`) to the board and see whether the behavior is as expected. Try changing the value of the `delay(milliseconds)` function to see how the behavior of the board changes.
    4. Once you're satisfied that the board is working, close the Arduino IDE.
4. In Code, install the following extensions (`Ctrl + Shift + X`):
    1. Arduino by Microsoft
    2. C/C++ by Microsoft
5. Open the Code command palette (`Ctrl + Shift + P`) and search for "Arduino Examples". Use the dialogue that opens to find the Blink project again, and open the Blink.ino file.
6. Use the command palette to find the "Arduino Board Configuration" and "Select Serial Port" dialogues. Configure Code as you configured the Arduino IDE previously.
7. Use the command palette to find the "Arduino Upload" dialogue. The upload process can also be started with the `Ctrl + Alt + U` keybinding.

One of the best reasons to use Code instead of the Arduino IDE is the choice of extensions offered by Code. You may have already noticed the more readable syntax highlighting, but other tools are even more valuable than that. Right now, your Blink.ino file has only two functions: `void setup()` and `void loop()`. However, the usual convention for C and C++ is to have an `int main()` function in a main.c or main.cpp file that will always start the project. So what's happening here?

Right click on the `setup` portion of `void setup()` and select "Go to Declaration" from the resulting menu. This will cause Code to search for the header file where the `setup()` function was first declared. Since we used the default install locations, this file is going to be at `C:\Program Files (x86)\Arduino\hardware\arduino\avr\cores\arduino\Arduino.h`. By right clicking and going directly to the header file, we saved a lot of time that otherwise would have been spent searching!

Next, right click on the tab at the top of the Code interface that says "Arduino.h" and select "Reveal in Explorer". This will open a new Windows explorer window in the project directory for Arduino.h. Once the window is open, type "main" and your file selector should jump to main.cpp. Open this file and find the `int main(void)` function it contains. You should now be able to see how the `setup()` and `loop()` functions are related to each other as well as how the actual loop is managed.

* Explain variable types: char, int, float, double, void.

* Explain other keywords: auto, break, case, const, continue, default, do, else, enum, extern, for, goto, if, long, register, return, short, signed, sizeof, static, struct, switch, typedef, union, unsigned, volatile, while.

#### More Exercises Related to Lesson 1

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

In this lesson, we will introduce basic components such as push buttons and light-emitting diodes (LEDs). This will include discussion of wiring, nodes, currents and charge carriers, cathodes and anodes, and operator precedence.

1. From your starter kit, remove the large breadboard, the small breadboard, the jumper wires, the packet of LEDs, and the five push buttons. From the packet of LEDs, remove one of each type of LED (white, blue, green, yellow, red, tricolor). The tricolor LEDs appear similar to the white LEDs but have four legs instead of two.
2. Examine each of the components you just removed.
    * Examine the small breadboard. It is essentially a plastic block with a bit of adhesive foam on the underside. The adhesive is good for only a few uses, especially if left in place for quite a while and then removed, but it can be used to anchor a breadboard to a surface after a circuit has been completed. This is useful for some hobby projects. Peel away a corner of the non-adhesive film from the bottom of the smaller breadboard, then peel away a corner of the foam to reveal the conductive inserts that allow solderless breadboards to conduct electricity. These inserts can be pried out from the breadboard with a pin or mechanical pencil. Once understand what breadboards are made of, undo your changes and put the small breadboard back into the box. We will not be using it much.
    * Examine the button. You will see that it has four legs, and is longer in one direction than the other. Each "side" of the button has two legs that are facing the same direction. These legs that face the same direction are electronically separated by a very large resistance, such that the flow of charge carriers between them is equal to or very close to zero. These legs are said to be in an "open circuit" state. The legs that are located directly across from and are facing away from each other are separated by a very small resistance, such that the flow of charge carriers between them is unrestricted or very close to unrestricted. These legs are said to be in a "closed circuit" or "short circuit" state. When the button is pushed, two pieces of conductor inside the button are forced to touch. This shorts the two nodes together, bypassing the large resistance and allowing charge carriers to flow freely from any of the legs to any other.
        * Do a better job explaining "nodes".
        * Do a better job explaining "resistance".
    * Examine a single color LED and a tricolor LED.
        * Discuss semiconductor materials.
        * Explain charge carriers and anodes / cathodes.
3. We will now begin wiring our breadboard. Using your jumper wires, connect the two red rails of your breadboard together. Next, do the same with the two blue rails. By convention, the red rail is the highest voltage node ("supply") and uses red wires while the blue rail is the lowest voltage supply ("ground") and uses black wires. Staying with convention can help others understand your circuit more quickly, but is not required. Use more jumper wires to connect your supply rail to a 3.3V port of your controller board and your ground rail to a GND port of your controller board.
4. Take one of your single color LEDs, and see that one of the legs is shorter than the other. Insert the short leg of the LED into the ground rail of our circuit board, and insert the long leg into one of the rows that has been connected to a button.
5. Take one of your 220Ω resistors and connect it from the supply rail of your breadboard to the same row as the longer LED leg. The LED should light up! Using a smaller resistor will allow higher current, which will result in a brighter LED. Using a larger resistor will do the opposite and result in a dimmer LED. Each LED is likely to have a different level of brightness for a certain amount of current, but allowing too much current to flow through the LED will damage it very quickly. Some of your LEDs will be able to handle all of the current your controller can output, but some will burn out instead. If any of your LEDs become damaged and no longer light up, set it aside or throw it away. It cannot be repaired.
6. Remove the resistor from the row with the LED's longer leg and instead connect it to the other leg of the button that is on the same side of the breadboard. Push the button to turn the LED back on.
7. Remove the single color LED and put it back with the others, then find the tricolor LED.
8. Insert the longest leg of the tricolor LED into the ground rail of the breadboard and insert the three shorter legs into rows for three different buttons. Use jumper wires to connect the buttons together in a way that leaves the LED legs isolated until the buttons are pushed, then use the 220Ω resistor to connect that node to the supply rail. Use the buttons to examine the tricolor LED's behavior.

We have finished examining the behavior of our equipment - it's time to start our next firmware project.

1. Pull everything out of your breadboard except the jumper wires that power the rails.
2. Open Code, navigate to the Arduino Examples menu, and open `Built-in Examples > Digital > Button`.
3. Take some time to examine the file, then compile and upload with `Ctrl + Alt + U`.
4. Notice that the authors of this file have helpfully provided directions for wiring your circuit:

    ```c
    /*
      The circuit:
      - LED attached from pin 13 to ground
      - pushbutton attached to pin 2 from +5V
      - 10K resistor attached to pin 2 from ground
    */
    ```

5. Do not wire the circuit like this. If you use the wrong type of LED, it will burn out when powered without a current limiting resistor. There's also no real reason to use +5V instead of +3.3V as our supply rail for the button, and we already prepared +3.3V in the previous sequence for the LEDs.
6. Place a button and a single color LED on the breadboard. The button should be placed across the middle of the breadboard, and the two legs of the LED should be inserted into different rows. Do not insert either leg of the LED into a powered rail or a row with one of the button's legs.
7. Use a 220Ω resistor to connect the LED's shorter leg to ground. Use a jumper wire to connect the LED's longer leg to pin 13.
8. Use a 10kΩ resistor to connect one of the button's legs to ground. Use a jumper wire to connect that same leg to pin 2. Use another jumper wire to connect the other node of the button to the supply rail.
9. Push the button to light up the LED. You should notice that the on-board LED lights up at the same time. This is because pin 13 is used to power the on-board LED in most Arduino or Elegoo microcontroller breakout boards.

You should now have a basic program that turns on a light while you hold down a button. But that's not very useful! What if you need the light to stay on even while you're too far away to touch the circuit? What if you want a way to use all the colors of the tricolor LED instead of just one?

1. Remove the LED and the smaller resistor from your breadboard. Replace it with the tricolor LED, making sure that each of the legs isn't connected to anything, and then use the smaller resistor you just removed to connect the longest leg of the LED to ground.
2. Use jumper wires to connect the other legs of the LED to pins 10, 11, and 12.
3. Update `Button.ino` to use pins 10, 11, and 12 instead of 13 as outputs for the LED.
4. Debug the code until the LED has the correct behavior. The tricolor LED should change color exactly once per button press no matter how long the button is held down, and pressing the button repeatedly should cycle the LED through these four states: green, red, blue, and off. The order doesn't really matter, but it shouldn't change between cycles.

Most of what you need has already been demonstrated in either `Blink.ino` or `Button.ino`, but you might need more information. Here's a tip: the C language uses the several logical operators. They are very useful! It is almost impossible to use if statements in more complicated situations without understanding logical operators well. Scan through the following table to see different examples of how logical expressions are evaluated in the C language:

| Expression | Evaluates As |
|-|-|
| `1 == 1` | `TRUE` |
| `1 == 2` | `FALSE` |
| `1 != 2` | `TRUE` |
| `1 <= 2` | `TRUE` |
| `1 > 2` | `FALSE` |
| `TRUE == TRUE` | `TRUE` |
| `TRUE == FALSE` | `FALSE` |
| `TRUE != FALSE` | `TRUE` |
| `TRUE && TRUE` | `TRUE` |
| `TRUE && FALSE` | `FALSE` |
| `FALSE && FALSE` | `FALSE` |
| `TRUE \|\| TRUE` | `TRUE` |
| `TRUE \|\| FALSE` | `TRUE` |
| `FALSE \|\| FALSE` | `FALSE` |

Additionally, `0` evaluates as `FALSE` and all non-zero integers evaluate as `TRUE`. If you work towards a solution for a while but are still having trouble then don't hesitate to look at `Built-in Examples > Digital > Debounce`. This example is a little more detailed than is strictly necessary for this problem, but it will definitely help you find a valid solution. Alternatively, try looking at [our](#Lesson-2-Code-Examples) solution for this problem.

* Add explanation of operator precedence. Second table?

#### More Exercises Related to Lesson 2

### Lesson 3: Introduction to Analog-Digital Conversion (ADC) and Pulse Width Modulation (PWM)

Draft deadline: 20 October 2019

#### More Exercises Related to Lesson 3

### Lesson 4: The Seven-Segment LED Display

Draft deadline: 20 October 2019

#### More Exercises Related to Lesson 4

### Lesson 5: The Liquid Crystal Display (LCD)

Draft deadline: 27 October 2019

#### More Exercises Related to Lesson 5

### Lesson 6: The LCD continued

Draft deadline: 27 October 2019

#### More Exercises Related to Lesson 6

### Lesson 7: Monitoring Analog Sensors with the LCD

Draft deadline: 27 October 2019

#### More Exercises Related to Lesson 7

### Lesson 8: Monitoring Digital Sensors with the LCD

Draft deadline: 3 November 2019

#### More Exercises Related to Lesson 8

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
void setup() {
  pinMode(LED_BUILTIN, OUTPUT);
}

const uint32_t dly_ms = 1000;

void loop() {
    uint32_t start;
    uint8_t pin = LED_BUILTIN, bit;
    volatile uint8_t *out;

    digitalWrite(pin, HIGH);  // turn the LED on (HIGH is the voltage level)
    delay(dly_ms);            // wait for the specified amount of time

    out = portOutputRegister(       /* Get the address mapped to the state of the pin.      */
          digitalPinToPort(pin)     /* For more information about our controller, see       */
    );                              /* https://www.microchip.com/wwwproducts/en/ATMEGA328P  */
    bit = digitalPinToBitMask(pin); // Get the position of the pin on the register
    *out &= ~bit;                   // Set the pin's bit on the register to 0

    start = micros();   // Get the system time in microseconds (us)
    while(dly_ms * 1000 > micros() - start)
    { /* While the delay is greater than the time passed since checking micros() */
        yield();        // Let the controller handle other tasks
    }
}
```

### Lesson 2 Code Examples

Here's one solution for the tricolor LED problem:

```c
// Constant variables used by setup() and loop()
const int buttonPin = 2;
const int led_a =  12;
const int led_b =  11;
const int led_c =  10;

void setup() {
  pinMode(led_a,      OUTPUT);
  pinMode(led_b,      OUTPUT);
  pinMode(led_c,      OUTPUT);
  pinMode(buttonPin,  INPUT);
}

// State variables used by loop() only
int btn_read = 0;
int last_btn = 0;
int led_state = 0;

void loop() {
  // Sample the state of the button once every 100 ms
  delay(100);
  last_btn = btn_read;
  btn_read = digitalRead(buttonPin);
  if (btn_read == HIGH && last_btn == LOW) {
    // The button has been pushed - update the LED's color
    if (led_state == 0)
    {
      digitalWrite(led_a, HIGH);
      digitalWrite(led_b, LOW);
      digitalWrite(led_c, LOW);
      led_state++;
    }
    else if(led_state == 1)
    {
      digitalWrite(led_a, LOW);
      digitalWrite(led_b, HIGH);
      digitalWrite(led_c, LOW);
      led_state++;
    }
    else if(led_state == 2)
    {
      digitalWrite(led_a, LOW);
      digitalWrite(led_b, LOW);
      digitalWrite(led_c, HIGH);
      led_state++;
    }
    else
    {
      digitalWrite(led_a, LOW);
      digitalWrite(led_b, LOW);
      digitalWrite(led_c, LOW);
      led_state = 0;
    }
  }
}
```
