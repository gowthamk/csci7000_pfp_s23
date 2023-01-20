---
layout: page
title: 
permalink: /resources/
---

We make use of Jupyter notebooks with OCaml kernel in this course. Following installation instructions should work on Unix-based systems (Linux and Mac) and Windows with [WSL](https://learn.microsoft.com/en-us/windows/wsl/install) installed. 

1. [Opam](https://opam.ocaml.org/) is the official package manager for OCaml. You can use Opam to install OCaml. To install opam:
```
bash -c "sh <(curl -fsSL https://raw.githubusercontent.com/ocaml/opam/master/shell/install.sh)"
``` 
2. Set Opam env: 
```
eval $(opam env)
```
3.Update Opam repositories:
```
opam update
```
4. Install OCaml base compiler version 4.12.1 (You may use any version >= 4.08 and < 4.15):
```
opam switch create 4.12.1
```
5. Install Jupyter via python's package manager pip:
```
pip install jupyterlab
```
6. Install [ocaml-jupyter](https://akabe.github.io/ocaml-jupyter/) package:
```
opam install jupyter
```
7. Configure `ocamlinit`:
```
grep topfind ~/.ocamlinit || echo '#use "topfind";;' >> ~/.ocamlinit  # For using '#require' directive
grep Topfind.log ~/.ocamlinit || echo 'Topfind.log:=ignore;;' >> ~/.ocamlinit  # Suppress logging of topfind (recommended but not necessary)
ocaml-jupyter-opam-genspec
```
8. Install OCaml kernel for Jupyter (may need `sudo` sometimes):
```
jupyter kernelspec install --name "ocaml-jupyter-$(opam var switch)" "$(opam var share)/jupyter" 
```
9. Type `jupyter-lab` and press enter. A browser page with Jupyter notebook UI should open with an option to create OCaml notebooks.
