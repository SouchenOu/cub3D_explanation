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
 lets talk about Cub3D steps:
 
 1:::: parsing:
 ---------------
 
 
 
 
 
 
 2::: RAY-CASTING STEP 1: define some attribute:
 -----------------------------------------------------
 
*For our purpose, each cube will have the size_width 64 and size_height 64 units. (you can choose any size it should be just the same in height and width). 

The larger the size of the cube, the blockier the world will look like, but smaller cube will make the rendering slower.)

then we need to define some attributes before we can project and render the world:

1: player’s position

2 : player is direction.

3: player’s field of view (FOV); The player should be able to see what is in front of him/her. For this, we will need to define a field of view
(FOV). The FOV determines how wide the player sees the world in front of him/her

4: cub_width and cub_height (Tile_size).

5: read our map and put it in array double dimension.

6: calculate the looking angle by using the direction of the player


3: GridLine Hit Checkers :
--------------------------

here we will calculate ray.x and ray.y (ray coordinate)
 
Each time the ray will hit a grid line horizontally or vertically, that point actually should be the position where we can check if it's a wall or not. To do that we firstly need to know how to calculate the ray's cordinate using the player's coordinates, then add a specfic value (parameters) to hit the first grid line, then continually add a constant value to hit each grid line till the wall, these constant values called (Grid Offsets).

<img width="150" alt="1" src="https://user-images.githubusercontent.com/87101785/204095671-2f203d29-cee7-448d-926a-0949cdfb9f71.png">


Horizontal Grid Lines is the (NORTH & SOUTH), or the upper and the lower sides of a 2d map. Vertical Grid Lines is the (WEST & EAST), or the left and the right sides of a 2d map. Depending on the looking angle of the player we can decide where the ray is actually hitting vertically (left or right) and horizontally (up or down). Before that We actually need to understand how we can calculate the ray's coordinate and the distance between the player and the ray.
First thing to know in order to get the ray's coordinate (X and Y components) ray Y and ray X, is that we can use the rule of the right triangle.


(we check our looking angle to know where our player look exactly!!)


**************************************************************************************************************************
+++++vertical GridLine:
**************************************************************************************************************************

          1: *********firstly we check the looking angle then calculate the ray cordinate by using the right triangle rule :
                        -----------------------------------------------------------------------------------------

     -if the looking angle > 0 and looking angle < 3.14

        so our player look down
        
          +calculate rx:
          -------------
          
          we have rx = adj + px
          
          by using right triangle rule adj = opp/tan(looking_angle)
          
          and we have opp = (ry - py)
          
          so rx = (ry - py)/tan(looking_angle) + px
          
          +calculate ry:
          --------------
          
          ry: should be the player's Y coordinate but you should firstly scale the player's Y point to tile_size unit, for example  ((pY / 64) * 64);

        
<img width="80" alt="8" src="https://user-images.githubusercontent.com/87101785/204099806-96b42dd8-e45d-4a32-b701-27648a2b9c67.png">

     
     -if the looking angle > 3.14
 
       so our player look up
       
          +calculate rx:
          -------------
          
          we have rx = adj + px
          
          by using right triangle rule adj = opp/tan(looking_angle)
          
          and we have opp = (ry - py)
          
          so rx = (ry - py)/tan(looking_angle) + px
          
          +calculate ry:
          --------------
          
          ry: should be the player's Y coordinate but you should firstly scale the player's Y point to tile_size unit, for example  ((pY / 64) * 64);

        
 <img width="100" alt="7" src="https://user-images.githubusercontent.com/87101785/204099793-5bfeabf2-e84c-4db1-80be-aa349f5c71c7.png">

        


**************************************************************************************************************************
+++++horizontal Gridline :
**************************************************************************************************************************


     -if the looking angle < 3.14/2 or looking_angle > 3*3.14/2

        so our player look right
        
          +calculate rx:
          -------------
          
          we have rx = adj + px
          
          by using right triangle rule adj = opp/tan(looking_angle)
          
          and we have opp = (ry - py)
          
          so rx = (ry - py)/tan(looking_angle) + px
          
          +calculate ry:
          --------------
          
          ry: should be the player's Y coordinate but you should firstly scale the player's Y point to tile_size unit, for example  ((pY / 64) * 64);

        
<img width="150" alt="9" src="https://user-images.githubusercontent.com/87101785/204099840-3b4e3f21-78d1-4fd1-aacf-71b37111eafb.png">
     
     -sinon look left
     
          +calculate rx:
          -------------
          
          we have rx = adj + px
          
          by using right triangle rule adj = opp/tan(looking_angle)
          
          and we have opp = (ry - py)
          
          so rx = (ry - py)/tan(looking_angle) + px
          
          +calculate ry:
          --------------
          
          ry: should be the player's Y coordinate but you should firstly scale the player's Y point to tile_size unit, for example  ((pY / 64) * 64);

     
<img width="150" alt="10" src="https://user-images.githubusercontent.com/87101785/204099865-9a0325db-5ee6-415d-bf11-9f980e0345fd.png">


       *****************2 : GridLine offset:
       -------------------------------------------------------------------
 
Offset basically means the amount or a value by which the calculation is out of line or where it could hit the outlier. And here it means the value to add each time to hit the next grid line. So, we want the rays to hit the grid lines not more not a less. Therefore, to calculate these values we are going to use right triangle rule again. 


  wait wait to explaine more !!
 
 
until now we have ray coordinate right !
 
let this ray move forward on the 2D map, until it hits a map square that is a wall. and always check If it hit a wall, if not add the offset sinon calculate the distance of this hit point to the player.

<img width="1020" alt="Screen Shot 2022-11-20 at 11 33 21 AM" src="https://user-images.githubusercontent.com/69278312/203140125-ade7f73e-4ee8-4494-b2a3-176a460bd324.png">


**If the player was looking North:

<img width="250" alt="H-U" src="https://user-images.githubusercontent.com/87101785/204102509-356413cf-2984-4425-b8a5-60e292140e0e.png">

The Y offset will be the size of the grid (Tile_size).

      offset-Y = 64;
      
      offset-X = oY * tan(looking angle);

**If the player was looking South

<img width="250" alt="H-D" src="https://user-images.githubusercontent.com/87101785/204102595-60cd1aca-c163-49ce-86b5-d2f3f0866d49.png">


The offsets will be the same but only the direction of the Y will be changed..
       
       oY = -64;
       
       oX = oY * tan(looking angle);

**If the player was looking East

<img width="250" alt="V-R" src="https://user-images.githubusercontent.com/87101785/204102622-1b762241-4dc2-48ca-9c3f-7746f7b6a24e.png">

       oX = 64;
       
       oY = oX * tan(looking angle);

**If the player was looking West

<img width="250" alt="V-L" src="https://user-images.githubusercontent.com/87101785/204102651-33c93f7a-dfda-43e6-be42-dacce49f7ece.png">

The offsets will be the same but only the direction of the X will be changed..
       
       oX = -64;
       
       oY = oX * tan(looking angle);

Then we do the wall checking loop, in the loop we should add the offset values to the ray values till it hit the wall.

               while (1)
               {
                  if(!wall)
                  {
                     rayY += oY;
                     rayX += oX;
                  }
 
                  else {
                  // calcule the distance 
                  then
                   break ;
               }
       
      
      
      
  *******3: calculate the distance :
  ---------------------------------------------------
          
 Now we have ray coordinate in vertical side and horizontal side so we calculate the distance between ray and our player in the both side 
 then compare it  and we will use the smallest one to draw the wall. 
 
 to calculate the distance we use pythagorean rule:
     (X2−X1)2+(Y2−Y)2
          

4: Drawing the walls :
---------------------------


Okay let's wrap this all up. Using all of these ideas we can finally end up with these steps. Since the number of rays is the width of the map we can create this loop, inside the loop we should do the following steps..

1- Do the gridline check and get the final ray points.

2- Calculate the wall height using the HEIGHT of the screen and the ray length.

3- Calculate the starting point and the ending point of the walls.

4- Start drawing.





// we will drawing the wall pixel colonne by pixel colonne
// we will go from left to right, colone by colone depends of how many of rays we have(map width).
// each one of colonne represent each one of the rays that  representing in our field of view.
// then calcule the wallStripHeight is the height of each one of walls in the screen



<img width="432" alt="Screen Shot 2022-11-27 at 10 55 00 AM" src="https://user-images.githubusercontent.com/87101785/204129182-b847da76-e410-4e7f-83c9-daf596c3814c.png">

<img width="1082" alt="Screen Shot 2022-11-27 at 10 54 44 AM" src="https://user-images.githubusercontent.com/87101785/204129185-006a7bd7-7fbd-479a-8876-5b0c2028a2ab.png">


<img width="679" alt="Screen Shot 2022-11-27 at 11 06 14 AM" src="https://user-images.githubusercontent.com/87101785/204129627-89ca711b-3626-4d2e-a13a-190dba6976fa.png">






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

