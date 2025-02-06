---
title: "July Pilota: Pila o Pelota?"
date: 2025-02-06
categories: fun-things
tags:
  - game-dev
  - pygame
  - side-scroller
---

Writting posts like this makes me feel like I’m channeling my inner autistic. 

I made a video game for my sister’s birthday **"July Pilota: Pila o Pelota?"**. It’s an arcade-style game built with Pygame, basically a side-scrolling game with my own custom visuals.

---

## **Screenshots**

![Game Screenshot 1](/assets/images/july_pilota_1.png)

---

![Game Screenshot 2](/assets/images/july_pilota_2.png)

---

## The Concept

At its core, "July Pilota" is a remix of runner and “flappy” games. You control a little plane that’s constantly on the move, dodging obstacles that pop up in your path. If you miss a gap, you’ll lose a try. 

I didn't want to use the word *lives* because it sounds scary given all the plane accidents happening lately. If you get to the end (depending on the difficulty you select), you trigger a hidden celebration screen.

I really enjoyed the customization aspect because I got to pick the aesthetics and sounds:
- The **spacebar sound**
- The **win sound**
- The **background music**
- The **randomly generated clouds**
- The **animated stars** ✨

---

## Game Mechanics & Logic

- **Smooth Physics**  
  The game simulates gravity and lift to give the plane a natural, floaty movement. When you hit the spacebar, the plane gets a quick burst of lift, but gravity is always lurking, pulling it back down—so timing is key.

- **Dynamic Obstacles**  
  Instead of a static course, obstacles appear at intervals, with a gap that steadily shrinks over time to up the ante. Every so often, a new obstacle is generated with randomized gap positions, making each playthrough uniquely challenging.

- **Score & Tries**  
  As you progress, your score increases gradually. You start with three tries, and each collision with an obstacle costs you one. When you’re out, the game ends with a game-over screen—but that’s just an invitation to try again. 😎

- **Animated Celebrations**  
  I really liked learning how to generate a GIF, split it into frames, and run that within Pygame. It was hard, but I’m glad I learned how to do it.

---

This was a cool thing to try, and I hope my sister enjoys it! 🎮
