# Runing
Best game of runing 
import pygame
import sys

# Initialize Pygame
pygame.init()

# Game Constants
WIDTH, HEIGHT = 500, 500
BG_COLOR = (30, 30, 30)
PLAYER_COLOR = (0, 255, 0)
PLAYER_SIZE = 40
SPEED = 5

# Setup Screen
screen = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption("Simple 2D Game")

# Player Setup
player = pygame.Rect(WIDTH//2, HEIGHT//2, PLAYER_SIZE, PLAYER_SIZE)

# Game Loop
running = True
while running:
    pygame.time.delay(30)
    
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False
    
    keys = pygame.key.get_pressed()
    if keys[pygame.K_LEFT] and player.x > 0:
        player.x -= SPEED
    if keys[pygame.K_RIGHT] and player.x < WIDTH - PLAYER_SIZE:
        player.x += SPEED
    if keys[pygame.K_UP] and player.y > 0:
        player.y -= SPEED
    if keys[pygame.K_DOWN] and player.y < HEIGHT - PLAYER_SIZE:
        player.y += SPEED
    
    screen.fill(BG_COLOR)
    pygame.draw.rect(screen, PLAYER_COLOR, player)
    pygame.display.update()
    
pygame.quit()
sys.exit()
