---
layout: page
title: Woe to the Vanquished
permalink: /projects/wttv/
---

Coming December 2018
<br>Unreal Engine 4
<br>Inspired by <em>DOOM</em>, <em>The Last of Us</em>, and Arkane Studios

<h2><strong>Responsibilities</strong></h2>

Implemented combat gameplay, AI, object interaction, inventory system, objective system, and feedback in C++

Emphasized inheritance to reuse code and ensure substitutability of agents and interactive objects

Used deserialization to make gameplay systems data-driven, customizable, and transparent for designers

Supported extension of C++ classes in Blueprint using dynamic multi-cast delegates

Developed a player modeling system to provide dynamic difficulty and tailor item spawns to player preferences

Developed extensive debug features, including a gameplay analytics HUD and serialization of analytics after playtest sessions

Authored technical documentation and contributed to UX design documentation

<h2><strong>Selected code contributions</strong></h2>

[Player modeling system](https://github.com/samuelschimmel/contraband/blob/master/Actor/Info/PlayerModeling/PlayerModeling.cpp)<br>
[AI controller](https://github.com/samuelschimmel/contraband/blob/master/Actor/Controller/AIController/AgentAIController/AgentAIController.cpp)<br>
[AI positioning algorithm](https://github.com/samuelschimmel/contraband/blob/master/BTNode/BTTaskNode/BTTask_BlackboardBase/FindAttackLocation.cpp)<br>
[AI targeting algorithm](https://github.com/samuelschimmel/contraband/blob/e6719f881c7c3e1bf8d689961398ea0f1573fd78/Actor/Pawn/Character/Agent/Agent.cpp#L1124-L1199)<br>
[AI weighted random firearm selection algorithm](https://github.com/samuelschimmel/contraband/blob/e6719f881c7c3e1bf8d689961398ea0f1573fd78/Actor/Pawn/Character/Agent/Enemy/Enemy.cpp#L60-L111)<br>
[Gaussian random shot grouping](https://github.com/samuelschimmel/contraband/blob/e6719f881c7c3e1bf8d689961398ea0f1573fd78/Actor/InteractiveObject/Firearm/Firearm.cpp#L283-L317)<br>

<h2><strong>Behavior trees</strong></h2>

![]({{ "/assets/wttv/BT_Fight.png" | absolute_url }})

<h2><strong>Documentation contributions</strong></h2>

<iframe src="/assets/wttv/docs.pdf" width="100%" height="400"></iframe>

<h2><strong>Player modeling paper for CS 380</strong></h2>

<iframe src="/assets/wttv/PlayerModeling.pdf" width="100%" height="400"></iframe>
