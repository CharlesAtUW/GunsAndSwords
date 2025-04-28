# Design Journal

## Week 1
Team:
- Set up Perforce depot and workspace and set up Unreal project
- Found an avatar on Mixamo that we wanted to use
- Retargeted the Unreal default character animations onto the Mixamo avatar

Individual:
- Helped set up Perforce workspace and Unreal project

## Week 2
Team:
- For this week, we met and decided what we wanted to get done this week. Then, Yoyo split us off to complete the tasks individually, since the tasks this week were more independent.
- Divith got the character to hold a gun in one hand and a blade in the other, and also got the character to move slower when their health is low.
- I implemented glass that shatters into many pieces.

Individual:
- I implemented a "breaking-glass" mechanic. Currently, there is glass that will shatter into many pieces when the player runs into it.
- I fleshed out the ideas surrounding our combat design, of the character having a gun in one hand and a blade in the other. In particular, how to balance around the fact that the gun has range and the blade doesn't. I also wanted to design it in a way where the gun and the blade are used in tandem, rather than the blade being a "backup" weapon. I wrote about it and what I wanted to do for the design, but we still need to go over and refine the ideas.

## Week 3
Team:
- For this week, our team split up and worked on the different moves of our character, who we plan to have both melee and ranged moves (pistol + katana) in their moveset.
Divith and Yoyo worked on melee, adding a sword swing and a combo attack
- I worked on the gun’s usage, beginning with movement while aiming the gun.
Individual:
- Got animations from Mixamo for moving (for multiple directions) and idling while aiming a gun
- Put them into Unreal, blending them based on the player's movement speed and direction.
![animation blend space](https://github.com/user-attachments/assets/8b0a68ba-85e0-4758-8adc-b8051da3bd44)
- Edited the animation state machine to go between the default animations and these animations
![animation state machine](https://github.com/user-attachments/assets/de4d37de-a391-4f5f-b868-e4e6331310e9)
