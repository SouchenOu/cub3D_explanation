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

*The Basic Idea:

The basic idea of raycasting is as follows: the map is a 2D square grid, and each square can either be 0 (= no wall), or a positive value (= a wall with a certain color or texture).

For every x of the screen (i.e. for every vertical stripe of the screen), send out a ray that starts at the player location and with a direction that depends on both the player's looking direction, and the x-coordinate of the screen. Then, let this ray move forward on the 2D map, until it hits a map square that is a wall. If it hit a wall, calculate the distance of this hit point to the player, and use this distance to calculate how high this wall has to be drawn on the screen: the further away the wall, the smaller it's on screen, and the closer, the higher it appears to be. These are all 2D calculations. This image shows a top down overview of two such rays (red) that start at the player (green dot) and hit blue walls:



<img width="205" alt="Screen Shot 2022-11-05 at 5 54 04 PM" src="https://user-images.githubusercontent.com/87101785/200131911-b2845c00-659b-4023-8e90-43f67fd54bce.png">




- Ray is where something starts at a point, and then creates a line (you cannot see) in some direction away. The idea is that it then follows this line to see if it collides with anything.

Briefly, Raycasting is the process of shooting an invisible ray from a point, in a specified direction to detect whether any colliders lay in the path of the array. The name is pretty self-explanatory in that sense. Imagine you want your character to shoot an object. The impact and distance traveled by the bullet are calculated and executed by Raycasting.



**Raycasting for Unity 3D games:

<img width="682" alt="Screen Shot 2022-11-05 at 5 23 13 PM" src="https://user-images.githubusercontent.com/87101785/200129873-999179e7-3dad-4c13-8c7c-1d06fd252bbe.png">

Vector3 origin defines the point of origin for your ray. This point is stored as a Vector3, with an X, Y & Z position. This code is specific to Unity 3D games, all vectors will be handled in Vector3 because of the three dimensions of your game.

Vector3 direction determines the direction of our ray. Again, it’s a Vector3 to give our ray a dimension to travel in, different than the dimension of our point of origin.

float distance is the distance that our ray should travel from the point of origin in the direction we determined, as a float value.

int layerMask value is worth talking about, even if it’s not necessary. In your Unity 3D game, for the object, you are setting a ray for could ignore some specified objects while hitting the others. Int value helps you to tag what will be recognized. Rest will be ignored.

The idea : 
------------

In order to explain the main idea of the formulas, let's say that we have the player's postion on a 2D map (x, y) coordinates. The player is looking at the wall in front of him (NORTH), let's say the looking angle is 90 which is straight to north. The distance from his coordinate to the point of the wall called a ray. Depending on the player's field of view(is the range of the observable world visible at any given time through the human eye) the number of the rays will be decided. If the field of view is 120 then his looking width will be 60 degrees to the left and 60 degrees to the right from the looking angle (90).


---Using the player's coordinate and his looking angle we can calculate the ray's vector (X and Y components). Then calculate the offset (gridline outlier) the points where the rays could hit vertically and horizontally till the point of the wall.


 Wait Wait .....
 lets talk about raycasting steps:
 
 
 1::: RAY-CASTING STEP 1: CREATING A WORLDRAY-CASTING.
 -----------------------------------------------------
 
*For our purpose, each cube will have the size of 64x64x64 units. (The choice of 64 is arbitrary, but it will be useful to pick a number that is a multiple of 2; because we can perform some arithmetic shift operations on such number (shift operations are faster than multiplication or division). The larger the size of the cube, the blockier the world will look like, but smaller cube will make the rendering slower.)

<img width="566" alt="Screen Shot 2022-11-15 at 10 28 42 AM" src="https://user-images.githubusercontent.com/87101785/201882736-704333cf-0ad4-49a7-a9f6-ff2940c7bf75.png">


Before continuing, we will define our coordinate system so that there is no confusion. The coordinate system that we use is illustrated in

<img width="449" alt="Screen Shot 2022-11-15 at 10 30 17 AM" src="https://user-images.githubusercontent.com/87101785/201883051-8e60a731-2349-4041-b268-ca8088c65fab.png">

2::: RAY-CASTING STEP 2: DEFINING PROJECTION ATTRIBUTES:
--------------------------------------------------------

Now that we have the world, we need to define some attributes before we can project and render the world. Specifically, we need to know these attributes:

1. Player/viewer’s height, player’s field of view (FOV), and player’s position.
2. Projection plane’s dimension.
3. Relationship between player and projection plane.
The player should be able to see what is in front of him/her. For this, we will need to define a field of view (FOV). The FOV determines how wide the player sees the world in front of him/her (see Figure 8). Most humans have a FOV of 90 degrees or more. However, FOV with this angle does not look good on screen. Therefore, we define the FOV to be 60 degrees through trial and experimentation (on how good it looks on screen). The player’s height is defined to be 32 units because this is a reasonable assumption considering that walls (the cubes) are 64 units high.

<img width="542" alt="Screen Shot 2022-11-15 at 10 33 24 AM" src="https://user-images.githubusercontent.com/87101785/201883799-35d8eb04-ad87-4cdb-b7a6-9c8c3aef8520.png">

<img width="1045" alt="Screen Shot 2022-11-17 at 10 43 31 AM" src="https://user-images.githubusercontent.com/87101785/202470813-39bdeda4-3ba2-4f0d-9c49-381d22c7fa62.png">


<img width="1658" alt="Screen Shot 2022-11-17 at 3 03 00 PM" src="https://user-images.githubusercontent.com/87101785/202471018-6df854a1-b9d1-47d0-a952-ba174dae921d.png">



<img width="1658" alt="Screen Shot 2022-11-17 at 3 03 00 PM" src="https://user-images.githubusercontent.com/87101785/202471173-835e92f0-dca1-476a-b5f8-eeff0ec39008.png">





https://permadi.com/1996/05/ray-casting-tutorial-9/






