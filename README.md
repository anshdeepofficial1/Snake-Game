# Snake-Game

## Overview

This project is a simple, console-based Snake game implemented in C. The code demonstrates basic game programming concepts such as a game loop, real-time input handling, collision detection, and dynamic state management. The game utilizes a text-based interface where the snake, fruit, and boundaries are rendered using simple characters.

## Key Features

- **Game Initialization:**  
  Initializes the snake and fruit positions along with the initial score. The snake starts at the center of the board, and the fruit is placed at a random position.

- **Game Rendering:**  
  Uses the `Draw()` function to render the game board in the terminal. It draws the top and bottom borders, side walls, the snake’s head (using 'O'), tail segments (using 'o'), and the fruit (using 'F').

- **Input Handling:**  
  Processes keyboard inputs in real time using the `_kbhit()` and `_getch()` functions from `conio.h`. The controls are:
  - `'a'` for moving left  
  - `'d'` for moving right  
  - `'w'` for moving up  
  - `'s'` for moving down  
  - `'x'` to exit the game
  - `'r'` to restart the game

- **Game Logic:**  
  Updates the snake’s position based on user input, manages the tail by shifting previous positions, handles game boundary wrap-around (so the snake reappears on the opposite side), and detects collisions with the fruit or itself.

- **Score Management:**  
  The score increases by 10 each time the snake eats a fruit. The tail's length increases upon eating a fruit, adding to the challenge.

- **Game Loop:**  
  The `main()` function continuously loops until the game-over condition is met. Within each iteration, it clears the screen, draws the updated game board, processes input, performs game logic updates, and slows down the game using `Sleep()`.

## Step-by-Step Explanation

1. **Initialization (`Setup()`):**  
   - The snake's starting position is set at the center of the board (`x = WIDTH / 2; y = HEIGHT / 2`).
   - A fruit is randomly positioned on the board using the `rand() % WIDTH` and `rand() % HEIGHT` functions.
   - The game score is initialized to zero.

2. **Rendering the Game (`Draw()`):**  
   - The screen is cleared using `system("cls")` to update the display.
   - The top border is drawn using a loop to print `#` characters.
   - For each row:
     - A left border is printed.
     - Each cell is checked:
       - The snake’s head is printed if the current coordinates match the snake's `x` and `y`.
       - The fruit is printed if the current coordinates match `fruitX` and `fruitY`.
       - The tail segments are printed if any of the stored tail coordinates match.
       - An empty space is printed if none of the above conditions are met.
     - A right border is printed at the end of the row.
   - A final bottom border is drawn, and the current score is displayed.

3. **Handling User Input (`Input()`):**  
   - The function checks if a key press is available using `_kbhit()`.
   - Based on the pressed key (`'a'`, `'d'`, `'w'`, `'s'`, or `'x'`), the direction of the snake is updated or the game is exited.

4. **Game Logic Processing (`Logic()`):**  
   - The snake’s tail positions are updated by saving the previous position and shifting tail coordinates.
   - The snake's new head position is calculated based on the current direction.
   - Wrap-around logic makes the snake reappear on the opposite edge when it goes off the board boundaries.
   - Collision detection checks if the snake’s head touches any of its tail segments, which would set the `gameOver` flag.
   - If the snake reaches the fruit, the score increments by 10, the fruit is repositioned, and the tail length increases.

5. **Main Game Loop (`main()`):**  
   - The game is initialized by calling `Setup()`.
   - Inside a continuous loop (while `!gameOver`):
     - The game board is drawn.
     - User input is captured.
     - Game logic updates are applied.
     - The loop pauses briefly using `Sleep(10)` to control the game speed.
   - When the game-over condition is reached, a final score is printed.

## Support Development

This project is free and open source. If you find it useful, you can support continued development through:

- [GitHub Sponsors](https://github.com/sponsors/anshdeepofficial)
- [Buy Me a Coffee](https://buymeacoffee.com/anshdeepofficial)
