Advanced Computer Graphics 
===========================

normals as colors:

reduced time of rendering from a 5 hours to 30 seconds by using an Octree.

![alt text](https://raw.githubusercontent.com/TamerMograbi/realistic_renderer/master/ajax-normals.png)

Added light point source option:

![alt text](https://raw.githubusercontent.com/TamerMograbi/realistic_renderer/master/ajax-pointLight.jpg)

added ambient occlusion option.
ambient occlusion is computed using monte carlo integration.
the monte carlo samples are provided by a cosine hemisphere distribution. (from a random number generator in the interval
[0,1], we transform to directions on the hemisphere.)

![alt text](https://raw.githubusercontent.com/TamerMograbi/realistic_renderer/master/ajax-ao.jpg)

Added the ability to turn any mesh into a light emitter by the following method:
added an function that randomly chooses one of the triangles of the mesh (proportional to the surface area of the triangle).
after choosing the triangle, we randomly (and uniformly!) choose a point on the triangl using a barycentric conversion from a 2D point on a unit square into a point on the triangle.

this way the Li() function, for any point x on a mesh will be able to randomly choose a point on the emitter to recieve light from.
(monte carlo is used here too)

result:

![alt text](https://raw.githubusercontent.com/TamerMograbi/realistic_renderer/master/motoDiffuse.png)

this shows a mesh and two different color lights from two sides.
(the shadows are very smooth thanks to the are light!)


also added a dielectric bsdf so now we can also render glass-like materials!
Frensel equations and Snell's law are both used here.
method:
for each ray from the camera:
calculate the Frensel equation, we denote it Fr.
get a uniform float sample
if sample < Fr
    return reflected light
else 
    return refracted light
   
again we return either reflected or refracted light in proportion to the value of Fr because we are also using monte carlo here
to sum up on all the samples.

results:

![alt text](https://raw.githubusercontent.com/TamerMograbi/realistic_renderer/master/motoDielectric.png)

now for a cooler render that involves a dielctric glass sphere + a mirror glass sphere:

![alt text](https://raw.githubusercontent.com/TamerMograbi/realistic_renderer/master/cbox.png)

Here is another one, just like the one above but with area light instead of point light + light now jumps more than just once

![alt text](https://raw.githubusercontent.com/TamerMograbi/realistic_renderer/master/ref-cbox.png)

I've added the ability to smooth out rendering. result:

![alt text](https://raw.githubusercontent.com/TamerMograbi/realistic_renderer/master/mine-ajax-smooth.png)

Here is the rough image for comparasion:

![alt text](https://raw.githubusercontent.com/TamerMograbi/realistic_renderer/master/ref-ajax-rough.png)

rendering complex scene:

![alt text](https://raw.githubusercontent.com/TamerMograbi/realistic_renderer/master/mine-table_path_simple.png)

rendering complex scene with many different materials:

![alt text](https://raw.githubusercontent.com/TamerMograbi/realistic_renderer/master/mine-veach_path.png)

Note:

Had to remove code so it won't be copied by other students :)








