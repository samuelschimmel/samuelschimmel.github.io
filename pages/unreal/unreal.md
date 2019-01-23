---
layout: page
title: Unreal
permalink: /unreal/
---

<h2><strong>Videos</strong></h2>

<div style="padding:56.25% 0 0 0;position:relative;"><iframe src="https://player.vimeo.com/video/284635802?portrait=0" style="position:absolute;top:0;left:0;width:100%;height:100%;" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe></div><script src="https://player.vimeo.com/api/player.js"></script>

<h2><strong>Images</strong></h2>

![]({{ "/assets/unreal/1.png" | absolute_url }})

![]({{ "/assets/unreal/2.png" | absolute_url }})

![]({{ "/assets/unreal/3.png" | absolute_url }})

![]({{ "/assets/unreal/4.png" | absolute_url }})

![]({{ "/assets/unreal/5.png" | absolute_url }})

![]({{ "/assets/unreal/6.png" | absolute_url }})

![]({{ "/assets/unreal/7.png" | absolute_url }})

<h2><strong>Behavior tree</strong></h2>

![]({{ "/assets/unreal/bt.png" | absolute_url }})

<h2><strong>UE4 C++ workshop given as GAM 300 TA</strong></h2>

<iframe src="/assets/unreal/workshop.pdf" width="100%" height="400"></iframe>

<h2><strong>Features implemented</strong></h2>

<b>AI aiming</b>

AI aiming is handled by the custom behavior tree service CheckTargetActor. When CheckTargetActor is ticked, NPCs in combat will focus on an intercept point offset from their target. This point is calculated using the NPC’s firearm’s projectile speed and gravity in order to compensate for target velocity and bullet drop. Assuming zero spread and zero projectile gravity, NPCs are perfectly accurate against targets with constant velocity, which requires the player to vary their movement patterns in order to dodge projectiles.

<b>AI detection</b>

NPCs instantaneously detect other NPCs, and gradually detect the player. The detection meter fills while the player is in line of sight, and not 100% concealed (otherwise, the meter decays by a constant rate). The meter also fills by a constant amount when the AI hears the player, and immediately fills to max on collision with player. Visual fill rate is given as:

<img src="https://tex.s2cms.ru/svg/fillModifier%20*%20deltaTime%20*%20(weightedConcealmentModifier%20%2B%20weightedDistanceModifier%20%2B%20weightedFOVModifier)" alt="fillModifier * deltaTime * (weightedConcealmentModifier + weightedDistanceModifier + weightedFOVModifier)"
width="100%" height=400/>

…where player concealment is calculated once every 100 ms based on lighting and stance.

<b>[AI formations](https://github.com/samuelschimmel/perdition/blob/master/AIFormations.cpp)</b>

AI formations are handled by a custom behavior tree service called Command. When Command is ticked, agents of class Leader remove dead soldiers from their soldiers container, add new soldiers, and update their soldiers’ target locations. Soldiers can be added to the container if they don’t already have leaders, and are within range and line of sight of the leader. The algorithm for selecting target locations is as follows. First, the formation radius is calculated based on the number of soldiers in the squad. Then the soldiers are assigned evenly spaced points on a semicircle. The semicircle is based on the leader’s forward vector during the patrol state. During combat, it is based on the vector between the leader and the player, which allows the soldiers to take defensive positions around their leader.

<b>AI hearing</b>

Footsteps, gunshots, explosions, projectile impacts, and thrown prop impacts all create noise for AI purposes. Since explosions are the loudest sounds in the game, I made the explosion sound intensity 1, and set "max hearing radius" to the distance at which NPCs should be able to hear explosions. All other sound intensities are relative to the explosion sound intensity.

<b>[AI positioning](https://github.com/samuelschimmel/perdition/blob/master/AIPositioning.cpp)</b>

<b>AI vision</b>

Enemies are alerted if they see a dead body.

<b>Agent</b>

Agent is the shared player/NPC base class. Players and NPCs behave similarly enough that I could factor out and resuse over a thousand lines of code by moving it to the base class. In addition to code reuse, the Agent class also promotes consistency by making sure that players and NPCs are governed by the same ruleset. Deriving players and NPCs from the same base class also allowed me to use the same AI controller class for both of them, which proved useful when implementing autoplay.

Functionality shared between players and NPCs via the Agent class include obstacle climbing, health, stamina, damage, dashing, ladders, melee, object interaction, speed, stances, weapon usage, and weapon inventory.

Player-exclusive functionality includes health regeneration, losing and restarting, locking on, aiming with the scope, determining the player’s current target, illumination calculation, melee takedowns, a “last stand” state (in which lethal damage to the player is clamped to 1 HP, unless they are already at 1 HP), and input (including allowing or disallowing input depending on various states).

NPC-exclusive functionality includes AI state feedback (idle, alert, etc.), random equipment spawning, and stun.

<b>[Asset loading with caching](https://github.com/samuelschimmel/perdition/blob/master/GetAsset.cpp)</b>

I optimized my custom asset lookup function by having it cache the assets it loads in a TMap<FString, UObject *>. This way, it only has to call Unreal's asset loading code the first time my code requests an asset. All subsequent times it can get the asset from the map, with the key being the asset's path. The function is templatized to work with static meshes as well as UObjects.

<b>Behavior tree-compatible scripting nodes</b>

The built-in AIMoveTo node is incompatible with behavior trees. To combine custom scripting with procedural behaviors, I created custom MoveToActor and MoveToLocation nodes. When they are called, the agent will stop whatever they're doing, go to the given location or actor (and follow the actor if it moves), and then resume normal behavior once they arrive. This behavior takes priority over patrol and combat behaviors, but not stun or stationary behaviors. The biggest limitation of MoveToActor and MoveToLocation is that they lack AIMoveTo’s asychronous "OnSuccess" and "OnFailure" pins.

<b>[Checkpoints and saving](https://github.com/samuelschimmel/perdition/blob/master/SaveManager.cpp)</b>

All unsaved items are lost when players reload their last checkpoint.

<b>Combat feedback</b>

I added very brief slow motion after the player performs a scoped rifle headshot or melee kill. For both props and agents, point damage with knockback will push the damage receiver away from the damage instigator. For both props and agents, radial damage with knockback will push the damage receiver away from the origin of the damage.

Instead of immediately dropping their guns, dead enemies pull the trigger for one second and then release and drop the gun like in F.E.A.R. 2. During this time, the projectiles spawn with the rotation of the firearm world mesh instead of the agent's "actor eyes view point.”

Instead of having NPCs immediately drop all of their equipment on death, I have them wait a fraction of a second before doing so, so their armor goes flying when they ragdoll instead of just falling to the ground. I also made it so when you kill an enemy with a headshot, their helmet flies off.

<b>[Damage system](https://github.com/samuelschimmel/perdition/blob/master/AgentTakeDamage.cpp)</b>

<b>Dash mechanic</b>

<b>Destructible armor</b>

<b>Doors</b>

<b>Dynamic multicast delegate Blueprint interface</b>

<b>[Enemy wave spawning system](https://github.com/samuelschimmel/perdition/blob/master/Encounter.cpp)</b>

Instances of BP_Encounter are placed in the level, and spawners and triggers are attached to them in the world outliner. Parameters include spawn tickets for each enemy type, min and max concurrent enemies, wave size mean and standard deviation, and wave delay mean and standard deviation. Each wave size is calculated using a normal distribution, and each wave delay is calculated using a binomial distribution. Combat start and end feedback properly handles the player being in more than one encounter at the same time. When the player triggers an encounter, only the first wave will spawn (unaware of the player) until the player enters combat. If the player is already in combat when they trigger an encounter, the encounter will spawn waves of enemies normally. Enemies spawned by encounters while the player is in combat will automatically be aware of the player. Encounters can also be started from the level blueprint.

<b>[Firearms](https://github.com/samuelschimmel/perdition/blob/master/WeaponFiring.cpp)</b>

Projectiles can be rotated to follow the vector from the firearm’s muzzle to the user’s current target. This allows projectiles to always hit the center of the player’s crosshair. When the agent is more than 5 meters from their target, projectiles are rotated to fire directly at the target. Between 5 and 1 meters, projectiles fire at the average of the target vector and the look vector (if they are just fired at the target vector, the rotation is noticeable; if they are just fired at look vector, the transition is noticeable). Closer than 1 meter, projectiles can’t be fired. If the user has no target (i.e., while looking at the sky), just the look vector is used.

Spread is calculated using the weapon’s base spread and the agent’s movement. For players, RPG skills are also considered. NPCs have a minimum spread to prevent them from being too accurate with precise, high damage weapons.

An event is fired when players start and stop facing an obstacle (i.e., the raycast sent every frame from the camera hits a non-agent object at less than a certain distance) to allow for weapon handling animations. The event only fires when the result changes, not every frame if the result is the same.

<b>[Fire propagation](https://github.com/samuelschimmel/perdition/blob/master/DamageVolume.cpp)</b>

Damage volumes start with 0 radius and tick up to a given maximum within a few seconds. Fire spreads to the player, NPCs, interactive objects, and static mesh actors. When a damage volume overlaps an actor, it checks if is already has a damage volume attached to it before spawning one.

Environmental damage volumes are also supported. Designers can drag damage volumes into the level, which will act as hazards and never expire. If an actor is on fire and they overlap more fire, their fire’s timer restarts.

<b>[Inventory system](https://github.com/samuelschimmel/perdition/blob/master/InventorySystem.cpp)</b>

The inventory manager object persists between levels, but is reset to its state at the last checkpoint when the player dies.

<b>[Melee combat](https://github.com/samuelschimmel/perdition/blob/master/Melee.cpp)</b>

I originally tried implementing melee using colliders, but the player had to stand excessively close to their target in order to damage them. I tried making the collider bigger, but because overlap events are only fired when an actor enters a collider, the player was only able to melee targets that were just barely in melee range (if the player were any closer, the overlap event would have already fired). I tried storing a pointer to the current melee collider overlap actor and damaging it during the melee attack, but this lead to attacking nearby but incorrect targets. I also tried storing those overlapped actors in an array, but this would require an algorithm to pick the best one.

I think the collider approach would work well for a third person game, or for enemy melee attacks where collision can and should be more accurate. However, for first person player melee, I found it move effective to use raycasts. The player’s current target is checked every frame of the melee animation. Damage is dealt on the first frame that the target is within melee range of the weapon socket. Using the raycast method, designers can adjust first person melee weapon range, and attacks will always hit the target in the player’s crosshair. Checking distance from the weapon socket allows the range of the attack to extend slightly over the course of the animation.

In order for damage to only occur during the appropriate frames of the melee animation, the animation blueprint must call C++ functions that enable and disable damage. Damage is also disabled until the end of the animation after a target is struck.

Enemies can also melee attack instead of firing their weapon if their target is near enough.

I also implemented a melee takedown mechanic similar to those found in Far Cry and Dishonored. When the player targets a stunned enemy within a given distance and hits the melee button, input is disable, the player lerps to their target, and a melee attack is performed, which instantly kills the enemy. During this sequence, the camera also lerps to look at the target agent. All melee attacks on unaware enemies are takedowns. Enemies do not alert other enemies if they are killed by a takedown.

<b>Narrative manager</b>

Any time the player triggers a trigger or uses an interactive object, the persistent narrative manager checks if a) that actor is a narration actor and b) the game is not ready for narration. If both of those are true, the player can't use the item/trigger the trigger. The second condition is based on whether the player is in combat and whether narration is already playing.

If the actor is a narration actor and the game is ready for narration, the game mode sends an event with the name of the actor. Audio can use that name to play the right audio event, and the HUD can pass that name to the text manager to get the appropriate subtitle. Meanwhile, player input is disabled. When the audio is finished playing, the audio engine can call a function that will re-enable player input and tell the HUD to remove the subtitle.

<b>[Ladders](https://github.com/samuelschimmel/perdition/blob/master/Ladders.cpp)</b>

Ladders can be mounted from any position, including while the player is falling. Ladders calculate their mount and dismount locations based on position, rotation, and bounds. When dismounting, the player lerps to a position a bit past the ladder, where the height is the top of the ladder, or the height of the surface they're climbing onto plus capsule half height, whichever is higher.

<b>[Lock-on targeting](https://github.com/samuelschimmel/perdition/blob/master/LockOnAttack.cpp)</b>

<b>Object interaction</b>

Props receive and deal a fixed amount of damage when thrown. This allows thrown explosive props to detonate on impact.

<b>[Obstacle climbing](https://github.com/samuelschimmel/perdition/blob/master/ObstacleClimbing.cpp)</b>

The min and max slope of climbable obstacles can be specified in degrees. How directly the player needs to be facing obstacles in order to climb them can also be specified as an angle in degrees. Collision is disabled during the climbing sequence to make the sequence smoother. Climbing also cancels the player's velocity to make the sequence feel less floaty. An event is fired when the player is facing a climbable obstacle so that UMG can display a prompt.

<b>Options menu backend</b>

I made a derived class of GameUserSettings and edited DefaultEngine to use it. I also made a class with static blueprint callable functions for communication with an options menu. This allows for game options like difficulty, invert mouse, show objective locator, etc. When options are updated, the changes are reflected in-game and saved to a file. I also added a function which takes a string and returns a copy with actions/axes in square brackets (case insensitive) replaced with the first key currently bound to that action/axis. This allows tutorials and UI to avoid hardcoding rebindable inputs. I also added functions for rebinding keys that remove any previous bindings.

<b>[Player illumination calculation](https://github.com/samuelschimmel/perdition/blob/master/CamoIndex.cpp)</b>

Player illumination calculation works with directional lights, point lights, and spot lights. For point and spot lights, the calculation uses inverse square attenuation. The penalty to the player’s concealment is given as:

<img src="https://tex.s2cms.ru/svg/lightIntensity%20%5Cover%20distanceToPlayer%5E2" alt="lightIntensity \over distanceToPlayer^2" width="100%" height=400/>

Player illumination calculation requires iterating over a container of every light in the level, but this is mitigated by a) only updating every 100 ms, and b) culling lights by doing tests in order of least expensive to most expensive (distance, then field of view, then collision).

<b>[Player modeling, dynamic difficulty, dynamic tutorials, and weighted random item spawning](https://github.com/samuelschimmel/perdition/blob/master/PlayerModeling.cpp)</b>

At periodic intervals while the player is alive and not in combat, the player modeling system determines which action the player has performed the least, and displays a tutorial for that action. It will only display one tutorial per action per level. Tutorials that teach controls are responsive to key rebinding.

Player modeling also tracks weapon and item pickups in order to display tutorials the first time they are  acquired. These tutorials don't conflict with the tutorials that play the first two times weapons of any type are picked up (i.e., “press LMB to fire” and “use scroll wheel to switch weapons”).

A "use WASD to move" tutorial plays at the beginning of the game if the player doesn’t move for more than a few seconds. The tutorial uses the current movement mappings, and will never play after the player has moved.

<b>[Player targeting](https://github.com/samuelschimmel/perdition/blob/master/PlayerTargeting.cpp)</b>

<b>[Quest system](https://github.com/samuelschimmel/perdition/blob/master/QuestManager.cpp)</b>

The quest manager supports multiple simultaneous sets of objectives, each with their own separate objective locators. The quest system can handle objectives being destroyed early.

<b>[Radial damage](https://github.com/samuelschimmel/perdition/blob/master/RadialDamage.cpp)</b>

<b>Rifle scope</b>

<b>RPG mechanics</b>

The stat system supports multiple tiers of stats (e.g., tier 0 for player level, tier 1 for attributes, tier 2 for skills, and tier 3 for perks). Stats can have parent stats like in Shadowrun (i.e., your rifle skill level can’t exceed your ranged combat skill level). Players are awarded points for each tier. When the player attempts to level up a stat, the stat’s max level is checked, the parent stat’s level is checked, and their points in that tier are checked. Leveling up can award points for other tiers. Stat levels can be queried elsewhere in the code. For example, the player’s firearm skill is used to calculate the spread of each shot.

<b>Worldspace UI</b>
