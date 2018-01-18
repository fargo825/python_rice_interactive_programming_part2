# python_rice_interactive_programming_part2
# _*_ coding:utf-8 _*_

import SimpleGUICS2Pygame.simpleguics2pygame as simplegui
import math
# global variable
width = 300
height = 300
ball_position = [width/2, height/2]
ball_radius = 20
ball_color = 'red'

# helper-function
def distance(p,q):
    return math.sqrt((p[0]-q[0])**2+(p[1]-q[1])**2)

def mouse_handler(pos):
    global ball_position,ball_color


    if distance(ball_position,pos) < ball_radius:
        ball_color = 'green'
    else:
        ball_color = 'red'
        ball_position = list(pos)


def draw_handler(canvas):
    canvas.draw_circle(ball_position, ball_radius, 1, 'yellow', ball_color)





frame = simplegui.create_frame('mouse input',width,height)
frame.set_canvas_background('white')

# 注册函数
frame.set_draw_handler(draw_handler)
frame.set_mouseclick_handler(mouse_handler)

frame.start()

