import tkinter as tk
from tkinter import *
import random 

root = tk.Tk()

root.geometry("900x600")
root.resizable(width=False, height=False)
root.title("Tic-Tac-Toe")
root.config(bg="#008080")
players = ["x","o"]
player = random.choice(players)

def next_turn(row, column):

    global player
    if buttons[row][column]['text'] == "":
        if check_winner() is False:
            if player == players[0]:
                buttons[row][column]["text"] = str(player)
                if check_winner() is True:
                    label.config(text=(players[0]+" wins"))  

                elif empty_spaces() is False:
                    label.config(text="Tie!")

                else:
                    player = players[1]
                    label.config(text=player+" Turn")           



            else:
                buttons[row][column]["text"] = str(player)
                if check_winner() is True:
                    label.config(text=(players[1]+" wins"))  

                elif empty_spaces() is False:
                    label.config(text="Tie!")
                
                else:
                    player = players[0]
                    label.config(text=player+" Turn")           


def check_winner():

    r = 0
    for x in range(3):
        if buttons[0][x]['text'] == buttons[1][x]['text'] == buttons[2][x]['text'] != "":
            buttons[0][x].config(bg="green")
            buttons[1][x].config(bg="green")
            buttons[2][x].config(bg="green")
            r = 1 
        if buttons[x][0]['text'] == buttons[x][1]['text'] == buttons[x][2]['text'] != "":
            buttons[x][0].config(bg="green")
            buttons[x][1].config(bg="green")
            buttons[x][2].config(bg="green")
            r = 1

    if buttons[0][0]['text'] == buttons[1][1]['text'] == buttons[2][2]['text'] != "":
        buttons[0][0].config(bg="green")
        buttons[1][1].config(bg="green")
        buttons[2][2].config(bg="green")
        r = 1
        
    if buttons[0][2]['text'] == buttons[1][1]['text'] == buttons[2][0]['text'] != "":
        buttons[0][2].config(bg="green")
        buttons[1][1].config(bg="green")
        buttons[2][0].config(bg="green")
        r = 1
        
    if r == 0:
        return False
    else:
        return True


def empty_spaces():

    k=0
    for row in range(3):
        for column in range(3):
            if buttons[row][column]['text'] != "":
                k+=1
    if k==9:
        for row in range(3):
            for column in range(3):
                buttons[row][column].config(bg="rosybrown")
        return False
    else:
        return True
        

def new_game():

    global player
    player = random.choice(players)
    label.config(text=player+" Turn")
    for row in range(3):
        for column in range(3):
            buttons[row][column]['text'] = ""
            buttons[row][column].config(bg= "darkgrey")

#Buttons
buttons = [[0,0,0],
           [0,0,0],
           [0,0,0]]
bottom_frame = Frame(root)
bottom_frame.place(relx=.5, rely=.5, anchor="center")
for row in range(3):
    for column in range(3):
        buttons[row][column] = Button(bottom_frame, text="", font=('arial',40), width=5, height=1, bg= "darkgrey",
                                      command= lambda row=row, column=column: next_turn(row,column))
        buttons[row][column].grid(row=row,column=column)
        
        
#Button
btn = Button(root, text = 'Press for New game', font= ("arial", 18), bg="black", fg="white", bd = '10', command = lambda: new_game()) 
btn.pack(side=BOTTOM)

#Title
title= Canvas(root, width= 1000, height= 40, bg="black")
title.create_text(450, 20, text="Tic-Tac-Toe Game.", fill="teal", font=('arial', 25, "bold"))
title.pack()

#Text
label = Label(root, text=player + " Turn", font=('arial',18), bg = "teal", fg ="black")
label.pack()

root.mainloop()
