---
layout: page
title: Unreal
permalink: /unreal/
---

<h2><strong>Projects</strong></h2>

<b>Technical Director</b>, <i>Perdition</i>

2017-18

3D, systems-driven, emergent FPS developed in Unreal using C++

Published on Steam (87% of 97 user reviews are positive)

2019 DigiPen PAX West Senior Game Selection

[DRM-free download](https://www.digipen.edu/showcase/student-games/perdition)

<center><iframe src="https://store.steampowered.com/widget/1137910/" frameborder="0" width="100%" height="190"></iframe></center>

<h2><strong>Videos</strong></h2>

<style>.embed-container { position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; max-width: 100%; } .embed-container iframe, .embed-container object, .embed-container embed { position: absolute; top: 0; left: 0; width: 100%; height: 100%; }</style><div class='embed-container'><iframe src='https://www.youtube-nocookie.com/embed/s9_TVrtvwVw' frameborder='0' allowfullscreen></iframe></div>

<h2><strong>Steam Community screenshots</strong></h2>

<a href="https://steamcommunity.com/sharedfiles/filedetails/?id=1841958870"><img src="/assets/unreal/1.jpg"></a>

<a href="https://steamcommunity.com/sharedfiles/filedetails/?id=1843257925"><img src="/assets/unreal/2.jpg"></a>

<a href="https://steamcommunity.com/sharedfiles/filedetails/?id=1841958901"><img src="/assets/unreal/3.jpg"></a>

<a href="https://steamcommunity.com/sharedfiles/filedetails/?id=1841958935"><img src="/assets/unreal/4.jpg"></a>

<a href="https://steamcommunity.com/sharedfiles/filedetails/?id=1843258246"><img src="/assets/unreal/5.jpg"></a>

<a href="https://steamcommunity.com/sharedfiles/filedetails/?id=1841959062"><img src="/assets/unreal/6.jpg"></a>

<a href="https://steamcommunity.com/sharedfiles/filedetails/?id=1843258508"><img src="/assets/unreal/7.jpg"></a>

<a href="https://steamcommunity.com/sharedfiles/filedetails/?id=1841959025"><img src="/assets/unreal/9.jpg"></a>

<a href="https://steamcommunity.com/sharedfiles/filedetails/?id=1841959200"><img src="/assets/unreal/11.jpg"></a>

<a href="https://steamcommunity.com/sharedfiles/filedetails/?id=1843260952"><img src="/assets/unreal/12.jpg"></a>

<a href="https://steamcommunity.com/sharedfiles/filedetails/?id=1843261081"><img src="/assets/unreal/13.jpg"></a>

<a href="https://steamcommunity.com/sharedfiles/filedetails/?id=1841959221"><img src="/assets/unreal/14.jpg"></a>

<a href="https://steamcommunity.com/sharedfiles/filedetails/?id=1841959266"><img src="/assets/unreal/15.jpg"></a>

<a href="https://steamcommunity.com/sharedfiles/filedetails/?id=1846276144"><img src="/assets/unreal/16.jpg"></a>

<a href="https://steamcommunity.com/sharedfiles/filedetails/?id=1843261740"><img src="/assets/unreal/17.jpg"></a>

<h2><strong>Behavior tree</strong></h2>

![]({{ "/assets/unreal/bt.png" | absolute_url }})

<h2><strong>Features implemented</strong></h2>

<summary>AI formations <strong></strong></summary>
AI formations are handled by a custom behavior tree service called Command. When Command is ticked, agents of class Leader remove dead soldiers from their soldiers container, add new soldiers, and update their soldiers’ target locations. Soldiers can be added to the container if they don’t already have leaders, and are within range and line of sight of the leader. The algorithm for selecting target locations is as follows. First, the formation radius is calculated based on the number of soldiers in the squad. Then the soldiers are assigned evenly spaced points on a semicircle. The semicircle is based on the leader’s forward vector during the patrol state. During combat, it is based on the vector between the leader and the player, which allows the soldiers to take defensive positions around their leader.
<br><br>
<style>.embed-container { position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; max-width: 100%; } .embed-container iframe, .embed-container object, .embed-container embed { position: absolute; top: 0; left: 0; width: 100%; height: 100%; }</style><div class='embed-container'><iframe src='https://player.vimeo.com/video/315609030' frameborder='0' webkitAllowFullScreen mozallowfullscreen allowFullScreen></iframe></div>
<br>
<details>
<script src="https://gist.github.com/samuelschimmel/6c0cc776b004cbdbd40ad4f3091e24d5.js"></script>
<br>
</details>

<summary>First-person obstacle climbing <strong></strong></summary>
The min and max slope of climbable obstacles can be specified in degrees. How directly the player needs to be facing obstacles in order to climb them can also be specified as an angle in degrees. Collision is disabled during the climbing sequence to make the sequence smoother. Climbing also cancels the player's velocity to make the sequence feel less floaty. An event is fired when the player is facing a climbable obstacle so that UMG can display a prompt.
<br><br>
<style>.embed-container { position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; max-width: 100%; } .embed-container iframe, .embed-container object, .embed-container embed { position: absolute; top: 0; left: 0; width: 100%; height: 100%; }</style><div class='embed-container'><iframe src='https://player.vimeo.com/video/320170064' frameborder='0' webkitAllowFullScreen mozallowfullscreen allowFullScreen></iframe></div><br>
<br>
<details>
<script src="https://gist.github.com/samuelschimmel/ad73a4fe2a9bb1e2a6d5a26b4fac6338.js"></script>
<br>
</details>

<summary>Ladders <strong></strong></summary>
Ladders can be mounted from any position, including while the player is falling. Ladders can be rotated or scaled and will automatically calculate their mount and dismount locations without the need for level designer configuration. When the player reaches the top of a ladder, their dismount location's height is the height of the ladder or the height of the surface directly behind the ladder plus capsule half height, whichever is higher.
<br><br>
<style>.embed-container { position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; max-width: 100%; } .embed-container iframe, .embed-container object, .embed-container embed { position: absolute; top: 0; left: 0; width: 100%; height: 100%; }</style><div class='embed-container'><iframe src='https://player.vimeo.com/video/329509194' frameborder='0' webkitAllowFullScreen mozallowfullscreen allowFullScreen></iframe></div>
<br>
<details>
<script src="https://gist.github.com/samuelschimmel/ee2ed56011589091ea6b1fd2db11e9e5.js"></script>
<br>
</details>

<summary>Player illumination calculation <strong></strong></summary>
Player illumination calculation works with directional lights, point lights, and spot lights. For point and spot lights, the calculation uses inverse square attenuation. The penalty to the player’s concealment is given as:
<br><br>
<img src="https://tex.s2cms.ru/svg/lightIntensity%20%5Cover%20distanceToPlayer%5E2" alt="lightIntensity \over distanceToPlayer^2" />
<br><br>
Player illumination calculation requires iterating over a container of every light in the level, but this is mitigated by a) only updating every 100 ms, and b) culling lights by doing tests in order of least expensive to most expensive (distance, then field of view, then collision).
<br><br>
<style>.embed-container { position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; max-width: 100%; } .embed-container iframe, .embed-container object, .embed-container embed { position: absolute; top: 0; left: 0; width: 100%; height: 100%; }</style><div class='embed-container'><iframe src='https://player.vimeo.com/video/330944593' frameborder='0' webkitAllowFullScreen mozallowfullscreen allowFullScreen></iframe></div><br>
<br>
<details>
<script src="https://gist.github.com/samuelschimmel/6cd809d7dc35408418cc0153193f825b.js"></script>
<br>
</details>

<details>
<summary>AI aiming</summary>
AI aiming is handled by the custom behavior tree service CheckTargetActor. When CheckTargetActor is ticked, NPCs in combat will focus on an intercept point offset from their target. This point is calculated using the NPC’s firearm’s projectile speed and gravity in order to compensate for target velocity and bullet drop. Assuming zero spread and zero projectile gravity, NPCs are perfectly accurate against targets with constant velocity, which requires the player to vary their movement patterns in order to dodge projectiles.
</details><br>

<details>
<summary>AI detection</summary>
NPCs instantaneously detect other NPCs, and gradually detect the player. The detection meter fills while the player is in line of sight, and not 100% concealed (otherwise, the meter decays by a constant rate). The meter also fills by a constant amount when the AI hears the player, and immediately fills to max on collision with player. Visual fill rate is given as:
<br><br>
<img src="https://tex.s2cms.ru/svg/fillModifier%20*%20deltaTime%20*%20(weightedConcealmentModifier%20%2B%20weightedDistanceModifier%20%2B%20weightedFOVModifier)" alt="fillModifier * deltaTime * (weightedConcealmentModifier + weightedDistanceModifier + weightedFOVModifier)" />
<br><br>
…where player concealment is calculated once every 100 ms based on lighting and stance.
</details><br>

<details>
<summary>AI hearing</summary>
Footsteps, gunshots, explosions, projectile impacts, and thrown prop impacts all create noise for AI purposes. Since explosions are the loudest sounds in the game, I made the explosion sound intensity 1, and set "max hearing radius" to the distance at which NPCs should be able to hear explosions. All other sound intensities are relative to the explosion sound intensity.
</details><br>

<details>
<summary>AI positioning</summary>
<br>
<script src="https://gist.github.com/samuelschimmel/8dea9b991893a01987af134be038fb5e.js"></script>
</details><br>

<details>
<summary>Agent</summary>
Agent is the shared player/NPC base class. Players and NPCs behave similarly enough that I could factor out and resuse over a thousand lines of code by moving it to the base class. In addition to code reuse, the Agent class also promotes consistency by making sure that players and NPCs are governed by the same ruleset. Deriving players and NPCs from the same base class also allowed me to use the same AI controller class for both of them, which proved useful when implementing autoplay. Functionality shared between players and NPCs via the Agent class include obstacle climbing, health, stamina, damage, dashing, ladders, melee, object interaction, speed, stances, weapon usage, and weapon inventory. Player-exclusive functionality includes health regeneration, losing and restarting, locking on, aiming with the scope, determining the player’s current target, illumination calculation, melee takedowns, a “last stand” state (in which lethal damage to the player is clamped to 1 HP, unless they are already at 1 HP), and input (including allowing or disallowing input depending on various states). NPC-exclusive functionality includes AI state feedback (idle, alert, etc.), random equipment spawning, and stun.
</details><br>

<details>
<summary>Asset loading with caching</summary>
I optimized my custom asset lookup function by having it cache the assets it loads in a TMap<FString, UObject *>. This way, it only has to call Unreal's asset loading code the first time my code requests an asset. All subsequent times it can get the asset from the map, with the key being the asset's path. The function is templatized to work with static meshes as well as UObjects.
<br><br>
<script src="https://gist.github.com/samuelschimmel/57e2f107aca5d9b086eed2cf4f612b1e.js"></script>
</details><br>

<details>
<summary>Behavior tree-compatible scripting nodes</summary>
The built-in AIMoveTo node is incompatible with behavior trees. To combine custom scripting with procedural behaviors, I created custom MoveToActor and MoveToLocation nodes. When they are called, the agent will stop whatever they're doing, go to the given location or actor (and follow the actor if it moves), and then resume normal behavior once they arrive. This behavior takes priority over patrol and combat behaviors, but not stun or stationary behaviors. The biggest limitation of MoveToActor and MoveToLocation is that they lack AIMoveTo’s asychronous "OnSuccess" and "OnFailure" pins.
</details><br>

<details>
<summary>Checkpoints and saving</summary>
<br>
<script src="https://gist.github.com/samuelschimmel/f7aba5aff29d4abb295f86ecf2455c94.js"></script>
</details><br>

<details>
<summary>Combat feedback</summary>
I added very brief slow motion after the player performs a scoped rifle headshot or melee kill. For both props and agents, point damage with knockback will push the damage receiver away from the damage instigator. For both props and agents, radial damage with knockback will push the damage receiver away from the origin of the damage. Instead of immediately dropping their guns, dead enemies pull the trigger for one second and then release and drop the gun like in <i>F.E.A.R. 2</i>. During this time, the projectiles spawn with the rotation of the firearm world mesh instead of the agent's "actor eyes view point.” Instead of having NPCs immediately drop all of their equipment on death, I have them wait a fraction of a second before doing so, so their armor goes flying when they ragdoll instead of just falling to the ground. I also made it so when you kill an enemy with a headshot, their helmet flies off.
</details><br>

<details>
<summary>Damage system</summary>
<br>
<script src="https://gist.github.com/samuelschimmel/4cd3a5eea2195a8e301b38df336669d3.js"></script>
</details><br>

<details>
<summary>Dynamic multicast delegate Blueprint interface</summary>
<br>
<script src="https://gist.github.com/samuelschimmel/248c709d791b858c74bcad6758a93fde.js"></script>
</details><br>

<details>
<summary>Enemy wave spawning system</summary>
Instances of BP_Encounter are placed in the level, and spawners and triggers are attached to them in the world outliner. Parameters include spawn tickets for each enemy type, min and max concurrent enemies, wave size mean and standard deviation, and wave delay mean and standard deviation. Each wave size is calculated using a normal distribution, and each wave delay is calculated using a binomial distribution. Combat start and end feedback properly handles the player being in more than one encounter at the same time. When the player triggers an encounter, only the first wave will spawn (unaware of the player) until the player enters combat. If the player is already in combat when they trigger an encounter, the encounter will spawn waves of enemies normally. Enemies spawned by encounters while the player is in combat will automatically be aware of the player. Encounters can also be started from the level blueprint.
<br><br>
<script src="https://gist.github.com/samuelschimmel/72ee16b0e160b0a920ba3aebd52631e4.js"></script>
</details><br>

<details>
<summary>Firearms</summary>
Projectiles can be rotated to follow the vector from the firearm’s muzzle to the user’s current target. This allows projectiles to always hit the center of the player’s crosshair. When the agent is more than 5 meters from their target, projectiles are rotated to fire directly at the target. Between 5 and 1 meters, projectiles fire at the average of the target vector and the look vector (if they are just fired at the target vector, the rotation is noticeable; if they are just fired at look vector, the transition is noticeable). Closer than 1 meter, projectiles can’t be fired. If the user has no target (i.e., while looking at the sky), just the look vector is used. Spread is calculated using the weapon’s base spread and the agent’s movement. For players, RPG skills are also considered. NPCs have a minimum spread to prevent them from being too accurate with precise, high damage weapons. An event is fired when players start and stop facing an obstacle (i.e., the raycast sent every frame from the camera hits a non-agent object at less than a certain distance) to allow for weapon handling animations. The event only fires when the result changes, not every frame if the result is the same.
<br><br>
<script src="https://gist.github.com/samuelschimmel/2c8b9822296b5b096722de6f0519f46c.js"></script>
</details><br>

<details>
<summary>Fire propagation</summary>
Damage volumes start with 0 radius and tick up to a given maximum within a few seconds. Fire spreads to the player, NPCs, interactive objects, and static mesh actors. When a damage volume overlaps an actor, it checks if is already has a damage volume attached to it before spawning one. Environmental damage volumes are also supported. Designers can drag damage volumes into the level, which will act as hazards and never expire. If an actor is on fire and they overlap more fire, their fire’s timer restarts.
<br><br>
<script src="https://gist.github.com/samuelschimmel/2cb0d482e4f4237187f7b36341492943.js"></script>
</details><br>

<details>
<summary>Inventory system</summary>
<br>
<script src="https://gist.github.com/samuelschimmel/fee1f912d1a58ad05d20dd515f02cb4d.js"></script>
</details><br>

<details>
<summary>Melee attack</summary>
I originally tried implementing melee using colliders, but the player had to stand excessively close to their target in order to damage them. I tried making the collider bigger, but because overlap events are only fired when an actor enters a collider, the player was only able to melee targets that were just barely in melee range (if the player were any closer, the overlap event would have already fired). I tried storing a pointer to the current melee collider overlap actor and damaging it during the melee attack, but this lead to attacking nearby but incorrect targets. I also tried storing those overlapped actors in an array, but this would require an algorithm to pick the best one. I think the collider approach would work well for a third person game, or for enemy melee attacks where collision can and should be more accurate. However, for first person player melee, I found it more effective to use raycasts. The player’s current target is checked every frame of the melee animation. Damage is dealt on the first frame that the target is within melee range of the weapon socket. Using the raycast method, designers can adjust first person melee weapon range, and attacks will always hit the target in the player’s crosshair. Checking distance from the weapon socket allows the range of the attack to extend slightly over the course of the animation. In order for damage to only occur during the appropriate frames of the melee animation, the animation blueprint must call C++ functions that enable and disable damage. Damage is also disabled until the end of the animation after a target is struck. Enemies can also melee attack instead of firing their weapon if their target is near enough.
<br><br>
<script src="https://gist.github.com/samuelschimmel/7621e64308c0738b31d22953c1cde3df.js"></script>
</details><br>

<details>
<summary>Melee takedown</summary>
I implemented a melee takedown mechanic similar to those found in <i>Far Cry</i> and <i>Dishonored</i>. When the player targets a stunned enemy within a given distance and hits the melee button, input is disable, the player lerps to their target, and a melee attack is performed, which instantly kills the enemy. During this sequence, the camera also lerps to look at the target agent. All melee attacks on unaware enemies are takedowns. Enemies do not alert other enemies if they are killed by a takedown.
<br><br>
<script src="https://gist.github.com/samuelschimmel/3f8011f01004be1ec2ef937643c1b6f9.js"></script>
</details><br>

<details>
<summary>Narrative manager</summary>
Any time the player triggers a trigger or uses an interactive object, the persistent narrative manager checks if a) that actor is a narration actor and b) the game is not ready for narration. If both of those are true, the player can't use the item/trigger the trigger. The second condition is based on whether the player is in combat and whether narration is already playing. If the actor is a narration actor and the game is ready for narration, the game mode sends an event with the name of the actor. Audio can use that name to play the right audio event, and the HUD can pass that name to the text manager to get the appropriate subtitle. Meanwhile, player input is disabled. When the audio is finished playing, the audio engine can call a function that will re-enable player input and tell the HUD to remove the subtitle.
</details><br>

<details>
<summary>Lock-on targeting</summary>
<br>
<script src="https://gist.github.com/samuelschimmel/cc769718f7a05b23aa3203618fa98ed1.js"></script>
</details><br>

<details>
<summary>Options menu backend</summary>
I made a derived class of GameUserSettings and edited DefaultEngine to use it. I also made a class with static blueprint callable functions for communication with an options menu. This allows for game options like difficulty, invert mouse, show objective locator, etc. When options are updated, the changes are reflected in-game and saved to a file. I also added a function which takes a string and returns a copy with actions/axes in square brackets (case insensitive) replaced with the first key currently bound to that action/axis. This allows tutorials and UI to avoid hardcoding rebindable inputs. I also added functions for rebinding keys that remove any previous bindings.
</details><br>

<details>
<summary>Player modeling</summary>
Player modeling is a form of indirect adaptation that involves recording player behavior and using the resulting data to customize the gameplay experience. I used it for dynamic difficulty, dynamic tutorials, and weighted random item spawning.
<br><br>
<script src="https://gist.github.com/samuelschimmel/eaf4a9f4766c7ac291da34f6430805f6.js"></script>
</details><br>

<details>
<summary>Player modeling: dynamic difficulty</summary>
Dynamic difficulty is driven by the player’s “performance” moving average, which is recalculated at the end of every player modeling interval based on moving averages of damage dealt and damage taken. Moving averages are ideal for dynamic difficulty because they represent recent behavior – each new observation has the same weight regardless of sample size, and old observations don’t continue to skew data long after the player’s behavior has changed. The moving average is given as:
<br><br>
<img src="https://tex.s2cms.ru/svg/%24%24movingAverage%20%3D%20%5Calpha%20*%20newObservation%20%2B%20(1%20%E2%80%93%20%5Calpha)%24%24" />
<br><br>
α, the learning rate, is usually 0.05 if changes are common, or 0.01 if changes are rare. The performance moving average is used to calculate a player damage multiplier. I considered also having an enemy damage multiplier, but decided this would be too noticeable for players. In different games, the performance moving average could influence all kinds of variables, including item drops, enemy spawns, enemy reaction times, and enemy perception.
<br><br>
<script src="https://gist.github.com/samuelschimmel/7aca0ad39175844099e78867d09a8185.js"></script>
</details><br>

<details>
<summary>Player modeling: dynamic tutorials</summary>
At periodic intervals while the player is alive and not in combat, player modeling determines which action the player has performed the least, and displays a tutorial for that action. It will only display one tutorial per action per level. Tutorials that teach controls are responsive to key rebinding. Player modeling also tracks weapon and item pickups in order to display tutorials the first time they are acquired. These tutorials don’t conflict with the tutorials that play the first two times weapons of any type are picked up (i.e., “press LMB to fire” and “use the scroll wheel to switch weapons”).
<br><br>
<script src="https://gist.github.com/samuelschimmel/45280472ac09502055ca29ab53845411.js"></script>
</details><br>

<details>
<summary>Player modeling: weighted random item spawning</summary>
Enemies spawned without weapons are assigned a weighted random weapon that the player has used before but has been using less recently. At the end of each player modeling interval, after updating damage dealt moving averages for each weapon, I sum these moving averages, then divide each moving average by the sum and subtract the quotient from 1. This gives the probability of each weapon being the next weapon to spawn with a new enemy. Weapons the player has been using a lot recently have lower probabilities, and weapons the player hasn’t been using as much recently have higher probabilities.
<br><br>
<script src="https://gist.github.com/samuelschimmel/e8d2ab14953ddc998e06ed9489296670.js"></script>
</details><br>

<details>
<summary>Player targeting</summary>
The player targeting system uses a wide sphere sweep for agents and weapons, and a narrow sphere sweep for non-weapon interactive objects. This makes it easier to pick up weapons, melee enemies, perform takedowns, or lock-on to agents while in combat, while reducing the likelihood of players accidentally activating quest objects. This system is also responsible for detecting whether the player has just started or stopped facing an obstacle, so that the appropriate first person animation (i.e., raising or lowering the player's weapon) can be played.
<br><br>
<script src="https://gist.github.com/samuelschimmel/fdf19a98ca4247fd2643f2b3130cd109.js"></script>
</details><br>

<details>
<summary>Quest system</summary>
The quest manager supports multiple simultaneous sets of objectives, each with their own separate objective locators. The quest system can handle objectives being destroyed early.
<br><br>
<script src="https://gist.github.com/samuelschimmel/cd15bcb5213e3ead37c5e180c4b9f50a.js"></script>
</details><br>

<details>
<summary>Radial damage</summary>
<br>
<script src="https://gist.github.com/samuelschimmel/938c3645a8141f49dfcd36a404536c32.js"></script>
</details><br>

<details>
<summary>Rifle scope</summary>
<br>
<script src="https://gist.github.com/samuelschimmel/401eed69335b95aaa72f445065ae4490.js"></script>
</details><br>

<details>
<summary>RPG mechanics</summary>
The stat system supports multiple tiers of stats (e.g., tier 0 for player level, tier 1 for attributes, tier 2 for skills, and tier 3 for perks). Stats can have parent stats like in Shadowrun (i.e., your rifle skill level can’t exceed your ranged combat skill level). Players are awarded points for each tier. When the player attempts to level up a stat, the stat’s max level is checked, the parent stat’s level is checked, and their points in that tier are checked. Leveling up can award points for other tiers. Stat levels can be queried elsewhere in the code. For example, the player’s firearm skill is used to calculate the spread of each shot.
</details><br>
