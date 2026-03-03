# xxx
import turtle 
t = turtle.Turtle() t.speed(0) 
 
t.penup() 
t.goto(-300, 0) 
t.pendown() 
t.forward(600) 
t.write("  X", font=("Arial", 12, "bold")) 
 
t.penup() 
t.goto(0, -300) 
t.setheading(90) 
t.pendown() 
t.forward(600) 
t.write("  Y", font=("Arial", 12, "bold")) 
t.hideturtle() 
turtle.done() 
 
PRACTICAL NO. 2-- SCREEN DIVISION & HUT DRAWING 
a)	Divide the screen into four regions and draw shapes 
b)	Draw a simple hut 
 
PROGRAM (PART A) 
import turtle
t = turtle.Turtle()
t.speed(0)

# Divide screen
t.penup()
t.goto(-300, 0)
t.pendown()
t.forward(600)

t.penup()
t.goto(0, -300)
t.setheading(90)
t.pendown()
t.forward(600)

# Top-left Circle
t.penup()
t.goto(-150, 100)
t.pendown()
t.circle(50)

t.penup()
t.goto(-190, 170)
t.write("Circle")

# Top-right Rectangle
t.penup()
t.goto(100, 100)
t.pendown()

for i in range(2):
    t.forward(100)
    t.left(90)
    t.forward(60)
    t.left(90)

t.penup()
t.goto(110, 170)
t.write("Rectangle")

# Bottom-left Ellipse
t.penup()
t.goto(-200, -100)
t.pendown()

for i in range(2):
    t.circle(60, 90)
    t.circle(30, 90)

t.penup()
t.goto(-230, -30)
t.write("Ellipse")

# Bottom-right Half Ellipse
t.penup()
t.goto(150, -100)
t.setheading(0)
t.pendown()
t.circle(60, 180)

t.penup()
t.goto(120, -30)
t.write("Half Ellipse")

t.hideturtle()
turtle.done()

PROGRAM (PART B – HUT) 
import turtle
t = turtle.Turtle()
t.speed(0)
# Base
t.penup()
t.goto(-100, -100)
t.pendown()
for i in range(4):
    t.forward(200)
    t.left(90)
# Roof
t.goto(-100, 100)
t.goto(0, 200)
t.goto(100, 100)
t.goto(-100, 100)
# Door
t.penup()
t.goto(-30, -100)
t.pendown()
t.setheading(90)
t.forward(80)
t.right(90)
t.forward(60)
t.right(90)
t.forward(80)
t.hideturtle()
turtle.done()

 PRACTICAL NO. 3 – BASIC SHAPES DDA Algorithm
import turtle
t = turtle.Turtle()
t.speed(0)
def dda(x1, y1, x2, y2):
    dx = x2 - x1
    dy = y2 - y1
    steps = int(max(abs(dx), abs(dy)))
    xinc = dx / steps
    yinc = dy / steps
    x = x1
    y = y1
    t.penup()
    t.goto(x, y)
    t.pendown()
    for i in range(steps):
        x = x + xinc
        y = y + yinc
        t.goto(x, y)

dda(-100, -50, 150, 100)
turtle.done() 
 Part B – Bresenham’s Line Drawing Algorithm 
import turtle
t = turtle.Turtle()
t.speed(0)

def bresenham_line(x1, y1, x2, y2):
    dx = x2 - x1
    dy = y2 - y1
    x = x1
    y = y1
    p = 2 * dy - dx
    t.penup()
    t.goto(x, y)
    t.pendown()

    for i in range(dx):
        if p >= 0:
            y = y + 1
            p = p + 2 * (dy - dx)
        else:
            p = p + 2 * dy
        x = x + 1
        t.goto(x, y)
bresenham_line(-100, -50, 150, 100)
turtle.done() 
 
 PRACTICAL NO. 5 – MIDPOINT CIRCLE 
import turtle
t = turtle.Turtle()
t.speed(0)

r = 100
x = 0
y = r
p = 1 - r

while x <= y:

    points = [(x,y), (-x,y), (x,-y), (-x,-y),
              (y,x), (-y,x), (y,-x), (-y,-x)]

    for px, py in points:
        t.penup()
        t.goto(px, py)
        t.pendown()
        t.dot(3)

    x = x + 1

    if p < 0:
        p = p + 2*x + 1
    else:
        y = y - 1
        p = p + 2*(x - y) + 1

turtle.done()
PRACTICAL NO. 6 – 2D TRANSFORMATIONS 
 
A------Scaling  
import turtle
t = turtle.Turtle()
triangle = [(-50, -50), (50, -50), (0, 50)]
for p in triangle + [triangle[0]]:
    t.goto(p)
t.color("red")
Sx, Sy = 2, 2
scaled = [(x * Sx, y * Sy) for x, y in triangle]
for p in scaled + [scaled[0]]:
    t.goto(p)
turtle.done()

B-----Translation 

import turtle
t = turtle.Turtle()
triangle = [(-50, -50), (50, -50), (0, 50)]
for p in triangle + [triangle[0]]:
    t.goto(p)
t.color("green")
Tx, Ty = 100, 70
move = [(x + Tx, y + Ty) for x, y in triangle]
for p in move + [move[0]]:
    t.goto(p)

turtle.done() 
PRACTICAL NO. 7 – 2D ROTATION 
import turtle
t = turtle.Turtle()
t.speed(3)
# Draw original triangle
for _ in range(3):
    t.forward(100)
    t.left(120)
# Rotate the turtle by 45 degrees
t.left(45)
# Change color
t.color("red")
# Draw rotated triangle
for _ in range(3):
    t.forward(100)
    t.left(120)
turtle.done() 
PRACTICAL NO. 8 – LINE CLIPPING 
import turtle
xmin, xmax = -100, 100
ymin, ymax = -50, 100
t = turtle.Turtle()
# Draw window
t.penup()
t.goto(xmin, ymin)
t.pendown()
for _ in range(2):
    t.forward(xmax - xmin)
    t.left(90)
    t.forward(ymax - ymin)
    t.left(90)
# Original line
x1, y1, x2, y2 = -150, -100, 200, 150
t.color("red")
t.penup()
t.goto(x1, y1)
t.pendown()
t.goto(x2, y2)

# ---- LINE CLIPPING ----
if x1 < xmin:
    y1 += (y2 - y1) * (xmin - x1) / (x2 - x1)
    x1 = xmin

if x2 > xmax:
    y2 += (y2 - y1) * (xmax - x2) / (x2 - x1)
    x2 = xmax

if y1 < ymin:
    x1 += (x2 - x1) * (ymin - y1) / (y2 - y1)
    y1 = ymin
if y2 > ymax:
    x2 += (x2 - x1) * (ymax - y2) / (y2 - y1)
    y2 = ymax
# Clipped line
t.color("green")
t.penup()
t.goto(x1, y1)
t.pendown()
t.goto(x2, y2)
turtle.done()
PRACTICAL NO. 9 – FILL ALGORITHMS 
A) Flood Fill
import turtle
t = turtle.Turtle()
# Shape
t.penup()
t.goto(-50, -50)
t.pendown()
for _ in range(4):
    t.forward(100)
    t.left(90)
# Fill (simulated)
t.penup()
t.goto(0, 0)
t.fillcolor("yellow")
t.begin_fill()
t.circle(40)
t.end_fill()
turtle.done()

B) Boundary Fill 

import turtle
t = turtle.Turtle()
t.color("black", "green")
t.begin_fill()
# Square
t.penup()
t.goto(-60, -60)
t.pendown()
for _ in range(4):
    t.forward(120)
    t.left(90)
t.end_fill()
turtle.done() 
(MOVING CAR) 
import turtle
import time
t = turtle.Turtle()
t.hideturtle()
t.speed(0)
def car(x):
    t.penup()
    t.goto(x, -50)
    t.pendown()
    # Car body
    for _ in range(2):
        t.forward(100)
        t.left(90)
        t.forward(40)
        t.left(90)
    # Wheels
    t.penup()
    t.goto(x + 20, -50)
    t.dot(20)
    t.goto(x + 80, -50)
    t.dot(20)
# Animation loop
for x in range(-200, 200, 10):
    t.clear()
    car(x)
    time.sleep(0.05)
turtle.done()
SOLAR SYSTM




import turtle, math, time
screen = turtle.Screen()
screen.bgcolor("black")
sun = turtle.Turtle(shape="circle")
sun.color("yellow")
sun.shapesize(2)
sun.penup()
planets_data = [
    ("gray", 0.4, 50, 2),
    ("orange", 0.6, 80, 1.7),
    ("blue", 0.7, 110, 1),   # Earth
    ("red", 0.5, 140, 0.8),
    ("brown", 1.2, 190, 0.5),
    ("gold", 1.0, 230, 0.4),
    ("lightblue", 0.8, 270, 0.3),
    ("darkblue", 0.8, 310, 0.2)
]# Create planet turtles
planets = []
for color, size, _, _ in planets_data:
    t = turtle.Turtle(shape="circle")
    t.color(color)
    t.shapesize(size)
    t.penup()
    planets.append(t) # Moon
moon = turtle.Turtle(shape="circle")
moon.color("white")
moon.shapesize(0.3)
moon.penup()# Draw orbits
orbit = turtle.Turtle()
orbit.hideturtle()
orbit.color("white")
orbit.penup()
orbit.speed(0)
for _, _, r, _ in planets_data:
    orbit.goto(0, -r)
    orbit.pendown()
    orbit.circle(r)
    orbit.penup()# Animation
angle = 0
while True:
    for p, (_, _, r, speed) in zip(planets, planets_data):
        x = r * math.cos(angle * speed)
        y = r * math.sin(angle * speed)
        p.goto(x, y) # Moon around Earth (3rd planet)
    ex, ey = planets[2].xcor(), planets[2].ycor()
    moon.goto(ex + 20 * math.cos(angle*4), ey + 20 * math.sin(angle*4))   /angle += 0.03  / time.sleep(0.02)
SNOWFALL
import turtle
import random
# Screen setup
screen = turtle.Screen()
screen.bgcolor("black")
screen.title("Snowfall Animation")
screen.setup(width=800, height=600)
screen.tracer(0)
# Create snowflakes
snowflakes = []
for _ in range(150):
    snow = turtle.Turtle()
    snow.shape("circle")
    snow.color("white")
    snow.shapesize(0.3)
    snow.penup()
    snow.speed(0)
    x = random.randint(-390, 390)
    y = random.randint(-290, 290)
    snow.goto(x, y)
    snowflakes.append(snow)
# Animation loop
while True:
    for snow in snowflakes:
        x, y = snow.position()
        # Falling speed (slightly random for natural effect)
        y -= random.randint(1, 3)
        # Reset to top if snow reaches bottom
        if y < -300:
            y = 300
            x = random.randint(-390, 390)
        snow.goto(x, y)
    screen.update()



SMILEY FACE import turtle
import time
screen = turtle.Screen()
screen.bgcolor("white")
screen.title("Smiley Blink")
screen.tracer(0)

t = turtle.Turtle()
t.hideturtle()
t.speed(0)# Draw Face
t.penup()
t.goto(0, -150)
t.pendown()
t.color("yellow")
t.begin_fill()
t.circle(150)
t.end_fill()# Draw Smile
t.penup()
t.goto(-80, -20)
t.setheading(-60)
t.pendown()
t.color("black")
t.width(5)
t.circle(100, 120)
t.width(1)# Eye function
def eye(x, blink=False):
    t.penup()
    t.goto(x, 60)
    t.setheading(0)
    t.pendown()
    if blink:
        t.width(5)
        t.forward(40)
        t.width(1)
    else:
        t.begin_fill()
        t.circle(20)
        t.end_fill()
while True: # Open eyes
    t.color("black")
    eye(-50, False)
    eye(50, False)
    screen.update()
    time.sleep(1) # Erase open eyes
    t.color("yellow")
    eye(-50, False)
    eye(50, False)  # Draw closed eyes
    t.color("black")
    eye(-50, True)
    eye(50, True)
    screen.update()
    time.sleep(0.2)  # Erase closed eyes
    t.color("yellow")
    eye(-50, True)
    eye(50, True)                      
 BOUNCING BALL
import turtle
import time

# Screen setup
screen = turtle.Screen()
screen.bgcolor("black")
screen.title("Bouncing Ball Animation")
screen.setup(width=800, height=600)
screen.tracer(0)

# Ball setup
ball = turtle.Turtle()
ball.shape("circle")
ball.color("cyan")
ball.penup()
ball.goto(0, 0)

# Movement speed
dx = 3
dy = 3

# Animation loop
while True:
    ball.setx(ball.xcor() + dx)
    ball.sety(ball.ycor() + dy)

    # Bounce from left & right walls
    if ball.xcor() > 380 or ball.xcor() < -380:
        dx = -dx

    # Bounce from top & bottom walls
    if ball.ycor() > 280 or ball.ycor() < -280:
        dy = -dy

    screen.update()
    time.sleep(0.01)




MOVING CAR:import turtle
import time

# Screen setup
screen = turtle.Screen()
screen.bgcolor("white")
screen.setup(600, 300)
screen.title("Moving Car Animation")
screen.tracer(0)

# Car body
car = turtle.Turtle()
car.penup()
car.speed(0)
car.shape("square")
car.shapesize(2, 4)
car.color("red")

# Wheel 1
wheel1 = turtle.Turtle()
wheel1.penup()
wheel1.speed(0)
wheel1.shape("circle")
wheel1.color("black")

# Wheel 2
wheel2 = turtle.Turtle()
wheel2.penup()
wheel2.speed(0)
wheel2.shape("circle")
wheel2.color("black")

x = -300

# Animation loop
while True:
    car.goto(x, 0)
    wheel1.goto(x - 30, -25)
    wheel2.goto(x + 30, -25)

    x += 3

    if x > 320:
        x = -320

    screen.update()
    time.sleep(0.02)


 
 
 
