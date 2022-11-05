# cub3D_explination

This project’s objectives are similar to all this first year’s objectives: Rigor, use of C, use
of basic algorithms, information research etc.

As a graphic design project, cub3D will enable you to improve your skills in these
areas: windows, colors, events, fill shapes, etc.

To conclude cub3D is a remarkable playground to explore the playful practical applications of mathematics without having to understand the specifics.

With the help of the numerous documents available on the internet, you will use
mathematics as a tool to create elegant and efficient algorithms.


<img width="273" alt="Screen Shot 2022-11-05 at 11 18 46 AM" src="https://user-images.githubusercontent.com/87101785/200115000-1a216b34-1f88-4fbe-9cee-c97d9f9bf486.png">

-----------------------------------------------------------------------------------------------------------------------------------------------------


********

I will explain here the formulas that I have used to implement the ray-casting. This raycast has been made in order to create a 3D game Cub3D. The project still in progress ⚙️🛠.

Note: Im NoT DoNe yEt 🧟‍♀️

1: Introduction:
---------------

I will explain what kind of calculation I will used to create, draw, and move around the walls.

2: Ray-Casting:
--------------

- Ray is where something starts at a point, and then creates a line (you cannot see) in some direction away. The idea is that it then follows this line to see if it collides with anything.

Briefly, Raycasting is the process of shooting an invisible ray from a point, in a specified direction to detect whether any colliders lay in the path of the array. The name is pretty self-explanatory in that sense. Imagine you want your character to shoot an object. The impact and distance traveled by the bullet are calculated and executed by Raycasting.



**Raycasting for Unity 3D games:

<img width="682" alt="Screen Shot 2022-11-05 at 5 23 13 PM" src="https://user-images.githubusercontent.com/87101785/200129873-999179e7-3dad-4c13-8c7c-1d06fd252bbe.png">

Vector3 origin defines the point of origin for your ray. This point is stored as a Vector3, with an X, Y & Z position. This code is specific to Unity 3D games, all vectors will be handled in Vector3 because of the three dimensions of your game.

Vector3 direction determines the direction of our ray. Again, it’s a Vector3 to give our ray a dimension to travel in, different than the dimension of our point of origin.

float distance is the distance that our ray should travel from the point of origin in the direction we determined, as a float value.

int layerMask value is worth talking about, even if it’s not necessary. In your Unity 3D game, for the object, you are setting a ray for could ignore some specified objects while hitting the others. Int value helps you to tag what will be recognized. Rest will be ignored.
