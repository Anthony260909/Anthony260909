import pygame
import random

# Initialisation de Pygame
pygame.init()

# Configuration de la fenêtre du jeu
win_width = 800
win_height = 600
win = pygame.display.set_mode((win_width, win_height))
pygame.display.set_caption("Hill Climb Racing Clone")

# Définition des couleurs
white = (255, 255, 255)
black = (0, 0, 0)


# Classe pour la voiture du joueur
class Car:
    def __init__(self, x, y):
        self.x = x
        self.y = y
        self.width = 50
        self.height = 30
        self.velocity = 5

    def draw(self):
        pygame.draw.rect(win, black, (self.x, self.y, self.width, self.height))

# Fonction principale du jeu
def main_game():
    run = True
    car = Car(400, 300)

    while run:
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                run = False

        keys = pygame.key.get_pressed()
        if keys[pygame.K_LEFT]:
            car.x -= car.velocity
        if keys[pygame.K_RIGHT]:
            car.x += car.velocity

        # Rafraîchissement de l'écran
        win.fill(white)
        car.draw()
        pygame.display.update()

    pygame.quit()

# Fonction de démarrage du jeu
def game_start():
    main_game()

# Démarrage du jeu
game_start()
