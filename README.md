# GunsAndSwords
- January-April 2025
- Unreal Engine 5
- Team of 4

A combat design prototype where the player uses a pistol and a katana together to fend off multiple enemies at once. Inspired by the combat scenes in the *John Wick* movies.

# Design Journal
This is a week-by-week log of the progress our team made on this project.

## Week 1
#### Team
- Set up Perforce depot and workspace and set up Unreal project
- Found an avatar on Mixamo that we wanted to use
- Retargeted the Unreal default character animations onto the Mixamo avatar

#### Individual
- Helped set up Perforce workspace and Unreal project

## Week 2
#### Team
- For this week, we met and decided what we wanted to get done this week. Then, Yoyo split us off to complete the tasks individually, since the tasks this week were more independent.
  - Divith got the character to hold a gun in one hand and a blade in the other, and also got the character to move slower when their health is low.
  - I implemented glass that shatters into many pieces.

#### Individual
- I implemented a "breaking-glass" mechanic. Currently, there is glass that will shatter into many pieces when the player runs into it.
- I fleshed out the ideas surrounding our combat design, of the character having a gun in one hand and a blade in the other. In particular, how to balance around the fact that the gun has range and the blade doesn't. I also wanted to design it in a way where the gun and the blade are used in tandem, rather than the blade being a "backup" weapon. I wrote about it and what I wanted to do for the design, but we still need to go over and refine the ideas.

## Week 3
#### Team
- For this week, our team split up and worked on the different moves of our character, who we plan to have both melee and ranged moves (pistol + katana) in their moveset.
  - Divith and Yoyo worked on melee, adding a sword swing and a combo attack
  - I worked on the gun’s usage, beginning with movement while aiming the gun.
#### Individual
- Got animations from Mixamo for moving (for multiple directions) and idling while aiming a gun
- Put them into Unreal, blending them based on the player's movement speed and direction.
![animation blend space](https://github.com/user-attachments/assets/8b0a68ba-85e0-4758-8adc-b8051da3bd44)
- Edited the animation state machine to go between the default animations and these animations
![animation state machine](https://github.com/user-attachments/assets/de4d37de-a391-4f5f-b868-e4e6331310e9)

## Week 4
#### Team
- Again, we split up to work on the different moves in our character's moveset.
  - Divith and Yoyo worked on melee attacks, with Divith adding a combo attack (different melee attacks occurring when doing them one after the other), and Yoyo adding a jump attack.
  - I worked on the mechanics related to shooting attacks.

#### Individual
- I worked on the shooting mechanic. Specifically, I implemented an aiming mechanic (to add onto the aiming animation I added last week), where when aiming, the camera angle will lock, and the player will have access to their cursor to point and click at enemies to shoot. I chose to do it this way (instead of a usual crosshair that's always at the center, with the camera moving to point at targets), since I anticipated the player to have to shoot multiple different enemies in rapid succession, and they'd be able to do that a bit faster if the camera wasn't moving when they moved their cursor between different targets. I also made the camera shift to a slightly high angle, so that if the player aims while looking at a bad angle, they aren't locked there.
- I also added an automatic "lock-on" mechanic, where the player doesn't have to be pointed at the enemy (just a cylinder with no behavior for now), just near them, for them to be properly targeted. This is so that the player can aim and shoot at them faster. I also added a visual indicator for which enemy is being locked on to.
- Note that the shooting animation is currently broken, I will work on fixing it in the future.
- But I was short on time this week, so I wasn't able to complete everything I wanted. Divith and Yoyo were able to complete theirs for the deliverable.

#### Video
[![wk4](https://img.youtube.com/vi/XaI4cpIyaTo/0.jpg)](https://www.youtube.com/watch?v=XaI4cpIyaTo)

## Week 5
#### Team
- This week, we focused on adding polish/effects to our game mechanics, to make them feel juicier.
  - I worked on various polishes for the shooting system.
  - Yoyo worked on polish for the movement, including wind that appears behind you when running, and footstep sounds
  - Divith worked on polish for the health system, including a blood effect on the screen when taking damage, and the screen going grayscale when at low health.

#### Individual
- Like last week, I worked on the gun. This time, I was adding polish to the gun's shooting and aiming.
  - Shoot animation - before this week, I had gotten a shooting animation from Mixamo, but it didn't match the gun idle/strafing animations, so it looked weird when shooting. This week, I figured out how to fix the shooting animation to match the others, it didn't look weird when shooting. I basically just went into the skeleton and copy-pasted the transforms from the gun idle animation to the gun shoot animation, for each bone (only from the spine up, since I was blending the shoot animation for the upper body with idle/strafe animations for the lower body) (except for the fingers, which there were too many bones for).
  - Aim offsets - added poses for the character aiming upwards, downwards, left, right, and the diagonals. Made a blend space for these poses. Then I made it so that the character aims where the mouse is pointed.
  - Gunfire sound - played a pistol gunshot sound, whenever firing the gun.
  - Gunfire particles - emitted a basic gun smoke particle effect from the gun, whenever firing the gun.
  - Shoot input buffering - the pistol has a cooldown, so the player can't just rapid-fire super fast. But, it would feel unresponsive if they inputted a shot right before the cooldown finished, and the character didn't shoot when they expected one. So, if they do that, we remember the input, and then shoot immediately once the cooldown ends.


## Week 6
#### Team
- This week, our team playtested our project with a few people, and made changes to the game based on the feedback.
  - We got feedback that the camera lock while aiming didn’t feel good, so I worked on having the aiming no longer lock the camera.
  - We got feedback that the melee attacks felt weird with the player completely stationary, so Divith worked on there being player movement during their melee attacks.
  - We got feedback that the inputs for the combo attack didn’t really mesh well with the inputs for the game, so Yoyo changed the inputs for it.
  - Yoyo and Ray added sound effects for the melee attacks.
  - Divith also worked on getting melee abilities onto Unreal’s GAS system.

#### Individual
- This week, I implemented some changes suggested by the feedback we got during playtesting:
  - Multiple people didn't like that the camera locked while aiming the gun, so I made it so that the camera moves where you aim. Still WIP--I'd still like to somehow incorporate the aim offset poses that I worked on in a previous week.
  - Someone noticed that the interaction between the melee system and gun system were causing a number of janky bugs. So I went in and cleaned up the interaction, so that you can't aim/shoot while performing a melee attack.

#### Before & After
[![wk6 before](https://img.youtube.com/vi/1gZ5M0ZfDz4/0.jpg)](https://www.youtube.com/watch?v=1gZ5M0ZfDz4) [![wk6 after](https://img.youtube.com/vi/oQY5pofTEJw/0.jpg)](https://www.youtube.com/watch?v=oQY5pofTEJw)

## Week 7
#### Team
- This week, we focused on making enemies for the player to fight. We decided on two enemies to make, then split off.
  - Yoyo and Divith worked on an enemy with close-ranged attacks.
  - I made a ranged enemy, which shoots at the player on sight.
  - Ray worked on re-adding VFX, after the attack animations were updated.

#### Individual
- This week, I implemented one of the enemies, specifically the one that uses ranged attacks. (This enemy's AI is WIP)
  - By default, the enemy will wander.
  - When the enemy sees the player, they will look at them and aim their gun.
  - If the enemy sees the player for a long enough time, they will shoot at the player. They might miss, depending on the distance between them and the player, as well as how fast the player is moving (tangent to the vector between them and the player).
  - When the enemy loses sight of the player, they will run to the location where they last saw them.
  - Once they finish that and don't see the player for some time, they will start wandering again.
![enemy behavior tree](https://github.com/user-attachments/assets/6edb44c4-4d30-4235-a575-b9c65f485c1a)

#### Before & After
[![wk7 before](https://img.youtube.com/vi/jCXWEZuZM6M/0.jpg)](https://www.youtube.com/watch?v=jCXWEZuZM6M) [![wk7 after](https://img.youtube.com/vi/1r4ix1vUmls/0.jpg)](https://www.youtube.com/watch?v=1r4ix1vUmls)

## Week 8
#### Team
- This week, we focused on adding relevant elements to the game’s user interface. We met up to decide on what UI elements to make, and then mostly split off to do them.
  - Ray made an enemy direction indicator.
  - Yoyo worked on the health bar, as well as adding polish to some elements from previous weeks.
  - I worked on the ammo count, since I was the main person working on the shooting mechanic.

#### Individual
- This week, I implemented the ammo counter UI.
  - This also comes with an ammo mechanic and an ability to reload (when the gun is not at full magazine ammo).
  - Additionally, there is now "Low Ammo" text at the center of the screen when there is both low magazine ammo and zero reserve ammo (ammo that isn't in the gun (to the right of the "/")), and there is "No Ammo" text when completely out of ammo.
  - The reload animation is WIP -- I couldn't find a proper pistol reload animation on Mixamo (it's a rifle reload animation), so I would need to find a better solution. But right now it's close enough.

#### Before & After
[![wk7 before](https://img.youtube.com/vi/xjSjcvXqLaI/0.jpg)](https://www.youtube.com/watch?v=xjSjcvXqLaI) [![wk7 after](https://img.youtube.com/vi/oKti-zKPfQ4/0.jpg)](https://www.youtube.com/watch?v=oKti-zKPfQ4)

## Week 9
#### Individual
- This week, I implemented another move to our character's ranged moveset, the headshot.
  - To perform it, hold the shoot input (left click) while aiming at an enemy.
  - After some time, focus for the headshot will charge up (as shown by the crosshair closing in on the enemy and the camera zooming in).
  - Once fully charged (green crosshair), you can release the shoot input to perform it. (If released before fully charged, it will just do a normal shot.)
  - I added a few things to contribute to the 'power fantasy' aspect of it. First, while charging, time slows down to half speed, to signify the character's focus. Second, the headshot will also send the enemy flying, more than if they're killed normally.
- This move is complementary to the regular shot. While the regular shot is fast and takes multiple shots to kill an enemy, the headshot is slow (even with the slow-mo during focusing) but takes only one shot to kill an enemy. I am still thinking about whether the headshot needs more balancing.

#### [Before](https://drive.google.com/file/d/1ZSFlTp7Yw50UfgSMzkcLGcqxPCJz9ofj/view?usp=sharing) & [After](https://drive.google.com/file/d/12bw7Esz8nbmBNxJS1_H_VQlrAmVfXeeD/view?usp=sharing)

## Week 10-11
Week 10 was spring break, and our whole team/class went to GDC during week 11.

## Week 12
#### Individual
- I noticed a lot of duplicated code between our different enemy classes.
  - To combat this, I factored out a lot of the common behavior between these classes into one superclass, BP_Enemy. This superclass handles detecting the player/their decoy, as well as what happens when taking damage (a lot of things, such as stun, knockback, and dying)
  - Doing this also had the effect (which was intended) of making the melee enemies now shootable, and the ranged enemy now melee-able, when they previously weren't.
  - It also resulted in both our melee enemies now using the exact same behavior tree (BTT_Attack calls BP_Enemy's Attack which is overridden by each enemy type).
![updated behavior tree](https://github.com/user-attachments/assets/1afcc8d2-8a2e-439d-8be0-238918f7b9ad)

#### [Before](https://drive.google.com/file/d/1yVVod8U0iR63k150cu9PRf2cnAkEwXIM/view?usp=sharing) & [After](https://drive.google.com/file/d/1qezXXHscYEe2lrOgRi4x-Cd7U4hJkqfW/view?usp=sharing)

## Week 14
#### Individual
- I focused on defensive abilities for our character this week, working on two of them.
  - First, is the decoy. The decoy is created whenever you dodge, at the spot where you dodged (also indicated by Divith's dodge VFX). It's invisible and lasts a few seconds before despawning. While present, enemies will target it instead of you.
  - Second, is the parry. For the existing block ability, if you block right before an enemy lands their attack, you will parry that attack, and they will be stunned briefly.

#### Before ([Decoy](https://drive.google.com/file/d/1emkLd_TXDsgrvti4ZxASscYW4wkKJs1G/view?usp=sharing), [Parry](https://drive.google.com/file/d/1uaI7I3H2eAXq5FoPvPgIvlNhmfVoE4fn/view?usp=sharing)) & [After](https://drive.google.com/file/d/11WZkrGytk1NOFLtjKdFdm506vdRozIOb/view?usp=sharing)

## Week 15
#### Individual
- This week I worked on a lot of things in preparation for the final assignment for the class:
  - Added some additional player feedback/polish, such as shield particles, blood particles, melee slash sound, and shield hitting sound.
  - Reworked the flamethrower enemy to differentiate it more from the katana enemy. Instead of doing a lot of damage at once, it now does a little damage per frame (as if it's 'burning' the player with their flamethrower).
  - Finished the implementation of blocking for the melee and ranged enemies. They will block if all three apply: you're far away enough from them, you're aiming your gun, and you're looking in their general direction. When blocking, they will put their shield up and face you, and attacks will have no effect on them.
  - Put the katana enemy on the GAS system, reusing some of the player's gameplay tags. This also resulted in their attacks feeling more correct (i.e. the damage occurrs more accurately to when they're swinging their weapon) (since we're using animation notifies) compared to the previous implementation.
  - Enemies will now detect you if you damage them.
  - Added a few mini-levels to the main level, each with different positionings and combinations of enemies.

#### Before ([Flamethrower](https://drive.google.com/file/d/135klBtcEm1WryUIAXwZYaGBU4hmUqxCD/view?usp=sharing), [Katana](https://drive.google.com/file/d/1PJ5m5QRwPRUQBjZTrPhHQizGTLiaF7RZ/view?usp=sharing), [Shield](https://drive.google.com/file/d/1SZubx6qKRzJsh3O7M9W4nWf0GFpaY_BG/view?usp=sharing))
#### After (General, Flamethrower)
[![wk15 after](https://img.youtube.com/vi/T05F3lYViWo/0.jpg)](https://www.youtube.com/watch?v=T05F3lYViWo) [![wk15 after flamethrower](https://img.youtube.com/vi/p-eJ7ZnOY-A/0.jpg)](https://www.youtube.com/watch?v=p-eJ7ZnOY-A)
