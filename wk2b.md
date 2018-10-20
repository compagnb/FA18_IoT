## Week 2: Schematics & Relays

### Breadboards 
* Breadboards are pieces of plastic with wholes in them that allow us to prototype our projects. 
* The wholes are designed to grip components (like buttons and switches), and wires. 
* The bottom of the breadboard are strips of metal that will carry the currents throughout the row. 
![Breadboard](https://github.com/compagnb/w18_intro_to_iot/blob/master/imgs/breadboard.png "breadboard")

#### Photon Exercise 1: Blink An External LED
* LEDs emit light when a current passes through them. They will draw as much current as they are fed, showing no restraint. This can potentially lead to over heating, burning them out, or damaging the Photon board. 
* To avoid this, a **resistor** is used. Resistors are passive, and implement electrical resistance as a circuit element.
* In order to blink LEDs set to other pins on the Photon board, first we need to declare **global** variables to hold the pin information. 
``` C
int led0 = D0;
int led7 = D7;
 ```
    * These are declared first and outside of all other functions, so that they can be used in all of the functions we write. These types are variables are also known as **Global**.
    * Notice how each of the variables have a type defined next to the name. Even though they may not look like numbers, they are the pin number that we are assigning.  
    * The **D0** pin does not control an LED on the photon board itself, so we will need to wire an LED to the pin labeled D0 (Digital 0). 
    * The **D7** pin not only controls the D7 (Digital 7) pin, but also controls a small LED next to it on the board. 
* Before we move further with the code, lets wire our breadboard. 
    * First, push the Photon into the center of the breadboard. 
    * Connect the GND pin to the negative (blue) vertical line on the breadboard with a small black wire.
    * Connect the 3.3V pin to the positive (red) vertical line on the breadboard with a small red wire.
    * Connect the two negative (blue) vertical lines on the breadboard with a longer black wire. This will ensure both sides are grounded, and can be used. 
    * Connect the two positive (red) vertical lines on the breadboard with a longer red wire. This will ensure both sides are powered, and can be used. 
    * This is the skeleton for all breadboarded projects. Here is a diagram and the Schematic drawing for this skeleton:

    * Now, put one end of the 220 Ohm resistor into the whole next to the pin D0.
    * The LED will have two pins. The smaller leg is the negative terminal and the longer is the positive terminal. Place these in the breadboard in two different horizontal rows. * Put the other end of the resistor into a hole in the same row as the positive terminal on the LED. 
    * Put a small black cable to connect the negative terminal to the negative (blue) vertical line on the breadboard.
* With the hardware ready and the variables declared, now we have to initialize them. This will take place in the **set up function**.
``` C
void setup(){
    // initialize the pins as output
    pinMode(led0, OUTPUT);
    pinMode(led7, OUTPUT);
}
```
    * The **pinMode** function requires two parameters, one to list what pin will be setup and the other to tell us how that pin will be used. 
    * **OUTPUT** allows us to controll the voltage flowing out of that pin, while **INPUT** allows us to read what is coming into that pin. * The **pinMode** is called in the **setup** function/method, because it only needs to be called once. 
* Now that each of our pins are declared and initialized, we can turn them on and off in the **loop** method. 
``` C
void loop(){
    digitalWrite(led0, HIGH);
    digitalWrite(led7, HIGH);
    delay(1000);
    digitalWrite(led0, LOW);
    digitalWrite(led7, LOW);
    delay(1000);
}
```
    * The **digitalWrite** function takes two parameters, one for the pin and one for HIGH or LOW. It sets the pin to HIGH or LOW, which either connects it to 3.3V (the maximum voltage of the system) or to GND (ground). 
    
#### Photon Exercise 3: Attaching A Switch To Morse Flasher  
* Before we begin to code, lets modify our breadboard to attach a switch to the D3 pin. Below is the diagram and schematic.

* Now, that the hardware is put together, use the basic skeleton to begin our code. Also include global variables for the pin that will connect to our button. 
``` C
int led0 = D0;
int button = D3;
 ```
* Similarly to how we did in the external LED code, we need to initialize the pins in the setup method. This time the button will be a input, and uses one of three possible types:
    *  **INPUT** 
        * This means there will be no pull-up resistors.
        * It is commonly used for connecting inputs to digital ouputs on modules or chips.
    *  **INPUT-PUllUP**
        * This type is when a pull-up resistor is enabled. 
        * We use this when connecting a digital input to a switch that switches the input to GND.
    *  **INPUT-PUllDOWN**
        * This type is when a pull-down resistor is enabled. 
        * We use this when connecting a digital input to a switch that switches the input to 3.3v.
* In this case, we will be using the **INPUT-PUllUP**. (because on this board if we leave the pin on it will be on LOW by default.)
``` C
void setup(){
    pinMode(led0, OUTPUT);
    pinMode(button, INPUT_PULLUP);
}
 ```
* We can then use most of our code from the previous version of the Morse Flasher Project. The only piece that will change is the loop method. This should be changed to run the code to display the message if the button is pressed. To do this we can use an if statement.
``` C
void loop() {
    if (digitalRead(button) == LOW) {
        flashMessage(message);
    }
}
 ```
* In addition to digitalWrite, there are some other built in functions that control pin activity:
    * **digitalRead**: This will read the digital value of a pin, which can be read as either HIGH or LOW. If you were to connect the pin to 3.3V, it would read HIGH; if you connect it to GND, it would read LOW. Anywhere in between, it'll probably read whichever one it's closer to, but it gets dicey in the middle.




### Vocabulary:
breadboard, resistor, 

### HTML Tags:

### JavaScript:

### C /C#:
INPUT, INPUT-PUllUP, INPUT-PUllDOWN, digitalRead(), 



   