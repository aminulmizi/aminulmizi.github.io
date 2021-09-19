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
     <figcaption style="text-align: center; font-size: 15px; font-style: italic;"><strong>Using Python, I was able to display the CPU temperature of the Raspberry Pi and the Time</strong></figcaption>
</figure>
</p>

<p>
    To start of, I decided I wanted to run the RC-Car using two 3-12V DC motors. The voltage range would allow me to increase or decrease the power supply accordingly to what I desired. Powering the motor directly through the Raspberry Pi was not possible since the GPIO pins on the board have a limited current supply, doing so would have most likely damaged the pins and rendered the Pi unusable. 
</p>

<p>
    My first attempt of powering the motor was by using a breadboard and breadboard power module, 2 10KΩ resistors, a PCF8591 chip (ADC chip) and a L293D chip (motor controller chip). I followed a freenove starter kit tutorial in setting up the circuit, this tutorial can be found <a href="https://github.com/Freenove/Freenove_Ultrasonic_Starter_Kit_for_Raspberry_Pi/blob/master/Tutorial.pdf">here</a> on page 162. 
    <figure>
        <img src="https://i.imgur.com/NO1CZre.jpg?3" alt="Breadboard setup" style="width:200px;height:250px;"/>
        <figcaption style="text-align: center; font-size: 15px; font-style: italic;"><strong>Breadboard Circuit</strong></figcaption>
    </figure>
</p>

<p> The circuit worked, and with the potentiometer, it allowed me to control the output of the motor. The main problem I encountered with this circuit, however, was the amount of wires being used to construct the circuit. It meant that if the circuit broke, locating the issue would be very time consuming and inefficient. Also, even though voltage would be capped to 9v here, having too many wires can be hazardous for overheating. I came to the conclusion that using this setup was not ideal for those reasons and more. </p>

<p> The L298N motor controller board is a H-Bridge motor driver which can start, stop and, crucially, regulate the speed of more than   one motor. Using this board meant it would condense the previous circuit I built down, whilst still carrying out the same functions. Below, using fritzing, is a circuit diagram incorporating the L298N motor controller board.
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
    I then used the holes I had made in the frame to wrap cable tidies around the car, making it more secure and rigid. Before securing in the motor and Pi wires down with cable tidies, I made sure to check the circuit was still intact, this was indicated by the Pi and L298N motor red lights turning on.
    <figure>
        <img src="https://i.imgur.com/6h9z3xl.png?1" alt="Components layoput" style="width:600px;height:250px;"/>
        <figcaption style="text-align: center; font-size: 15px; font-style: italic"><strong>Birds eye view on the left and on the right, a side view of the RC-Car</strong></figcaption>
    </figure>
</p>

<p>
    Now that the circuit and chassis has been built, I moved onto coding the motors with Python. Firstly, I needed to check whether both motors were
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
    I imported the Robot and sleep classes from the gpiozero library to allow me to use functions to control the movement of the motor. Next I declared the GPIO pins for both the left and right motor and named the function robot. I began a loop with 'While True' and called the robot function to drive the motors forward. This is the result I got:
    <figure>
        <img src="https://i.imgur.com/mAsgI98.gif" alt="Components layoput" style="width:250px;height:350px;"/>
        <figcaption style="text-align: center; font-size: 15px; font-style: italic"><strong></strong></figcaption>
    </figure>
    Both wheels turned at the same rate in the right direction which was perfect as it showed that the GPIO pins, motor board and motors were functional. Had either motor rotated backwards, swapping over the polarity with the wires would have fixed that issue.Now that I knew the RC-Car worked, it was time to detail the code more, to have more control over the car.
</p>

<p>
    The L298N motor controller boards have enabler pins next to the input pins. This allows the user to control the output of the motor should the script be coded properly. I wanted the user to be able to easily direct the car forwards, backwards and both to the left and right. The user would also be able to stop the car easily whenever they pleased. Most crucially, I wanted the user to be able to increase or decrease the power output to their liking, the enabler pins would help me do this. Below is the code I wrote to do carry out these tasks:
    <blockquote>
        <pre>
            <code>
    #importing Python module to control GPIO pins and sleep module to allow for delays
    import RPi.GPIO as GPIO

    #Assigning each input from the L298N motor-board to RPi GPIO pins
    in1 = 7
    in2 = 8
    enA = 20
    in3 = 9
    in4 = 10
    enB = 21
    temp1 = 1

    #For GPIO numbering
    GPIO.setmode(GPIO.BCM)


    #setting GPIO pins as outputs
    GPIO.setup(in1,GPIO.OUT)
    GPIO.setup(in2,GPIO.OUT)
    GPIO.setup(in3,GPIO.OUT)
    GPIO.setup(in4,GPIO.OUT)
    #setting enabler pins as output
    GPIO.setup(enA,GPIO.OUT)
    GPIO.setup(enB,GPIO.OUT)

    #setting default output to low
    GPIO.output(in1,GPIO.LOW)
    GPIO.output(in2,GPIO.LOW)
    GPIO.output(in3,GPIO.LOW)
    GPIO.output(in4,GPIO.LOW)

    #Assigning PWM frequency [p = GPIO.PWM(channel, frequency)]
    pA = GPIO.PWM(enA,100)
    pB = GPIO.PWM(enB,100)

    #p.start(DutyCycle)
    pA.start(25)
    pB.start(25)
    print('\n')
    print('Default speed and direction is LOW and FORWARD')
    print('r-run, s-stop, f-forward, b-backward, l-low, m-medium, h-high, e-exit, right- Turn right, left- Turn left')
    print('\n')

    while(1):
    
    x = input()
    
    if x=='r':
        print('Run')
        if(temp1==1):
            GPIO.output(in1,GPIO.HIGH)
            GPIO.output(in2,GPIO.LOW)
            GPIO.output(in3,GPIO.HIGH)
            GPIO.output(in4,GPIO.LOW)
            print('Forward')
            x='z'
        else:
            GPIO.output(in1,GPIO.LOW)
            GPIO.output(in2,GPIO.HIGH)
            GPIO.output(in3,GPIO.LOW)
            GPIO.output(in4,GPIO.HIGH)
            print('Backward')
            x='z'
            
    elif x=='right':
        print('Turn right')
        GPIO.output(in1,GPIO.HIGH)
        GPIO.output(in2,GPIO.LOW)
        GPIO.output(in3,GPIO.LOW)
        GPIO.output(in4,GPIO.HIGH)
        x='z'
    
    elif x=='left':
        print('Turn left')
        GPIO.output(in1,GPIO.LOW)
        GPIO.output(in2,GPIO.HIGH)
        GPIO.output(in3,GPIO.HIGH)
        GPIO.output(in4,GPIO.LOW)
        x='z'
        
    elif x=='s':
        print('Stop')
        GPIO.output(in1,GPIO.LOW)
        GPIO.output(in2,GPIO.LOW)
        GPIO.output(in3,GPIO.LOW)
        GPIO.output(in4,GPIO.LOW)
        x='z'
            
    elif x=='f':
        print('Forward')
        GPIO.output(in1,GPIO.HIGH)
        GPIO.output(in2,GPIO.LOW)
        GPIO.output(in3,GPIO.HIGH)
        GPIO.output(in4,GPIO.LOW)
        temp1=1
        x='z'
            
    elif x=='b':
        print('Backward')
        GPIO.output(in1,GPIO.LOW)
        GPIO.output(in2,GPIO.HIGH)
        GPIO.output(in3,GPIO.LOW)
        GPIO.output(in4,GPIO.HIGH)
        temp1=1
        x='z'
            
    elif x=='l':
        print('Low')
        pA.ChangeDutyCycle(45)
        pB.ChangeDutyCycle(45)
        x='z'
            
    elif x=='m':
        print('Medium')
        pA.ChangeDutyCycle(75)
        pB.ChangeDutyCycle(75)
        x='z'
            
    elif x=='h':
        print('High')
        pA.ChangeDutyCycle(100)
        pB.ChangeDutyCycle(100)
        x='z'  
        
    elif x=='e':
        print('Exit')
        GPIO.cleanup()
        print('GPIO cleanup')
        break
        
    else:
        print('--- Wrong data ---')
        print('--- Please enter defined data to continue ---')
</code>
        </pre>
    </blockquote>
</p>

<p>
    To start of I have imported classes from the RPi.GPIO library to give me full control over the Pi's pins. I then assigned the GPIO pins I used to the different inputs on the L298N board. These numbers depend on what GPIO pins you use to connect to the motor controller board. Next, I made sure to setup the input and enabler ports on the motor controller board as outputs and afterwards set them to be off as a default setting. This would mean when I run the code the motors wont start spinning straight away. I set the frequency of the enabler pins for motor A and B at 100Hz, this sets the motor speed and current. 
</p>
<p>Now that I've setup the pins, I can write the code which the user will engage with. First, I set the output to low by changing the DutyCycle to a low number, the number inside the DutyCycle function ranges from 0-100, with 100 being 100% output for the motor and 0 being 0%. Using print(), I explained to the user what controls they had, this text would be printed into the console. Controlling the motors output and direction was simple, moving the car forwards would be done by setting the output of In1 and In3 as HIGH and In2 and In4 as LOW. Backwards would be the opposite, In1 and 3 as LOW and In2 and 4 as HIGH. To stop, the output would be setting In1,2,3 and 4 as LOW. To turn left, the left motor would rotate backwards and the right would rotate forwards, this was done by setting In2 and 3 as HIGH. To turn right the opposite would need to be done.
</p>

<p>
    Next, using ChangeDutyCycle, I created three functions which could be called to change the speed of the motors. These functions were labelled 'High', 'Medium', and 'Low', this gave the user a variety of speed cycles to choose from. Finally, I added in the GPIO cleanup function to stop the code from running entirely, and a message to be printed into the console should the user not use the correct controls.
<br>I have used comment lines throughout the script to explain what the code is doing, this script can be found on GitHub <a href="">here.</a>
</p>

<p>
    Below is a video displaying car going forwards, backwards, rotating right and left using the script
    <figure>
        <img src="" alt="RC-Car in action" style="width: px;height: px;"/>
        <figcaption style="text-align: center; font-size: 15px; font-style: italic"><strong></strong></figcaption>
    </figure>
</p>

<p>
    The code used worked well and did exactly what I wanted it to. However, the script was unecessarily long. Any piece of code written for motor 1 would then need to be rewritten for motor 2, which made finding any faults in the code a longer process than it needed to be. Instead rewriting the code by constructing a class using __init__ and having the parameters set to the enabler and input pins would mean I would have to describe the functions (forwards, backwards, stop, etc...) once. The code would look something like this:
<blockquote>
        <pre>
            <code>
            import RPi.GPIO as GPIO
            from time import sleep

            GPIO.setmode(GPIO.BCM)
            GPIO.setwarnings(False)

            class Motor():
                def __init__(self,Ena,In1,In2):
                    self.Ena = Ena
                    self.In1 = In1
                    self.In2 = In2
                    GPIO.setup(self.Ena,GPIO.OUT)
                    GPIO.setup(self.In1,GPIO.OUT)
                    GPIO.setup(self.In2,GPIO.OUT)
                    self.pwm = GPIO.PWM(self.Ena,100)
                    self.pwm.start(0)

                def moveF(self, x=50, t=0):
                        GPIO.output(self.In1,GPIO.LOW)
                        GPIO.output(self.In2,GPIO.HIGH)
                        self.pwm.ChangeDutyCycle(x)
                        sleep(t)
                def moveB (self, x=50, t=0):
                        GPIO.output(self.In1,GPIO.HIGH)
                        GPIO.output(self.In2,GPIO.LOW)
                        self.pwm.ChangeDutyCycle(x)
                        sleep(t)
                def stop(self, t=0):
                        self.pwm.ChangeDutyCycle(0)
                        sleep(t)


            motor_left = Motor(20,7,8)
            motor_right = Motor(21,9,10)
</code>
    </pre>
    </blockquote>
This code is much easier to read and locate any issues. After defining the left and right motor pins you would now be able to call any of the functions created for both motors, e.g <code>motor_left.moveF()</code>.
</p>

<p>And there you have it, a fully functional remote controlled car!</p>

<h2 style="text-align:center;"><u>Learning outcomes and what I would do different</u><h2>

<h6>
<p>
    What I learnt doing this project:
    <ul>
        <li>Managing and following a structured plan helps in being organised</li>
        <li>Furthered my knowledge in Python and Linux</li>
        <li>Improved my ability to manage files using terminal for both windows and linux </li>
        <li>Having a support system is key when building a project. In this case, having spare parts and an easily accessible
            build was very important</li>
        <li>Creating blueprints (e.g the fritzing diagram) makes it easy for others and yourself to understand what you have built</li>
</ul>
    What I would do different:
    <ul>
        <li>Cardboard was too fragile and bent too easily, it was one of the reasons why the wheels werent straight. Using acrylic
        would have been the best alternative as it isnt too costly and it is rigid </li>
        <li>Incorporated an axel of somesort to make sure the motors were parallel to eachother all the time. This, along with the cardboard issue, meant that the RC-Car tended to drift off to the left or right went going forwards or backwards</li>
        <li>Used more durable or stronger motors. The ones used utilised plastic cogs, which, after sometime, began to grind down and become useless after some time. </li>
        <li>I had anticipated the RC-Car to use a lot of battery, hence why I bought a large battery pack. This was not the case and this only ended up weighing down the car</li>     
</ul>
  
</p>