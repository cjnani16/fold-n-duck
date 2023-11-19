# Paperations!
![paperations intro gif](http://www.jnani.me/images/portfolio%20image/paperations/pr.gif)
**(Unreal Engine 5, Blueprints)** A first-person 3D creative sandbox game with unique paper folding mechanic. You sit in the back of the class, play with paper, and dodge your classmates' wads of paper.

## Project status: 
**Released! 🎊**

## Features & implementations:

### Folding 3D meshes like origami using procedural meshes and linear algebra:
Example | Implementation | Code <br> (In Actor BP_FoldablePaper)
--- | --- | ---
![image of the enemy throw + dodging mechanics](https://img.itch.zone/aW1hZ2UvMjM1MTQzMC8xMzkyODg1My5wbmc=/original/Ri1nh4.png) | 1. **Create a pivot point where the user right clicks** on the mesh. <br> 2. **Calculate a normal vector** pointing from the pivot point -> the mouse's current point on the mesh <br> 2. Define a plane with the pivot + normal, and **perform a plane slice of the mesh**. Set mesh vertex color on selection for highlighting as well. <br> 3. **Use cross product** on the fold pivot normal with the mesh's normal to get an axis of rotation for the fold. <br> 4. When the player scrolls, **rotate the plane slice about an axis that goes through the pivot point**. | ![Example blueprint calculating the slice plane for a paper mesh](https://imgur.com/dHgXRVl.png)

### "Enemy" classmates that periodically throw back their own balled-up paper + Dodging mechanic:
Example | Implementation | Code <br> (In Main Game Mode BP)
--- | --- | ---
![image of the enemy throw + dodging mechanics](https://imgur.com/d51tJ0c.png) | 1. **Select a random student** to perform the attack. <br> 2. **Use a timeline** to rotate the student by modifying the actor's rotation. <br> 3. **Spawn a "FlyingPaper" actor** that approaches the target player in a fast arc. <br> 4. Trigger the above process at random intervals! <br> 5. Dodge by moving player pawn and setting "bIsInvincible" flag on input. | ![Example blueprint performing the spin and attack](https://imgur.com/TvamWQz.png)


### Physics-based projectile system:
Implementation | Code <br> (In Main Player Controller BP)
--- | ---
1.**Set the BP_FoldingPaper mesh to simulate physics**, being careful to disable physics when player picks up or moves the paper. <br> 2. **Add an impulse to the actor** pointing towards the target when throw input is received. <br> 3. **Upon collision, display particle effects for feedback** and check the collided actor. If it's a student and the impact velocity is above a threshold, play an "OOF" sound effect as well! | ![Example blueprint handling input for the throw](https://imgur.com/BSQs3Ky.png)
