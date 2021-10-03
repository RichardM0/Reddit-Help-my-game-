# Reddit-Help-my-game-
Fighter_a and Bullet problem
Here's my code:
import turtle
import os

# Sets a screen for everything to be ran on
wn = turtle.Screen()
wn.bgcolor("light blue")
wn.setup(width = 800, height = 600)

# Fighter 1
fighter_a = turtle.Turtle()
fighter_a.speed(0)
fighter_a.shape("square")
fighter_a.color("green")
fighter_a.penup()
fighter_a.goto(-325, 0)

# Fighter 2
fighter_b = turtle.Turtle()
fighter_b.speed(0)
fighter_b.shape("square")
fighter_b.color("red")
fighter_b.penup()
fighter_b.goto(325, 0)

# Bullet
bullet = turtle.Turtle()
bullet.speed(0)
bullet.penup()
bullet.goto(310, 0)
bullet.shape("circle")
bullet.color("yellow")
bullet.dx = -4
bullet.dy = -4

# Functions
def fightera_up():
  y = fighter_a.ycor()
  y+=20
  fighter_a.sety(y)
  return y
  
def fightera_down():
  y = fighter_a.ycor()
  y-=20
  fighter_a.sety(y)
  return y
  
def fightera_right():
  x = fighter_a.xcor()
  x+=20
  fighter_a.setx(x)
  return x
  
def fightera_left():
  x = fighter_a.xcor()
  x-=20
  fighter_a.setx(x)
  return x
  
# Keybinds
# wn.listen() allows the console to listen for something like key presses.

wn.listen()
wn.onkeypress(fightera_up, "w")
wn.onkeypress(fightera_left, "a")
wn.onkeypress(fightera_down, "s")
wn.onkeypress(fightera_right, "d")

# Game Loop
while True:
  # Refreshes game screen everytime
  wn.update()
  # bullet movement
  bullet.setx(bullet.xcor() + bullet.dx)
  bullet.sety(bullet.ycor() + bullet.dy)
  x = fighter_a.xcor()
  y = fighter_a.ycor()
  # border check
  if bullet.ycor() > 290:
    bullet.sety(290)
    bullet.dy *= -1
  if bullet.ycor() < -290:
    bullet.sety(-290)
    bullet.dy *= -1
  if bullet.xcor() > 390:
    bullet.setx(390)
    bullet.dx *= -1
  if bullet.xcor() < -390:
    bullet.setx(-390)
    bullet.dx *= -1
  if bullet.setx == x and bullet.sety == y:   # PROBLEM IS HERE
    bullet.goto(0, 0)
    bullet.dx *= 0

