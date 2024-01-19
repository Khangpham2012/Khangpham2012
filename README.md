import pygame
import sys

# Initialize Pygame
pygame.init()

# Constants
WIDTH, HEIGHT = 800, 600
BLOCK_SIZE = 40
WHITE, BLACK, RED = (255, 255, 255), (0, 0, 0), (255, 0, 0)

# Initialize game window
window = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption("Block Builder")

# Create a grid for blocks
blocks = [[0] * (WIDTH // BLOCK_SIZE) for _ in range(HEIGHT // BLOCK_SIZE)]

# Main game loop
running = True
while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False
        elif event.type == pygame.MOUSEBUTTONDOWN:
            # Place a block where the mouse was clicked
            x, y = event.pos
            block_x, block_y = x // BLOCK_SIZE, y // BLOCK_SIZE
            if blocks[block_y][block_x] == 0:
                blocks[block_y][block_x] = 1

    # Draw the blocks
    window.fill(BLACK)
    for y, row in enumerate(blocks):
        for x, block in enumerate(row):
            if block == 1:
                pygame.draw.rect(window, WHITE, (x * BLOCK_SIZE, y * BLOCK_SIZE, BLOCK_SIZE, BLOCK_SIZE))

    # Update display
    pygame.display.flip()

# Quit the game
pygame.quit()
sys.exit()


<!---
Khangpham2012/Khangpham2012 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
