
A python game or bet type program in which you will select one turtle and will bet which one will win.
from turtle import Turtle, Screen, width
import random


is_race_on = False


turtle = Turtle()
screen = Screen()


screen.setup(width=700, height=600)


make_bet = screen.textinput(title="Make Your Bet", prompt="Which turtle win the race? Enter a color(red, yellow, orange, green, blue, purple),: ",)


colors = ["red", "yellow", "orange", "green", "blue", "purple", ]

position = [-70, -40, -10, 20, 50, 80]

all_turtle = []

for turtle_index in range(0, 6):
    # turtle shape
    turtle = Turtle(shape="turtle")
    # stop pen writing
    turtle.penup()
    # add colors to turtle
    turtle.color(colors[turtle_index])
    # start from left edge of screen
    turtle.goto(x=-330, y=position[turtle_index])
    # add all turtle on the list
    all_turtle.append(turtle)

if make_bet:
    is_race_on = True

while is_race_on:

    for turtle in all_turtle:
        # checking if the x coordinate value is grater than 230
        if turtle.xcor() > 330:
            is_race_on = False
            # checking wining color
            winning_color = turtle.pencolor()
            if winning_color == make_bet:
                print(f"You've won! The {winning_color} turtle is the winner!")
            else:
                print(f"You've lost! The {winning_color} turtle is the winner!")

        rand_distance = random.randint(0, 11)
        turtle.forward(rand_distance)

screen.exitonclick()
