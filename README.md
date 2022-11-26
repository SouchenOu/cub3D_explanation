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



******The Basic Idea:
-------------------------------------------------------------------------------------------------------------------------

The basic idea of raycasting is as follows: the map is a 2D square grid, and each square can either be 0 (= no wall), or a positive value (= a wall with a certain color or texture).

For every x of the screen (i.e. for every vertical stripe of the screen), send out a ray that starts at the player location and with a direction that depends on both the player's looking direction, and the x-coordinate of the screen. Then, let this ray move forward on the 2D map, until it hits a map square that is a wall. If it hit a wall, calculate the distance of this hit point to the player, and use this distance to calculate how high this wall has to be drawn on the screen: the further away the wall, the smaller it's on screen, and the closer, the higher it appears to be. These are all 2D calculations. This image shows a top down overview of two such rays (red) that start at the player (green dot) and hit blue walls:

<img width="205" alt="Screen Shot 2022-11-05 at 5 54 04 PM" src="https://user-images.githubusercontent.com/87101785/200131911-b2845c00-659b-4023-8e90-43f67fd54bce.png">

(Ray: is where something starts at a point, and then creates a line (you cannot see) in some direction away. The idea is that it then follows this line to see if it collides with anything.)

-------------------------------------------------------------------------------------------------------------------------
So What is Raycasting: 
---------------------

Briefly, Raycasting is the process of shooting an invisible ray from a point, in a specified direction to detect whether any colliders lay in the path of the array. The name is pretty self-explanatory in that sense. Imagine you want your character to shoot an object. The impact and distance traveled by the bullet are calculated and executed by Raycasting.

-------------------------------------------------------------------------------------------------------------------------

 Wait Wait .....
 lets talk about raycasting steps:
 
 
 1::: RAY-CASTING STEP 1: CREATING A WORLDRAY-CASTING.
 -----------------------------------------------------
 
*For our purpose, each cube will have the size_width 64 and size_height 64 units. (you can choose any size it should be just the same in height and width). 

The larger the size of the cube, the blockier the world will look like, but smaller cube will make the rendering slower.)

then we need to define soma attributes before we can project and render the world:

1: player’s position

2 : player is demension.

3: player’s field of view (FOV); The player should be able to see what is in front of him/her. For this, we will need to define a field of view
(FOV). The FOV determines how wide the player sees the world in front of him/her


<img width="566" alt="Screen Shot 2022-11-15 at 10 28 42 AM" src="https://user-images.githubusercontent.com/87101785/201882736-704333cf-0ad4-49a7-a9f6-ff2940c7bf75.png">


<img width="449" alt="Screen Shot 2022-11-15 at 10 30 17 AM" src="https://user-images.githubusercontent.com/87101785/201883051-8e60a731-2349-4041-b268-ca8088c65fab.png">

<img width="542" alt="Screen Shot 2022-11-15 at 10 33 24 AM" src="https://user-images.githubusercontent.com/87101785/201883799-35d8eb04-ad87-4cdb-b7a6-9c8c3aef8520.png">

<img width="1045" alt="Screen Shot 2022-11-17 at 10 43 31 AM" src="https://user-images.githubusercontent.com/87101785/202470813-39bdeda4-3ba2-4f0d-9c49-381d22c7fa62.png">


<img width="1658" alt="Screen Shot 2022-11-17 at 3 03 00 PM" src="https://user-images.githubusercontent.com/87101785/202471018-6df854a1-b9d1-47d0-a952-ba174dae921d.png">



<img width="1658" alt="Screen Shot 2022-11-17 at 3 03 00 PM" src="https://user-images.githubusercontent.com/87101785/202471173-835e92f0-dca1-476a-b5f8-eeff0ec39008.png">





https://permadi.com/1996/05/ray-casting-tutorial-9/


<img width="1507" alt="Screen Shot 2022-11-17 at 4 04 25 PM" src="https://user-images.githubusercontent.com/87101785/202481974-1d558cfd-ff10-4601-bb92-d56841ca0732.png">



<img width="1027" alt="Screen Shot 2022-11-23 at 9 43 18 AM" src="https://user-images.githubusercontent.com/87101785/203503413-73add313-aa3f-4875-a65e-4625c02bd500.png">


<img width="1027" alt="Screen Shot 2022-11-23 at 9 43 11 AM" src="https://user-images.githubusercontent.com/87101785/203503427-b4bc10b1-1d99-4e02-a083-2a4f2b44febd.png">

Texture:
--------


<img width="714" alt="Screen Shot 2022-11-23 at 2 12 18 PM" src="https://user-images.githubusercontent.com/87101785/203555439-3846066d-3b1a-4ec2-b117-49dbe71395b5.png">

