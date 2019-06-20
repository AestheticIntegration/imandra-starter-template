# Imandra Starter Template

This repository contains a suggested layout for an Imandra project to support the following workflows:

* Developing a pure-IML model with the Imandra Commander REPL.
* Developing an OCaml program which uses the pure model directly, using `dune` to compile a fast native executable.
* An automated test runner to run verification goals over the IML model, suitable for CI/CD.

## Prerequisites

- A working [Imandra installation](https://docs.imandra.ai/imandra-docs/notebooks/installation-simple/)


## Project layout

* `./src-iml/` contains pure IML (Imandra Modelling Langauge - a subset of OCaml) code. All the code to be reasoned about should go here.
* `./src-ocaml/` contains any OCaml code. This could be your CLI tool, web server, etc. The code here can use the model code defined in `./src-iml/`.
* `./test-vgs/` contains the automated script for running verification goals.


## Model development with Imandra

```
$ cd src-iml
$ imandra-repl
...
# #use "load.iml";;
...
# Gauss.sum_integers_up_to 10;;
- : Z.t = 55
# verify Gauss.gauss_theorem [@@auto];;
[✓] Theorem proved.
#
```


## OCaml development

```
$ make setup
$ make run
```

## Verification goals

```
$ make test
```
