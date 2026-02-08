# The West Village Wiener Dash

A Subway Surfers-style 3-lane endless runner game featuring a dachshund (wiener dog) running along the West Side Highway in NYC.

## Project Overview

This is a single-page HTML5 canvas game with vanilla JavaScript. The entire game is contained in `index.html`.

### Technology Stack

- **HTML5 Canvas** for rendering
- **Vanilla JavaScript** for game logic
- **Lottie Web** for animated particle effects
- **Fredoka font** from Google Fonts for UI

## Game Mechanics

### Core Gameplay

- **3-lane runner**: Player controls a dachshund that can move between 3 lanes
- **Controls**:
  - Arrow keys or A/D for lane changes
  - Up arrow/W or Space to jump (dodge ground obstacles)
  - Down arrow/S to slide (dodge air obstacles)
  - Tap/swipe on mobile
- **Duration**: 60-second run
- **Objective**: Collect items, avoid obstacles, find all 5 Smiskis

### Collectibles

- **Tennis Ball**: Speed boost + 100 points
- **Fashion Magazine**: 200 points
- **Yoga Mat**: Invincibility shield (4 seconds) + 100 points
- **Chili Pepper**: Magnet effect (5 seconds) + 100 points
- **Smiski**: Rare collectible, 500 points each, 5 total to find

### Obstacles

- Taxi cabs
- Meeting groups
- Runners
- Frogs
- Ducks

## Visual Layout

### Scene Composition (Left to Right)

1. **NYC Skyline Silhouette** (far left horizon) - includes Freedom Tower
2. **City Buildings** - 3D perspective buildings with windows
3. **Sidewalk Strip** - between highway and buildings
4. **Highway** - with traffic moving north (toward camera)
5. **Green Median** - separating highway from bike path
6. **Bike Path** - scenery element
7. **Sidewalk** - between bike path and running path
8. **Running Path** (CENTER) - the main gameplay area with 3 lanes
9. **Railing** - separating path from river
10. **Hudson River** - with animated wave ripples
11. **Statue of Liberty** (far right horizon)

### Perspective System

- `VANISH_X = W/2` (400) - center of screen
- `VANISH_Y = 180` - horizon line height
- `FOCAL = 300` - focal length for 3D projection
- `DOG_Z = 80` - fixed Z position for the dog character
- `MAX_Z = 2000` - far clipping distance

### Key Drawing Functions

- `drawSky()` - Sky gradient, clouds, sun glow, NYC skyline, Statue of Liberty
- `drawRoad()` - All ground surfaces with proper perspective
- `drawBuilding()` - 3D projected city buildings and piers
- `drawDog()` - Main character with running animation
- `drawObstacle()` - Various obstacle types
- `drawCollectibleObj()` - Power-ups and collectibles

## Game States

1. **TITLE** - Start screen with animated title and "Tap to Start"
2. **PLAYING** - Main gameplay
3. **FINALE** - Transition scene after 60 seconds
4. **DONE** - Final apartment scene with Smiski shelf display

## File Structure

```
wiener-dash/
├── index.html          # Main game file (all code)
├── CLAUDE.md           # This documentation
├── images/
│   ├── 4-charles.jpg   # Landmark billboard
│   ├── apollo.jpeg     # Apollo Bagels landmark
│   ├── bagel-pub.jpeg  # Bagel Pub landmark
│   ├── google-sjt.jpg  # Google office landmark
│   ├── johns.jpeg      # John's Pizza landmark
│   ├── quique-crudo-logo.jpeg  # Restaurant landmark
│   ├── si-dachshunds.png       # SI cover for apartment
│   ├── smiski.png      # Smiski character image
│   └── tashkent.jpeg   # Tashkent Market landmark
└── lottie/
    ├── glow.json       # Smiski glow effect
    ├── sparkle.json    # Collection sparkle effect
    ├── speed-lines.json # Speed boost effect
    └── shield-glow.json # Invincibility shield effect
```

## Constants & Colors

Key color constants in `COL` object:

- `river`, `riverLight`, `riverDark` - Hudson River blues
- `skyline`, `skylineLight` - NYC silhouette colors
- `runningPath` - Reddish-brown track color (#A1887F)
- `pink`, `pinkLight` - UI accent colors
- `smiski` - Mint green for Smiski items (#A8D8A8)

## Running the Game

The game is served via a local HTTP server:

```bash
python3 -m http.server 8080
```

Then visit: http://localhost:8080
