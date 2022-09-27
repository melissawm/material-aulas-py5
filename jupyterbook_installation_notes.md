# how to set up this repo

Context: This is an attempt at making a jupyter{book} version of my `material-aulas` teaching repository

Goal: Make class materials that can profit from Thebe/MyBinder.org execution.

Work in progress. Published as proof of concept here: https://abav.lugaralgum.com/material-aulas-py5/

## Recording steps taken so far (work in progress)

- 2021-09-18 First attempt, lots of help from @hx2A, first jupyter book working page!
- 2021-09-19 Cleaning up the steps needed (removing some wrong turns taken)

### Steps

- Cloned requirements and settings from https://py5.ixora.io Jupyter Book docs
   - This repo starts as a hollowed out clone of the `py5` doc
- Reading https://jupyterbook.org/start/overview.html
   - Installed `jupyter-book` in my `pycoding` conda env that I also use to run `py5`
   - Installed `ghp-import`
   - Created a `gh-pages` branch in this repo
   - Do not change the `_config.yml` to point to the gh-pages branch, keep it looking for `main` (where the binder folder is)
   - For GitHub token authentication, now using [GitHub CLI auth login](https://cli.github.com/manual/gh_auth_login), to install follow https://github.com/cli/cli#installation
   - Rebuild TOC with `jupyter-book toc from-project / > _toc.yml`
   - Use `jupyter-book build /` 
   - Use `ghp-import -n -p -f _build/html` command to rebuild the publishing `gh-pages` branch, needs `push` afterwards!

TO DO:
   - [ ] Work out why the images are broken :(
   - [ ] Study how to use a makefile & pre- and post-processing scripts
   - [X] install additional `py5bot` kernel to use "static mode" examples. [Instructions here](https://py5.ixora.io/content/install.html#jupyter-notebook-kernels).
   
### How to pair jupyter notebooks with md

1. Install `jupytext`
2. Run `jupytext --set-formats ipynb,myst imported_mode.ipynb`