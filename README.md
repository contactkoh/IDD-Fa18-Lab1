# IDD-Fa18-Lab1: Blink!

**A lab report by Hongyun(Kevin) Oh **

**Fork** this repository to get a template for Lab 1 for *Developing and Designing Interactive Devices* at Cornell Tech, Fall 2018. You should modify this `README.md` file to delete this paragraph and update below. As the lab asks:

> Include your responses to the bold questions on your own fork of the lab activities. Include snippets of code that explain what you did. Deliverables are due next Tuesday. Post your lab reports as `README.md` pages on your GitHub, and post a link to that on your main class hub page.

We've copied the questions from the lab here. Answer them below!

## Part A. Set Up a Breadboard

![alt text](https://github.com/contactkoh/IDD-Fa18-Lab1/blob/master/board1.jpg)
![alt text](https://github.com/contactkoh/IDD-Fa18-Lab1/blob/master/board2.jpg)


## Part B. Manually Blink a LED

**a. What color stripes are on a 100 Ohm resistor?**
Brown,  Black,   Brown,           Gold
 1 (Color band-black)      0 (color band-black)     10(Multiplier- brown)  Tolerance (+-5% gold)
 
**b. What do you have to do to light your LED?**
First, connect the ardunio board to USB (5V) and then 5v pin connects via wire to red rail of the breadboard to connect to a button switch. The button switch connects with the the LED light and the other end of the LED light connects with a registor (100 Ohms). The registor is necessary to avoid shorting to the ground, as a resistor to the 5V. The other end of the registor connects to the blue rail of the breadboard which connects back to the GND pin.  When pressing the Switch button, the current would run through the LED and LED would light up. When releasing the Switch button, the LED would turn off.  Registor is a pull down resistor here because it is connected to the ground and holds the logic signal near zero volts when no other active device is connected. 

## Part C. Blink a LED using Arduino


### 1. Blink the on-board LED

**a. What line(s) of code do you need to change to make the LED blink (like, at all)?**
digitalWrite as shown below:  

//setup to pinMode
void setup() {
  pinMode(LED_BUILTIN, OUTPUT);
}
// turn the LED on  (HIGH voltage level)
void loop() {
  digitalWrite(LED_BUILTIN, HIGH);   // turn the LED on (HIGH is the voltage level)
}

**b. What line(s) of code do you need to change to change the rate of blinking?**
delay argument value as shown below:  the lower --> the quicker rate of blinking

void setup() {
  pinMode(LED_BUILTIN, OUTPUT);
}

// the loop function runs over and over again forever
void loop() {
  digitalWrite(LED_BUILTIN, HIGH);   // turn the LED on (HIGH is the voltage level)
  delay(1000);                       // wait for a second
  digitalWrite(LED_BUILTIN, LOW);    // turn the LED off by making the voltage LOW
  delay(1000);                       // wait for a second
}
**c. What circuit element would you want to add to protect the board and external LED?**
Resistor after the LED to pull down the current to the Ground. 

**d. At what delay can you no longer *perceive* the LED blinking? How can you prove to yourself that it is, in fact, still blinking?**
15 ms.  My eyes can see the LED blinking and shaking. 


**e. Modify the code to make your LED blink your way. Save your new blink code to your lab 1 repository, with a link on the README.md.**
Blink on for 1 second and then Blink on for 5 seconds, alternatively, and then loop likewise afterwards.

[Code- blinking](https://github.com/contactkoh/IDD-Fa18-Lab1/blob/master/Blink1.ino) 31 Aug2018



### 2. Blink your LED

**Make a video of your LED blinking, and add it to your lab submission.**
[My Led- blinking] (https://youtu.be/FVidNY44AdY) LED blinking

## Part D. Manually fade an LED

**a. Are you able to get the LED to glow the whole turning range of the potentiometer? Why or why not?**
Yes.  Looking at the Voltage Divider Schematics, the 3 pins of potentiometer are connected to: one to 5 V (V in), middle one to the resistor and LED (V out) and the last one to the Ground. So when I turn the knob on the potentiometer to one extreme, the V out toward the LED is intensified, vice versa. 

## Part E. Fade an LED using Arduino

**a. What do you have to modify to make the code control the circuit you've built on your breadboard?**


**b. What is analogWrite()? How is that different than digitalWrite()?**


## Part F. FRANKENLIGHT!!!

### 1. Take apart your electronic device, and draw a schematic of what is inside. 

**a. Is there computation in your device? Where is it? What do you think is happening inside the "computer?"**

**b. Are there sensors on your device? How do they work? How is the sensed information conveyed to other portions of the device?**

**c. How is the device powered? Is there any transformation or regulation of the power? How is that done? What voltages are used throughout the system?**

**d. Is information stored in your device? Where? How?**

### 2. Using your schematic, figure out where a good point would be to hijack your device and implant an LED.

**Describe what you did here.**

### 3. Build your light!

**Make a video showing off your Frankenlight.**

**Include any schematics or photos in your lab write-up.**
