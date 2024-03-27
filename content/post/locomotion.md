+++
title = 'Locomotion'
date = 2024-03-25T15:54:24+01:00
draft = false
+++

For the locomotion technique I decided to let players fly around using a broom.


In concrete: Players put a stick between the legs simulating sitting on a broom and move around by moving that.

Something I learned here is the importance of choosing the correct speed for every movement because of caber sickness.

To see the implementation of the locomotion take a look the following scripts in the GitHub repository: 
* LocomotionTechnique.cs
* ControlBroom.cs (makes the broom modell follow the controller transform)


### Forward movement


The forward movement is triggered by going a little on the knees, like doing a squad, simulating the pose people in those kind of movies do when going forward.
This is possible because the game stores the height of the hmd when starting the game.


When players go down and the distance between the initial and the current height is bigger then the given threshold players will start moving forward.
They stop moving when standing up.

I also decided to use physics when starting and stopping by adding a force to give a filling of floating.

A problem I encountered when implementing and developing this was that the game doesn't know the current height of the hmd in the first frame.
Because of that the height was always set to 0. I managed to fix this by implementing a delay of this calculation.
The variable is stored only when the height is recognized as bigger then a given threshold.


### Horizontal movement


The horizontal movement is triggered by the local position of the left controller, which has to be physically attached to the stick.

With that and having the hmd and the controllers as a child object of the player object, it allows us to calculate the local position of the left controller compared to the start local position and rotation.
Those are stored as variables at the beginning of the game.

When the distance compared to the initial position is bigger than the defined threshold the player will trigger horizontal movement when moving the broom to the right or left.
The player object is the one rotating to keep the local transform the same and make the calculation easier. This is used for all the movement options.


### Vertical movement


The vertical movement was a little more difficult to calculate due to the fact that players have to go down.
The first idea was to update the start local position every time players start or finish moving forward.
This helped for a while, but during the evaluation I noticed a bug...


At the end I decided to store the distance between the hmd and the controller once at the beginning.
This had the advantage that the distance is always the same no matter if players are standing or going down.


The movement is then triggered by moving the broom up and down:
* Up: when the current distance is smaller then the initial distance - threshold.
* Down: when the current distance is bigger then the initial distance + threshold.

![alt text](/img/BroomMovement.png "Title Text")


### Future work


After the evaluation someone came to the idea of making the horizontal and vertical movement based on the rotation of the controller to make this more intuitive when not playing with the stick.
To be honest I though during the entire implementation about having them using one but I realized that it would make sense, so I will be working on that in the future :D

Another problem that I encountered was that players aren't supposed to physically move in any other direction than up and down. That's why I didn't notice a bug until the evaluation, when players started rotating once they left their initial position. This should also be fixed in the future.


### Example video

Here is a link to a an example video of the locomotion: [link](https://youtube.com/shorts/TjYE3UZuBT8?feature=share)
