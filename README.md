# Free Motion Camera Rig

Check out [full presentation](https://www.behance.net/gallery/44375157/Free-Motion-Camera-Rig) on behance.

Free Motion Camera Rig is simple but effective camera animation concept which may be useful 
for both professionals and beginners. With a little bit of practice it would be not a problem to make
nice "free motion" camera animations. But it's important to notice, that Free Motion Camera Rig
is mostly concept of usage than just a tool.


The key of the concept is to keep set of necessary parameters separately, 
so we can easely working with them. There are 10 controls of camera in 3 groups. 
3 & 3 in basic two groups and 4 in extra.



# Controls

1. Position Group
XYZ-Base positions usually stands on Main Point of Action

- X-Position
- Y-Position
- Z-Position


2. Rotations Group
DHV point Intersection of Distance, Horizon, Vertical

- Distance
- Horizon
- Vertical

3. Head Extra Group
"Head on Shoulders" on DHV point (limit -90° to 90°)

- Roll
- Tilt (aka Pitch)
- Sideways (aka Yaw)
- Slide (aka Dolly)

— All parameters controls stored in the main node of "FMCR".
Animating other transforms of the rig will break 
the concept of usage. They are locked by default.

— Use parametric control of the rig. Good method to operate
movement from camera view just like you are a pilot in the plane. 
It's very convenient way to keep things organized in mind.

— Use trajectory curves for animation tracks of rig.
Since all parameters are clearly separate from each other,
all graphs represents human-readable data.

— It's nice to use align tool (or some sort of snap tool)
for positioning XYZ-Base coordinate of the rig.
By shortcut, of course.

— It's recommended to assign a hotkey 
to "select FMCR in scene" action for the nice feel
of animation workflow. (To select it again and again)






# Theory
Problem. During the camera animation work we are always dealing with at least one Main Point of Action (MPA),
which we are currently looking at. Very basic way to control MPA by camera is to constrain angle of view to "target" point.
But when we do that we lose complete control of Rotation which became dynamically generated by "look at target" constrain, and camera movement becomes unpredictable.  In other hand, if we use just basic transforms of the camera, we never can precisely control MPA, especially in motion, because every rotation will be to turn camera away from MPA.

Basic Solution. If we set up camera on ring around MPA we can precisely control all possible view angles with only three simple parameters: Distance, Horizon angle, Vertical angle (all relatively to MPA). This is a common solution in camera animation strategy, but a little bit further things may go complicated. It's always easy to start adding unnecessary nodes
and axis in rig structure, some sort of additional nodes for every particular situations. But every addition child node bring
all rotations and offsets into the structure. It's hard to deal with several rotation points, especially if degrees are not limited.

Improved solution. If we want to make a camera rig a little bit more universal, it's good idea to keep as less active parameters as possible. At first step we had simple "camera on ring". To keep things organized, lets name a point, received from intersection of Distance, Horizon, Vertical values — DHV point. This is second important point after MPA.


In addition to previous simple structure "camera on ring" we can make some extra camera movement possibilities (from real life situations) if we add just one "head" structure on the DHV point. We probably don't want use all possible transforms parameters from our new "head". For most cases it’s enough to use just rotations. And our movement will be more natural
if we limit rotation from -90 to 90 degrees, which imitate the rotation of the real "head on shoulders".
After all, we'll get three more parameters:

Tilt — to look up and down. Like "Pitch" in airplanes control.
Sideways — left and right. Like "Yaw" in airplanes control.
Roll — it is also called "bank" sometimes.

In fact, all these parameters we can call "extra", because they really don’t make basic movement of camera, they just improve animation of DHV. It's better to think about this control's group as an additional, and animate these parameters after all others. Otherwise, they can mess things up in mind.

This rig structure seems to work just fine in years of practice. But after many experiments with this setup, one more parameter appear to be very useful for slowdowns on the end of animation movements. In terms of rig structure we can call it an additional "camera slider" to make "head" movement forward and backwards instead of just staying still.
This improvement requires addition of one new axis to previous structure.

Eventually, we have 10 controls of camera in three groups, optimized for all kind of situations.
To make more complicated camera movement we can constrain XYZ-Base position of rig to follow a path, or to several other points in the scene (nulls, locators, dummies, etc.) that could also move, rotate or just define different parts of scene.





# Issues
Since all software packages exports animation and rigged objects differently (and in different formats), in some cases there may appear camera export problem.
Baking singe camera object and exporting it should solve the issue.



# Thank you
for interesting in this research about camera animation.
Wish you to keep things under control.