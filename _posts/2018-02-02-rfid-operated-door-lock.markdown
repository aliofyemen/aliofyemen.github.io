---
title: "RFID-Operated Door Lock"
layout: post
tags: how-to
---

# Introduction
> The RFID-Operated Door Lock is a system designed to replace traditional door locks for a relatively cheap cost. It is very useful as it can be used to make any door “smart” and effectively remove the hassle of using keys to open doors (i.e jamming keys, dropping them while holding groceries, etc) and it’s generally more secure as you won't have a pick-able lock that can be easily broken into (most petty thieves do not have the technical knowledge to hack an RFID-operated door lock.) The way the RFID-Operated Door Lock will work is by using an RFID scanner to read an RFID card that will authenticate the user and unlock/lock accordingly. This system will be very helpful to anyone who wants a more secure and reliable door lock.

# What You Will Need
## Hardware

#### 1. Arduino Uno
The project is mainly powered by an Arduino Uno that acts as the brain of the project, the Arduino Uno handles all connections from the various parts used in the system and also contains the code to make them work together.

#### 2. RFID-RC522 (with RFID tag or card and header pins)
The RC522 is an RFID scanner/reader that will act as the “authenticator” of the user, the user will introduce the RFID card or tag on the sensor (within 2 inches) and it will determine if they are authorized to open the lock or otherwise.

#### 3. 16x2 Liquid Crystal Display Module HD44780 (with header pins and potentiometer)
The LCD is used to display to the user a welcome message that instructs them to “Scan their card”, the message changes when the user authenticates themselves and it prints out “Access Granted” or “Access Denied” depending on the situation. The LCD basically acts as the User Interface of the project along with the RFID scanner/reader.

#### 4. Servo Motor SG90
The servo motor is controlled by the Arduino Uno to lock or unlock the door based on the authentication process provided by the RFID scanner/reader.

#### 5. Breadboard
The breadboard acts as an intermediary for all the parts and helps them work together.

#### 6. Male-to-male Jumper Wires (30 of them)
These will be used to connect the hardware parts together.

## Software

For the software part of things, you would need to download the following:
#### 1. [Arduino IDE][1]
To program the Arduino Uno.
#### 2. [Source Code][2] 
For our program logic.

Still here? I commend your perseverance. In that case, I would like to challenge you to finish the next part! Feel free to email [me][email] if you have any questions along the way.

# Putting it All Together


## Hardware

If your inclinations lie in the software realm, you might find this part quite intimidating - as did I - so just take it slow and follow my lead :)

#### 1. Place the Arduino Uno, RFID-RC522 chip, 16x2 LCD, Servo motor, and breadboard on a clean and spacious surface such as a table

#### 2. Connecting the LCD
Hopefully, your LCD came with header pins soldered on, if not, at the very least it should have came with header pins included, you can follow tutorials on [YouTube][3] on how to solder header pins to components. Once you're all set with the header pins, connect them vertically on line `H` on the breadboard.

When you are done with that, pickup the jumper wires and start connecting them from the Arduino Uno to the LCD in the following mapping:

{% highlight c %}
{% raw %}
[ARDUINO] -> [BREADBOARD] -> [LCD]
//with USB port facing up, the following connections should be on the left
[5V]  ->  [+] -> [VDD]
[GND] ->  [+] -> [VSS]
[GND] -> [-] -> [RW]
//with USB port facing up, the following connections should be on the right
[3] -> [J] -> [D7]
[4] -> [J] -> [D6]
[6] -> [J] -> [D5]
[7] -> [J] -> [RS]
[8] -> [J] -> [E]
[9] -> [J] -> [D4]

{% endraw %}
{% endhighlight %}

And finally, connect the LCD to the power rails on the breadboard

{% highlight c %}
{% raw %}
[BREADBOARD] -> [LCD]
[+] -> [A]
[-] -> [K]
{% endraw %}
{% endhighlight %}

You're doing great so far, now we need to connect the potentiometer that came with the LCD to the breadboard. Place it anywhere *past* the end of the LCD in line `J` (that way we can connect the LCD to the potentiometer without trouble.)

After you have done that, we follow the same convention from earlier to connect one more wire from the LCD to the potentiometer on the breadboard

{% highlight c %}
{% raw %}
[LCD] -> [POTENTIOMETER]
//with the knob on the potentiometer facing up
[V0] -> [MIDDLE PIN]
{% endraw %}
{% endhighlight %}

Now we connect the breadboard to the potentiometer
{% highlight c %}
{% raw %}
[BREADBOARD] -> [POTENTIOMETER]
//with the knob on the potentiometer facing up
[-] -> [LEFT PIN]
[-] -> [RIGHT PIN]
{% endraw %}
{% endhighlight %}

Who-hoo! You did it! The LCD should be fully connected now and you can control its backlight using the potentiometer.

#### 3. Connecting the RFID-RC522 Module
You're already a champion in my eyes, but a few more steps are required to get this thing working. 

Assuming you have soldered the header pins on the RFID-RC522 module, plug the pins vertically on line `D`. We will send power to the other half of the breadboard so that we can power the RFID-RC522 module

{% highlight c %}
{% raw %}
[ARDUINO] -> [BREADBOARD] -> [RFID-RC522]
//make sure you are powering the opposite half of the breadboard
//that the LCD is being plugged into
[3V] -> [+] -> [3.3V]
[GND] -> [-] -> [GND]
{% endraw %}
{% endhighlight %}

Then for the rest of the connections

{% highlight c %}
{% raw %}
[ARDUINO] -> [RFID-RC522]
[5] -> [RST]
[10] -> [SDA]
[11] -> [MOSI]
[12] -> [MISO]
[13] -> [SCK]
{% endraw %}
{% endhighlight %}

And then there were two, and so you have done it.

#### 4. Connecting the Servo Motor
We now venture on the trivial task of connecting the Servo motor 

First we power it

{% highlight c %}
{% raw %}
[BREADBOARD] -> [SERVO]
[+] -> [MIDDLE]
[-] -> [BROWN WIRE]
{% endraw %}
{% endhighlight %}

Then we connect it to the Arduino Uno

{% highlight c %}
{% raw %}
[ARDUINO] -> [SERVO]
[2] -> [ORANGE WIRE]
{% endraw %}
{% endhighlight %}

And we are done. Congratulations! I know that you can't believe it but you definitely did it!

## Software

For the software part, all you have to do is navigate to the repository you cloned earlier and copy the `portable` folder to the root of the Arduino IDE. If you are having any trouble refer to this [tutorial][4] on how to set up the `portable` folder.

#### 1. Launch the Arduino IDE and click on `sketch` drop down menu and load `rfid-lock`
#### 2. Connect your Arduino Uno to your computer through USB
#### 3. Click on `sketch` drop down menu and click on `upload`

Everything should work now, feel free to email [me][email] if you have any questions! Thanks for taking the time to read this tutorial!


[email]: mailto:aliofye@gmail.com
[1]: https://www.arduino.cc/en/Main/Software
[2]: https://github.com/aliofye/rfid-door-lock
[3]: https://www.youtube.com/watch?v=uzxw1yl1s_M
[4]: https://www.arduino.cc/en/Guide/PortableIDE