---
jupytext:
  formats: ipynb,md:myst
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.13
    jupytext_version: 1.14.0
kernelspec:
  display_name: Python 3 (ipykernel)
  language: python
  name: python3
---

# Imported mode

```{code-cell} ipython3
from itertools import product
from random import randint

hor = lambda x, y, w, h: random(0, 2.5) < 1 - cos(x / w * TWO_PI)
ver = lambda x, y, w, h: random(0, 2.5) < 1 - cos(y / h * TWO_PI)    

def setup():
    size(960, 960)
    stroke_weight(1.5)
    # noSmooth()
    #size(512 + 256 + 128, 512 + 256 + 128)
    no_loop()
    
def grid(xo, yo, w):
    qw = w // 4
    for i in range(4):
        x = xo + i * qw
        for j in range(4):
            y = yo + j * qw
            r = randint(1, 3)
            if qw > 32 and r == 1:
                grid(x, y, qw)
            elif r == 2:
                stroke(0, 100, 200); stroke(200)
                region(x, y, qw, qw, hor)
            else:
                stroke(100, 0, 200)#; stroke(100)
                region(x, y, qw, qw, ver)
def draw():
    scale(0.5)
    background(32)
    grid(0, 0, width * 2)

                
def region(xo, yo, w, h, rule):
    grid = product(range(xo, xo + w), range(yo, yo + h))
    for x, y in grid:
        if rule(x - xo, y - yo, w, h):
            point(x, y)
            
```

```{code-cell} ipython3
run_sketch()
```
