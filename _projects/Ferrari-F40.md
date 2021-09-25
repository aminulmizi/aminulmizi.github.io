---
name: Ferrari F40 in CAD
tools: [Fusion 360, 3DS Max]
image: https://i.imgur.com/2laqpjO.png?1
description: Rebuilding the Ferrari F40 in Fusion 360 using Form bodies and T-Splines!
---

<h1 style="text-align:center;"><u>Ferrari F40 in CAD</u></h1>

<figure>
    <img src="https://i.imgur.com/1a0upJg.jpg" alt="2D sketch" style="width:425px;height:275px;"/>
    <figcaption style="text-align: center; font-size: 15px; font-style: italic"><strong></strong></figcaption>
</figure>

<h3><u>Contents</u></h3>
<a href="#wheels">Wheels</a>
<br><a href="#body">Rebuilding the main body</a>
<br><a href="#panels">Sketching all the panels</a>
<br><a href="#patching">Patching and thickening the panels</a>
<br><a href="#finish">Completing the car and rendering</a>
<br><a href="#Learning">Learning outcomes and what I would do different</a>


<p>Upon completing this <a href="https://www.linkedin.com/learning/fusion-360-essential-training-2/use-fusion-360-to-turn-your-ideas-into-designs?u=55815585">LinkedIn Learning tutorial</a> on Fusion 360, I began designing random objects
in Fusion 360 to progress my skills in CAD. My first major project was designing a model rocket which had product specifications. 
This was the same rocket I used to simulate a rocket launch which you can check out <a href="https://aminulmizi.com/projects/rocket-lauch">here.</a>

<h3>Adding the canvas</h3>
Before starting, I needed to find the blueprints of the Ferrari F40, this would give me dimensions of the car. After doing so, I was able to use them as canvases to guide the build. I imported them in, and then calibrated them to the dimensions that were shown.
<figure>
    <img src="https://i.imgur.com/pmiP8gU.png?1" alt="2D sketch" style="width:400px;height:225px;"/>
    <figcaption style="text-align: center; font-size: 15px; font-style: italic"><strong>Canvases</strong></figcaption>
</figure>

<h3><a id="wheels">Wheels</a></h3>
To begin with I started off with the wheels. Using a cylindrical form body, I made two bodies, one to replicate the tire and the other to act as the center of the rim. This was done by simply editing the form body of the cylcinders by pushing and pulling the edges. 
<figure>
    <img src="https://i.imgur.com/cDjbfzI.png?1" alt="Tires and center of rim" style="width:400px;height:200px;"/>
    <figcaption style="text-align: center; font-size: 15px; font-style: italic"><strong>Tires and center of rim</strong></figcaption>
</figure>
Next I moved onto adding in the spokes. I sketched out the shape of the spokes by using the side canvas as a guidline and then extruded them inwards. To create the divots found of the wheel of an F40, I sketched out the outline of the divots and proceeded to extrude them inwards aswell.
<figure>
    <img src="https://i.imgur.com/WZigA0U.png?1" alt="Process of building spokes" style="width:650px;height:200px;"/>
    <figcaption style="text-align: center; font-size: 15px; font-style: italic"><strong>Process of building spokes</strong></figcaption>
</figure>
Now to join the tire and rim together, I needed to build an outer rim. This was, once again, done by using a cylindrical form body and editing the form to give it enough depth and edges.
<figure>
    <img src="https://i.imgur.com/9J1BiUN.png?1" alt="Outer rim" style="width:400px;height:400px;"/>
    <figcaption style="text-align: center; font-size: 15px; font-style: italic"><strong>Outer rim</strong></figcaption>
</figure>
Lastly, the F40 wheels have little nuts going aroud the edge of the outer rim. I added these by using 24 sphere balls and layering them around the rim by using the circular patter feature. The wheel is now complete, below is a side by side comparison.
<figure>
    <img src="https://i.imgur.com/scUpB9X.png?1" alt="Ferrari F40 wheel" style="width:400px;height:200px;"/>
    <figcaption style="text-align: center; font-size: 15px; font-style: italic"><strong>Ferrari F40 wheel</strong></figcaption>
</figure>

<h3><a id="body">Rebuilding the main body</a></h3>
To build the body I planned to entirely use T-Splines and draw sketches that would follow the guildlines from the canvases. I would then edit the points along the T-spline and pull them in any of the X, Y, or Z axis. This would turn the sketch into a 3D sketch which I can then patch. Having access to a mirror function meant that I would only need to build half the car from T-splines, once I was done, I could mirror the car to the other side, giving me a full car. Here is a step by step guide on me building the front left bumper from just using a T-Spline.
<br>First, I sketched the side profile of the front bumper which stretches around to the wheel arches. Since all sketches are drawn at the origin (unless you input a construction canvas), I needed to select the whole sketch and move it in the right spot, I used the front canvas to help me with this. 
<figure>
    <img src="https://i.imgur.com/qyEItZx.png?1" alt="Ferrari F40" style="width:600px;height:300px;"/>
    <figcaption style="text-align: center; font-size: 15px; font-style: italic"><strong>Ferrari F40 wheel</strong></figcaption>
</figure>
I then moved to the front plane and started a new sketch to complete the bumper. I couldn't draw the whole bumper from the side since I would have been able to draw along the X-axis. I drew the sketch and made sure to edit all the points to satisfy the guidlines of the canvases. 
<figure>
    <img src="https://i.imgur.com/tpOCVOg.png?1" alt="Ferrari F40" style="width:675px;height:200px;"/>
    <figcaption style="text-align: center; font-size: 15px; font-style: italic"><strong>Ferrari F40 wheel</strong></figcaption>
</figure>
Now that the bumper was complete I was able to patch the sketch together and then, using the thicken function, give it some depth.
<figure>
    <img src="https://i.imgur.com/TDHZmM7.png?1" alt="Ferrari F40" style="width:400px;height:250px;"/>
    <figcaption style="text-align: center; font-size: 15px; font-style: italic"><strong>Ferrari F40 wheel</strong></figcaption>
</figure>

<h3><a id="panels">Sketching all the panels</a></h3>
Now that I've found the method I want to use to structure the body, I followed the blueprints and sketched every panel.
<figure>
    <img src="https://i.imgur.com/f5UKJcX.png?1" alt="Ferrari F40" style="width:600px;height:450px;"/>
    <figcaption style="text-align: center; font-size: 15px; font-style: italic"><strong>Sketches alongside the blueprints</strong></figcaption>
</figure>
<figure>
    <img src="https://i.imgur.com/aaLVbXS.png?1" alt="Ferrari F40" style="width:600px;height:651px;"/>
    <figcaption style="text-align: center; font-size: 15px; font-style: italic"><strong>T-splines making up the F40 body</strong></figcaption>
</figure>

<h3><a id="patching">Patching and thickening the panels</a></h3>
Now that all the panels have been sketched seperately, next I needed to patch the sketches and turn them into surface body. However, a surface body cannot exist in real life because they will have a zero-thickness geometery. This will mean I will give each panel a thickness aswell. Below is an example using the front left fender.
<figure>
    <img src="https://i.imgur.com/M0mOCC7.png?1" alt="Ferrari F40" style="width:500px;height:225px;"/>
    <figcaption style="text-align: center; font-size: 15px; font-style: italic"><strong>Patching and thickening fender</strong></figcaption>
</figure>
As you can see the colour changes from a dark yellow to white, indicating it has turned from a a surface body into a solid body.
Below is an image showing all the panels patched and then thickend
<figure>
    <img src="https://i.imgur.com/OMAPhOg.png?1" alt="Ferrari F40" style="width:600px;height:200px;"/>
    <figcaption style="text-align: center; font-size: 15px; font-style: italic"><strong></strong></figcaption>
</figure>

<h3><a id="finish">Completing the car and rendering</a></h3>
Now that all the panels and body parts have been patched, I can now mirror the car to complete the full body
<figure>
    <img src="https://i.imgur.com/wnHZqaA.png?1" alt="Ferrari F40" style="width:600px;height:330px;"/>
    <figcaption style="text-align: center; font-size: 15px; font-style: italic"><strong>Complete Body</strong></figcaption>
</figure>
I then mirrored the wheels and adjusted their position. Now the car was complete, I could add paint to the Ferrari F40 and render some images.
<figure>
    <img src="https://i.imgur.com/bxZnaIe.png?1" alt="Ferrari F40" style="width:500px;height:300px;"/>
    <figcaption style="text-align: center; font-size: 15px; font-style: italic"><strong>Adding paint</strong></figcaption>
</figure>
Here are some rendered photos
<figure>
    <img src="https://i.imgur.com/7EVMJla.png" alt="Ferrari F40" style="width:700px;height:275px;"/>
    <figcaption style="text-align: center; font-size: 15px; font-style: italic"><strong></strong></figcaption>
</figure>
<figure>
    <img src="https://i.imgur.com/IshHvMq.png" alt="Ferrari F40" style="width:700px;height:225px;"/>
    <figcaption style="text-align: center; font-size: 15px; font-style: italic"><strong></strong></figcaption>
</figure>
<figure>
    <img src="https://i.imgur.com/Pmc1c1k.png" alt="Ferrari F40" style="width:700px;height:225px;"/>
    <figcaption style="text-align: center; font-size: 15px; font-style: italic"><strong></strong></figcaption>
</figure>
</p>

<h2><a id="Learning">Learning outcomes and what I would do different</a></h2>
<p>
    What I learnt doing this project:
    <ul>
        <li>T-Splines allow the user to follow any path they want to </li>
        <li>Management of the timeline was key to making changes later on </li>
        <li>Broadend my knowledge in CAD</li>
</ul>
    What I would do different:
    <ul>
        <li>Not solely rely on T-splines. Process can be very tedious and if too many points are made a long the path of a T-Spline, it can be very troublesome to edit</li>
        <li>Incorporate more tools to make sure that sone sketches werent so rough </li>
        <li>Make sure to calibrate the canvases as accurately as I can. The blueprints I used were not accurate enough.</li>    
        <li>Label bodies/surface bodies on the go. Makes looking back on my work a lot easier to understand</li> 
</ul>



