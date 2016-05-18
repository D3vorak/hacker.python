# hacker.python
# simple game with python #

import pygame
pygame.init()
from pygame.locals import *

tela = (500, 500)
screen = pygame.display.set_mode(tela, 0, 32)

man = pygame.image.load("/root/python/intro/bart.png")# this will depenter where 'll be saving your images #
keys = [False, False, False, False]
player = [200, 100]
velocidade = 0.5

while True:
    screen.blit(man, player)
    pygame.display.flip()
    screen.fill(0)
    pygame.draw.polygon(screen ,(0, 255,0), ( (10, 250), (250, 110), \
(500, 250), (250, 390), (10, 250)), 0)
    pygame.draw.line(screen, (170, 150, 0), (9, 270), (250, 410), 42)
    pygame.draw.line(screen, (100, 80, 0), (250,410), (499, 270),42)

    casa = pygame.image.load("/root/python/intro/casa.png")
    screen.blit(casa, (30, 180) )
    lua = pygame.image.load("/root/python/intro/lua/lua.jpeg")
    screen.blit(lua, (1, 1) )


    for event in pygame.event.get():
        if event.type == pygame.KEYDOWN:
            if event.key == K_w:
                keys[0] = True
            elif event.key == K_a:
                keys[1] = True
            elif event.key == K_s:
                keys[2] = True
            elif event.key == K_d:
                keys[3] = True
        if event.type == pygame.KEYUP:
            if event.key == pygame.K_w:
                keys[0] = False
            elif event.key == pygame.K_a:
                keys[1] = False
            elif event.key == pygame.K_s:
                keys[2] = False
            elif event.key == pygame.K_d:
                keys[3] = False
    if keys[0]:
        player[1] -= velocidade
    elif keys[2]:
        player[1] +=velocidade
    if keys[1]:
        player[0] -= velocidade
    elif keys[3]:
        player[0] +=velocidade
    if event.type == pygame.QUIT:
        pygame.quit()
        exit(0)
