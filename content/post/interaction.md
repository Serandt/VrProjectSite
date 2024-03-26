+++
title = 'Interaction'
date = 2024-03-25T16:54:45+01:00
draft = false
+++

The idea was to make the interaction a little more magical by replacing the given interaction task of the T-shape with a task where they have to catch and exorcize ghosts using a wand and a portal.

When reaching the task players will see a wand floating around which they can catch by touching it with the right controller.
the wand is then automatically set to the position of it.
Also the way of starting a task was changed to start when players grab the wand.

While in this task players still have the possibility to move around with the broom.


### Shooting

Players have the task to hunt ghosts by shooting at them using a wand.

To achieve this i mainly followed the tutorial from Unity to spawn projectiles and shot them in a direction:
[tutorial](https://learn.unity.com/tutorial/using-c-to-launch-projectiles#)

Players can shoot projectiles at the ghosts by pressing the inner trigger of the right controller.
I decided to use this button so players could experience the feeling of grabbing the wand instead of using the front trigger which the wand doesn't have.

A cooldown was also added to prevent players from accidentally shooting more than one projectile at once which could lead to a worse accuracy.
On the other hand I experimented a little with that so it looks like a laser beam, but at the end I went for the single projectile thinking about the accuracy.

For the sound of the projectiles being shot I used the following sound:
[magic beam](https://mixkit.co/free-sound-effects/sweep/)

![alt text](/img/ShootingProjectileExample.png "Title Text")


### Translation

Ghosts are captured after they get hit by the wand projectile then transported to the position of the wand so players can move them around.

To do this the transform of the ghosts is set to the current transform of the projectile spawner of the wand and updated every frame.

Ghosts get smaller when being attached to the wand so they don't block the view field of players too much.

A problem that I encountered with this feature was that the wand was still able to shoot when holding a ghost. So the ghost kept getting smaller.
To fix this I disabled the ability of shooting before the ghost was exorcized in the next step.

![alt text](/img/ShootingProjectileExampleGhostCaptured.png "Title Text")


### Exorcise

At the end players have to transport the ghosts to the portal and rotate the wand with them still in the portal to exorcize them.

When a ghost collides with the portal it stores the local rotation so when rotating it and the rotation value is bigger than the threshold the ghost will be exorcized.

When implementing this I had no idea about working with euler degrees so when I saw the other presentations I thought this might be a really cool function and better then mine.
So maybe I will be changing this in the future. On the other hand, my implementation gives a little randomness due to the position and rotation of the player.
Still this could be better.

![alt text](/img/ShootingProjectileExampleExorciseGhost.png "Title Text")


### User Interface

Because the T-shape was completely replaced by this task I had to change many things like the way of calculating the accuracy (number of ghosts divided by projectiles used).
I also wanted to show this in the UI so I extended the string with the time on the top left corner and also the one when it was finished.

A new field was added so players can see how many ghosts are left for this task and it's hidden when the task is finished.

Because I noticed the text field showing which part is currently being played I also fixed this.

