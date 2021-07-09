# Python Summer Camp

​																					**Peter Edmonds, Summer 2021**





[TOC]



## Introductory Matter

Python camp provides an introduction to the Python programming language through the PyGame library. This curriculum will assume the kids do not have a proper Python development environment available. We have a web-based implementation of Python + PyGame running at https://www.newcastlecode.com/python. Python was never meant to be run in the browser, but this solution allows for students to get started immediately, whether from home or in-center. However, web-based Python does have its quirks as you shall soon see, so be aware of that. 

If you wish to abandon the online Python environment, just make sure all the laptops are set up with a sensible development environment and have the PyGame package installed.



**Important Note:** A major flaw with the online environment is that it often does not kill the current script when you click "Stop". That means that clicking "Stop" and "Start" multiple times will cause a bunch of scripts to run simultaneously and they will all render at the same time. For now, just refresh the page and paste your code back in to kill all scripts.

## The Online Environment



The online Python environment looks like this:

![image-20210704192715461](/home/peteredmonds/.var/app/io.typora.Typora/config/Typora/typora-user-images/image-20210704192715461.png)



The left is the editor and the right pane shows the video output from PyGame. If you wish to only see the console output, select Edit -> Console. You can also click "Send Code" and enter an arbitrary keyword which will save your current program under that keyword. To load that saved program, simply click "Load Code" then enter your keyword. This is useful for sending a project to students or saving progress between days,

## Day 1: Bare Minimum Programming

### What are programs?

- A computer program is a set of instructions that causes a computer to perform some kind of action

- Without computer programs, almost every device you use daily would either stop working or be much less useful than it is now

### What are programming languages?

- Like humans, computers use multiple languages to communicate— in this case, programming languages
- There are programming languages named after people (like Ada and Pascal)
- Some are programming languages named after letters (like B and C, and R)
- Other are named using simple acronyms (COBOL and BASIC )
- Some are even named after films (Python...as in Monty)
- All languages have their own strength and weaknesses, but Python is a well rounded place to start

### Writing your first program

- Open up your development environment and switch to the console output view

- Enter the following code:

- ```python
  print("Hello, world!")
  ```

  and hit "Start"

  - What do you see?
  - What happens if you forget the quotes?

- Explain that a program is made up of instructions, and that the **print** instruction will simply display whatever your put between its parentheses (called **arguments**)

### Basic calculation

- Printing is cool, but now lets have the computer actually do some work for us...

- Change the **argument** of the **print** instruction like so:

  - ```python
    print(5 + 5)
    ```

  - What do you see?

  - What happens if you remove the spaces? 

  - Now try some others...

  - ```python
    print(5 + 5)
    print(5 - 5)
    print(5 / 5)
    print(5 * 5)
    ```

  - Notice that we use the slash (/) for divide and the asterisk (*) for multiplication.

### More complicated calculations

- Those calculations you could probably do in your head...lets try something a little harder

- Calculations can be extended like so:

- ```python
  print(2 + 2 * 10)
  ```

  - What will this output? 40 or 22? Why?

  - Lets remember order of operations!

    #### Some puzzles to give out

    Using Python, solve these problems:

    - How many minutes are in a day?

      - ```python
        print(60 * 24)
        ```

    - Should notHow many minutes are in a week?

      - ```python
        print(60 * 24 * 7)
        ```

    - How many hours are in a year?

      - ```python
        print(24 * 365)
        ```

    - Anything else you can come up with...

### Storing our answers

- As we do more complicated computations, it would be nice to store our answers for later

- This would mean we don't have to type out

- ```python
  60 * 24 * 7
  ```

  every time we want to know how many minutes are in a week

- To store a variable, write it like this:

- ```python
  minutes_in_week = 60 * 24 * 7
  ```

- In Python, most people write_variables_like_this. This convention is called snake_case and it is **not** required.

- Other people prefer writingVariablesLikeThis. This is called camelCase.

- Both work! But there are some requirements. Variables:

  - Must start with a letter or the underscore character.

  - Can only contain alpha-numeric characters and underscores (A-z, 0-9, and _ )

    - This means no punctuation or emojis...

  - Are case-sensitive (name, Name and NAME are three different variables)

  - **Cannot** be a **keyword**

    - **for, while, as, etc...**

  - **Should not** be **functions**

  - ```python
    print = 5
    print(print)
    
    # bad!!!
    # this will overwrite the function print with the number 5
    ```

### Different data types

- So far we have only seen numbers (boring!)

- Lets see what else we can store

  - #### **Strings**

    - These are things surrounded by quotes

    - "Hello, World!"

    - "Sensei Peter"

    - "Game Over!"

    - They are **different** than numbers

    - Try this out:

    - ```python
      print("5 + 5")
      print(5 + 5)
      ```

    - What is the difference?

    - Now try this:

    - ```python
      print("5" * 5)
      ```

    - Interesting!!

- #### **Lists**

  - What if we wanted to keep track of all of our classmates' names?

  - Would have have to make a new variable for each name?

  - What if we had 100 classmates?!

  - Lists provide a simple way to store a collection of numbers, string, or even other lists!

  - Make a list in Python like this:

  - ```python
    languages = ["Python", "COBOL", "JavaScript", "FORTRAN"]
    ```

  - Now how do we access these items?

  - Try this:

  - ```python
    print(languages[1])
    ```

  - It didn't print the first item! Explain that computers start at 0, not 1

  - Adding to a list:

    - ```python
      languages.append("C++")

    - Append will add on to the **end** of the list

  - Remove from list:

    - ```python
      languages.pop()
      ```

    - Pop will remove from the **end** of the list

    - You can also give it an **index** like this:

    - ```python
      languages.pop(0)
      
      # this will remove the first element
      ```

  - #### Tuples

    - A tuple is just like a list, but you **cannot** change it after it is created!

    - It is used a lot in PyGame as we shall soon see...

    - Make a tuple like this

    - ```python
      size = (100, 200)
      ```

    - Notice the use of parenthesis instead of brackets...

    - You can **index** a tuple just like a list

### Intro to PyGame

Switch back to the visual view in the programming environment and begin talking about PyGame. Here is the most basic example you can write:

```python
import pygame 									# include the python library
pygame.init()									# start up the pygame renderer

win = pygame.display.set_mode((800,700))		# define your window / screen

while True:										# start the main loop
    pygame.time.delay(10)						# slow the game down a bit. REQUIRED!!!
    win.fill((255,255,255))						# set the background to white

    pygame.draw.rect(win, (255,0,0), (20, 20, 20, 20))   # draw a 20x20 rectangle
    pygame.display.update() 					# update the display
```





Go through each line and explain what it does.

- pygame.display.set_mode takes in a tuple which is the screen resolution. You can set any resolution but I suggest **800x700**
- pygame.time.delay set the delay in ms between frames. **Without this function, the browser will freeze up and you may lose all your progress. Stress this point!!**
- The draw.rect function is self-explanatory, but more information is always at http://www.pygame.org/docs/ref/draw.html
- Make sure everyone has this working before moving on
- Explain the **while True:**

Lets clean up that code with some variables

```python
import pygame
pygame.init()

win = pygame.display.set_mode((800,700))
RED = (255,0,0)
GREEN = (0, 255,0)

playerWidth = 100
playerHeight = 100
playerX = 0
playerY = 0

while True:
    pygame.time.delay(10)
    win.fill((255,255,255))
    pygame.draw.rect(win, RED, (playerX, playerY, playerWidth, playerHeight))
    pygame.display.update() 
    
pygame.quit()

# much better :)
```



PyGame also adds in its own data types. Just like **string** and **number**, PyGame adds types like **Rect**



```python
import pygame
pygame.init()

win = pygame.display.set_mode((800,700))
RED = (255,0,0)
GREEN = (0, 255,0)

player = pygame.Rect(0,0,100,100)

while True:
    
    for event in pygame.event.get():
        if event.type == pygame.MOUSEBUTTONDOWN:
            print("key pressed!")
    
    pygame.time.delay(10)
    win.fill((255,255,255))
    pygame.draw.rect(win, RED, player)
    pygame.display.update() 
    
    
    
pygame.quit()

# much better :)
```









#### The event loop

There are many things to react to in a video games

- Keyboard pressed
- Mouse clicks
- Window exits out

All of these are known as **events**



We can see all the current events in our game with



```python
pygame.event.get()
```

This returns a **list** of events

- Explain how to iterate over a list with a **for loop**

Add the following code to explore events



```python
import pygame
pygame.init()

win = pygame.display.set_mode((800,700))
RED = (255,0,0)
GREEN = (0, 255,0)

player = pygame.Rect(0,0,100,100)

while True:
    
    for event in pygame.event.get(): # check each events
        if event.type == pygame.KEYDOWN: # if it is a keydown event...
            print("key pressed!")		# print something!
    
    pygame.time.delay(10)
    win.fill((255,255,255))
    pygame.draw.rect(win, RED, player)
    pygame.display.update() 
    
    
    
pygame.quit()

# much better :)
```

Now run the code and check the console view...what happens after you hit some buttons?

#### Mouse events

```python
import pygame
pygame.init()

win = pygame.display.set_mode((800,700))
RED = (255,0,0)
GREEN = (0, 255,0)
player = pygame.Rect(0,0,100,100)

while True:  
    for event in pygame.event.get(): # check each events
        if event.type == pygame.MOUSEBUTTONDOWN: # if it is a mousedown event...
            player.x += 5
    
    pygame.time.delay(10)
    win.fill((255,255,255))
    pygame.draw.rect(win, RED, player)
    pygame.display.update() 
    
    
    
pygame.quit()

# much better :)
```

This code will move the rectangle whenever the player clicks the screen.



Now lets add some **collision detection**

```python
import pygame
pygame.init()

win = pygame.display.set_mode((800,700))
RED = (255,0,0)
GREEN = (0, 255,0)
player = pygame.Rect(0,0,100,100)

while True:
    for event in pygame.event.get(): # check each events
        if event.type == pygame.MOUSEBUTTONDOWN: # if it is a mousedown event...
            pos = pygame.mouse.get_pos()		# get the mouse position
            if player.collidepoint((pos[0], pos[1])): # the rect type can check if a point is inside
                player.x += 5    
    pygame.time.delay(10)
    win.fill((255,255,255))
    pygame.draw.rect(win, RED, player)
    pygame.display.update() 
    
    
    
pygame.quit()

# much better :)
```

Now the rectangle will only move if you click directly on it



Lets use the **random** module to make the rectangle go to a random coordinate when its clicked. 6154

```python
import pygame
import random
pygame.init()

win = pygame.display.set_mode((800,700))
RED = (255,0,0)
GREEN = (0, 255,0)
player = pygame.Rect(0,0,100,100)

while True:
    for event in pygame.event.get(): # check each events
        if event.type == pygame.MOUSEBUTTONDOWN: # if it is a mousedown event...
            pos = pygame.mouse.get_pos()
            if player.collidepoint((pos[0], pos[1])):
                player.x = random.randint(0, 800 - player.width)
                player.y = random.randint(0, 700 - player.height)
                
    pygame.time.delay(10)
    win.fill((255,255,255))
    pygame.draw.rect(win, RED, player)
    pygame.display.update() 
    
    
    
pygame.quit()

# much better :)
```

#### Text

Lets learn how to use Text objects in PyGame. We will make a score counter to keep track of how many times we have clicked the rectangle.



In PyGame, there are 3 steps to using text

1. Choose a font family and size using the **Font** type

   ```python
   font = pygame.font.Font("helvetica", 24)
   ```

   ​	You can list all the available fonts using pygame.font.get_fonts()

2. **Render** some text at a location to get a new **surface**

   ```python
   text = font.render("Score: " + str(score), True, (0,0,0))
   ```

   The boolean toggles anti-aliasing. Either True or False are fine for our purposes. The tuple at the end represents colo

3. **Blit** (copy) the rendered surface onto our main surface.

```python
win.blit(text, (0,0))
```



Lets put that all together now:



```python
import pygame
import random

pygame.init()

win = pygame.display.set_mode((800,700))
RED = (255,0,0)
GREEN = (0, 255,0)
player = pygame.Rect(0,0,100,100)
font = pygame.font.Font("helvetica", 24)
print(font)
score = 0

while True:
    for event in pygame.event.get(): # check each events
        if event.type == pygame.MOUSEBUTTONDOWN: # if it is a mousedown event...
            pos = pygame.mouse.get_pos()
            if player.collidepoint((pos[0], pos[1])):
                player.x = random.randint(0, 800 - player.width)
                player.y = random.randint(0, 700 - player.height)
                score += 1
    text = font.render("Score: " + str(score), True, (0,0,0)) # notice how we add a string + number. What happens if we get rid of the str 'cast'?
       
    pygame.time.delay(10)
    win.fill((255,255,255))
    
    win.blit(text, (0,0))   # notice that we blit AFTER we draw the white background!
    pygame.draw.rect(win, RED, player)
    pygame.display.update() 
    
    
    
pygame.quit()

# much better :)
```



Some things to mention:

- Why do we need to put str(score) and not just score?
- What would happen if we blit before we fill?
- What other information would we display using text?



Lets add a timer to show how long we have been playing 



```python
import pygame
import random

pygame.init()

win = pygame.display.set_mode((800,700))
RED = (255,0,0)
GREEN = (0, 255,0)
player = pygame.Rect(0,0,100,100)
font = pygame.font.Font("helvetica", 24) # we can use the same font for two renders
print(font)
score = 0
    
start_ms =pygame.time.get_ticks() # the time at the start of the game. note: this actually tells you the number of ms since pygame.init() was called. should be near 0 at the start of the game
while True:
    for event in pygame.event.get(): # check each events
        if event.type == pygame.MOUSEBUTTONDOWN: # if it is a mousedown event...
            pos = pygame.mouse.get_pos()
            if player.collidepoint((pos[0], pos[1])):
                player.x = random.randint(0, 800 - player.width)
                player.y = random.randint(0, 700 - player.height)
                score += 1
                
    current_ms = pygame.time.get_ticks() # the time right now
    elapsed_ms = current_ms - start_ms
    elapsed_seconds = elapsed_ms / 1000 # the current time in seconds
    score_text = font.render("Score: " + str(score), True, (0,0,0))
    timer_text = font.render("Time: " + str(elapsed_seconds), True, (0,0,0))
       
    pygame.time.delay(10)
    win.fill((255,255,255))
    win.blit(score_text, (0,0))
    win.blit(timer_text, (500,0)) # make sure we dont render both surfaces at the same coords!

    pygame.draw.rect(win, RED, player)
    pygame.display.update() 
    
pygame.quit()

# much better :)
```

Finally, lets add an **exit condition** so the game will finish once we click 30 targets



```python
import pygame
import random

pygame.init()

win = pygame.display.set_mode((800,700))
RED = (255,0,0)
GREEN = (0, 255,0)
player = pygame.Rect(0,0,100,100)
font = pygame.font.Font("helvetica", 24)
print(font)
score = 0
    
start_ms =pygame.time.get_ticks() # the time at the start of the game

running = True

while running:
    for event in pygame.event.get(): # check each events
        if event.type == pygame.MOUSEBUTTONDOWN: # if it is a mousedown event...
            pos = pygame.mouse.get_pos()
            if player.collidepoint((pos[0], pos[1])):
                player.x = random.randint(0, 800 - player.width)
                player.y = random.randint(0, 700 - player.height)
                score += 1
                
                if score == 30:
                    running = False

    current_ms = pygame.time.get_ticks() # the time right now
    elapsed_ms = current_ms - start_ms
    elapsed_seconds = elapsed_ms / 1000 # the current time in seconds
    score_text = font.render("Score: " + str(score), True, (0,0,0))
    timer_text = font.render("Time: " + str(elapsed_seconds), True, (0,0,0))
       
    pygame.time.delay(10)
    win.fill((255,255,255))
    win.blit(score_text, (0,0))
    win.blit(timer_text, (500,0))

    pygame.draw.rect(win, RED, player)
    pygame.display.update() 
    
    
win.fill(GREEN)
win_text = font.render("You win!!", True, (0,0,0))
win.blit(win_text, (700/2,800/2))
win.blit(score_text, (0,0))
win.blit(timer_text, (500,0))
pygame.display.update() 

pygame.quit()

# much better :)
```



How long does it take you to click 30 targets? Who is the fastest in the class? How could we make this game more interesting?



Some programming challenges

- Have the target alternate colors on click
- Pick a **random** color for the background
- Add another target
- Add a good target and a bad target
- Have the target move up and down



That should wrap up day 1. Feel free to supplement with a Kahoot or extra programming challenges. A good website for Python challenges is https://codingbat.com/python.



## Day 2: Getting Comfortable with PyGame

### Adding Movement

Keeping our code from yesterday, lets add another rectangle that will be our player.



```python
import pygame
import random

pygame.init()

win = pygame.display.set_mode((800,700))
RED = (255,0,0)
GREEN = (0, 255,0)
rect = pygame.Rect(0,0,100,100)

player = pygame.Rect(0,0,50,50) # NEW

font = pygame.font.Font("helvetica", 24)
print(font)
score = 0
    
start_ms =pygame.time.get_ticks() # the time at the start of the game

running = True

while running:
    for event in pygame.event.get(): # check each events
        if event.type == pygame.MOUSEBUTTONDOWN: # if it is a mousedown event...
            pos = pygame.mouse.get_pos()
            if rect.collidepoint((pos[0], pos[1])):
                rect.x = random.randint(0, 800 - player.width)
                rect.y = random.randint(0, 700 - player.height)
                score += 1
                
                if score == 30:
                    running = False

    current_ms = pygame.time.get_ticks() # the time right now
    elapsed_ms = current_ms - start_ms
    elapsed_seconds = elapsed_ms / 1000 # the current time in seconds
    score_text = font.render("Score: " + str(score), True, (0,0,0))
    timer_text = font.render("Time: " + str(elapsed_seconds), True, (0,0,0))
       
    pygame.time.delay(10)
    win.fill((255,255,255))
    win.blit(score_text, (0,0))
    win.blit(timer_text, (500,0))

    pygame.draw.rect(win, RED, rect
                     
    pygame.draw.rect(win, GREEN, player) # NEW!

    pygame.display.update() 
    
    
win.fill(GREEN)
win_text = font.render("You win!!", True, (0,0,0))
win.blit(win_text, (700/2,800/2))
win.blit(score_text, (0,0))
win.blit(timer_text, (500,0))
pygame.display.update() 

pygame.quit()

# much better :)
```



Now we can see our green player. Lets make it move:



Add this section to our event loop 



```python
        if event.type == pygame.KEYDOWN:
            if event.key == pygame.K_UP:
                player.y -= 1
            elif event.key == pygame.K_DOWN:
                player.y += 1
            elif event.key == pygame.K_LEFT:
                player.x -= 1
            elif event.key == pygame.K_RIGHT:
                player.x += 1
```



This will handle the event when a key is pressed



Full code:



```python
import pygame
import random

pygame.init()

win = pygame.display.set_mode((800,700))
RED = (255,0,0)
GREEN = (0, 255,0)
rect = pygame.Rect(0,0,100,100)

player = pygame.Rect(0,0,50,50) # NEW

font = pygame.font.Font("helvetica", 24)
print(font)
score = 0
    
start_ms =pygame.time.get_ticks() # the time at the start of the game

running = True

while running:
    for event in pygame.event.get(): # check each events
        if event.type == pygame.MOUSEBUTTONDOWN: # if it is a mousedown event...
            pos = pygame.mouse.get_pos()
            if rect.collidepoint((pos[0], pos[1])):
                rect.x = random.randint(0, 800 - player.width)
                rect.y = random.randint(0, 700 - player.height)
                score += 1
                if score == 30:
                    running = False
        if event.type == pygame.KEYDOWN:
            if event.key == pygame.K_UP:
                player.y -= 1
            elif event.key == pygame.K_DOWN:
                player.y += 1
            elif event.key == pygame.K_LEFT:
                player.x -= 1
            elif event.key == pygame.K_RIGHT:
                player.x += 1
                
                
    current_ms = pygame.time.get_ticks() # the time right now
    elapsed_ms = current_ms - start_ms
    elapsed_seconds = elapsed_ms / 1000 # the current time in seconds
    score_text = font.render("Score: " + str(score), True, (0,0,0))
    timer_text = font.render("Time: " + str(elapsed_seconds), True, (0,0,0))
       
    pygame.time.delay(10)
    win.fill((255,255,255))
    win.blit(score_text, (0,0))
    win.blit(timer_text, (500,0))

    pygame.draw.rect(win, RED, rect)
    
    pygame.draw.rect(win, GREEN, player)

    pygame.display.update() 
    
    
win.fill(GREEN)
win_text = font.render("You win!!", True, (0,0,0))
win.blit(win_text, (700/2,800/2))
win.blit(score_text, (0,0))
win.blit(timer_text, (500,0))
pygame.display.update() 

pygame.quit()

# much better :)
```





This works, but you will notice that the player will not move if you hold down the buttons. It only works when the key is hit the first time. This is because the keydown event only fires on the frame that the key is hit, not the subsequent frames. Lets make a collection that keeps track of the keys that are currently held.



First, lets add a **set**:

```python
keys_down = set()

# a set is just like a list!
# the only difference is that a list can have duplicates, but a set cannot
# a set makes more sense for this case, because you could not have two of 
# the same key held down
```



Now, lets attach our keydown event:



```python
        if event.type == pygame.KEYDOWN:
            keys_down.add(event.key)
```

This will add the key that was pressed into our set



Next, add an event that will remove that key from the set when it is released:

**Note: Also check that the key is already in the set before you try to remove it**

```python
        if event.type == pygame.KEYUP and event.key in keys_down:
            keys_down.remove(event.key)
```

Now our set should always contain the keys that are held down. Lets use that information to make us move!



```python
            
    if pygame.K_UP in keys_down:
        player.y -= 1
    if pygame.K_DOWN in keys_down:
        player.y += 1
    if pygame.K_LEFT in keys_down:
        player.x -= 1
    if pygame.K_RIGHT in keys_down:
        player.x += 1
```



And putting it all together:



```python
import pygame
import random

pygame.init()

win = pygame.display.set_mode((800,700))
RED = (255,0,0)
GREEN = (0, 255,0)
rect = pygame.Rect(0,0,100,100)

player = pygame.Rect(0,0,50,50) # NEW

font = pygame.font.Font("helvetica", 24)
print(font)
score = 0
    
start_ms =pygame.time.get_ticks() # the time at the start of the game

running = True

keys_down = set()

while running:
    for event in pygame.event.get(): # check each events
        if event.type == pygame.MOUSEBUTTONDOWN: # if it is a mousedown event...
            pos = pygame.mouse.get_pos()
            if rect.collidepoint((pos[0], pos[1])):
                rect.x = random.randint(0, 800 - player.width)
                rect.y = random.randint(0, 700 - player.height)
                score += 1
                if score == 30:
                    running = False
        if event.type == pygame.KEYDOWN:
            keys_down.add(event.key)
        if event.type == pygame.KEYUP and event.key in keys_down:
            keys_down.remove(event.key)
            
    if pygame.K_UP in keys_down:
        player.y -= 1
    if pygame.K_DOWN in keys_down:
        player.y += 1
    if pygame.K_LEFT in keys_down:
        player.x -= 1
    if pygame.K_RIGHT in keys_down:
        player.x += 1

                
    current_ms = pygame.time.get_ticks() # the time right now
    elapsed_ms = current_ms - start_ms
    elapsed_seconds = elapsed_ms / 1000 # the current time in seconds
    score_text = font.render("Score: " + str(score), True, (0,0,0))
    timer_text = font.render("Time: " + str(elapsed_seconds), True, (0,0,0))
       
    pygame.time.delay(10)
    win.fill((255,255,255))
    win.blit(score_text, (0,0))
    win.blit(timer_text, (500,0))

    pygame.draw.rect(win, RED, rect)
    
    pygame.draw.rect(win, GREEN, player)

    pygame.display.update() 
    
    
win.fill(GREEN)
win_text = font.render("You win!!", True, (0,0,0))
win.blit(win_text, (700/2,800/2))
win.blit(score_text, (0,0))
win.blit(timer_text, (500,0))
pygame.display.update() 

pygame.quit()

# much better :)
```

Now we have smooth movement. Lets turn our speed into a variable so we can change it on the fly.

```python
speed = 5
```

```python
    if pygame.K_UP in keys_down:
        player.y -= speed
    if pygame.K_DOWN in keys_down:
        player.y += speed
    if pygame.K_LEFT in keys_down:
        player.x -= speed
    if pygame.K_RIGHT in keys_down:
        player.x += speed
```

Finally, lets change the logic from yesterdays game to collide with our new player rectangle instead of our mouse pointer:



```python
   
    if rect.colliderect(player):
        rect.x = random.randint(0, 800 - player.width)
        rect.y = random.randint(0, 700 - player.height)
        score += 1
        if score == 30:
            running = False
```

Finished code:



```python
import pygame
import random

pygame.init()

win = pygame.display.set_mode((800,700))
RED = (255,0,0)
GREEN = (0, 255,0)
rect = pygame.Rect(0,0,100,100)

player = pygame.Rect(0,0,50,50) # NEW

font = pygame.font.Font("helvetica", 24)
print(font)
score = 0
    
start_ms =pygame.time.get_ticks() # the time at the start of the game

running = True

speed = 5

keys_down = set()

while running:
    for event in pygame.event.get(): # check each events
        if event.type == pygame.KEYDOWN:
            keys_down.add(event.key)
        if event.type == pygame.KEYUP and event.key in keys_down:
            keys_down.remove(event.key)
            
    if pygame.K_UP in keys_down:
        player.y -= speed
    if pygame.K_DOWN in keys_down:
        player.y += speed
    if pygame.K_LEFT in keys_down:
        player.x -= speed
    if pygame.K_RIGHT in keys_down:
        player.x += speed
        
    if rect.colliderect(player):
        rect.x = random.randint(0, 800 - player.width)
        rect.y = random.randint(0, 700 - player.height)
        score += 1
        if score == 30:
            running = False

                
    current_ms = pygame.time.get_ticks() # the time right now
    elapsed_ms = current_ms - start_ms
    elapsed_seconds = elapsed_ms / 1000 # the current time in seconds
    score_text = font.render("Score: " + str(score), True, (0,0,0))
    timer_text = font.render("Time: " + str(elapsed_seconds), True, (0,0,0))
       
    pygame.time.delay(10)
    win.fill((255,255,255))
    win.blit(score_text, (0,0))
    win.blit(timer_text, (500,0))

    pygame.draw.rect(win, RED, rect)
    
    pygame.draw.rect(win, GREEN, player)

    pygame.display.update() 
    
    
win.fill(GREEN)
win_text = font.render("You win!!", True, (0,0,0))
win.blit(win_text, (700/2,800/2))
win.blit(score_text, (0,0))
win.blit(timer_text, (500,0))
pygame.display.update() 

pygame.quit()

# much better :)
```

