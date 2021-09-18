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

<p> The L298N motor controller board is a H-Bridge motor driver which can stop, start and, crucially, regulate the speed of more than one motor. Using this board meant it would condense the previous circuit I built down, whilst still carrying out the same functions. Below, using fritzing, is a circuit diagram I used for the RC-Car.
<figure>
    <img src="https://i.imgur.com/aToh02t.png?1" alt="Circuit Diagram using L298N Motor board" style="width:350px;height:300px;"/>
    <figcaption style="text-align: center; font-size: 15px; font-style: italic"><strong>Circuit Diagram using L298N Motor board</strong></figcaption>
</figure>
</p>



