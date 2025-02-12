# InSem1Project

### Group Name : Titans
### Name : Tanvi Nakum
### Student ID : 202401262

# "THE SNAKE GAME" 

## Table of Contents
- [Introduction](#introduction)
- [Game Components](#game-components)
  - [Snake Representation](#snake-representation)
  - [Food Generation](#food-generation)
  - [Game Board](#game-board)
  - [User Input and Movement](#user-input-and-movement)
- [Controls](#controls)
- [Collision Detection](#collision-detection)
- [Score Tracking](#score-tracking)
- [Game Loop and Logic](#game-loop-and-logic)
- [Requirements](#requirements)
- [Compilation and Execution](#compilation-and-execution)
- [Screenshot](#screenshot)
- [Conclusion](#conclusion)
- [License](#license)

## Introduction
The Snake Game is a classic arcade game where the player controls a
snake that grows in size as it consumes food. The game ends if the snake
collides with itself or the boundaries of the play area. The game starts with a snake with 3 cells in length, and as the player progresses, the difficulty increases as the snake grows longer, making movement more challenging.

## Game Components
The game consists of several key components that contribute to its functionality and gameplay experience.

### Snake Representation
The snake is represented as a linked list, where each node stores the position (x, y) of a part of the snake's body. The head of the list represents the current position of the snake's head, and new segments are added as food is consumed. This structure allows for easy movement and growth of the snake without requiring complex data management.

### Food Generation
Food is randomly generated on the grid at an empty location that is not occupied by the snake. The game ensures that the food does not appear at a position already occupied by the snake. When the snake consumes the food, it grows in length by 1, increasing the difficulty of movement, and new food is generated at another random location.

### Game Board
The game board defines the playing field dimensions. It consists of a bounded area where the snake moves. The boundaries of the board serve as obstacles, and the snake must navigate within these limits without colliding into the walls. The size of the board can be adjusted.

### User Input and Movement
The game captures user input to control the movement of the snake. The snake can move in four directions: left, right, up, and down. The movement must be continuous, meaning the snake moves in the chosen direction until a new input is received. Additionally, the snake cannot reverse its direction immediately to prevent unintended game-ending moves.

## Controls
The game is controlled using the following keys:

- l - Move Left
- r - Move Right
- u - Move Up
- d - Move Down
- t - Terminate the game
- Eat the food '*' to grow longer and increase your score.

## Collision Detection
Collisions occur when the snake either runs into the boundaries of the board or collides with itself. If a collision is detected, the game ends, and the final score is displayed. This mechanism ensures that the game remains challenging as the snake grows in size, making self-collision more likely.

## Score Tracking
The game keeps track of the score, which increases whenever the snake consumes food. The score is directly proportional to the length of the snake, meaning the longer the snake grows, the higher the player's score.

## Game Loop and Logic
The game operates within a loop that continuously updates the game state. The loop consists of the following stages:

1. Rendering the game board and displaying the snake and food to ensure a dynamic visual representation.
2. Capturing user input to determine the movement direction of the snake.
3. Updating the snake's position, handling food consumption, and growing the snake accordingly.
4. Checking for collisions with the walls or itself, and terminating the game if necessary.

The loop continues until the player either decides to quit or the game ends due to a collision.

## Requirements
To run this project, you need:
-A C++ compiler (e.g., g++, MinGW)
-A terminal
-Windows

## Compilation and Execution
To compile the program, use a C++ compiler like g++:

g++ InSem1Project.cpp -o InSem1Project

Run the executable:

./InSem1Project

## Screenshot
Below is a screenshot of the game:

![Snake Game Screenshot](Screenshot%202025-02-10%20185727.png)

## Conclusion
The Snake game is a simple yet engaging project that demonstrates fundamental programming concepts such as linked lists, input handling, collision detection, and game loops. This game serves as an excellent introduction to game development and logical thinking in programming.

## License
This project is released under the MIT License, allowing for open-source usage and modification. Users are free to modify and distribute the game as long as proper credit is given to the original creator.
