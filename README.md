import tkinter
import tkinter as tk
import random
from tkinter import PhotoImage


def move_by_keys(event):
    if event.keysym == 'Up':
        canvas.move(player,0,-20)
    elif event.keysym == 'Down':
        canvas.move(player,0,20)
    elif event.keysym == 'Left':
        canvas.move(player,-20,0)
    elif event.keysym == 'Right':
        canvas.move(player,20, 0)

def prepare_and_start():
    global player
    player_pos = (random.randint(0, N_X - 1) * step,
                  random.randint(0, N_Y - 1) * step)
    player = canvas.create_image((player_pos[0], player_pos[1]),
                                 image=player_pic,
                                 anchor='nw')
    canvas.delete("all")
    label.config(text="НАЙТИ ВЫХОД!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!")
    win.bind("<KeyPress>",move_by_keys)
def move_wrap(obj,move_x,move_y):
    xy=canvas.coords(obj)
    canvas.move(obj,move_x,move_y)
    print(xy)
    if xy[0]<=0:
        canvas.move(obj,WINDTH,0)
    if xy[0]>=WINDTH:
        canvas.move(obj,-WINDTH,0)
    if xy[1] <=0:
        canvas.move(obj,0,HEIGHT)
    if xy[1] >=HEIGHT:
        canvas.move(obj,0,-HEIGHT)

win=tkinter.Tk()
step=32
N_X=10
N_Y=10
WINDTH=step*N_X
HEIGHT=step*N_Y
a=False
player_pic=PhotoImage(file="K.png")
canvas=tkinter.Canvas(win,bg="#FCAB08",
                      width=WINDTH,height=HEIGHT)
player_pos=(random.randint(0,N_X -1)*step,
                random.randint(0,N_Y-1)*step)
label=tkinter.Label(win,text="НЕ ПОПАДИСЬ!!!!!!!!!!!!!")
restart=tkinter.Button(win,text="НАЧАТЬ ЗАНОВО!!!!!!!!!!!!!!!!!!",
                        command=prepare_and_start)
label.config(text="Найди выход!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!")
win.bind("<KeyPress>", move_by_keys)
restart.pack()
label.pack()
canvas.pack()
prepare_and_start()
win.bind("<KeyPress>", move_by_keys)
win.mainloop()
