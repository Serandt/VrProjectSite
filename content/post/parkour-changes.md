+++
title = 'Parkour Changes'
date = 2024-03-25T13:30:39+01:00
draft = false
+++

to make the experience more magical and immersive I decided to make some changes.

### Environment

Starting by changing the color of the light aswell as the sky from having a normal skybox to having a dark blueish color to simulate the night sky.

Also more lamps were added to the scene and the Prefabs of them were modified to look like they are glowing.

![alt text](/img/EnvironmentExample.png "Title Text") 

### Music

Because the given music didn't match to the setting I was trying to get, I decided to change it with something more mysterious and adventurer like. 
Here the [link](https://www.chosic.com/download-audio/28030/) for the site were I found it.

Also here is the acknoledgement needed to use it:

Main Theme (Overture) | The Grand Score by Alexander Nakarada | https://creatorchords.com/
Music promoted by https://www.chosic.com/free-music/all/
Attribution 4.0 International (CC BY 4.0)
https://creativecommons.org/licenses/by/4.0/

### Task

The task was changed to make it more magical.
This lead to many changes in the UI and classes managing the task:
* task start now when grabbing a wand 
* ui shows accuracy (number of ghosts divided by projectiles used)
* interaction between task script and other interaction scripts(e.g. wand, projectile, portal, ...) 