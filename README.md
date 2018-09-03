# IDD-Fa18-Lab1: Blink!

**A lab report by Hongyun(Kevin) Oh **

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
Yes. Looking at the Voltage Divider Schematics, the potentiometer are connected to: one to 5 V (V in), one to the resistor and LED (V out) and the last one to the Ground. So when I turn the knob on the potentiometer to one extreme, the V out toward the LED is intensified lighting the LED and when I turn the knob the other way around, the LED fades to turn off. 


## Part E. Fade an LED using Arduino

**a. What do you have to modify to make the code control the circuit you've built on your breadboard?**
I had to change the int pin from 9 to 11 because my LED is connected to pin 11 at arduino.

**b. What is analogWrite()? How is that different than digitalWrite()?**
alalogWrite() writes and requests for value between 0-255 and with 255 being 100% duty cycle(always on), 50% (half the time on) and 0%(not on at tll), etc. to use PWM (Pulse Width Modulation) as an analog ouput to produce analog results (e.g. varying the brightness of LED, etc)
[Arduino] (https://www.arduino.cc/reference/en/language/functions/analog-io/analogwrite/) *reference: ardunino web site

digitalWrite() writes HIGH (voltage high) or LOW (GND) to produce either on or off (not analog) effects. 


## Part F. FRANKENLIGHT!!!

### 1. Take apart your electronic device, and draw a schematic of what is inside. 
[Code- blinking](https://github.com/contactkoh/IDD-Fa18-Lab1/blob/master/mouse1.jpg)
[Code- blinking](https://github.com/contactkoh/IDD-Fa18-Lab1/blob/master/mouse2.jpg)

**a. Is there computation in your device? Where is it? What do you think is happening inside the "computer?"**
I chose my bluetooth mouse. Opening it and looking at the front and back of the circuit board, it seemed to me that the 1.5V AA battery flows into (+) the switch and then into some sort of a squire-sized microprocessor chip(?) located in the middle. The microprocessor is attached with the optical sensor(?) on the back/bottom side of the circuit board.  I am new to the electronics but it seems that then, the optical sensor reads values of movement into the microprocessor and calculates that into machine-readable digital form to represent the position of the mouse in X-Y coordinates.

**b. Are there sensors on your device? How do they work? How is the sensed information conveyed to other portions of the device?**
There is LED and light picking up sensor in the center of the bottom side of the mouse. 
The LED emits light and the light bounces back from the surface which is picked up by the sensor located just next to the LED.
The LED light and light picking up sensor working together takes the pictures in a given time to figure out how the movement is made. The sensed information seems to feed into the image processing chip within the mouse (although I cannot figure out where exactly it is..) 
[Arduino] (https://www.pctechguide.com/input-devices/optical-mice)  *reference: web site

**c. How is the device powered? Is there any transformation or regulation of the power? How is that done? What voltages are used throughout the system?**
One 1.5V AA battery is housed in the mouse itself which runs into (+) the switch in the mouse. 
I could not figure out how the circuit board is designed and it was so small to see the lines running on the board, but there is a GND pin that is located next to the optical sensor which seems to indicate that the voltage ends around there after running through the board. 

**d. Is information stored in your device? Where? How?**
It doesn't seem any information is stored in the mouse. It may be transmitted to the computer to translate into X-Y coordinates perhaps. 

### 2. Using your schematic, figure out where a good point would be to hijack your device and implant an LED.

**Describe what you did here.**
Having very little experience with electronics at all, 
I tried to find the electricity running circuit on the board of the mouse. 
Unfortunately, I could not really figure out from the tiny circuit board, where the current is running and what is happening in different chips, etc. 
I used the Arduino board to source the power into the battery

### 3. Build your light!

**Make a video showing off your Frankenlight.**

https://youtu.be/KjgJuvxJ9EA

**Include any schematics or photos in your lab write-up.**
