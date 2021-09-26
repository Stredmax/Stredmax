from ursina import *
from ursina.prefabs.first_person_controller\
  import FirstPersonController

app = Ursina()



groud = Entity(model='plane',
              texture= 'grass',
              collider = 'mesh',
              scale=(100000,1,10
                     ))
player = FirstPersonController()
Sky()
mctest = Entity(model='cube',
               color = color.azure,
               collider='sphere',
               position = (5,0.5,1),
               scale = (1,50,10000))
mctest2 = Entity(model='cube',
               color = color.azure,
               collider='sphere',
               position = (-2,0.5,0),
               scale = (1,50,10000))

blocks =[]
directions = []
from random import uniform
for i in range(17):
  r = uniform(-2,2)
  block = Entity(
    position=(r, 1+i , 3+i*5),
    model='cube',
    texture='white_cube',
    color=color.violet,
    scale=(3, 0.5, 3),
    collider='box',
  )
  blocks.append(block)
  if r < 0:
    directions.append(1)
  else:
    directions.append(-1)
  blocks.append(block)
def update():
    i = 0
    for block in blocks:
      if abs (block.x)> 5:
            directions[i] *= -1
      i = i + 1
empty = Entity(model='sphere',
               color = color.yellow,
               scale = (1 , 1 ,1),
               position = (0,0,0),
               )

app.run()
