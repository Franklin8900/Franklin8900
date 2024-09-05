import pygame
import random

# Inicializar pygame
pygame.init()

# Configuración del juego
WIDTH, HEIGHT = 640, 480
NUM_PIECES = 9

# Cargar imagen de fondo
background_image = pygame.image.load('background.png')

# Crear piezas de puzzle
pieces = []
for i in range(NUM_PIECES):
    piece_image = pygame.image.load(f'piece_{i}.png')
    piece_rect = piece_image.get_rect()
    piece_rect.x = random.randint(0, WIDTH - piece_rect.width)
    piece_rect.y = random.randint(0, HEIGHT - piece_rect.height)
    pieces.append((piece_image, piece_rect))

# Crear ventana del juego
screen = pygame.display.set_mode((WIDTH, HEIGHT))

# Bucle principal del juego
while True:
    # Manejar eventos
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            pygame.quit()
            sys.exit()

    # Dibujar fondo y piezas
    screen.blit(background_image, (0, 0))
    for piece in pieces:
        screen.blit(piece[0], piece[1])

    # Actualizar pantalla
    pygame.display.flip()
