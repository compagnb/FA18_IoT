## Week 2: C/C# Syntax

![c/c#](https://miro.medium.com/max/1012/1*Hu1Ci0OvIgJg7RTi3oOlfQ.png)

### Particle Cloud Overview (from Particle Support Website  )
![Particle Cloud](https://github.com/compagnb/w18_intro_to_iot/blob/master/imgs/particlecloud.png "Particle Cloud")
* Particle Build is an **Integrated Development Environment**, or IDE. (IDE's allow software development in an application.
* The **Navigation bar** is on the left. On the top, there are three buttons, which serve important functions:
    * **Flash**: Flashes the current code to the device. This initiates an over-the-air firmware update and loads the new software onto your device.
    * **Verify**: This compiles your code without actually flashing it to the device; if there are any errors in your code, they will be shown in the debug console on the bottom of the screen.
    * **Save**: Saves any changes you've made to your code.
* At the bottom, there are four more buttons to navigate through the IDE:
    * **Code**: Shows a list of your firmware applications and lets you select which one to edit/flash.
    * **Library**: Explore libraries submitted by other users, and develop your own.
    * **Docs**: Brings you to the documentation for Particle.
    * **Devices**: Shows a list of your devices, so you can choose which to flash, and get more information on each device.
    * **Settings**: Change your password, log out, or get your access token for API calls.
* Keyboard shortcuts: https://github.com/ajaxorg/ace/wiki/Default-Keyboard-Shortcuts

### C /C# Syntax
Every new application for the Photon or Arduino should begin with this skeleton:
``` C 

void setup(){
    
}

void loop(){
    
}

```
* When we start a new program we always have to include two functions, they are: **void setup** & **void loop**. They are called with a **void** because functions need to specify a type, since neither of these has a type, they are considered void. 
* The **setup** function is similar to an init in Java and Python Classes, it will only run once -- to set the program/class/object up. 
* The **loop** function, loops until it is told to stop. 
* The **( )** next to each of these functions will hold parameters, or variables that we can pass through the function. 
* The **{ }** will hold the contents of each of the functions. All of our code is written within these two brackets, and will end with a **;** after each line.
* **Indent each of the lines of code appropriately, so that it is easy to see what it belongs to. 

#### Photon Exercise 1: Photo Exercise 1: Control The RGB LED
* Now that we know the syntax, lets write a program to blink the RGB LED on the Photon Board. 
* Using our skeleton the first thing we need to do in the **setup** function is tell the computer what we will be controlling. We do this here, in the **set-up** because we only have to tell the computer this once... and it will not change. (Just like when Mom tells you to make your bed... )
* To select the RGB LED, we state the LED we will control, followed by the control function and then set it's parameter to true. 
``` C 
void setup(){
    RGB.control(true);
}
```
* Now that we have control of that LED, we can change its color of the LED. Since we are changing the color of the RGB LED we need to identify this before the color function, like we did earlier with the control function. 
``` C 
void loop(){
    RGB.color(255, 0, 0);
}
```
* The **color** function has three integer parameters, one for **R**ed, one for **G**reen, and one for **B**lue. These numbers go from **0**-**255**. **0** is the absence of that color, and **255** is the full brightness of that color.  
![RGB color](https://github.com/compagnb/w18_intro_to_iot/blob/master/imgs/rgb.png "RGB Color")

* If we add another color change to our code, it will change the color... but the change will happen so fast that we will not be able to see it. In this case we can use a built in function called **delay**. 
``` C 
void loop(){
    RGB.color(255, 0, 0);
    delay(2000);
    RGB.color(0, 255, 0);
    delay(2000);
}
```
* The **delay** function hold a numberic parameter representative of milliseconds. This function will stop the loop from running until the amount of millisends in the parameter has passed. This is really important when creating applications that will update data... too long a delay may create a lag in the information, while to short of a delay could create a communication error. 


### Creating Custom Functions/Methods
* Up until now, we have only been using built-in functions, but you can also write custom functions as you can when coding in other languages. 
* These follow the same format as the **setup** and **loop** functions
``` C
type name(type parameter1, type parameter2 ){
    //lines of code here.
}
```

### Types & Other Syntax
* **int** is a type for whole numbers, positive or negative, between **-2,147,483,648** to **-2,147,483,647**. Although there is also a **long** type, the **int** type will cover just about all the whole numbers needed... so there is little point in using anything else. It is good to use **int**s for pins, counting, etc.
* **float** is the type used for floating points like decimals. These range from **-3.4028235E+38** to **3.4028235E+38**. (E+38 means that there are 38 0's on the end of the number.) 
* **double** is the 64bit version of a float. Because it has more places in it, it can be more accurate then a float. It is good to use **floats**s and **double**s for sensor readings like temperature, pressure, etc. It will take the computer longer to compute using floats and even longer for doubles, so only use them if needed. 
* **true** and **false** are used as boolean values, as with other languages.
* **string** is used to hold text, as with other languages.
    * You can also use the **length** function to determine the length of a string or the **charAt** to determine the letter at a specific space. The charAt method will count from 0 like an array, so take that into account when coding.
    ```C
    String s= "strings are just text";
    int strLength = string.length();
    char thirdCharacter = string.charAT(2);
    ```
* **Arrays** will hold multiple variables. They need a type to declare, and have **[]** after the name. For example:
``` C
int numbArray[] = {1, 2, 3, 4, 5, 6, 7, 8, 9 }
```
    * Loops can be called similar to other languages, although the syntax may be a little different. **for** loops are good for counting, and iterating through Arrays.
    ``` C
    for (int i = 0; i < 9; i++){
        //repeatable code gets written here.
    }
    ```
* Basic **if** Statements are written like so:
```C
if (temp > 30){
    freeze();
}else{
    melt();
}
```
    * **==** is used to say something is equal to
    * **!=** is used to say something is not equal to
    * **<** is used to say something is less than
    * **<=** is used to say something is less than or equal to
    * **>** is used to say something is greater than
    * **>=** is used to say something is greater than or equal to
* If you have more then one condition that needs to be met, they can be written like so:
```C
if (letter >= 'a' && letter <= 'z'){
    //Do something
}
```
    * **&&** is used to say both conditions need to be met
    * **||** is used to say the one of the conditions need to be met

### In-class Exercises/Challenges: 
* Hello World Web Page thru C9.
* Build HTML/Javascript version of Madlibs.
* Photo Exercise 1: Control the RGB LED.
* Photon Exercise 2: Blink the D0 and D7 LEDs.
* Build a Morse Code Flasher App.

### Vocabulary:
Internet Of Things (IoT), Browser, Web Server, Protocol, Server, Path, ISP, DNS, IP Address, HTTP Request, HTTP Respond, Client Side Programming, Server Side Programming, Microcontroller, Micro-Computer, Digital to Analog Converter (DAC)

### HTML Tags:

### JavaScript:

### C /C#:
 RGB, control(), color(), delay(), int, long, float, double, string, length(), charAt, char, array
