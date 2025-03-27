import pygame

pygame.init()
width, height = 600, 400
win = pygame.display.set_mode((width, height))
clock = pygame.time.Clock()

tank_size = 40

tank1 = pygame.Rect(100, 100, tank_size, tank_size)
tank2 = pygame.Rect(400, 300, tank_size, tank_size)

def draw():
    win.fill((50, 50, 50))
    pygame.draw.rect(win, (0, 255, 0), tank1)
    pygame.draw.rect(win, (255, 0, 0), tank2)
    pygame.display.update()

def move_tank(keys, tank):
    if keys[pygame.K_w]: tank.y -= 5
    if keys[pygame.K_s]: tank.y += 5
    if keys[pygame.K_a]: tank.x -= 5
    if keys[pygame.K_d]: tank.x += 5

def main():
    run = True
    while run:
        clock.tick(30)
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                run = False

        keys = pygame.key.get_pressed()
        move_tank(keys, tank1)  # Управление первым танком

        draw()

    pygame.quit()

main()
