---
title: Trimester 3 Individual Report
layout: post
description: Trimester 3 Individual Report
permalink: /individual_report
toc: true
comments: true
---

# Game Development Commit Summary (May 2025)

## Road & Racing Games

- **Fixed Player Positioning in Road Game**  
  Corrected how the player’s car aligns with the road and other vehicles. Ensured it stays on track and doesn’t start off-screen or collide immediately.

- **Tweaked Racing Path and Gameplay**  
  Improved the layout of the race track. Made racing smoother and ensured the path curves or boundaries were better defined.

- **Added Full Racing Game**  
  Introduced the racing mechanics. Likely added collision detection, lap tracking, and speed control.  
  ```js
  player.x += speed;
  if (player.x > finishLine) {
    winGame();
  }
  ```

## Pack Opening Game

- **Fixed Bugs in the Pack Game**  
  Addressed issues like packs not opening correctly, rewards not displaying, or visuals lagging behind logic.

- **Added Core Pack Opening Feature**  
  Players can now open packs to receive randomized cards or items. The system selects a card from a list.  
  ```js
  const randomCard = cards[Math.floor(Math.random() * cards.length)];
  showCard(randomCard);
  ```

- **Linked Pack Game to Farming Game**  
  Balanced the rewards or functionality between the two. For example, pack items might affect farm stats or offer new seeds.

## Farming Game

- **Updated Visuals and Mechanics**  
  Refined crop animations and added clearer stages of plant growth.

- **Farming Game Semi-Finished**  
  Most core features are in place: planting, growing, watering, and harvesting. Minor tuning might be left.  
  ```js
  if (waterLevel > 5) {
    crop.grow();
  }
  ```

## Mini Games and Features

- **Tower Defense-Inspired Balloon Game**  
  Added towers and balloon enemies. Likely included logic for towers attacking balloons as they pass.

- **Added Party Game**  
  Introduced a new mini-game possibly focused on group mechanics or random events.

- **Slot Machine Game Added**  
  Created logic to spin slots and provide rewards based on match combinations.  
  ```js
  const result = reels.map(reel => getRandomSymbol());
  displayResult(result);
  ```

- **Test Game Updates**  
  Built or revised a playground/test environment to check mechanics before applying them to full games.

- **Skirmish Game Fixes**  
  Cleaned up battle logic or interface issues in a combat-style mini-game.

- **Updated Building Block Game**  
  Improved how blocks are placed or moved. Might have fixed snapping or collision detection.

## NPCs and Dialogue

- **Updated NPC Logic**  
  NPCs respond more intelligently to player actions (like quests or item possession).  
  ```js
  if (player.hasItem("key")) {
    npc.say("You can open the gate!");
  }
  ```

- **Added Extra Dialogue**  
  Included new conversations or story progression through dialogue interactions.

- **Updated Index Page for NPC Features**  
  Made it easier to access or showcase NPC-related content in the main menu or home page.

## Crossy Road and Platformers

- **Fixed Crossy Road Game**  
  Adjusted traffic or player hit detection to make movement and deaths more consistent.

- **Removed Door from Platformer Game**  
  Possibly replaced with another exit method or removed due to bugs or confusion.

- **Adjusted Boss and Levels in Platformer**  
  Smoothed out level difficulty and made boss fights more balanced or interesting.

## Flappy Game

- **Flappy Game Added (Image Pending)**  
  Built a basic version of Flappy Bird-style gameplay. Core physics and controls likely work, with image updates pending.  
  ```js
  flappy.y += gravity;
  if (spacePressed) {
    flappy.jump();
  }
  ```

## Game Menus and Help System

- **Home Button Menu Added**  
  Allows players to return to a main menu easily.

- **Help System Introduced**  
  Added basic instructions, game guides, or tutorials for new players.

- **Updated World Help Pages**  
  More in-depth explanations or maps to help navigate game areas.

## Music and Audio

- **Changed Music Tracks**  
  Swapped out background music to better fit game moods or levels.

- **Added More Sounds**  
  SFX for interactions, actions, or events were included or improved.

## Gambling Game

- **Added Gambling Game**  
  Introduced mechanics for chance-based games. Could involve betting, winning coins, or unlocking rewards.

- **Updated Slot Location**  
  Moved where in the world or game UI players access the gambling or slot mini-game.

## World Map Updates

- **Added Visible Barrier to World 6**  
  Prevents players from walking into restricted or unfinished areas.

- **Adjusted World 8**  
  Changed layout or added new obstacles/enemies for gameplay balance.

## Adventure Game Series

- **Redesigned Level 1**  
  Refreshed the layout, objectives, and flow of the first level to make it clearer and more fun.

- **Fixed Mushroom Logic in Level 1**  
  Ensured mushrooms behave as intended—maybe bouncing or giving power-ups.

- **Objective System Introduced**  
  Players now get missions or clear goals.  
  ```js
  if (collectedItems.length === goal) {
    completeObjective();
  }
  ```

- **Updated to Adventure Game v3**  
  Iterated major version of the game with combined improvements across levels, UI, and logic.

## Cosmetic and UI Additions

- **New Cosmetics Added**  
  Players can customize their characters or UI with new outfits, colors, or items.

- **Index Page Updated**  
  Improved navigation or game listings for easier access to new features.
