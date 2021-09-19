---
name: Remote Controlled Car 
tools: [Python, Linux]
image: https://i.imgur.com/pXudSrb.jpg
description: Using a Raspberry Pi 4 and external modules, discover how I built a fully functional RC-CAR!
---

<h1 style="text-align:center;"><u>Remote Controlled Car</u></h1>

<p>After purchasing a Raspberry Pi 4 with extra external modules, I began teaching myself to code little projects and 
   tasks using Python. These small tasks helped me develop a fundamental understanding of Python and Linux, which I then used to set myself a more challenging task in building a remote-controlled car.
<figure>
    <img src="https://i.imgur.com/IuUtosV.jpg?1" alt="Example" style="width:200px;height:250px;text-align:center;"/>
     <figcaption style="text-align: center; font-size: 15px; font-style: italic;"><strong>Using Python, I was able to display the CPU temperature of the Raspberry Pi the Time</strong></figcaption>
</figure>
</p>

<p>
    To start of, I decided I wanted to run the RC-Car using two 3V-12V DC motors. The voltage range would allow me to increase or decrease the power supply accordingly to what I desired. Powering the motor directly through the Raspberry Pi was not possible since the GPIO pins on the board have a limited current supply, doing so would have most likely damaged the pins and rendered the Pi unusable. 
</p>

<p>
    My first attempt of powering the motor was by using a breadboard and breadboard power module, 2 10KΩ resistors, a PCF8591 chip (ADC chip) and a L293D chip (motor controller chip). I followed a freenove starter kit tutorial in setting up the circuit, this tutorial can be found <a href="https://github.com/Freenove/Freenove_Ultrasonic_Starter_Kit_for_Raspberry_Pi/blob/master/Tutorial.pdf">here</a> on page 162. 
    <figure>
        <img src="https://i.imgur.com/NO1CZre.jpg?3" alt="Breadboard setup" style="width:200px;height:250px;"/>
        <figcaption style="text-align: center; font-size: 15px; font-style: italic;"><strong>Breadboard Circuit</strong></figcaption>
    </figure>
</p>

<p> The circuit worked, and with the potentiometer, it allowed me to control the output of the motor. The main problem I encountered with this circuit, however, was the amount of wires being used to construct the circuit. It meant that if the circuit broke, locating the issue would be very time consuming and inefficient. Also, even though voltage would be capped to 9v here, having too many wires can be hazardous for overheating. I came to the conclusion that using this setup was not ideal for those reasons and more. </p>

<p> The L298N motor controller board is a H-Bridge motor driver which can stop, start and, crucially, regulate the speed of more than   one motor. Using this board meant it would condense the previous circuit I built down, whilst still carrying out the same functions. Below, using fritzing, is a circuit diagram I used for the RC-Car.
    <figure>
        <img src="https://i.imgur.com/aToh02t.png?1" alt="Circuit Diagram using L298N Motor board" style="width:350px;height:300px;"/>
        <figcaption style="text-align: center; font-size: 15px; font-style: italic"><strong>Circuit Diagram using L298N Motor board</strong></figcaption>
    </figure>
    The image below is the circuit from fritzing constructed.
    <figure>
        <img src="https://i.imgur.com/a7m0bBu.jpg?1" alt="Circuit Diagram using L298N Motor board" style="width:430px;height:300px;"/>
    </figure>
</p>

<p>
    Next I needed to construct the chassis to house all the components. Since I was keeping costs low as possible, cardboard was the best alternative to acrylics and plastics. In designing the chassis my main priority was having easy access to the major components so I could locate any issues without difficulty. Therefore, I chose to have two layers, the first base would store the battery pack , to power the Pi, and hold both motors which would be glued to the cardboard. It would also have a ball cast acting as a front pivot to allow the car to turn. The second layer would have the Pi, motor board and motor board power bank. 
    <figure>
        <img src="https://i.imgur.com/emSEA6Y.jpg?1" alt="Components layoput" style="width:600px;height:380px;"/>
        <figcaption style="text-align: center; font-size: 15px; font-style: italic"><strong>Component laypout, on the left is bottom layer and on the right, the top layer</strong></figcaption>
    </figure>
</p>

<p>
    I flipped the bottom layer so that the battery pack was facing the ground and glued the top layer onto the bottom.
    I then used the holes I had made in the frame to wrap cable tidies around the car, making it more secure and rigid. Before securing in the motor and Pi wires down aswell with cable tidies, I made sure to check the circuit was still intact, this was indicated by the Pi and L298N motor red lights turning on.
    <figure>
        <img src="https://i.imgur.com/6h9z3xl.png?1" alt="Components layoput" style="width:600px;height:250px;"/>
        <figcaption style="text-align: center; font-size: 15px; font-style: italic"><strong>Birds eye view on the left and on the right, a side view of the RC-Car</strong></figcaption>
    </figure>
</p>

<p>
    Now that the circuit and chassis has been built, I moved onto coding the motors. Firstly, I needed to check whether both motors were
    spinning in the right direction. To do this I used the following code:
    <blockquote>
        <pre>
            <code>
    from gpiozero import Robot
    from time import sleep
    robot = Robot(left = (7,8), right = (9,10))
    while True:
    robot.forward()
    sleep(5)
    robot.stop()
            </code>
        </pre>
    </blockquote>
    I imported the Robot and sleep classes from the gpiozero library to allow me to use functions to control the movement of the motor. Next I assigned declared the GPIO pins for both the left and right motor and named the function robot. I began a loop with 'While True' and called the robot function to drive the motors forward. This is the result I got:
    <figure>
        <img src="https://i.imgur.com/mAsgI98.gif" alt="Components layoput" style="width:250px;height:350px;"/>
        <figcaption style="text-align: center; font-size: 15px; font-style: italic"><strong></strong></figcaption>
    </figure>
    Both wheels turned at the same rate in the right direction which was perfect as it showed that the GPIO pins, motor board and motors were functional. Now that I knew the RC-Car worked, it was time to detail the code more, to have more control over the car.
</p>

<p>
    The L298N motor controller boards have enabler pins next to the GPIO input pins. This allows the user to control the output of the motor should the script be coded properly.
</p>