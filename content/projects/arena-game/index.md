---
title: "Arena C++ Game"
icon: "https://user-images.githubusercontent.com/35240934/175382129-482ad244-5739-4485-b9e4-959cbe844422.png"
date: 2022-04-01
draft: false
project_tags: ["C++", "entt", "OpenGL", "Multithreading"]
summary: "A simple 16-bit arena game implemented in modern C++ that features a multithreaded Job System and an Entity Component System."
weight: 1
---

<div>
<video src="https://user-images.githubusercontent.com/35240934/175192721-d98a1925-aa89-469b-aa42-ffd87ef5b20d.mp4" autoplay="true" loop="true"></video>
</div>

## About

A simple 16-bit arena game implemented in modern C++ that features a multithreaded Job System and an Entity Component System.

This project is open-source, and <a href="https://github.com/PedroMartelleto/ModernCppGame">the code is available on Github</a>.


## How to play

The game only has one mode: two players in a 1v1. The player first moves with the WASD keys on the keyboard. By pressing the G key, player 1 starts preparing a projectile that can be thrown to damage opponents (monsters or other players). To aim the projectile, use the WASD keys on the keyboard. Player 2 has the same actions, but moves with the IJKL keys and shoots with P.

<img src="https://raw.githubusercontent.com/PedroMartelleto/ModernCppGame/master/Res/image11.png" />

<img src="https://raw.githubusercontent.com/PedroMartelleto/ModernCppGame/master/Res/image2.png" />

Periodically, monsters appear on the map. When a player comes into contact, the monster deals damage to the player. The player can shoot projectiles to kill the monsters. Also, projectiles can be used to shoot the other player, dealing damage.

<img src="https://raw.githubusercontent.com/PedroMartelleto/ModernCppGame/master/Res/image10.png" />

The player who survives the longest or who reduces their opponent's health to zero wins.


## Pathfinding

Pathfinding is the means by which enemies find the player. In general, these algorithms boil down to finding the least expensive path in a graph to get to point B, starting from point A. We can represent the "level" at which the player and enemies are by a graph that determines how to jump in order to reach the platforms. Using a pathfinding algorithm (in the game's case, A*), the enemy finds the shortest possible path between the enemy and its target.

<img src="https://raw.githubusercontent.com/PedroMartelleto/ModernCppGame/master/Res/image9.gif" />

The problem here is that the game is needs to be updated in real-time, since the position of the player and enemies changes (almost) every frame. That is, 60 times per second. We don't need to run the pathfinding algorithm every frame (since the positions of game objects don't change instantly), but every X frames we need to do pathfinding for N enemies. An algorithm that is not that complex ends up becoming a bottleneck, and it competes for CPU time with rendering, physics, and game logic. In fact, let's look at an extreme case: putting 80 enemies on the screen at the same time, and making them all search for the player in the graph, we spend between 26 and 46 ms every X frames with pathfinding! This is a lot since we want to render the game 60 times per second (so each frame should last a maximum of 16.6 ms).

<img src="https://raw.githubusercontent.com/PedroMartelleto/ModernCppGame/master/Res/image1.png" />


## Multithreading

To resolve the issue raised in [About pathfinding](#about-pathfinding), we can parallelize the A* pathfinding algorithm by using a [Job System](https://wickedengine.net/2018/11/24/simple-job-system-using-standard-c/). Including 80 enemies on the map, all running pathfinding algorithms in real time, we can still maintaining 60 frames per second without any trouble.
In fact, the parallelization decreased the pathfinding time from 32.8 ms to 0.37 ms!

<img src="https://raw.githubusercontent.com/PedroMartelleto/ModernCppGame/master/Res/image15.gif" />
<img src="https://raw.githubusercontent.com/PedroMartelleto/ModernCppGame/master/Res/image12.png" />