# Implementation Brief: Polished Snake Game in a Single HTML File

## Overview
Create a complete, fully functional, and highly polished Snake game contained entirely within a single, self-contained HTML file named `index.html`. The game must be playable on both desktop and mobile devices, feature a modern visual design, and require strictly no external dependencies (no external CSS, JS libraries, or remote assets like fonts or images).

## 1. File & Output Constraints
*   **File Name:** The output must be exactly one file named `index.html`.
*   **Self-Contained:** All HTML, CSS, and JavaScript must be embedded within this single file.
*   **Zero Dependencies:** Do not use React, Vue, jQuery, Bootstrap, Tailwind, or any other framework/library. Do not link to external fonts, icons, or images. Everything must be implemented with plain HTML, inline `<style>`, and inline `<script>`.
*   **Asset Free:** Use Canvas API or DOM elements for rendering. If icons or images are strictly necessary, use inline SVG or base64 data URIs.

## 2. Gameplay Rules & Mechanics
*   **Grid System:** The game takes place on a 2D grid. The snake and food snap to the grid cells.
*   **Initial State:** The snake starts with a length of 3 segments, positioned near the center of the grid, moving initially to the right.
*   **Movement:** The snake moves automatically in the current direction. It cannot instantly reverse direction (e.g., if moving right, it cannot immediately move left).
*   **Food:** A single piece of food appears at a random, unoccupied grid coordinate. When the snake's head occupies the same cell as the food, the snake eats it.
*   **Growth:** Eating food increases the snake's length by 1 segment.
*   **Increasing Speed:** The game must start at a manageable speed. For every 5 pieces of food eaten, the game speed (movement interval) should increase by a noticeable but fair amount, capping at a maximum speed.
*   **Collision Behavior (Game Over):**
    *   **Wall Collision:** The game ends if the snake's head hits or moves beyond the boundaries of the grid.
    *   **Self Collision:** The game ends if the snake's head collides with any part of its own body.

## 3. Controls (Keyboard & Touch)
*   **Desktop (Keyboard):**
    *   Arrow Keys (`ArrowUp`, `ArrowDown`, `ArrowLeft`, `ArrowRight`) to change direction.
    *   `W`, `A`, `S`, `D` as alternative directional controls.
    *   `Space` to pause/resume the game, and to restart when on the Game Over screen.
*   **Mobile (Touch):**
    *   Implement on-screen directional buttons (D-pad) or a swipe gesture detection system on the game board to control the snake.
    *   Provide on-screen buttons for Pause/Resume and Restart.

## 4. UI/UX & Visual Design
*   **Responsive Layout:** The game canvas/board must scale to fit nicely on both desktop monitors and mobile screens, preserving a square or fixed aspect ratio for the play area. Use a CSS Flexbox or Grid layout to center the game.
*   **Visual Style:**
    *   Use a modern, clean color palette (e.g., dark mode theme: dark gray background, bright green snake, bright red food).
    *   The snake head should be visually distinct from the body segments (e.g., slightly darker color, or rounded corners if using DOM/Canvas paths).
    *   Add a subtle grid line background to help players judge distance.
*   **Screens/States:**
    *   **Start Screen:** Display the game title, high score, and a "Press Space or Tap to Start" instruction.
    *   **Playing State:** Show the active game board, current score, and high score.
    *   **Paused State:** Dim the game board and display a clearly visible "PAUSED" overlay.
    *   **Game Over Screen:** Display "Game Over", the final score, whether a new high score was reached, and a "Play Again" button/instruction.

## 5. Scoring & Persistence
*   **Scoring:** Each piece of food eaten awards 10 points.
*   **High Score:** Track the highest score achieved.
*   **Persistence:** Save the high score to the browser's `localStorage` so it persists across page reloads.

## 6. Accessibility & Browser Compatibility
*   **Accessibility:** Add `aria-labels` to interactive on-screen buttons. Ensure sufficient color contrast between text/UI elements and the background.
*   **Browser Compatibility:** The game must run flawlessly on the latest versions of Chrome, Firefox, Safari, and Edge. Use standard ES6+ JavaScript, standard HTML5 Canvas/DOM, and standard CSS3.

## 7. Deterministic Testable Acceptance Criteria
1.  **Constraint Check:** The delivery consists of exactly one file, `index.html`, which opens locally without fetching external resources.
2.  **Start State:** Upon opening `index.html`, the Start screen is visible.
3.  **Initiation:** Pressing Space or tapping the screen transitions to the Playing state, and the snake begins moving.
4.  **Directional Control Check:** Pressing 'ArrowDown' changes the snake's direction downwards. Subsequent 'ArrowUp' presses are ignored (no immediate reverse).
5.  **Food Collection:** When the snake head coordinates match the food coordinates, the score increases by 10, the snake length increases by 1, and the food relocates to a random empty cell.
6.  **Speed Increase Check:** After the score reaches 50, the time interval between snake movements is measurably shorter than at score 0.
7.  **Wall Collision Check:** When the snake's head x/y coordinates exceed the grid boundaries, the Game Over screen appears immediately.
8.  **Self Collision Check:** When the snake's head coordinates match any of its body segment coordinates, the Game Over screen appears immediately.
9.  **High Score Persistence:** Achieving a score of 20, dying, and refreshing the page displays a high score of 20 on the Start screen.
10. **Pause/Resume Check:** Pressing Space during gameplay pauses the snake's movement and shows the Pause overlay. Pressing Space again resumes movement.
