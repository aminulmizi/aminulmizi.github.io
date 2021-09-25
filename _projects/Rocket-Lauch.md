---
name: Simulating a Rocket launch 
tools: [Fusion 360, Blender, Unity]
image: https://i.imgur.com/Zpj19Gz.png?2
description: Animating a rocket launch in blender which, using Unity, will be viewable in the VR world!
---
<h1 style="text-align:center;"><u>Simulating a rocket launch</u></h1>
<p>The aim of this project was to design and model a rocket in CAD to set specifications and then, using the 3D model, simulate a rocket launch using Blender. Using Unity I will then make this animation viewable in the VR world</p>
<h3><u>Contents</u></h3>
<a href="#rocket">Designing the rocket</a>
<br><a href="#base">The base</a>
<br><a href="#body">Main body</a>
<br><a href="#clip">Parachute clip</a>
<br><a href="#cone">Nose cone</a>
<br><a href="#together">Putting the components together</a>
<br><a href="#blender">Transferring to Blender</a>
<br><a href="#domain">Fluid domain box</a>
<br><a href="#wind">Adding a force field</a>
<br><a href="#launch">Animating the rocket launch</a>
<br><a href="#camera">Adding in a camera</a>
<br><a href="#bake">Adding the final bake to the animation</a>

<h3 id="rocket">Designing the rocket</h3>
<p>I needed to create the model of the rocket that was going to be used in the animation. This was done using Fusion 360. I set specifications for the rocket to meet and broke the rocket down into four sections; The base, main body, nose cone and a parachute clip. The idea was to model the rocket like I was going to have it manufactured afterwards, this meant all my measurements needed to be precise. The height of the rocket was going to be 30cm tall and have a diameter of 41.5mm. The holding bay for the rocket engine in the base will have a diameter of 30mm to house any 29mm rocket engine. </p>
<h4><a id="base">The base</a></h4>
<p>To begin with, I set out by sketching 3 circles with the inner circle having a diameter of 31mm. I then extruded all three to height of 60mm, before extruding the inner circle out a bit more to make the total height 65mm. The 5mm extra material will slot into the main body. 
<figure>
    <img src="https://i.imgur.com/I9kcgx6.png?1" alt="Base cylinder" style="width:500px;height:225px;text-align:center;"/>
     <figcaption style="text-align: center; font-size: 15px; font-style: italic;"><strong>Sketching the 3 circles and extruding them</strong></figcaption>
</figure>
Next I added the fins. First, I made a recrtangle 40mm long, and extruded it upwards 60mm to the top of the base and then a further 15mm. This meant the fins would be 75mm tall. Next I made sketches on the rectangle to give create three shapes, one of them being the fin. The other two shapes, I extruded them inwards to cut themselves out. This left me with just the fin. 
<figure>
    <img src="https://i.imgur.com/GlWGpUa.png?1" alt="designing fins" style="width:500px;height:225px;text-align:center;"/>
     <figcaption style="text-align: center; font-size: 15px; font-style: italic;"><strong>Process of building fins</strong></figcaption>
</figure>
Using the circular pattern function, I duplicated the fin 2 more times around the cylindrical base. Next I used the fillet command on the sharp edges to smooth them down. To make sure that the base would grip into the main body, I input a new canvas halfway up the lip and sketched out another circle 1mm in diamter larger than the base. I then extruded this slightly.  
<figure>
    <img src="https://i.imgur.com/PzCbkqX.png?1" alt="Fins" style="width:500px;height:175px;text-align:center;"/>
     <figcaption style="text-align: center; font-size: 15px; font-style: italic;"><strong>Duplicating fins, using fillet and adding bump on the lip</strong></figcaption>
</figure>
To launch this model rocket, it will need a launch rod to be inserted through the rocket to guide it during it's inital liftoff. I added a launch lug to the side of the base to help with this. The diameter is 15mm.
<figure>
    <img src="https://i.imgur.com/h6kt048.png?1" alt="Launch lug" style="width:500px;height:225px;text-align:center;"/>
     <figcaption style="text-align: center; font-size: 15px; font-style: italic;"><strong>Adding a launch lug</strong></figcaption>
</figure>
</p>
<h4><a id="body">Main body</a></h4>
<p>Building the main body was simple, it was just a circle of diameter 39.5mm which was then extruded to a height of 100mm
    <figure>
        <img src="https://i.imgur.com/fjdt7Wn.png?1" alt="Main body" style="width:300px;height:275px;text-align:center;"/>
        <figcaption style="text-align: center; font-size: 15px; font-style: italic;"><strong>Building the main body</strong></figcaption>
    </figure>
</p>
<h4><a id="clip">Parachute clip</a></h4>
<p>
The rocket needed to have enough space to store a parachute, which also needed to be secured tightly to the rocket frame. To accomplish this, I made a seperate component that would sit into the top of the main body. First, I extruded out a circle of diameter 39.3mm, and then sketched out a trapezium which I then revolved around 360°. 
<figure>
    <img src="https://i.imgur.com/vyie7F1.png?1" alt="Main body" style="width:350px;height:200px;text-align:center;"/>
    <figcaption style="text-align: center; font-size: 15px; font-style: italic;"><strong>Sketching and extruding out the parachute clip</strong></figcaption>
</figure>
Next I added a clip to which the parachute would be strung to. I did this by simply by sketching out a circle, trimming the construction lines I didn't need and then extruding it. To make sure the component wasnt too heavy, I shelled out the inside.
<figure>
    <img src="https://i.imgur.com/3nZElXT.png?1" alt="Main body" style="width:350px;height:200px;text-align:center;"/>
    <figcaption style="text-align: center; font-size: 15px; font-style: italic;"><strong>Adding in the clip and shelling the component</strong></figcaption>
</figure>
</p>
<h4><a id="cone">Nose cone</a></h4>
<p>
First, I sketched out the layout of the nose cone in 2d, which I did by using a T-spline and editing it until I was sattisfied with the shape. Next, I revolved the sketch 360°. 
<figure>
    <img src="https://i.imgur.com/cxFNviH.png?1" alt="Nose cone" style="width:350px;height:250px;text-align:center;"/>
    <figcaption style="text-align: center; font-size: 15px; font-style: italic;"><strong>Designing the nose cone</strong></figcaption>
</figure>
I needed to create a lip for the bottom of the nose cone, this would be inserted into the top of the main body, securing it in place.I did this by sketching two circles on the underside and extruding out the edge. Lastly I shelled out the inside material.
<figure>
    <img src="https://i.imgur.com/uwOQRLn.png?1" alt="Nose cone" style="width:450px;height:200px;text-align:center;"/>
    <figcaption style="text-align: center; font-size: 15px; font-style: italic;"><strong>Adding the lip and shelling</strong></figcaption>
</figure>
</p>
<h4><a id="together">Putting the components together</a></h4>
<p>Now that all the components have been designed, all that was left was for them to be put together
<figure>
    <img src="https://i.imgur.com/D4TibPt.png?1" alt="rocket" style="width:350px;height:250px;text-align:center;"/>
    <figcaption style="text-align: center; font-size: 15px; font-style: italic;"><strong>Putting the parts together</strong></figcaption>
</figure>
</p>

<h3><a id="blender">Transferring to Blender</a></h3>
<p>Now that the the rocket had been designined and built, I exported it as an .OBJ file from fusion 360 to the import it into blender. Exporting as an .OBJ file allows me to then add texures to an object, in this case the rocket.</p>

<h3><a id="domain">Fluid domain box</a></h3>
<p>I imported the file and made sure there was a plane underneath the rocket for it to stand on. I then added a cube to surround the whole rocket and platform. This was then turned into a fluid domain box so that the fire and smoke from the engine of the rocket would have something to bounce off of. 
<figure>
    <img src="https://i.imgur.com/ly2PAPf.png?1" alt="rocket" style="width:420px;height:250px;text-align:center;"/>
    <figcaption style="text-align: center; font-size: 15px; font-style: italic;"><strong>Orange highlight is the fluid domain box</strong></figcaption>
</figure>
<h3><a id="engine">Adding the engines</a></h3>
Now that there will be an environment for fire and smoke to rebound off, I can now add the engines that will produce the flames. I created a new plane which now sits inside the engine bay, and assigned it as a 'fluid' with a type of 'flow' from the 'physics properties' setting.
<figure>
    <img src="https://i.imgur.com/MeWFPzP.png?1" alt="rocket" style="width:420px;height:250px;text-align:center;"/>
    <figcaption style="text-align: center; font-size: 15px; font-style: italic;"><strong>Assigning the engine</strong></figcaption>
</figure>
Next I changed the settings to make sure I had access to all settings and could make any changes I wanted. The settings are here:
<figure>
    <img src="https://i.imgur.com/8sEqk01.png?1" alt="rocket" style="width:450px;height:350px;text-align:center;"/>
    <figcaption style="text-align: center; font-size: 15px; font-style: italic;"><strong>Settings for the engine</strong></figcaption>
</figure>
<h3><a id="wind">Adding a force field</a></h3>
Now that the engine has been assigned and will give an output, I need to give it a direction to travel. To do this I assigned the rocket a 'force field' with a type 'wind', once again from the physics properties. I rotated the direction of the wind 180° so it faced downwards and then increased the radius and strength.
<figure>
    <img src="https://i.imgur.com/dV46I7K.png?2" alt="rocket" style="width:350px;height:450px;text-align:center;"/>
    <figcaption style="text-align: center; font-size: 15px; font-style: italic;"><strong>Adding wind</strong></figcaption>
</figure>
Next I began adjusting the strength of the wind and the amount of 'fuel' the rocket was carrying to give me the best plumes. I would then bake the smoke and fire, this will generate the animation.
<figure>
    <img src="https://i.imgur.com/Fusqg8s.png?2" alt="rocket" style="width:500px;height:200px;text-align:center;"/>
    <figcaption style="text-align: center; font-size: 15px; font-style: italic;"><strong>On the left the fuel supply and wind strength is much lower, on the right is the final bake</strong></figcaption>
</figure>
<h3><a id="launch">Animating the rocket launch</a></h3>
First I made sure that the rocket was in position for the first frame, by adjusting it's position to sit perfectly ontop of the platform. Next I set the 'location' of the rocket in the first frame and then set the location once again for the 250th frame(the last frame). This will tell blender where I want the rocket to end up at for the last frame.
<figure>
    <img src="https://i.imgur.com/xJBWsne.png?1 " alt="rocket" style="width:350px;height:250px;text-align:center;"/>
    <figcaption style="text-align: center; font-size: 15px; font-style: italic;"><strong>Setting the location of the first and final frame</strong></figcaption>
</figure>
In the animation, blender has automatically slowed down the object as it approaches the final frame, which is not what a rocket does. To change this I needed to go into the graph editor and change the trajectory curve to an exponential one.
<figure>
    <img src="https://i.imgur.com/Y4QwU4j.png?2" alt="rocket" style="width:350px;height:210px;text-align:center;"/>
    <figcaption style="text-align: center; font-size: 15px; font-style: italic;"><strong>Chnaging trajectory</strong></figcaption>
</figure>

<h3><a id="camera">Adding in a camera</a></h3>
I added a larger plane that would cover any remaining floor space that wasn't covered. Then I setup the camera in a position that, I felt, would get the best shot of the rocket launch. I set the location of where the camera will point to in the first frame and then in the final 250th frame just like I did with the movement of the rocket. Once again, I went into the graph editor and adjusted the trajectory of the camera and made sure to emphasise the speed of the rocket by having the rocket fly out of it's point of view.
<figure>
    <img src="https://i.imgur.com/6XX4npM.gif" alt="rocket" style="width:700px;height:350px;text-align:center;"/>
    <figcaption style="text-align: center; font-size: 15px; font-style: italic;"><strong>Adjusting the camera animation</strong></figcaption>
</figure>


<h3><a id="bake">Adding the final bake to the animation</a></h3>
Now that the animation is complete it was time to add the engine smoke and fire to it. I increased the resolution divisions to 400 to get really detailed and realistic looking plumes. Here's the result:
<figure>
    <img src="https://i.imgur.com/0MYUl2S.gif" alt="rocket" style="width:700px;height:350px;text-align:center;"/>
    <figcaption style="text-align: center; font-size: 15px; font-style: italic;"><strong></strong></figcaption>
</figure>
</p>


<p>
<h2>To do list</h2>
 <ol>
    <li>Add textures and render animation</li>
    <li>Using unity, make animation viewable in VR world</li>
</ol>
</p>