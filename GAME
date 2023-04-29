#Создай собственный Шутер!

from pygame import *
from random import randint
from time import time as timer
class Gamesprite(sprite.Sprite):
    def __init__(self, player_image, player_x, player_y, player_speed, size_x, size_y):
        super().__init__()
        self.size_x = size_x
        self.size_y = size_y
        self.image = transform.scale(image.load(player_image), (size_x, size_y))
        self.speed = player_speed
        self.rect = self.image.get_rect()
        self.rect.y = player_y
        self.rect.x = player_x
    def reset(self):
        win.blit(self.image,(self.rect.x, self.rect.y))

class PLAYER(Gamesprite):
    def update(self):
        key_pressed = key.get_pressed()
        if key_pressed[K_DOWN] and self.rect.x < win_width -80:
            self.rect.y += self.speed
        if key_pressed[K_UP] and self.rect.x < 5:
            self.rect.y -= self.speed
    def update2(self):
        key_pressed = key.get_pressed()
        if key_pressed[K_a] and self.rect.x < win_width -80:
            self.rect.y += self.speed
        if key_pressed[K_z] and self.rect.x > 5:
            self.rect.y -= self.speed




i_e = 'mach.PNG'
i_p1 = 'ROCKET.PNG'
i_p2 = 'ROCKET_2.PNG'

score = 0
lost = 0
max_lost = 200
goal = 10
rel_time = 3
shoot_bul = 7
speed_x = 3
speed_y = 3




display.set_caption("PING PONG")
win_height = 900
win_width = 900
win = display.set_mode((win_height,win_width))
background = transform.scale(image.load('POLE.PNG'), (1100,900))



pl = PLAYER(i_p1, 60, 320, 12, 50, 160)
pl2 = PLAYER(i_p2, 810, 320, 12, 50, 160)
ball = Gamesprite(i_e, 300, 400, 3, 78, 75)





font.init()
font = font.SysFont('Arial', 80)
win_q = font.render('VICTORY', True, (224, 67, 56))
lose = font.render('YOU LOSE!', True, (224, 67, 56))






finish = False
game = True
clock = time.Clock()
FPS = 60
while game:
    if finish != True:
        ball.rect.x += speed_x
        ball.rect.y += speed_y
    for e in event.get():
        if e.type == QUIT:
            game = False
    if not finish:
        win.blit(background,(0,0))
        text = font.render('Счёт' + str(score), True, (34, 88, 98))
        win.blit(text, (10,20))


    if sprite.collide_rect(pl2, ball) or (pl, ball):
        ball.rect.x *= -1
        ball.rect.y *= -1


    pl.update()
    pl2.update2()
    ball.update()

    pl.reset()
    pl2.reset()
    ball.reset()



    display.update()
    clock.tick(FPS)
quit()
