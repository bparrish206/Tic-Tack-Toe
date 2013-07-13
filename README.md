Tic-Tack-Toe
============

# import Gui module
import Gui3

# main function builds canvas, board and lays out pieces
def main():
    win = Gui3.Gui()
    win.title('Tic-Tac-Toe')
    canvas = win.ca(350, 350)
    canvas.rectangle([[-150, -150], [150, 150]],  fill='cyan')
    board(-150, -150, canvas, 300)
    drawX(upper_left, canvas)
    drawO(center, canvas)
    drawX(lower_left, canvas)
    drawO(mid_left, canvas)
    drawX(mid_right, canvas)
    drawO(upper_middle, canvas)
    drawX(lower_middle, canvas)
    drawO(lower_right, canvas)
    drawX(upper_right, canvas)
    
    win.mainloop()
# global positions for the gameboard
upper_left = 1
upper_middle = 2
upper_right = 3
mid_left = 4
center = 5
mid_right = 6
lower_left = 7
lower_middle = 8
lower_right = 9

#board function.  Takesn in 4 arguments two for X & Y, one for the canvas and one for the total size of game.
def board(x, y, canvas, size):
    # a number of global variables to be used in the X & O pieces
    global Ssize
    Ssize = size
    global Xp
    Xp = x
    global Yp
    Yp = y
    global x2
    x2 = size * (1/3)
    global x3
    x3 = size * (2/3)
    global x4
    x4 = size * .05
    global x5
    x5 = size * .95
    # set the width of the game lines 
    global x6
    if size < 50:
        x6=1
    else:
        x6=3
    # set the lines of the game
    canvas.line([[x+x2,y+x4], [x+x2, y+x5]], fill='blue', width=x6)
    canvas.line([[x+x3, y+x4], [x+x3, y+x5]], fill='blue', width=x6)
    canvas.line([[x+x4, y+x2], [x+x5, y+x2]], fill='blue', width=x6)
    canvas.line([[x+x4, y+x3], [x+x5, y+x3]], fill='blue', width=x6)

# X pieces function takes in two arguments, one for the position of the piece and one for the canvas.
def drawX(position, canvas):
    #sets the width of the lines
    Xw = 7
    if Ssize < 150:
        Xw = 3
        if Ssize < 50:
            Xw = 1
    #draws the X's for each spot on the game board
    if position == 7:
        canvas.line([[Xp+x4,Yp+x4], [Ssize*.285+Xp, Ssize*.285+Yp]], fill='gold', width=Xw)
        canvas.line([[Xp+Ssize*.31, Yp+x4], [Xp+x4, Ssize*.285+Yp]], fill='gold', width=Xw)
    elif position == 8:
        canvas.line([[Xp +Ssize*.38, Yp+x4], [Ssize*.62+Xp, Ssize*.285+Yp]], fill='gold', width=Xw)
        canvas.line([[Xp+Ssize*.62, Yp+x4], [Xp+Ssize*.38, Ssize*.285+Yp]], fill='gold', width=Xw)
    elif position == 9:
        canvas.line([[Xp + Ssize*.70, Yp+x4], [Xp+Ssize*.93, Ssize*.285+Yp]], fill='gold', width=Xw)
        canvas.line([[Xp+Ssize*.93, Yp+x4], [Xp+Ssize*.70, Ssize*.285+Yp]], fill='gold', width=Xw)
    elif position == 4:
        canvas.line([[Xp+Ssize*.07, Yp+Ssize*.35], [Xp +Ssize*.285, Yp+Ssize*.62]], fill='gold', width=Xw)
        canvas.line([[Xp+Ssize*.31, Yp+Ssize*.35], [Xp+Ssize*.07, Yp+ Ssize*.62]], fill='gold', width=Xw)
    elif position == 5:
        canvas.line([[Xp+Ssize*.38, Yp+Ssize*.35], [Xp +Ssize*.62, Ssize*.62+Yp]], fill='gold', width=Xw)
        canvas.line([[Xp+Ssize*.62, Yp+Ssize*.35], [Xp + Ssize*.38, Ssize*.62+Yp]], fill='gold', width=Xw)
    elif position == 6:
        canvas.line([[Xp+Ssize*.70, Yp+Ssize*.35], [Xp + Ssize*.93, Ssize*.62+Yp]], fill='gold', width=Xw)
        canvas.line([[Xp+Ssize*.93, Yp+Ssize*.35], [Xp +Ssize*.70, Ssize*.62+Yp]], fill='gold', width=Xw)
    elif position == 1:
        canvas.line([[Xp + Ssize*.07, Yp+Ssize*.69], [Xp +Ssize*.285, Ssize*.93+Yp]], fill='gold', width=Xw)
        canvas.line([[Xp + Ssize*.31, Yp+Ssize*.69], [Xp+Ssize*.07, Ssize*.93+Yp]], fill='gold', width=Xw)
    elif position == 2:
        canvas.line([[Xp+Ssize*.38, Yp+Ssize*.69], [Xp+Ssize*.62, Ssize*.93+Yp]], fill='gold', width=Xw)
        canvas.line([[Xp+Ssize*.62, Yp+Ssize*.69], [Xp+Ssize*.38, Ssize*.93+Yp]], fill='gold', width=Xw)
    elif position == 3:
        canvas.line([[Xp+Ssize*.7, Yp+Ssize*.69], [Xp+Ssize*.93, Ssize*.93+Yp]], fill='gold', width=Xw)
        canvas.line([[Xp+Ssize*.93, Yp+Ssize*.69], [Xp+Ssize*.7, Ssize*.93+Yp]], fill='gold', width=Xw)

# O piece functions
def drawO(position, canvas):
    #Sets width of the O lines
    Ow = 7
    if Ssize < 150:
        Ow = 3
        if Ssize < 50:
            Ow = 1
    # draws the O depending on what piece of the game they are in
    if position == 1:
        canvas.circle([Xp+Ssize*.19, Yp+Ssize*.83], Ssize*.13, fill='#ffee22', width=Ow, outline='green')
    elif position == 2:
        canvas.circle([Xp+Ssize*.5, Yp+Ssize*.83], Ssize*.13, fill='#ffee22', width=Ow, outline='green')
    elif position == 3:
        canvas.circle([Xp+Ssize*.82, Yp+Ssize*.83], Ssize*.13, fill='#ffee22', width=Ow, outline='green')
    elif position == 4:
        canvas.circle([Xp+Ssize*.19, Yp+Ssize*.5], Ssize*.13, fill='#ffee22', width=Ow, outline='green')
    elif position == 5:
        canvas.circle([Xp+Ssize*.5, Yp+Ssize*.5], Ssize*.13, fill='#ffee22', width=Ow, outline='green')
    elif position == 6:
        canvas.circle([Xp+Ssize*.82, Yp+Ssize*.5], Ssize*.13, fill='#ffee22', width=Ow, outline='green')
    elif position == 7:
        canvas.circle([Xp+Ssize*.17, Yp+Ssize*.17], Ssize*.13, fill='#ffee22', width=Ow, outline='green')
    elif position == 8:
        canvas.circle([Xp+Ssize*.5, Yp+Ssize*.17], Ssize*.13, fill='#ffee22', width=Ow, outline='green')
    elif position == 9:
        canvas.circle([Xp+Ssize*.82, Yp+Ssize*.17], Ssize*.13, fill='#ffee22', width=Ow, outline='green')
# calls main
main()
