---
title: RFID-Operated Door Lock
layout: post
---

# Introduction
> The RFID-Operated Door Lock is a system designed to replace traditional door locks for a relatively cheap cost. It is very useful as it can be used to make any door “smart” and effectively remove the hassle of using keys to open doors (i.e jamming keys, dropping them while holding groceries, etc) and it’s generally more secure as you won't have a pick-able lock that can be easily broken into (most petty thieves do not have the technical knowledge to hack an RFID-operated door lock.) The way the RFID-Operated Door Lock will work is by using an RFID scanner to read an RFID card that will authenticate the user and unlock/lock accordingly. This system will be very helpful to anyone who wants a more secure and reliable door lock.

# What You Will Need
## Hardware

#### 1. Arduino Uno
The project is mainly powered by an Arduino Uno that acts as the brain of the project, the Arduino Uno handles all connections from the various parts used in the system and also contains the code to make them work together.

#### 2. RFID-RC522 (with RFID tag or card)
The RC522 is an RFID scanner/reader that will act as the “authenticator” of the user, the user will introduce the RFID card or tag on the sensor (within 2 inches) and it will determine if they are authorized to open the lock or otherwise.

#### 3. 16x2 Liquid Crystal Display Module (HD44780)
The LCD is used to display to the user a welcome message that instructs them to “Scan their card”, the message changes when the user authenticates themselves and it prints out “Access Granted” or “Access Denied” depending on the situation. The LCD basically acts as the User Interface of the project along with the RFID scanner/reader.

#### 4. Servo Motor (SG90)
The servo motor is controlled by the Arduino Uno to lock or unlock the door based on the authentication process provided by the RFID scanner/reader.

#### 5. Breadboard
The breadboard acts as an intermediary for all the parts and helps them work together.

#### 6. Male-to-male Jumper Wires (30 of them)
These will be used to connect the hardware parts together.

## Software

For the software part of things, you would need to download the following:
#### 1. Arduino IDE [[link]][1]
To program the Arduino Uno.
#### 2. Source code [[link]][2] 
For our program logic.

Still here? I commend your perseverance. In that case, I would like to challenge you to finish the next part! Feel free to email [me][email] if you have any questions along the way.

# Putting it All Together


## Hardware

If your inclinations lie in the software realm, you might find this part quite intimidating - as did I - so just take it slow and follow my lead :)

#### 1. Place the Arduino Uno, RFID-RC522 chip, 16x2 LCD, Servo motor, and breadboard on a clean and spacious surface such as a table.

#### 2. Pick up the male-to-male jumper wires and start connecting parts in the following format:

{% highlight c++ linenos %}
{% raw %}
[SOURCE] -> [DESTINATION]
{% endraw %}
{% endhighlight %}

{% highlight c++ linenos %}
{% raw %}
[pin 1] -> [pin 2]
{% endraw %}
{% endhighlight %}

[email]: mailto:alimorsh@buffalo.edu
[1]: https://www.arduino.cc/en/Main/Software
[2]: https://github.com/aliofye/rfid-door-lock