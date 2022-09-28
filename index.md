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

# Introdução à programação em um contexto visual
> com Python e Processing, usando a biblioteca [py5](https://py5.ixora.io)

```{code-cell} ipython3
import time

import py5
import py5_tools
```

```{code-cell} ipython3
def setup():
    py5.size(500, 500, py5.P3D)
```

Any user-defined functions must come before their use:

```{code-cell} ipython3
def my_box(x, y, z, tamanho):
    py5.push()
    py5.translate(x, y, z)
    py5.box(tamanho)
    py5.pop()
```

```{code-cell} ipython3
def draw():
    py5.translate(250, 250, 0)
    py5.background(255)
    py5.rotate_y(mouse_x / 4.0) # 22.5 graus
    for x in range(-100, 101, 50):
        for y in range(-100, 101, 50):
            for z in range(-100, 101, 50):
                py5.fill(100 + x, 100 + y, 100 + z)
                my_box(x, y, z, 25 + 25 * sin(x + y + frame_count / 20.0))
```

```{code-cell} ipython3
py5.run_sketch()  # chama o setup() uma vez, e o draw() em repetição.
```

```{code-cell} ipython3
:tags: [remove-input]
time.sleep(3)
py5_tools.screenshot()
```

Se você está executando esse notebook no mybinder.org, pode remover o comentário
na próxima célula para executar o comando de forma interativa.

```{code-cell} ipython3
# portal = py5_tools.sketch_portal(quality=75, scale=1.0)
```

