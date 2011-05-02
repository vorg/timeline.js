# Timeline.js

A compact JavaScript animation library with a GUI timeline for fast editing.

by Marcin Ignac (http://marcinignac.com) 

## Usage:

### 1. Animation
   
<script type="text/javascript" src="timeline/timeline.js"></script>   
   
	anim(target).to(delay, {property:value,...}, duration, easing);    

After specyfing target using anim() you can chain as many to() 
animations as you want. To start parallel track simply call 
anim() on the same target again.

### 1.1 Basic example

Animate x property of the sprite object to 100 over 1s using 
quadratic easing. Then wait 5s and animate it back to 0 over 2s  

	anim(sprite)
		.to({x:100}, 1, Timeline.Easing.Quadratic.EaseIn)
		.to(5, {x:0}, 2);

### 1.2 Example of parallel animations

Animate width and height of the rect object to 50 and 75 over 3s.
At the same time animate opacity to 0 over 4s.

	anim(rect).to({width:50, height:75}, 3);
	anim(rect).to({opacity:0}, 4); 
   
### 2. Timeline GUI    

	<script type="text/javascript" src="timeline/gui.js"></script>   

	anim(targetName, target)
		.to(delay, {property:value,...}, duration, easing);

In this case we have to specify targetName in anim() that will be
used when we export the code from the timeline GUI. For each property 
used in to() call there will be an animation track created. Animation
data is stored in localStorage and shared between sessions so 
refresing the page and adding new properties and objects to be 
animated is possible. When an animation track exists in localStorage 
all to() calls modifying this property are ignored. 

### 2.1 Example

	anim("rect", rect).to({x:rect.x, y:rect.y});

Add the rect object and it's x and y properties to animation and use
their default values. Target name should be always exactly the same as 
variable name.  

       