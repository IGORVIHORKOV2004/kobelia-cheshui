
import tkinter as tk
import random
from tkinter import PhotoImage
def move_by_keys(event):
    info_coords = canvas.coords(player)
    x = info_coords[0]
    y = info_coords[1]
    label.config(text=str(x)+ ' '+ str(y))
    if event.keysym == 'Up':
        canvas.move(player,0,-20)
    elif event.keysym == 'Down':
        canvas.move(player,0,20)
    elif event.keysym == 'Left':
        canvas.move(player,-20,0)
    elif event.keysym == 'Right':
        canvas.move(player,20, 0)
step=10
win = tk.Tk()
canvas = tk.Canvas(win, bg='#fff', width=700, height=700)
label = tk.Label(win, text='ИГОРЬ ВИХОРЬКОВ')
player_pos = (200,200)
player_pic = tk.PhotoImage(file=r"ghost.png")
player = canvas.create_image((player_pos[0], player_pos[1]), image=player_pic, anchor='nw')
label.config(text="Найди выход!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!")
win.bind("<KeyPress>", move_by_keys)
canvas.pack()
win.mainloop()
